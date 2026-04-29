## Purpose

Describe the config or repository change and the intended release tag.

## Checklist

- [ ] The change contains no secrets, credentials, tokens, private keys, or sensitive customer data.
- [ ] Config files are under `configs/<area>/<name>`.
- [ ] `manifest.json` has been updated for every added, changed, or removed config file.
- [ ] Manifest `sha256` values match the referenced files.
- [ ] Manifest `rawUrl` values are pinned to the intended release tag, not `main`.
- [ ] `release-checks` passes.

## Consumer Impact

Describe whether existing tag-pinned consumers are unaffected, or whether this prepares a new release for updated consumers.

## Validation

List the local checks or fetch tests performed.
