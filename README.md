# lioncub-releases

Release distribution repository for the Lioncub VS Code extension.

## Release Distribution

This repository exists to host **GitHub Release assets** for Lioncub. Built VSIX packages are published here from the private source repository, [`nikan/lioncub`](https://github.com/nikan/lioncub), using GitHub Actions.

## Downloads

Download the latest extension package from the [Releases page](https://github.com/nikan/lioncub-releases/releases).

After downloading a `.vsix` asset, install it with:

```bash
code --install-extension lioncub-<version>.vsix
```

## Repository Rules

- Do not commit VSIX files or other binaries into git history.
- Publish extension packages as GitHub Release assets only.
- Keep source code changes in the private `lioncub` repository.
- Include a link back to the source commit in each release body.

## Release Flow

1. A release workflow runs in the private `lioncub` source repository.
2. The workflow builds and packages the extension into a VSIX file.
3. The workflow creates or updates a matching release in `lioncub-releases`.
4. The workflow uploads the VSIX as a release asset here.

## Notes

This repository is intentionally lightweight. It is for distribution, not development.
