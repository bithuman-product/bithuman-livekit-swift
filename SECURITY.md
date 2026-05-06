# Security Policy

This repo is bitHuman's fork of [`livekit/client-sdk-swift`](https://github.com/livekit/client-sdk-swift). Most of the code here is upstream's; a small patch set on top adds a no-device app-audio path used by bitHuman products.

## Where to report

### If the issue is in upstream LiveKit code

Almost everything in this repo is upstream's. If you can reproduce the issue against `livekit/client-sdk-swift` directly, please report it through LiveKit's security process: <https://github.com/livekit/client-sdk-swift/security>. They'll fix it faster, and we'll pick up the fix on the next sync.

### If the issue is in bitHuman's fork-specific changes

If the bug only reproduces here — most likely in the app-audio / no-device microphone path or the IPC additions — please **email security@bithuman.ai** instead of filing a public issue.

Include:

- A description of the issue and the impact (what an attacker can do).
- Steps to reproduce, ideally a minimal sample.
- The commit / tag where you saw it.
- The OS, Xcode version, and hardware.
- Your name or handle if you'd like public credit.

### If you're not sure which bucket it falls into

Default to **email security@bithuman.ai**. We'll triage and forward to upstream if it's their territory, with credit to you.

## What to expect

- We aim to acknowledge every report **within 48 hours**.
- We'll keep you posted while we triage and fix.
- We support **coordinated disclosure** — we'll agree on a public date with you before publishing.
- Fixes ship via a tagged release and a GitHub Security Advisory.

## Out of scope

- Issues that require physical access to the device, jailbreak, or disabled OS protections.
- Social engineering against bitHuman or LiveKit staff.
- Findings that depend on third-party WebRTC vendor code we don't ship in this repo (report those upstream — likely to `webrtc-sdk/webrtc`).

Thanks for helping keep users safe.
