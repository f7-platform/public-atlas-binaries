# public-atlas-binaries — LLM Instructions

This is a PUBLIC, customer-facing repository. It is a distribution point:
release assets (published by the private Atlas release pipeline) plus the
documentation in this tree. No source code lives or may land here.

Rules:

- Never commit binaries to the tree — they belong on Releases, published by
  the pipeline, never by hand.
- Every claim in the docs must match published artifacts or the release
  workflow that produces them (see `fseven-docs/docs/PUBLIC-REPO-PROTOCOL.md`
  in the private workspace). No roadmap language, no planned features stated
  as current.
- Releases here are created by the private repo's `release-binary.yml` via
  `PUBLIC_BINARIES_PAT`. Fixes to what gets published belong in that private
  workflow, not here — content pushed here directly gets overwritten by the
  next release.
- Keep the required governance files (README, CHANGELOG, LICENSE,
  CONTRIBUTING, SECURITY, this file) present and accurate.
