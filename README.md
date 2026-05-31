# k6-with-recording

> ⚠️ This is an unofficial build of an unmerged, experimental feature. Not supported by Grafana Labs.

A custom build of [k6](https://github.com/grafana/k6) that includes **browser video recording**, from [grafana/k6#6020](https://github.com/grafana/k6/pull/6020).

## Usage

The feature is **opt-in** and disabled by default. Enable it by setting an output directory:

```bash
K6_BROWSER_RECORDING_DIR=./recordings k6 run my-browser-test.js
```

This produces one WebM video per VU + iteration, e.g. `vu-1-iter-0-<id>.webm`.

### Requirements

- **ffmpeg** on your `PATH`. If ffmpeg is missing, the test still runs normally — just without recording.
- A Chromium/Chrome browser (same as any k6 browser test).

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



