# Contributing

This repo is **bitHuman's fork of [`livekit/client-sdk-swift`](https://github.com/livekit/client-sdk-swift)**. We carry a small patch set on top of upstream — primarily a "no-device" app-audio path that lets a Swift host pump pre-rendered PCM into a LiveKit `LocalAudioTrack` without claiming the system microphone. Everything else tracks upstream.

That fork relationship shapes how to contribute here. Please read this before opening a PR.

## Where to send your change

### If your change is generally useful (a bug fix, performance work, a new feature that any LiveKit Swift consumer would want)

**Send the PR to upstream first**: <https://github.com/livekit/client-sdk-swift>.

Upstream's contributing guide and CLA: <https://github.com/livekit/client-sdk-swift/blob/main/CONTRIBUTING.md>.

Once upstream merges, we'll pull it in on the next sync. This keeps the diff between this fork and upstream small, which is the only thing that keeps the fork sustainable.

You can absolutely open a parallel PR here so we can pick up the fix sooner — just please **link the upstream PR in the description** so we know it's headed home.

### If your change is bitHuman-specific

That means it touches our app-audio / no-device microphone path, the IPC bits we layered on top, or anything else that wouldn't make sense to upstream. Open the PR here. Keep the patch as small and well-isolated as you can — ideally behind a clearly named API or build flag — so that future upstream merges stay clean.

### If you're not sure which bucket your change falls into

Open an issue or draft PR and we'll help you figure it out. Default assumption: it probably belongs upstream.

## What this fork actually changes

The short version (see `CHANGELOG.md` and the git log for the complete picture):

- **`Sources/LiveKit/.../AudioManager*` and friends** — added a path that registers an app-supplied audio source as a publishable track without configuring the system audio session for capture. This is what lets a host process render avatar audio in software and republish it to a LiveKit room without ever asking macOS / iOS for the microphone.
- **`livekit_ipc.proto` and the `protocol/` directory** — light additions for our process-boundary use cases.
- A few minor build / packaging tweaks.

Anything not in that list is upstream's. If you find yourself editing core WebRTC plumbing, audio routing for the device path, or the public `Room`/`Participant` API, that change almost certainly belongs upstream.

## Building and testing

The build setup is upstream's — `Package.swift` / `Package@swift-6.2.swift`, `Makefile`, and the Xcode workflows in `.github/workflows/` all came from `livekit/client-sdk-swift`. To run the test suite locally:

```sh
swift test
```

Benchmark suite:

```sh
make benchmark
```

If your change affects audio, please test against both the device path (mic capture) and the app-audio path. They share enough machinery that regressions in one can hide in the other.

## Commit hygiene

- Conventional-style prefixes are appreciated (`fix:`, `feat:`, `audio:`, `ipc:`, etc.).
- Reference the upstream PR in the commit body when applicable: `Upstream: livekit/client-sdk-swift#1234`.
- Keep fork-specific commits clearly identifiable so we can rebase cleanly when we sync.

## Reporting bugs

- **Bugs in core LiveKit functionality** (signaling, video, the public Swift API): please file at <https://github.com/livekit/client-sdk-swift/issues>. They have more eyes on it.
- **Bugs in our fork-specific app-audio path or IPC layer**: file [here](https://github.com/bithuman-product/bithuman-livekit-swift/issues).
- **Security issues**: see [`SECURITY.md`](SECURITY.md). Don't file a public issue.

## Code of conduct

Be kind. Assume good intent. We follow the same standards LiveKit does in the upstream community.
