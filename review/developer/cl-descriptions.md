# Writing good CL descriptions



A CL description is a public record of change, and it is important that it
communicates:

1.  **What** change is being made? This should summarize the major changes such
    that readers have a sense of what is being changed without needing to read
    the entire CL.

1.  **Why** are these changes being made? What contexts did you have as an
    author when making this change? Were there decisions you made that aren't
    reflected in the source code? etc.

The CL description will become a permanent part of our version control history
and will possibly be read by hundreds of people over the years.

Future developers will search for your CL based on its description. Someone in
the future might be looking for your change because of a faint memory of its
relevance but without the specifics handy. If all the important information is
in the code and not the description, it's going to be a lot harder for them to
locate your CL.

And then, after they find the CL, will they be able to understand *why* the
change was made? Reading source code may reveal what the software is doing but
it may not reveal why it exists, which can make it harder for future developers
to know whether they can move
[Chesterton's fence](https://abseil.io/resources/swe-book/html/ch03.html#understand_context).

A well-written CL description will help those future engineers -- sometimes,
including yourself!

## First Line {#first-line}

<a id="firstline"></a> <!-- Keep previous permalink to avoid breaking old links. -->

*   Short summary of what is being done.
*   Complete sentence, written as though it was an order.
*   Follow by empty line.

The **first line** of a CL description should be a short summary of
*specifically* **what** *is being done by the CL*, followed by a blank line.
This is what appears in version control history summaries, so it should be
informative enough that future code searchers don't have to read your CL or its
whole description to understand what your CL actually *did* or how it differs
from other CLs. That is, the first line should stand alone, allowing readers to
skim through code history much faster.

Try to keep your first line short, focused, and to the point. The clarity and
utility to the reader should be the top concern.

By tradition, the first line of a CL description is a complete sentence, written
as though it were an order (an imperative sentence). For example, say
\"**Delete** the FizzBuzz RPC and **replace** it with the new system." instead
of \"**Deleting** the FizzBuzz RPC and **replacing** it with the new system."
You don't have to write the rest of the description as an imperative sentence,
though.

## Body is Informative {#informative}

The [first line](#first-line) should be a short, focused summary, while the rest
of the description should fill in the details and include any supplemental
information a reader needs to understand the changelist holistically. It might
include a brief description of the problem that's being solved, and why this is
the best approach. If there are any shortcomings to the approach, they should be
mentioned. If relevant, include background information such as bug numbers,
benchmark results, and links to design documents.

If you include links to external resources consider that they may not be visible
to future readers due to access restrictions or retention policies. Where
possible include enough context for reviewers and future readers to understand
the CL.

Even small CLs deserve a little attention to detail. Put the CL in context.

## Bad CL Descriptions {#bad}

"Fix bug" is an inadequate CL description. What bug? What did you do to fix it?
Other similarly bad descriptions include:

-   "Fix build."
-   "Add patch."
-   "Moving code from A to B."
-   "Phase 1."
-   "Add convenience functions."
-   "kill weird URLs."

Some of those are real CL descriptions. Although short, they do not provide
enough useful information.

## Good CL Descriptions {#good}

Here are some examples of good descriptions.

### Functionality change {#functionality-change}

Example:

> RPC: Remove size limit on RPC server message freelist.
>
> Servers like FizzBuzz have very large messages and would benefit from reuse.
> Make the freelist larger, and add a goroutine that frees the freelist entries
> slowly over time, so that idle servers eventually release all freelist
> entries.

The first few words describe what the CL actually does. The rest of the
description talks about the problem being solved, why this is a good solution,
and a bit more information about the specific implementation.

### Refactoring {#refactoring}

Example:

> Construct a Task with a TimeKeeper to use its TimeStr and Now methods.
>
> Add a Now method to Task, so the borglet() getter method can be removed (which
> was only used by OOMCandidate to call borglet's Now method). This replaces the
> methods on Borglet that delegate to a TimeKeeper.
>
> Allowing Tasks to supply Now is a step toward eliminating the dependency on
> Borglet. Eventually, collaborators that depend on getting Now from the Task
> should be changed to use a TimeKeeper directly, but this has been an
> accommodation to refactoring in small steps.
>
> Continuing the long-range goal of refactoring the Borglet Hierarchy.

The first line describes what the CL does and how this is a change from the
past. The rest of the description talks about the specific implementation, the
context of the CL, that the solution isn't ideal, and possible future direction.
It also explains *why* this change is being made.

### Small CL that needs some context

Example:

> Create a Python3 build rule for status.py.
>
> This allows consumers who are already using this as in Python3 to depend on a
> rule that is next to the original status build rule instead of somewhere in
> their own tree. It encourages new consumers to use Python3 if they can,
> instead of Python2, and significantly simplifies some automated build file
> refactoring tools being worked on currently.

The first sentence describes what's actually being done. The rest of the
description explains *why* the change is being made and gives the reviewer a lot
of context.

## Using tags {#tags}

Tags are manually entered labels that can be used to categorize CLs. These may
be supported by tools or just used by team convention.

For example:

-   "[tag]"
-   "[a longer tag]"
-   "#tag"
-   "tag:"

Using tags is optional.

When adding tags, consider whether they should be in the [body](#informative) of
the CL description or the [first line](#first-line). Limit the usage of tags in
the first line, as this can obscure the content.

Examples with and without tags:

``` {.good}
// Tags are okay in the first line if kept short.
[banana] Peel the banana before eating.

// Tags can be inlined in content.
Peel the #banana before eating.

// Tags are optional.
Peel the banana before eating.

// Multiple tags are acceptable if kept short.
#banana #apple: Assemble a fruit basket.

// Tags can go anywhere in the CL description.
> Assemble a fruit basket.
>
> #banana #apple
```

``` {.bad}
// Too many tags (or tags that are too long) overwhelm the first line.
//
// Instead, consider whether the tags can be moved into the description body
// and/or shortened.
[banana peeler factory factory][apple picking service] Assemble a fruit basket.
```

## Generated CL descriptions

Some CLs are generated by tools. Whenever possible, their descriptions should
also follow the advice here. That is, their first line should be short, focused,
and stand alone, and the CL description body should include informative details
that help reviewers and future code searchers understand each CL's effect.

## Review the description before submitting the CL

CLs can undergo significant change during review. It can be worthwhile to review
a CL description before submitting the CL, to ensure that the description still
reflects what the CL does.

Next: [Small CLs](small-cls.md)
