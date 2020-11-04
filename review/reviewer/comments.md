# How to Write Code Review Comments



## Summary

-   Be kind.
-   Explain your reasoning.
-   Balance giving explicit directions with just pointing out problems and
    letting the developer decide.
-   Encourage developers to simplify code or add code comments instead of just
    explaining the complexity to you.

## Courtesy

In general, it is important to be
[courteous and respectful](https://chromium.googlesource.com/chromium/src/+/master/docs/cr_respect.md)
while also being very clear and helpful to the developer whose code you are
reviewing. One way to do this is to be sure that you are always making comments
about the *code* and never making comments about the *developer*. You don't
always have to follow this practice, but you should definitely use it when
saying something that might otherwise be upsetting or contentious. 

For example:

Bad: "Why did **you** use threads here when there's obviously no benefit to be
gained from concurrency?"

Good: "The concurrency model here is adding complexity to the system without any
actual performance benefit that I can see. Because there's no performance
benefit, it's best for this code to be single-threaded instead of using multiple
threads."

## Explain Why {#why}

One thing you'll notice about the "good" example from above is that it helps the
developer understand *why* you are making your comment. You don't always need to
include this information in your review comments, but sometimes it's appropriate
to give a bit more explanation around your intent, the best practice you're
following, or how your suggestion improves code health.

## Giving Guidance {#guidance}

**In general it is the developer's responsibility to fix a PR, not the
reviewer's.** You are not required to do detailed design of a solution or write
code for the developer.

This doesn't mean the reviewer should be unhelpful, though. In general you
should strike an appropriate balance between pointing out problems and providing
direct guidance. Pointing out problems and letting the developer make a decision
often helps the developer learn, and makes it easier to do code reviews. It also
can result in a better solution, because the developer is closer to the code
than the reviewer is.

However, sometimes direct instructions, suggestions, or even code are more
helpful. The primary goal of code review is to get the best PR possible. A
secondary goal is improving the skills of developers so that they require less
and less review over time.

Remember that people learn from reinforcement of what they are doing well and
not just what they could do better. If you see things you like in the PR,
comment on those too! Examples: developer cleaned up a messy algorithm, added
exemplary test coverage, or you as the reviewer learned something from the PR.
Just as with all comments, include [why](#why) you liked something, further
encouraging the developer to continue good practices.

## Accepting Explanations {#explanations}

If you ask a developer to explain a piece of code that you don't understand,
that should usually result in them **rewriting the code more clearly**.
Occasionally, adding a comment in the code is also an appropriate response, as
long as it's not just explaining overly complex code.

**Explanations written only in the code review tool are not helpful to future
code readers.** They are acceptable only in a few circumstances, such as when
you are reviewing an area you are not very familiar with and the developer
explains something that normal readers of the code would have already known.

Next: [Handling Pushback in Code Reviews](pushback.md)
