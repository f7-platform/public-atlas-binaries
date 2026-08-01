# Atlas — Downloads

Public distribution point for **Atlas** by F7: signed installers for macOS and
Windows, their checksums, and the self-update manifest.

Atlas's source code is hosted in a private repository; this repo is the public
surface downloads come from. There is no source here — only release assets and
this documentation.

---

## Download

Grab the latest release from the
[**Releases page**](https://github.com/f7-platform/public-atlas-binaries/releases/latest):

| Platform | File | Notes |
|---|---|---|
| macOS (Apple Silicon) | `atlas-<version>-macos-arm64.dmg` | macOS 13+; notarized |
| macOS (Intel) | `atlas-<version>-macos-x86_64.dmg` | macOS 13+; notarized |
| Windows (x64) | `atlas-<version>-windows-x86_64-setup.exe` | Per-user installer, no administrator needed; signed |
| Windows (x64, no installer) | `atlas-<version>-windows-x86_64.zip` | Flat layout for manual/portable installs; signed binary |
| macOS CLI-style layout | `atlas-serve-<version>-macos-<arch>.tar.gz` | The same binary in a flat folder, for terminal users |

One download is the whole product: the web app is compiled into the binary and
it starts its own private PostgreSQL. Nothing else has to be installed.

## First run

- **macOS**: open the dmg, drag `Atlas.app` to Applications, double-click it.
  Your browser opens with Atlas running locally.
- **Windows**: run the installer; Atlas lands on your Start menu. Click it and
  your browser opens with Atlas running locally.

To connect Atlas to your F7 account and license, use **Settings → License →
Connect account** inside the app — it hands you to [fseven.ai](https://fseven.ai/connect)
to sign in and installs your license automatically.

## Verifying a download

Every release attaches:

- `SHA256SUMS` and per-file `.sha256` — verify with `shasum -a 256 -c` (macOS)
  or `Get-FileHash` (Windows).
- `latest.json` — the update manifest packaged instances poll (with its
  detached signature once update signing is live).

You can verify the signatures yourself on the files you downloaded:

- macOS: `spctl -a -vv -t open --context context:primary-signature <dmg>` and
  `codesign --verify --strict <dmg>` — Developer ID, hardened runtime,
  notarization ticket stapled.
- Windows: `Get-AuthenticodeSignature <file>` — signed via Azure Trusted
  Signing with a timestamp.

The release pipeline additionally captures full verification transcripts from
the exact published files; those are archived with the internal build record.

macOS artifacts are notarized by Apple; Windows artifacts are Authenticode
signed. Gatekeeper and SmartScreen should accept them without overrides — if
either warns on a file whose checksum matches, treat it as suspicious and
report it (see below).

This release process does not currently publish an SBOM; the release notes on
each release state what evidence is and is not included.

## Support

Open an issue on this repository for install/download problems, or contact
your F7 representative for product support.

## Security

Report vulnerabilities to **security@f7-platform.io** — see [SECURITY.md](SECURITY.md).
