<!--
Heads up: this is bitHuman's FORK of livekit/client-sdk-swift.

If your change is generally useful (a bug fix, perf, or a feature any LiveKit
Swift consumer would want), please send it to upstream first:
  https://github.com/livekit/client-sdk-swift

You can open a parallel PR here so we can pick it up sooner — just link the
upstream PR below. See CONTRIBUTING.md for the full picture.
-->

## What this changes

One paragraph. Link related issues (`Fixes #123`).

## Where this belongs

- [ ] **Upstream-bound** — generally useful; an upstream PR exists or will exist.
      Upstream PR: ____
- [ ] **Fork-specific** — touches the app-audio / no-device path, IPC layer, or other bitHuman-only bits.

## Why

The motivation in 1–3 sentences.

## How I tested it

- [ ] `swift test` passes locally
- [ ] Tested on device path (mic capture)
- [ ] Tested on app-audio path (no-device)
- [ ] Benchmarks unchanged / improved (`make benchmark`)
- [ ] N/A — docs / non-code change

## Checklist

- [ ] Patch is minimal and well-isolated (so we stay close to upstream)
- [ ] Public API changes (if any) are noted in `CHANGELOG.md`
- [ ] No accidental upstream-overwrite (don't reformat untouched files)
