# Code Review Process

This is not yet final but this will provide us guidelines on how we do code reviews of our pull requests (PRs). Everyone gets to code review as we wanted to develop a stake or ownership of our codebase. And this is a great opportunity for us to build up our team and learn from one another as we aim to do better with our code. 

“I love code reviews in theory. In practice, they are only as good as the group that’s responsible for conducting them in the right manner. “ - Unknown

## Checklist
1. Provide context about your PR by filling in the information needed in our [PR template](https://github.com/carabao-capital/first-circle-app/blob/master/.github/PULL_REQUEST_TEMPLATE.md). 
2. Make sure to write tests before you open a PR. 

## Code-review Proper

1. After creating a PR, run the slack bot command `@plankbot reviewer for (PR number)` in the #coding channel
to pick your PR's code reviewers. The slack bot command will pick two randomly selected
reviewers - one of them is always going to be a senior product engineer: Vic or Neil.
2. Assign the PR's Asana task to the **non-senior** code reviewer. After that write a comment in the
Asana task with something like "Please code review (tag the **non-senior** code reviewer here)"
3. Ping the code reviewers in Slack if necessary. E.g. urgent shipping of a hotfix
4. Two :+1:'s are needed before the code reviewee can merge it into master or any other base branch

* Note: Only coders can assign a code reviewer for their PRs. After a successful testing,
the QA's have to assign the Asana task back to the owner. They have to write a comment
in the task that it is now ready for code review

### If You are the Code Reviewer and Want Other Code Reviewer's Opinion

1. Assign the PR's Asana task to another code reviewer. You do not need to run the
Slack bot command. After that write a comment in the Asana task
with something like "Please code review (tag the code reviewer)"
2. Ping the other code reviewer if necessary

## Etiquette

### Everyone

* Accept that many programming decisions are opinions. Discuss tradeoffs, which
  you prefer, and reach a resolution quickly.
* Ask good questions; don't make demands. ("What do you think about naming this
  `:user_id`?")
* Good questions avoid judgment and avoid assumptions about the author's
  perspective.
* Ask for clarification. ("I didn't understand. Can you clarify?")
* Avoid selective ownership of code. ("mine", "not mine", "yours")
* Avoid using terms that could be seen as referring to personal traits. ("dumb",
  "stupid"). Assume everyone is intelligent and well-meaning.
* Be explicit. Remember people don't always understand your intentions online.
* Be humble. ("I'm not sure - let's look it up.")
* Don't use hyperbole. ("always", "never", "endlessly", "nothing")
* Don't use sarcasm.
* Keep it real. If emoji, animated gifs, or humor aren't you, don't force them.
  If they are, use them with aplomb.
* Talk synchronously (e.g. chat, screensharing, in person) if there are too many
  "I didn't understand" or "Alternative solution:" comments. Post a follow-up
  comment summarizing the discussion.

### Having Your Code Reviewed

* Be grateful for the reviewer's suggestions. ("Good call. I'll make that
  change.")
* A common axiom is "Don't take it personally. The review is of the code, not you." We used to include this, but now prefer to say what we mean: Be aware of [how hard it is to convey emotion online] and how easy it is to misinterpret feedback. If a review seems aggressive or angry or otherwise personal, consider if it is intended to be read that way and ask the person for clarification of intent, in person if possible.
* Keeping the previous point in mind: assume the best intention from the reviewer's comments.
* Explain why the code exists. ("It's like that because of these reasons. Would
  it be more clear if I rename this class/file/method/variable?")
* Extract some changes and refactorings into future tickets/stories.
* Link to the code review from the ticket/story. ("Ready for review:
  https://github.com/organization/project/pull/1")
* Push commits based on earlier rounds of feedback as isolated commits to the
  branch. Do not squash until the branch is ready to merge. Reviewers should be
  able to read individual updates based on their earlier feedback.
* Seek to understand the reviewer's perspective.
* Try to respond to every comment.
* Wait to merge the branch until Continuous Integration (TDDium, TravisCI, etc.)
  tells you the test suite is green in the branch.
* Merge once you feel confident in the code and its impact on the project.

[how hard it is to convey emotion online]: https://www.fastcodesign.com/3036748/why-its-so-hard-to-detect-emotion-in-emails-and-texts

### Reviewing Code

Understand why the change is necessary (fixes a bug, improves the user
experience, refactors the existing code). Then:

* Communicate which ideas you feel strongly about and those you don't.
* Identify ways to simplify the code while still solving the problem.
* If discussions turn too philosophical or academic, move the discussion offline
  to a regular Friday afternoon technique discussion. In the meantime, let the
  author make the final decision on alternative implementations.
* Offer alternative implementations, but assume the author already considered
  them. ("What do you think about using a custom validator here?")
* Seek to understand the author's perspective.
* Sign off on the pull request with a :thumbsup: or "Ready to merge" comment.

## Style Comments

Reviewers should comment on missed [style](../style)
guidelines. Example comment:

    [Style](../style):

    > Order resourceful routes alphabetically by name.

An example response to style comments:

    Whoops. Good catch, thanks. Fixed in a4994ec.

If you disagree with a guideline, open an issue on the guides repo rather than
debating it within the code review. In the meantime, apply the guideline.
