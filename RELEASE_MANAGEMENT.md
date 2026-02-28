# Release Management

This repository is the distribution target for Lioncub extension packages.

## Purpose

`lioncub-releases` exists to host GitHub Release assets only.

What belongs here:
- GitHub Releases
- VSIX assets attached to releases
- lightweight documentation describing the distribution process

What does not belong here:
- source code copied from `nikan/lioncub`
- committed `.vsix` files in git history
- build output directories
- local development workflow files unless they are specifically needed for release-shell maintenance

## Source of Truth

The private source repository is `nikan/lioncub`.

Release builds are created there and published here through GitHub Actions using `RELEASE_TOKEN`.

## Maintainer Checks

Before considering this repository healthy, confirm:
- `README.md` describes the repo as distribution-only
- `.gitignore` blocks `.vsix` files and common binary/build artifacts
- release assets are attached to GitHub Releases instead of committed to git
- no source directories such as `src/`, `test/`, or `node_modules/` are committed here

## Release Asset Rules

Expected asset naming:
- `lioncub-<version>.vsix`

Expected release body content:
- version tag
- link back to the source commit in `nikan/lioncub`
- install snippet using `code --install-extension`

## Optional Workflow Shell

If a workflow is added to this repository later, keep it minimal.

It should only support distribution-repo maintenance tasks. It should not rebuild the extension or duplicate the private source workflow logic.
