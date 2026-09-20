# Changelog

User-visible changes to the Atlas distribution channel. Per-release product
changes live in each release's notes on the Releases page.

## 2026-09-20

- The claims check now also reads the issue templates under `.github/`, not just
  the markdown at the top of the repository. The links those forms show you
  before you file an issue are asserted at people who are not signed in, so they
  are now held to the same rule as the links in the README: if one stops
  resolving, the check fails.

## 2026-08-14

- The README's verification section now describes update-manifest signing,
  which went live with Atlas 0.2.2. Every release attaches `latest.json`
  together with its detached signature `latest.json.sig` and the Ed25519 public
  key `atlas-update.pub.pem`. The section previously said signatures were
  coming; it now carries the commands that check them, and the key fingerprint
  to compare against before trusting the key.

## 2026-08-13

- Added a claims check that runs on every change here, and weekly against the
  live releases. It fails if a link this repository documents stops resolving,
  if the latest release is a draft or carries no downloads, or if an internal
  file enters the public tree — so these instructions cannot quietly drift from
  what the download page actually serves.

## 2026-08-09

- Removed internal agent instructions and audit workflow machinery from this
  repository. GitHub attaches a source archive of this tree to every release,
  so everything tracked here reaches customers; it now carries only what a
  downloader needs.

## 2026-07-31

- Repository created: Atlas's public distribution point, following the
  `public-agent-binaries` pattern. Releases are published here by the private
  Atlas release pipeline; the first release lands with the next `binary-v*`
  tag.
