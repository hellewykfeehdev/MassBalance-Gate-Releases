# MassBalance Gate — Official Desktop Releases

This is the **public, binary-only distribution channel** for MassBalance Gate, a Windows desktop workspace for material traceability and documentary review.

The application source code is maintained separately in a **private** repository. No source files, customer records, private signing keys, Stripe credentials or evidence documents belong here.

> **Release status: No customer-ready installer is published yet.** The current 0.2.0-preview.1 development version is undergoing native Windows acceptance testing. Do not download or run an installer from an unofficial link.

## What will appear here

Once a release is tested and approved, its GitHub Release may contain:

- Windows NSIS installer (.exe) with a versioned release tag.
- Tauri updater signature for that exact installer (.exe.sig).
- A published SHA-256 checksum and clearly dated release notes.
- An HTTPS latest.json update manifest, only after all release checks pass.

The desktop app will check this channel only **after an updater-enabled build** is installed. An ordinary source-code push does **not** deliver or install software to users. Updates are opt-in and the updater must verify its Ed25519 release signature. The first updater-enabled release requires a one-time bootstrap installation.

## Security and limitations

- **Updater Ed25519 signatures** ensure package integrity/authenticity against the configured public key. They **do not replace Windows Authenticode code signing**, SmartScreen reputation or independent security assessment.
- No private keys or signing passwords will be published.
- No telemetry, evidence files, customer databases or customer licences will be published.
- **No release currently verifies UK PPT tax eligibility or represents HMRC approval.** Any future regulatory functionality must be validated independently against authoritative final rules.
- Unofficial GitHub uploads and unsigned previews should not be used for regulated or customer production activity.

## Release checklist

1. Run desktop/Rust tests, security checks and clean Windows acceptance tests.
2. Verify active database backups and migration/upgrade recovery with synthetic data.
3. Build the installer with the operator-held Tauri signing key and the pinned update public key.
4. Check the Authenticode/distribution strategy, SHA-256 and generated .exe.sig.
5. Upload the exact tested installer and its signature to the versioned GitHub Release.
6. Only **after** the release assets are available, publish or replace latest.json with that release's exact version, HTTPS asset URL and detached signature contents.
7. Independently test the app update and failed-signature rejection on a disposable Windows workspace.

The release manifest must never reference a private source-code repository, an HTTP URL, an unsigned preview or a missing installer.

For the latest status, see the [Releases page](https://github.com/hellewykfeehdev/MassBalance-Gate-Releases/releases). If no release exists, **there is no approved public download**.
