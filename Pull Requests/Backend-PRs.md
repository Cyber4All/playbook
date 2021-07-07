# Backend Pull Requests

This file details the practices that should be followed when creating a backend pull request (PR), in addition to the [general PR practices](README.md).

## Table of Contents

- [Backend Pull Requests](#backend-pull-requests)
  - [Table of Contents](#table-of-contents)
  - [Guidelines](#guidelines)
    - [Added/Updated Routes](#addedupdated-routes)
    - [Schema Definitions Changed](#schema-definitions-changed)
    - [Updates to Wikis](#updates-to-wikis)

## Guidelines

Backend PRs should contain added/updated routes, schema definitions changed, and/or any updates to wikis required if the PR required changes to them.

### Added/Updated Routes

If a PR added or updated a route (or routes), the PR should include the API contract of the route(s) that were added.  For instance, if you work on a story that adds a new route to user authentication, the API contract of this route should be added for review.

### Schema Definitions Changed

If a PR changed or added any schema definitions (such as a database or request body schema), the PR should include what part of the schema was added or updated.  For instance, if you work on a story that requires the user's age during user registration, the request body and user schema is changed and should be noted in the PR.

### Updates to Wikis

If a PR significantly changes the workflow or requirements of a existing procedure, the wiki associated with the procedure should be updated with the new info and linked in the PR.  For instance, if you work on a refactor for our user authentication system that rewrites how we verify users, the wiki associated with user authentication should be updated.

**Note:** If the wiki doesn't exist, please create one in it's repository.