# Security Policy

This repository is public by design. Treat every committed file as visible to anyone.

## Reporting a Security Issue

Do not open a public issue or pull request for secrets, vulnerabilities, exposure concerns, or security incidents.

Report security-sensitive findings through private Netrics security or repository-owner channels. Include:

- affected file path or release tag
- description of the concern
- whether the content is already present in a public release
- recommended remediation, if known

## Public-Safety Rules

- Do not commit credentials, tokens, passwords, private keys, certificates with private material, or customer-sensitive values.
- Do not commit internal-only endpoint details unless they have been explicitly approved for public distribution.
- Prefer removing sensitive content from future releases and rotating affected credentials over relying on Git history changes.
- Avoid using floating `main` raw URLs for devices or automation.

## Supported Releases

Consumers should use the latest published release tag unless they have a controlled reason to remain pinned to an older tag. Security fixes are released by merging to `main` and publishing a new tag.
