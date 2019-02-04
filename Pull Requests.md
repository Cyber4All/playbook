# Pull Requests

Pull Requests (often referred to as PRs) are how we manage all product changes. Whether you're fixing a bug, adding a feature, or updating a build process, you'll do it through a Pull Request.

This allows us to do two main things:
1. Build a better product
2. Build a better team

The first of these probably makes sense. We should review each other's work to ensure standards are adhered to, it's well tested, etc. The second may not be intuitive, but is even more important than the first. PRs are a way of promoting an environment of learning, which is one of our core tenets here at Cyber4All. A code review is a way to share knowledge and experience across the team, allowing both the author and reviewer to learn from each other's experiences.

Reviewing PRs is a routine task for every member of the team each work day. Because of this, we should always aim to keep our PRs as concise and descriptive as possible. Doing so allows our teammates to more quickly get up to speed with the work we are doing, and minimizes the risk of side effects and bugs.

## Authoring a New PR
When opening a PR, there are a few things to do. 

### Give it a Good Description
Describe why you are making the change and any nuances of the implementation that you chose. This is not a substitute for comments in your code, but rather serves to scope the PR before a reviewer even reads a line of code.

### Assign Reviewers
For a PR to be approved, it'll need to be reviewed. When you open a PR, assign reviewers to it. This will send them a slack notification via the [Pull Reminders](https://pullreminders.com/) bot. If you updated a PR after a reviewer has left comments or requested changes, assigning them again will let them know updates have been made.

### Link Relevant Issues
It is possible to close an issue with a PR in GitHub, as detailed in [this blog post](https://blog.github.com/2013-05-14-closing-issues-via-pull-requests/). When opening up a new PR that resolves a feature request or bug noted in an issue, be sure to link the PR to the issue.

#### Epics
When an enhancement is too large to have its full scope logged in a single issue, it is called an epic. Epics span multiple issues and are only completed after each child issue is closed. To denote an issue as an epic, prepend the phrase **Parent of** before the issue number of the child.

*Example*

Issue #1 is an epic that contains issue #2 and #3. The description of issue #1 would then contain the following:

> Parent of #2
> Parent of #3

#### Dependencies
When an issue requires another to be resolved before it can be, there is a dependency between them. In these cases, the issue that needs the other to be resolved first, should contain the keyword **Needs** before the issue number of the dependency.

*Example*

Issue #5 cannot be resolved until issue #4 is. The description of issue #5 would then contain the following:

> Needs #4

### Versioning the Change
After your PR has been approved, it's time to version it. Read more about proper versioning [here](Versioning.md). After giving it a shiny new version number, go ahead and merge it into master. Congrats, you just put a PR through :tada:

## After Merging a PR

### Deleting the Branch
After a PR is approved and merged, common convention is to delete the branch.  This clears up branch clutter when selecting branches and removes code that will likely never be touched after merging.
