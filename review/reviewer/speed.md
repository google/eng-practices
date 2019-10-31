# Speed of Code Reviews



## Why Should Code Reviews Be Fast? {#why}

When code reviews are slow, several things happen:

*   **The velocity of the team as a whole is decreased.** Yes, the individual,
    who doesn't respond quickly to the review, gets other work done. However,
    new features and bug fixes for the rest of the team are delayed by days,
    weeks, or months as each PR waits for review and re-review.
*   **Developers start to protest the code review process.** If a reviewer only
    responds every few days, but requests major changes to the PR each time,
    that can be frustrating and difficult for developers. Often, this is
    expressed as complaints about how "strict" the reviewer is being. If the
    reviewer requests the _same_ substantial changes (changes which really do
    improve code health) but responds _quickly_ every time the developer makes
    an update, the complaints tend to disappear. **Most complaints about the
    code review process are actually resolved by making the process faster.**
*   **Code health can be impacted.** When reviews are slow, there is increased
    pressure to allow developers to submit PRs that are not as good as they
    could be. Slow reviews also discourage code cleanups, refactorings, and
    further improvements to existing PRs.

## How Fast Should Code Reviews Be? {#fast}

If you are not in the middle of a focused task, **you should do a code review
shortly after it comes in.**

**One business day is the maximum time it should take to respond** to a code
review request (i.e. first thing the next morning).

Following these guidelines means that a typical PR should get multiple rounds of
review (if needed) within a single day.

## Speed vs. Interruption {#interruption}

There is one time where the consideration of personal velocity trumps team
velocity. **If you are in the middle of a focused task, such as writing code,
don't interrupt yourself to do a code review.** Research has shown that it can
take a long time for a developer to get back into a smooth flow of development
after being interrupted. So interrupting yourself while coding is actually
_more_ expensive to the team than making another developer wait a bit for a code
review.

Instead, wait for a break point in your work before you respond to a request for
review. This could be when your current coding task is completed, after lunch,
returning from a meeting, coming back from the microkitchen, etc.

## Fast Responses {#responses}

When we talk about the speed of code reviews, it is the _response_ time that we
are concerned with, as opposed to how long it takes a PR to get through the
whole review and be submitted. The whole process should also be fast, ideally,
but **it's even more important for the _individual responses_ to come quickly
than it is for the whole process to happen rapidly.**

Even if it sometimes takes a long time to get through the entire review
_process_, having quick responses from the reviewer throughout the process
significantly eases the frustration developers can feel with "slow" code
reviews.

If you are too busy to do a full review on a PR when it comes in, you can still
send a quick response that lets the developer know when you will get to it,
suggest other reviewers who might be able to respond more quickly, or
[provide some initial broad comments](navigate.md). (Note: none of this means
you should interrupt coding even to send a response like this&mdash;send the
response at a reasonable break point in your work.)

**It is important that reviewers spend enough time on review that they are
certain their "LGTM" means "this code meets [our standards](standard.md)."**
However, individual responses should still ideally be [fast](#fast).

## Cross-Time-Zone Reviews {#tz}

When dealing with time zone differences(EST vs PST), try to get back to the author when they
are still in the office. If they have already gone home, then try to make sure
your review is done before they get back to the office the next day.

## LGTM With Comments {#lgtm-with-comments}

In order to speed up code reviews, there are certain situations in which a
reviewer should give LGTM/Approval even though they are also leaving unresolved
comments on the PR. This is done when either:

*   The reviewer is confident that the developer will appropriately address all
    the reviewer's remaining comments.
*   The remaining changes are minor and don't _have_ to be done by the
    developer.

The reviewer should specify which of these options they intend, if it is not
otherwise clear.

LGTM With Comments is especially worth considering when the developer and
reviewer are in different time zones and otherwise the developer would be
waiting for a whole day just to get "LGTM, Approval."

## Large PRs {#large}

If somebody sends you a code review that is so large you're not sure when you
will be able to have time to review it, your typical response should be to ask
the developer to
[split the PR into several smaller PRs](../developer/small-cls.md) that build on
each other, instead of one huge PR that has to be reviewed all at once. This is
usually possible and very helpful to reviewers, even if it takes additional work
from the developer.

If a PR *can't* be broken up into smaller PRs, and you don't have time to review
the entire thing quickly, then at least write some comments on the overall
design of the PR and send it back to the developer for improvement. One of your
goals as a reviewer should be to always unblock the developer or enable them to
take some sort of further action quickly, without sacrificing code health to do
so.

## Emergencies

There are also [emergencies](../emergencies.md) where PRs must pass through the
_whole_ review process very quickly, and where the quality guidelines would be
relaxed. However, please see [What Is An Emergency?](../emergencies.md#what) for
a description of which situations actually qualify as emergencies and which
don't.

Next: [How to Write Code Review Comments](comments.md)
