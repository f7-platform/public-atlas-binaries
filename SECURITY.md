# Security Policy

## Reporting a vulnerability

Email **security@f7-platform.io** with:

- the affected artifact and version (e.g. `atlas-0.1.1-macos-arm64.dmg`),
- reproduction steps or a proof of concept,
- the impact as you understand it.

We acknowledge reports within 3 business days. Please do not open public
issues for security reports.

## Verifying artifacts

Every release attaches `SHA256SUMS` and a `.sha256` companion for each
download. The release pipeline's full verification transcripts are not
attached; they stay with the internal build record. macOS artifacts are
Developer ID signed, hardened-runtime, and notarized; Windows artifacts are
signed via Azure Trusted Signing. A file that fails checksum or signature
verification should be reported as above, not run.
