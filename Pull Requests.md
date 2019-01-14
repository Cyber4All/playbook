# Pull Requests

Pull Requests (often referred to as PRs) are how we manage all product changes. Whether you're fixing a bug, adding a feature, or updating a build process, you'll do it through a Pull Request.

This allows us to do two main things:
1. Validate the change works in the way we intend
2. Keep other team members up to date on changes to the code base

Reviewing PRs is a routine task for every member of the team each work day. Because of this, we should always aim to keep our PRs as concise and descriptive as possible. Doing so allows our teammates to more quickly get up to speed with the work we are doing, and minimizes the risk of side effects and bugs.

## Authoring a New PR
When opening a PR, there are a few things to do. 

### Give it a Good Description
Describe why you are making the change and any nuances of the implementation that you chose. This is not a substitute for comments in your code, but rather serves to scope the PR before a reviewer even reads a line of code.

### Assign Reviewers
For a PR to be approved, it'll need to be reviewed. When you open a PR, assign reviewers to it. This will send them a slack notification via the [Pull Reminders](https://pullreminders.com/) bot. If you updated a PR after a reviewer has left comments or requested changes, assigning them again will let them know updates have been made.

### Link Relevant Issues
It is possible to close an issue with a PR in GitHub, as detailed in [this blog post](https://blog.github.com/2013-05-14-closing-issues-via-pull-requests/). When opening up a new PR that resolves a feature request or bug noted in an issue, be sure to link the PR to the issue.

### Versioning the Change
After your PR has been approved, it's time to version it. Read more about proper versioning [here](Versioning.md). After giving it a shiny new version number, go ahead and merge it into master. Congrats, you just put a PR through :tada:
