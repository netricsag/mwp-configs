# Contributing

This repository distributes public, non-sensitive device and automation configuration files. It is not an application repository and should stay small, predictable, and easy for consumers to pin by release tag.

## Change Process

All changes must land through a pull request to `main`.

Before opening a pull request:

- Confirm every changed config value is safe to publish publicly.
- Place config files under `configs/<area>/<name>`.
- Update `manifest.json` for every added, changed, or removed config file.
- Use release-tag raw URLs in the manifest, never floating `main` URLs.
- Update each manifest checksum with the SHA-256 of the referenced file.
- Keep documentation focused on consumption, ownership, and release behavior.

The `release-checks` workflow validates repository structure, JSON syntax, manifest consistency, checksums, tag-pinned raw URLs, and obvious secret patterns.

## Manifest Entries

Every published config file must have one manifest entry with:

- `path`: relative path under `configs/`
- `area`: first path segment after `configs/`
- `name`: file name
- `sha256`: lowercase SHA-256 checksum
- `rawUrl`: tag-pinned raw GitHub URL

Example URL pattern:

```text
https://raw.githubusercontent.com/netrics/mwp-config/<tag>/configs/<area>/<name>
```

## Review Expectations

Reviewers should verify that config content is public-safe, the manifest matches the file tree, checksums are correct, and consumers can keep using existing tag-pinned URLs.

Do not add source-code application folders, build systems, deployment scaffolding, or generated artifacts unless they are required for this repository's config distribution contract.
