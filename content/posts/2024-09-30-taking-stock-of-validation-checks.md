---
title: "Taking Stock of Validation Checks"
date: 2024-09-30
tags: ["mls", "openmls", "validation", "rfc9420"]
notoc: true
author: "Jan Winkelmann"
---

When implementing cryptographic protocols, probably the most important thing is to not forget validating all inputs. Failing to do so can lead to inadvertant leakage of private information, state corruption, impersonation attacks... all kinds of vulnerabilities.

To give an example, you might remember [the "goto fail" vulnerability], a bug in the TLS implementation used in iOS. Here, the verification function of signatures sent along with the `ServerKeyExchange` message, which ties the server identity to the transcript and ephemeral key material. Due to a hard-to-spot slipup, it returned success early and never really checked the signature, which would allow an attacker to man-in-the-middle the connection. While in this case they didn't just _forget_ to do the check, it does demonstrate why these checks are important.

In the context of MLS, consider what would happen if we didn't do the [check][FramedContent Signature Validation Check RFC] that validates the signature over `FramedContent` objects, which wrap the relevant parts of MLS messages to provide authentication. An attacker could change the sender field of `FramedContent` to a different member and we wouldn't notice, because we don't get an error when trying to validate the signature with that other member's public key.

This is a drastic example of course, and it's unlikely one would forget to implement this particular check. However, MLS is a large complex protocol and there are a lot of these checks in the MLS RFC that need to be done by OpenMLS (we counted 50 so far). The good news is that the RFC lays them all out. The bad news is that they are somewhat scattered across the document and there is no good overview.

In addition, the way the RFC abstracts away delivery and authentication also means that it is not always obvious whether a check would need to happen inside the client implementation (e.g. [OpenMLS]), the Delivery Service or the Authentication Service. This means that understanding whether a check has to be done inside or outside of OpenMLS is not always straightforward. And while in theory it is enough that all the checks are in the code, in practice it's also important to test that all the checks are being performed, so they don't accidentally get removed or circumvented in a refactor years later.

We knew we needed some sort of list or database of checks. This raised two questions: What sort of data do we want to keep, and how do we structure it? What is the format of the list?

# The Data We Need

Let's look at the data first. The main information we want to capture are checks, and each check consists of an ID, a text quoted from and linking to the RFC text, and some way of referring to the code where the check is implemented and tested. We are still experimenting with that last part, but for now we have settled on keeping the modpath of the function we refer to, as well as a permalink to the specific part of the code. We also mention the check ID in the code, so that can also be searched for.

Most validation checks belong to a group of checks that are performed together, and we would like to maintain that grouping, so each "check" is part of a "check set". The check set also provides some context for the check. So a check set consists of another RFC quote (with link) and a list of checks.

# The Format We Keep It In

As for the formats, we wanted a uniform structure, and we want it to be relatively simple to update. And, maybe most importantly, we want to be able to look at and understand what we are missing. Let's first look at what we thought didn't work very well:

- A large text file (or md/html file, or a google doc) that we manually edit to render to a nice visual overview seems difficult to maintain
- The fact that some of the items each check carries are lists, makes using anything that resembles spreadsheets or CSV-files pretty awkward to use

The obvious third choice would be a JSON file that contains an array of check sets. We could then write a tool that generates an HTML file providing an overview over the checks from the JSON. However, this would mean everything is in a single large file, and modifying that by hand seems pretty error-prone. YAML might be a bit nicer to write, but is also error-prone. It would be nice if we had a language that was a bit like JSON, but nicer to write and with strong types, to catch errors early.

I had heard of the [Dhall language] before and while it always sounded interesting, I never had use for it. It's a small programming language that mostly seems to be intended for generating config files. The idea is that it enforces termination and handling of all possible inputs. This means it can't hang or error out because the program doesn't handle an edge case. This seemed like an interesting option, and the fact that one of the main features of Dhall is that it can easily produce a JSON representation of the contained data, it would be easy to pivot to a different format if Dhall would turn out to not work well for us.

We followed a pretty boring structure: In one file we define the domain types (e.g. `Check`, `CheckSet`, ), in another file we generate HTML for the domain types. We also have a folder that contains one check set per file and a file that bundles all the check sets into a single place that can be processed. These all behave a bit like libraries. We then have a file that imports the check sets and the code generating the HTML and returns a string containing the dashboard, which looks like [this](https://validation.openmls.tech).

# An example

Let's go back to the [check][FramedContent Signature Validation Check RFC] we looked at earlier. The check is part of a [section][Commit Validation Section RFC] that describes what need to be checked when validating a commit. In our dashboard, we made that whole section a [check set][Commit Validation Check Set Dashboard], and at the time of writing it looks like this:

![](https://md.cryspen.com/uploads/upload_76ae7721e9602891a60a302b0f2eaa63.png)

The check set starts with quotes from the RFC and links to the places in the RFC that the quotes come from. It is followed by a table of checks. Each check has an identifier for the check, if we want to reference it in text. We then have the text from the RFC and a link to the specific paragraph of the RFC that contains the text. In the rightmost column we have a link to a search for the check ID in the OpenMLS repository on Github, some notes as well as references to the implementation of the check and tests for the check (if available). Links into the code show modpath of the linked function but link to the permalink to the specific lines of code where a check is implemented or tested. The pilcrows (¶) link to the check set or check itself, to make it easier to link it elsewere.

For example, the [check set for commits][Commit Validation Check Set Dashboard] contains check [valn1203][FramedContent Signature Validation Check Dashboard], which has a link to the RFC at exactly the [right place][FramedContent Signature Validation Check RFC], as well as links to the [places][code link 1] [where][code link 2] the check is implemented. We don't have links to where we test that the check is done correctly, that's why there are no test refs, and that's also why the status of that check is _Partial_ instead of _Complete_.

The nice thing about having the data in a machine-readable format is that we can also do other things with it. For example, we generate a bookmarklet (a little snippet of JS that is stored in a bookmark) that when it is clicked while browsing the RFC, it highlights all the parts of the RFC that have already been captured in the database. This helps with searching the RFC for checks we missed. In the future, we could also generate a dashboard that has its focus on the checks that are not completely implemented or tested yet. Try it, it's [here](https://validation.openmls.tech/bookmarklet.html).

# Learnings

Overall, Dhall works pretty well for us. There are some warts, such as not-very-helpful syntax error messages, the linter sometimes removing comments as well as documentation sometimes being a bit confusing and spread across several places, but it was reasonably easy to set up something that works and does the job reliably.

Another thing we haven't completely figured out yet is how to best link into the code. Linking to source code lines at specific commits means we can link to specific lines, but also that links will quickly go out-of-date. Using Rust modpaths is more stable, in the sense that the path correctly identifies a piece of code across commits (unless you refactor). On the other hand, they are more granular (you can only reference functions) and there is no tooling for using them as hyperlinks. Also, it's unclear how to deal with aliases and visibility. Because we were not sure what the right thing to do is here, we do both for now. On top of that, we added a link to search the source code for the ID of the check, to quickly find mentions in comments and function names. However, this requires being logged into Github and only works on the current main branch.

# Next Steps

But now, the real work starts: Double-checking that we captured all the checks that we need to do, and making sure that we actually do all the checks, and properly test them. And while all that is going on, we are getting a better understanding of what we really need and how we can improve the dashboard.

We started adding [missing checks](https://github.com/openmls/openmls/pull/1655) and will continue doing so until all checks are implemented and tested.

In future we will also prove that all required checks have been performed. Stay tuned for more on this soon.

[the "goto fail" vulnerability]: https://www.imperialviolet.org/2014/02/22/applebug.html
[openmls]: https://github.com/openmls/openmls
[dhall language]: https://dhall-lang.org/

[Commit Validation Section RFC]: https://www.rfc-editor.org/rfc/rfc9420.html#section-12.4.2
[Commit Validation Check Set Dashboard]: https://validation.openmls.tech/#cs12
[FramedContent Signature Validation Check RFC]: https://www.rfc-editor.org/rfc/rfc9420.html#section-12.4.2-2.3
[FramedContent Signature Validation Check Dashboard]: https://validation.openmls.tech/#valn1203
[code link 1]: https://github.com/openmls/openmls/blob/5067034708f2332b0dfd8d7d28eb6618fd38f4c7/openmls/src/group/mls_group/processing.rs#L273-L274
[code link 2]: https://github.com/openmls/openmls/blob/5067034708f2332b0dfd8d7d28eb6618fd38f4c7/openmls/src/group/public_group/process.rs#L203-L204
