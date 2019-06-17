## Build Numbers

When working on a new feature or refactoring task in a service, there's a good chance that there are quite a few steps to completion. In order to introduce a new feature, perhaps you must first refactor a few pieces of a module. In these cases, build numbers can be used to integrate and deploy your work as you go, so that the scope of the eventual PR can be reduced.

Build numbers are SemVer compliant, and take the form:
```
[MAJOR].[MINOR].[PATCH]-[BUILD NUMBER]
```

For instance, when making a pure refactoring to a service (i.e. there is no change to any consumer contract) at version `1.0.0`, the version should be incremented to `1.0.0-1`.
