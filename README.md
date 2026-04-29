# netrics/mwp-config

Public, read-only distribution repository for non-sensitive device and automation configuration files.

This repository is intentionally quiet. It is not an application repository, does not contain buildable source code, and is not a support channel.

## Consumption

Consumers should pin every request to an immutable release tag.

Manifest URL:

```text
https://raw.githubusercontent.com/netrics/mwp-config/v1.0.0/manifest.json
```

Config URL pattern:

```text
https://raw.githubusercontent.com/netrics/mwp-config/<tag>/configs/<area>/<name>
```

Example:

```text
https://raw.githubusercontent.com/netrics/mwp-config/v1.0.0/configs/<area>/<name>
```

Do not consume floating `main` URLs. Tags such as `v1.0.0` and `v1.1.0` are the compatibility boundary for devices and automation.

## Manifest

The root `manifest.json` is machine-readable and contains:

- `repo`: repository owner and name
- `version`: release tag
- `generatedAt`: timestamp for the manifest content
- `configs`: published config entries

Each config entry contains `path`, `area`, `name`, `sha256`, and a tag-pinned `rawUrl`.

The initial `v1.0.0` release is scaffold-only and intentionally has no real config entries.

## Ownership

Netrics owns the repository and release process. Changes land through pull requests to `main`, then releases are created by tagging `main`.

GitHub Issues, Wiki, Projects, and Discussions should remain disabled. Use the owning team's internal channels for change requests and operational support.

## Public Data Only

Everything in this repository is public by design. Do not commit secrets, credentials, tokens, private keys, customer-specific sensitive values, or internal-only operational data.
