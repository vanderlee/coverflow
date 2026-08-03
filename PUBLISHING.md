# Publishing to npm

Releases are published as [`jquery.coverflow`](https://www.npmjs.com/package/jquery.coverflow) by the `Publish to npm` GitHub Actions workflow.

## One-time setup

1. Create an npm access token with permission to publish `jquery.coverflow`.
2. In the GitHub repository, create an environment named `npm`.
3. Add the access token to that environment as a secret named `NPM_TOKEN`.
4. Optionally add required reviewers to the `npm` environment.

## Publish a release

1. Update the `version` in `package.json` and merge that change into the default branch.
2. Create a GitHub release whose tag matches the package version, with an optional `v` prefix (for example, `v1.3.5`).
3. Publish the GitHub release. Prereleases are intentionally skipped.

The workflow verifies the tag, tests the package, and publishes it with npm provenance. A version can only be published once.
