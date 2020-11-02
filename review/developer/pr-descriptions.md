# Writing Good PR Descriptions



A PR description is a public record of **what** change is being made and **why**
it was made. It will become a permanent part of our version control history, and
will possibly be read by hundreds of people other than your reviewers over the
years.

Future developers will search for your PR based on its description. Someone in
the future might be looking for your change because of a faint memory of its
relevance but without the specifics handy. If all the important information is
in the code and not the description, it's going to be a lot harder for them to
locate your PR.

## First Line {#firstline}

*   Short summary of what is being done.
*   Complete sentence, written as though it was an order.
*   Follow by empty line.

The **first line** of a PR description should be a short summary of
*specifically* **what** *is being done by the PR*, followed by a blank line.
This is what appears in version control history summaries, so it should be
informative enough that future code searchers don't have to read your PR or its
whole description to understand what your PR actually *did* or how it differs
from other CLs. That is, the first line should stand alone, allowing readers to
skim through code history much faster.

Try to keep your first line short, focused, and to the point. The clarity and
utility to the reader should be the top concern.

By tradition, the first line of a PR description is a complete sentence, written
as though it were an order or command (an imperative sentence). For example, say
\"**Delete** the FizzBuzz RPC and **replace** it with the new system." instead
of \"**Deleting** the FizzBuzz RPC and **replacing** it with the new system."
You don't have to write the rest of the description as an imperative sentence,
though.

## Body is Informative {#informative}

The rest of the description should be informative. It might include a brief
description of the problem that's being solved, and why this is the best
approach. If there are any shortcomings to the approach, they should be
mentioned. If relevant, include background information such as bug numbers,
benchmark results, and links to design documents.

If you include links to external resources consider that they may not be visible
to future readers due to access restrictions or retention policies. Where
possible include enough context for reviewers and future readers to understand
the PR.

Even small PRs deserve a little attention to detail. Put the PR in context.

## Bad PR Descriptions {#bad}

"Fix bug" is an inadequate PR description. What bug? What did you do to fix it?
Other similarly bad descriptions include:

-   "Fix build."
-   "Add patch."
-   "Moving code from A to B."
-   "Phase 1."
-   "Add convenience functions."
-   "Kill weird URLs."

Some of those are real PR descriptions. Although short, they do not provide
enough useful information or context for the change.

## Good PR Descriptions {#good}

Here are some examples of good descriptions.

### Functionality change

Example:

> rpc: remove size limit on RPC server message freelist.
>
> Servers like FizzBuzz have very large messages and would benefit from reuse.
> Make the freelist larger, and add a goroutine that frees the freelist entries
> slowly over time, so that idle servers eventually release all freelist
> entries.

The first few words describe what the PR actually does. The rest of the
description talks about the problem being solved, why this is a good solution,
and a bit more information about the specific implementation.

### Refactoring

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

The first line describes what the PR does and how this is a change from the
past. The rest of the description talks about the specific implementation, the
context of the PR, that the solution isn't ideal, and possible future direction.
It also explains *why* this change is being made.

### Small PR that needs some context

Example:

> Create a Python3 build rule for status.py.
>
> This allows consumers who are already using this in Python3 to depend on a
> rule that is next to the original status build rule instead of somewhere in
> their own tree. It encourages new consumers to use Python3 if they can,
> instead of Python2, and significantly simplifies some automated build file
> refactoring tools being worked on currently.

The first sentence describes what's actually being done. The rest of the
description explains *why* the change is being made and gives the reviewer a lot
of context.

## Generated PR descriptions

Some PRs are generated by tools. Whenever possible, their descriptions should
also follow the advice here. That is, their first line should be short, focused,
and stand alone, and the PR description body should include informative details
that help reviewers and future code searchers understand each PR's effect.

## Review the description before submitting the PR

PRs can undergo significant change during review. It can be worthwhile to review
a PR description before submitting the PR, to ensure that the description still
reflects what the PR does.

Next: [Small CLs](small-cls.md)
