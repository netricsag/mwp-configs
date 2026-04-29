# Release Flow

This repository publishes non-sensitive config files through immutable release tags and a mutable Docker-style `latest` channel.

## Repository Settings

Configure `netrics/mwp-configs` as a public repository with Issues, Wiki, Projects, and Discussions disabled.

Protect `main` with:

- pull request review required before merge
- required status check: `release-checks`
- force pushes disabled
- branch deletion disabled

Protect `latest` with:

- pushes restricted to release maintainers or release automation
- pull requests to `latest` disabled by convention
- force pushes avoided unless recovering a broken channel pointer

## First Release

The first public release is scaffold-only:

```text
v1.0.0
```

It contains the repository contract, schema, validation workflow, and an empty manifest.

## Future Releases

1. Add or update files under `configs/<area>/<name>`.
2. Update `manifest.json` with the release tag, timestamp, config path, area, name, checksum, and tag-pinned raw URL.
3. Open a pull request to `main`.
4. Wait for `release-checks` and review approval.
5. Merge to `main`.
6. Tag `main`, for example `v1.1.0`.
7. Move the `latest` branch to the same commit.

Consumers that need deterministic behavior must use URLs pinned to release tags. Consumers that need automatic current-release behavior may use `latest` URLs. Do not publish or document floating `main` raw URLs for devices or automation.

Example release commands after `main` contains the reviewed release commit:

```powershell
git checkout main
git pull --ff-only origin main
git tag -a v1.1.0 -m "v1.1.0"
git push origin v1.1.0
git push origin main:latest
```

The `latest` branch must point at a commit that has already passed review and release checks on `main`.

## Post-Release Fetch Test

After publishing a tag, fetch the manifest and at least one config URL from the public raw endpoint.

```powershell
Invoke-WebRequest https://raw.githubusercontent.com/netrics/mwp-configs/v1.0.0/manifest.json
Invoke-WebRequest https://raw.githubusercontent.com/netrics/mwp-configs/<tag>/configs/<area>/<name>
Invoke-WebRequest https://raw.githubusercontent.com/netrics/mwp-configs/latest/manifest.json
Invoke-WebRequest https://raw.githubusercontent.com/netrics/mwp-configs/latest/configs/<area>/<name>
```

The first release has no config files, so the config fetch test starts with the first release that includes a real config entry.
