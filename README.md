# saidsure releases

Built installers for saidsure, the desktop app that listens to calls and meetings on your own
computer and keeps every word under keys only you hold. saidsure is a product of Takeeda LLC.

This repository holds ONLY release artifacts: installers, their SHA-256 checksums, release
notes, and a `latest.json` manifest that the saidsure portals read. No source code is published
here. Source lives in a private repository; customers get the app from their portal
(app.takeeda.com or app.saidsure.com) or from the Releases tab here.

## Current signing status

Builds are currently UNSIGNED, pending the code-signing certificate. Windows SmartScreen will
show "Windows protected your PC" with an unknown publisher on first run; choose "More info" and
then "Run anyway" after verifying the checksum below. Signed builds (publisher "Takeeda LLC")
will replace these as soon as the certificate is issued; the manifest field `signed` will flip
to `true`.

## Verify a download

Every release ships `<installer>.sha256`. On Windows PowerShell:

```
Get-FileHash .\saidsure_0.1.0_x64_en-US.msi -Algorithm SHA256
```

Compare the printed hash with the contents of the `.sha256` file and with the `sha256` field in
`latest.json`. If they differ, do not install; download again from this page.

## latest.json

`https://github.com/saidsure-hq/saidsure-releases/releases/latest/download/latest.json`

```
{
  "version": "0.1.0",
  "platforms": {
    "windows-x86_64": { "url": "...", "sha256": "...", "size": 12345678, "fileName": "..." }
  },
  "notes": "...",
  "publishedAt": "2026-10-11T00:00:00Z",
  "signed": false
}
```

## What saidsure does with your data

Transcripts, documents, keys, and recordings stay on your device and in storage you own. The
Takeeda cloud holds identity, your plan, and ciphertext it cannot open; the live-session relay
forwards encrypted frames and stores nothing. The full statement is in the app under Settings,
"How this is protected", and in the product's PRIVACY document shipped with every install.
