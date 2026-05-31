# k6-with-recording

A custom build of [k6](https://github.com/grafana/k6) that includes **browser video recording**, from [grafana/k6#6020](https://github.com/grafana/k6/pull/6020).

When a browser test fails, logs only get you so far. This build lets you watch a video of what the page actually did.

## What's included

This is a standard k6 binary built from the PR branch `add-browser-video-recording`. Everything in upstream k6 works as usual, plus the recording feature below.

## Usage

The feature is **opt-in** and disabled by default. Enable it by setting an output directory:

```bash
K6_BROWSER_RECORDING_DIR=./recordings k6 run my-browser-test.js
```

This produces one WebM video per VU + iteration, e.g. `vu-1-iter-0-<id>.webm`.

### Requirements

- **ffmpeg** on your `PATH`. If ffmpeg is missing, the test still runs normally — just without recording.
- A Chromium/Chrome browser (same as any k6 browser test).

### How it works

Chrome DevTools Protocol (CDP) screencast frames are piped to ffmpeg and encoded
to WebM. See the [upstream PR](https://github.com/grafana/k6/pull/6020) and
issue [#4487](https://github.com/grafana/k6/issues/4487) for details.

## Install

Download the archive for your platform from the [latest release](../../releases/latest),
extract it, and put the `k6` binary on your `PATH`:

```bash
tar xzf k6-recording-<os>-<arch>.tar.gz
./k6-recording-<os>-<arch>/k6 version
```

Verify the download against `checksums.txt`:

```bash
shasum -a 256 -c checksums.txt
```

## Build provenance

- Source: `grafana/k6` branch `add-browser-video-recording` (PR #6020)
- Built with `CGO_ENABLED=0`, `-trimpath`

> ⚠️ This is an unofficial build of an unmerged, experimental feature. Not affiliated with or supported by Grafana Labs.
