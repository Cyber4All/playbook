## Guidelines
* All packages being published to npm must follow [Semantic Versioning (semver)](https://semver.org/)
* Applications _should_ follow semver for organizational consistency, but product owners make the final decision on versioning strategies
  - If semver is not used, a detailed versioning strategy must be provided in its place

## Pre-releases
A [pre-release](https://semver.org/#spec-item-9) can be very useful when developing applications. Semantic Versioning does not specify any pattern for the pre-release. Therefore, to better coordinate versioning within the organization, a suggested pattern for pre-releases is described as follows.

```
[VERSION_NUMBER]-[TYPE].[MINOR].[PATCH]
```

Where,

| Identifier | Description |
| :---:        |     :---     |
| `VERSION_NUMBER`   | corresponds to the semver compliant version number of a release     | 
| `TYPE` | corresponds to the classification of the pre-release (alpha, beta, rc)       |
|`MINOR` | corresponds to the minor version of the pre-release type and inherits standards from [semver's minor spec](https://semver.org/#spec-item-7) |
|`PATCH` | corresponds to the patch version of the pre-release type and inherits standards from [semver's patch spec](https://semver.org/#spec-item-6)|

Thus, an example pre-release for version `2.0.0` could be `2.0.0-alpha.0.0`. Upon a patch being applied, the version would increment to `2.0.0-alpha.0.1`. Moving on, when a backwards-compatible feature is added to the alpha (a minor update) the version would be incremented to `2.0.0-alpha.1.0`. Following this pattern, alpha can move to beta or a release candidate (rc). Bumping the type will reset minor and patch version numbers to 0.

## Push New Version
To update the application to a newer version, run the [npm version](https://docs.npmjs.com/cli/version) command in the following format: `npm version <version number>`. This command will update the `package.json` and `package-lock.json` files. It will also create a new git tag and version commit. 

Once the `npm version` command has completed, simply use the `git push` command to push the changes to remote. 

When using `git push` it's important to push that newly created git tag up to the repository as well. If your git installation isn't configured to automatically push tags, simply append a flag to the end of your command as follows:

`git push --follow-tags`

You can also configure your git installation to always push any local tags to your remote:

`git config --global push.followTags true`

[Read more](https://git-scm.com/book/en/v2/Git-Basics-Tagging) about git tags 
