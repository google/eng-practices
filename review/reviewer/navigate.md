# Navigating a CL in review



## Summary

Now that you know [what to look for](looking-for.md), what's the most efficient
way to manage a review that's spread across multiple files?

1.  Does the change make sense? Does it have a good
    [description](../developer/cl-descriptions.md)?
2.  Look at the most important part of the change first. Is it well-designed
    overall?
3.  Look at the rest of the CL in an appropriate sequence.

## Step One: Take a broad view of the change {#step_one}

Look at the [CL description](../developer/cl-descriptions.md) and what the CL
does in general. Does this change even make sense? If this change shouldn't have
happened in the first place, please respond immediately with an explanation of
why the change should not be happening. When you reject a change like this, it's
also a good idea to suggest to the developer what they should have done instead.

For example, you might say "Looks like you put some good work into this, thanks!
However, we're actually going in the direction of removing the FooWidget system
that you're modifying here, and so we don't want to make any new modifications
to it right now. How about instead you refactor our new BarWidget class?"

Note that not only did the reviewer reject the current CL and provide an
alternative suggestion, but they did it *courteously*. This kind of courtesy is
important because we want to show that we respect each other as developers even
when we disagree.

If you get more than a few CLs that represent changes you don't want to make,
you should consider re-working your team's development process or the posted
process for external contributors so that there is more communication before CLs
are written. It's better to tell people "no" before they've done a ton of work
that now has to be thrown away or drastically re-written.

## Step Two: Examine the main parts of the CL {#step_two}

Find the file or files that are the "main" part of this CL. Often, there is one
file that has the largest number of logical changes, and it's the major piece of
the CL. Look at these major parts first. This helps give context to all of the
smaller parts of the CL, and generally accelerates doing the code review. If the
CL is too large for you to figure out which parts are the major parts, ask the
developer what you should look at first, or ask them to
[split up the CL into multiple CLs](../developer/small-cls.md).

If you see some major design problems with this part of the CL, you should send
those comments immediately, even if you don't have time to review the rest of
the CL right now. In fact, reviewing the rest of the CL might be a waste of
time, because if the design problems are significant enough, a lot of the other
code under review is going to disappear and not matter anyway.

There are two major reasons it's so important to send these major design
comments out immediately:

-   Developers often mail a CL and then immediately start new work based on that
    CL while they wait for review. If there are major design problems in the CL
    you're reviewing, they're also going to have to re-work their later CL. You
    want to catch them before they've done too much extra work on top of the
    problematic design.
-   Major design changes take longer to do than small changes. Developers nearly
    all have deadlines; in order to make those deadlines and still have quality
    code in the codebase, the developer needs to start on any major re-work of
    the CL as soon as possible.

## Step Three: Look through the rest of the CL in an appropriate sequence {#step_three}

Once you've confirmed there are no major design problems with the CL as a whole,
try to figure out a logical sequence to look through the files while also making
sure you don't miss reviewing any file. Usually after you've looked through the
major files, it's simplest to just go through each file in the order that
the code review tool presents them to you. Sometimes it's also helpful to read the tests
first before you read the main code, because then you have an idea of what the
change is supposed to be doing.

Next: [Speed of Code Reviews](speed.md)
