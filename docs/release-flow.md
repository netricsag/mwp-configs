# Release Flow

This repository publishes non-sensitive config files through tag-pinned raw GitHub URLs.

## Repository Settings

Configure `netrics/mwp-config` as a public repository with Issues, Wiki, Projects, and Discussions disabled.

Protect `main` with:

- pull request review required before merge
- required status check: `release-checks`
- force pushes disabled
- branch deletion disabled

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

Consumers must only use URLs pinned to release tags. Do not publish or document floating `main` raw URLs for devices or automation.

## Post-Release Fetch Test

After publishing a tag, fetch the manifest and at least one config URL from the public raw endpoint.

```powershell
Invoke-WebRequest https://raw.githubusercontent.com/netrics/mwp-config/v1.0.0/manifest.json
Invoke-WebRequest https://raw.githubusercontent.com/netrics/mwp-config/<tag>/configs/<area>/<name>
```

The first release has no config files, so the config fetch test starts with the first release that includes a real config entry.
