# CRUSH//WAVE

Mini studio bit crusher. Single HTML file, no dependencies, runs client-side in the browser.

## What it does

Web Audio bit crusher with a parametric EQ, drive, tone, dry/wet, and output stage, followed by a soft-clip limiter. Signal chain:

```
input → drive (soft saturation) → EQ → crusher (bit depth + sample rate reduction) → tone (low-pass) → dry/wet mix → output → limiter
```

- **Spectral Node**: drag a point on screen to set EQ frequency and gain at once. Q/width is a separate control.
- **Source**: drop or pick an audio file (wav/mp3/m4a/ogg), or route live mic input.
- **Crusher**: continuous bit depth (1–16) and sample rate decimation.
- **Capture**: records the fully processed output and exports a 16-bit stereo WAV.

Runs on an AudioWorklet when available, with a ScriptProcessor fallback for older browsers. Parameter updates go through `postMessage` rather than AudioParam automation, since k-rate params don't behave consistently across engines.

## Usage

Open `crushwave.html` in a browser. Tap to power on (required for audio context autoplay rules), load a file or enable mic, adjust controls.

## Notes

No build step, no external scripts, no analytics. Everything runs locally in the tab.
