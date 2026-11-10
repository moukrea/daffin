# Security model — unaudited preview

daffin's host runs in the user's session on a computer: it reads what game launchers and stores leave on disk and
starts games. A device paired with the host can do what the daffin app does there: browse the library, start a game,
stream it. Pair only your own devices.

## What is protected

Devices reach a host on the local network only. A device pairs with a code the host shows: a long code, or a short
10-digit one checked with the CPace protocol, so that whoever overhears an attempt cannot test guesses offline. A code
lasts ten minutes and works once. The link between a paired device and the host is encrypted and authenticated by a
random 256-bit secret per device, with ephemeral ECDH and AES-GCM. The host can revoke a device at any time.

## The Android app and its updates

Every Android release on this repository is signed with daffin's release key. Its certificate's SHA-256 fingerprint
is:

```
9A:CC:F5:15:31:39:97:58:4F:04:39:80:98:80:A3:5E:A7:52:02:D0:B8:E9:85:9B:C7:A0:83:6C:F1:E0:E2:E9
```

To check a downloaded APK, run `apksigner verify --print-certs` on it (Android SDK build-tools): the signer's SHA-256
digest must be this one, and the file's SHA-256 the one listed in the release's `SHA256SUMS`.

The app updates itself only from this repository. It reads `config.json` on this repository's page, downloads the APK
of the release that file names from this repository's releases, keeps it only if its SHA-256 is the one listed in that
release's `SHA256SUMS`, and checks that it is daffin, newer than the installed app and signed by the same key. Android
then asks the person to confirm; nothing is installed without their tap.

## The Linux packages and their updates

The Linux packages (`.deb` and `.rpm`) are not signed. To check a downloaded package, compare its SHA-256 with the one
listed in the release's `SHA256SUMS`.

The desktop app updates itself only from this repository, and only when it was installed from one of these packages.
It reads `config.json` on this repository's page, downloads the package of the release that file names from this
repository's releases, and keeps it only if its SHA-256 is the one listed in that release's `SHA256SUMS`. It then hands
the package to the system's package manager through `pkexec`. The system asks for an administrator's password, and
nothing is installed without it. Unlike on Android, no signature ties an update to daffin's key. An update is trusted
because it comes over HTTPS from this repository's releases.

## Reporting a vulnerability

Report it privately from this repository's Security tab (« Report a vulnerability »), not in public.
