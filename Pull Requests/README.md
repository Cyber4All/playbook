# Pull Requests

This file details the practices that should be followed when creating a pull request (PR) and links to additional practices that should be followed if making a PR in either a frontend or backend repository.

## Table of Contents

- [Pull Requests](#pull-requests)
  - [Table of Contents](#table-of-contents)
  - [About](#about)
  - [Guidelines](#guidelines)
    - [Description](#description)
    - [Changes Made](#changes-made)
    - [Clubhouse Stories](#clubhouse-stories)
    - [Re-Requesting Reviews](#re-requesting-reviews)
    - [Merging PRs](#merging-prs)
    - [Additional Requirements](#additional-requirements)

## About

Pull Requests (often referred to as PRs) are how we manage all product changes. Whether you're fixing a bug, adding a feature, or updating a build process, you'll do it through a Pull Request.

This allows us to do two main things:
1. Build a better product
2. Build a better team

We should review each other's work to ensure our standards are adhered to, it's well tested, implements business requirements etc. The second may not be intuitive, but is even more important than the first. PRs are a way of promoting an environment of learning, which is one of our core tenets here at SecurEd. A code review is a way to share knowledge and experience across the team, allowing both the author and reviewer to learn from each other's experiences.

Reviewing PRs is a routine task for every member of the team each work day. Because of this, we should always aim to keep our PRs as concise and descriptive as possible. Doing so allows our teammates to more quickly get up to speed with the work we are doing.

## Guidelines

At a minimum, a PR should have a description, a list of changes made, and the link(s) to the connected Clubhouse stories.

### Description

The description section should briefly describe the PR and what it aims to accomplish.  For instance, say you are working on a story that adds a section to a registration form that requests the user's age.  A description would include the goal of the PR: to add a section in the registration form for age verification.

**Note:** In most cases, this will most likely be similar if not the same as the clubhouse story description.

### Changes Made

The changes made section should include any information about what was changed in the PR, including code refactors, schemas, or requirement changes.  For instance, say you are working on a backend route that uses a singleton pattern for a class you need to complete your story.  While you are working on the story, you end up having to change the pattern for that class to a factory pattern and the database schema needs to change.  In your PR, you should include these changes so reviewers can review if they were necessary.

### Clubhouse Stories

The Clubhouse stories section should include any stories that are associated with the PR.  This should include at least the story number and the associated link.  The goal of this section is to allow reviewers to see the stories it's associated with for more information that is not present in the PR description and changes made sections (as some PRs can become quite large and involve multiple stories).

While not required, it is helpful to include a link to the PR created on the clubhouse story as well.

### Re-Requesting Reviews

Most PRs you create will have a 'changes requested' review, especially if the requirements of the associated story are more complex.  In these cases, you should always re-request the person who asked for changes and also re-request anyone who has reviewed, commented or approved your PR.  This is necessary because, for some changes, the changes requested could involve a large refactor of what you have already written.  In this case, the code that was already approved and reviewed has changed significantly and should be re-reviewed because of those changes.

### Merging PRs

Prior to merging, make sure you version the branch using semantic versioning if the repo does not have the hotfix-main-releases branching strategy set up.

After you merge a PR, make sure to **delete the branch in GitHub**.  Unless the branch may be needed to go back to or is one of the protected branches we use for version control (such as main/master, hotfix, and releases), you should always delete the branch in GitHub as this clears up space on these repositories and makes it easier to track branches.

### Additional Requirements

For frontend PRs, please refer to the [Frontend-PRs.md](Frontend-PRs.md) file.

For backend PRs, please refer to the [Backend-PRs.md](Backend-PRs.md) file.
