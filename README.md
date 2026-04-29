# netrics/mwp-configs

Public, read-only distribution repository for non-sensitive device and automation configuration files.

This repository is intentionally quiet. It is not an application repository, does not contain buildable source code, and is not a support channel.

## Consumption

Consumers should prefer immutable release tags. The repository also publishes a mutable `latest` channel for tooling that needs Docker-style "current release" behavior.

Pinned manifest URL:

```text
https://raw.githubusercontent.com/netrics/mwp-configs/v1.0.0/manifest.json
```

Pinned config URL pattern:

```text
https://raw.githubusercontent.com/netrics/mwp-configs/<tag>/configs/<area>/<name>
```

Example:

```text
https://raw.githubusercontent.com/netrics/mwp-configs/v1.0.0/configs/<area>/<name>
```

Mutable `latest` channel URL pattern:

```text
https://raw.githubusercontent.com/netrics/mwp-configs/latest/configs/<area>/<name>
```

Do not consume floating `main` URLs. Tags such as `v1.0.0` and `v1.1.0` are the compatibility boundary for deterministic consumers. The `latest` branch is mutable and is advanced only after a reviewed and tagged release.

## Manifest

The root `manifest.json` is machine-readable and contains:

- `repo`: repository owner and name
- `version`: release tag
- `generatedAt`: timestamp for the manifest content
- `configs`: published config entries

Each config entry contains `path`, `area`, `name`, `sha256`, and a tag-pinned `rawUrl`.

The `latest` branch carries the same manifest as the current release. Consumers can fetch `latest/manifest.json` to discover the current release version, then use the manifest's tag-pinned `rawUrl` values when they need checksum-stable downloads.

The initial `v1.0.0` release is scaffold-only and intentionally has no real config entries.

## Ownership

Netrics owns the repository and release process. Changes land through pull requests to `main`, releases are created by tagging `main`, and the `latest` branch is moved to the released commit.

GitHub Issues, Wiki, Projects, and Discussions should remain disabled. Use the owning team's internal channels for change requests and operational support.

## Public Data Only

Everything in this repository is public by design. Do not commit secrets, credentials, tokens, private keys, customer-specific sensitive values, or internal-only operational data.
