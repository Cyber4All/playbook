# Commits and Branches

This file details the practices that should be followed when committing code to the repository and creating branches.

## Table of Contents

## Guidelines

### Branches

Whenever you start a new story, you should create a new git branch for that story.  By doing this, it allows you to create a [pull request](./Pull%20Requests/README.md) which will allow the rest of the team to easily review your code and control the quality of the code.  For larger stories (such as new feature development), it also allows your work to exist separately of other developers and not interrupt the work they are doing until you are ready to merge.  This minimizes git change conflicts.

You are welcome to use any naming convention you would like for your branches, so long as there is a new branch for every story.  One example is using the clubhouse story id and providing a brief description of what the branch does: `1234-Create_login_form`.  You could also use your name/username and either the story id or a brief description.  Alternatively, you could only provide a brief description.

Before creating a new branch, make sure you are on the latest version of the base branch (for the most part this will be the `master/main` branches but it could be a base branch for a refactor).  To do this, checkout the base branch name and then pull the latest changes:

```
git checkout BASE_BRANCH_NAME
git pull
```

To create a branch and switch to it run the following in your terminal/console:

```
git branch BRANCH_NAME
git checkout BRANCH_NAME
```

To push your branch to github run the following:
```
git push --set-upstream origin BRANCH_NAME
```
After you run this to set up your branch in the GitHub repository, you can push your changes from your branch by using the following command while checking out your branch `git push`.

**Note:** If you are working on multiple small change or bug fix stories (such as one line fixes) its ok to use only one branch to incorporate all of these fixes.  Otherwise, you should always create a new branch for the story.

### Commits

When committing, your commit messages doesn't need to be very specific but it needs to be descriptive enough to distinguish what you did at that commit.  For instance, `initialize basic application` is a better commit message than `commit code`.

The frequency of how much you commit is also up to you.  The best practice though is to commit code when you reach a working state or complete a task during the development of a story.  For instance, say you are developing a login form.  You may want to commit the initialization of the form, then the working implementation of the form, and then finally the css styling of the form.  By making more frequent commits, it makes it easier to track during the development of a story what went wrong during your implementation.  It's easier to debug 4 changed files instead of 40.
