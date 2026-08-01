# TLM-JSFX

JSFX effects and instruments for REAPER, by Thomas LeRoy Meier.

Six plugins: a game-console codec emulator, a 12-tap delay with generated tap times, a cross modulator, a just-intonation drum synth, a saturator modelled on the inner ear, and a tap tempo readout.

## Install

**ReaPack** (recommended — you get updates)

```
https://raw.githubusercontent.com/ThomasListens/TLM-JSFX/main/index.xml
```

1. Install [ReaPack](https://reapack.com/)
2. Extensions → ReaPack → Import repositories
3. Paste the URL above
4. Extensions → ReaPack → Browse packages, filter by `TLM`

**Manually** — download the `.jsfx` files and drop them in your REAPER Effects folder:

| OS | Path |
|---|---|
| Windows | `%APPDATA%\REAPER\Effects` |
| macOS | `~/Library/Application Support/REAPER/Effects` |
| Linux | `~/.config/REAPER/Effects` |

Not using REAPER? JSFX can run in other DAWs — see [Joep Vanlier's guide](https://github.com/JoepVanlier/JSFX?tab=readme-ov-file#what-if-i-want-to-use-the-plugins-in-another-daw).

---

## Retro Codec Suite

![Retro Codec Suite](https://i.imgur.com/55v0koi.png)

Emulations of the audio compression used by 1990s game consoles, built on the actual predictor and step tables from each format.

**Codecs:** N64 VADPCM · IMA ADPCM · 4-bit PCM · PSX ADPCM · Apple 1-bit

| Control | Range | Default |
|---|---|---|
| Codec Type | 5 formats | N64 VADPCM |
| Sample Rate | 8 kHz → project rate | ~29 kHz at a 44.1 kHz project |
| Bit Depth | 1 → 16 bits | 11 bits |
| Saturation | soft saturation before encoding | off |
| Artifacts | scales the codec's own error | off |
| Mix | dry/wet | 100% wet |
| Output | −30 → +6 dB | 0 dB |
| Anti-Aliasing | optional pre-filter | **off** |
| Lo-Fi Filter | character filter matched to target rate | **off** |

Sample Rate is a proportion of the project rate rather than a fixed value, so the default moves with your project. Apple 1-bit forces a minimum of 44.1 kHz.

**Usage.** Hold `Shift` while dragging Sample Rate or Bit Depth for continuous values between the notched presets. Double-click any slider to reset it.

**Worth knowing.** These codecs alias, and the downsampling has no decimation filter, because that is what the originals did. Turn on Anti-Aliasing if you want the artifacts without the aliasing.

---

## Seed Delay

![Seed Delay](https://i.imgur.com/kbfxQ4Y.png)

A 12-tap delay where the tap times are generated rather than dialled in. An algorithm proposes a set of timings; you edit the result by hand on the grid.

**Algorithms.** Seed Random · Quantum Shuffle · Perlin Noise · Spiral Wave · Chromatic · Harmonic · Fibonacci · L-System

**Grid**

| Action | Effect |
|---|---|
| Click a square | Enable / disable that tap |
| Click and drag across a row | Draw a volume or pan envelope |
| `Shift`-click | Toggle modulation on that tap |
| `Ctrl`-click | Reset to default |
| REGEN | Re-roll the current algorithm |

**Worth knowing.** Feedback tops out at 0.99, not 1.0 — at exactly unity the loop neither decays nor settles, and because the taps sum coherently at low frequencies it builds without bound instead of sustaining. Dirt and Moonlight/Sunlight are the non-linear stages; with both at zero the delay path is linear and rings longer at high feedback than you might expect.

---

## Cross Modulator

Five ways for one signal to modulate another, each available with an external modulator or an internal oscillator. Modulation can be applied to the whole signal or restricted to one frequency band.

**Routing — read this first.** Four inputs. Carrier on channels 1–2, modulator on channels 3–4.

- The `x Osc` modes use the built-in oscillator and need no routing
- The `x Ext` modes need a send from another track into channels 3–4

If an `x Ext` mode does nothing, the send is missing. Set Modulator Source to `Main In 1-2` to modulate a signal with itself instead.

| Mode | What it does |
|---|---|
| Ring | Classic ring modulation, carrier suppressed |
| AM | Carrier stays present alongside the sidebands |
| Phase FM | Modulator displaces a short delay line |
| Envelope | A follower on the modulator gates the band — rhythm without pitch artifacts. Slow oscillator gives tremolo |
| Filter FM | Audio-rate modulation of the band filter cutoff |

Controls: Intensity · Osc Rate (20 Hz–5 kHz) · Max FM Depth · Modulated Band (LP/BP/HP/full) · Band Freq · Band Q · Output Trim

**Worth knowing.** Ring and FM produce inharmonic sidebands by design. Output level varies a lot between modes — use Output Trim.

---

## MonoDrum

A monophonic percussion synth whose partials are placed by whole-number frequency ratios rather than by an inharmonicity control. MIDI in, no audio in — put it on an empty track.

Real drums have inharmonic partials. Placing them at just ratios instead gives something that reads as pitched percussion. That is the point, not a limitation.

**Sources.** Tuned partials with per-partial ratio, level and decay · a noise channel with its own envelope and bandpass · a short click transient.

**Structure presets.** Several presets are tunings rather than timbres — the tuning *is* the patch. Spiral of Fifths is twelve Pythagorean steps. Euler Genus 105 is the divisor lattice of 3×5×7, octave-reduced. Otonal Nine is harmonics 8–16 as a chord.

**Usage.** Pitch follows MIDI note, or set Mode to `Hz Override` for a fixed frequency. Trigger Mode switches between `Gate` (holds while held) and `One-Shot` (always plays the full envelope). Velocity can be routed to decay and to pitch envelope depth. Auto-Normalize Partials keeps level roughly constant as you add partials — turn it off if you want adding partials to get louder.

---

## Cat Ears

Cochlear stereocilia distortion — a saturation curve taken from the inner ear rather than from a circuit.

The Boltzmann function used here describes how far a hair bundle has to bend before its ion channels open. The curve is asymmetric and level-dependent, so it behaves differently on transients than on sustained material. Based on the model in Peterson & Heil, 2020.

Controls: Input Gain · Drive · Asymmetry · Output Trim · Wet/Dry

Asymmetry biases the two directions of the curve, which sets how much even-order content is produced.

**Worth knowing.** Not oversampled. High Drive on bright material will alias. Use it on the way in or on a duplicated track rather than across a full mix.

---

## Tap Timing Utility

![Tap Timing Utility](https://i.imgur.com/xSkC0bt.png)

Tap along with something and read the interval back in the units other plugins ask for — for when you know how a delay should feel but not what number it is.

Reads out milliseconds, hertz, samples at the current project rate, and the nearest beat division against project tempo.

**Usage.** Choose Mouse or MIDI input, then tap the button or play notes. The running average steadies over several taps, so keep tapping rather than trying to land two perfect ones. Audio Click gives you something to tap against.

Measurement only — it does not process audio and can sit anywhere in a chain.

---

## Also in this repo

`Video Processors/` holds a few REAPER video processor presets — BOXCROP, Gentle Breathing & Blur, Progressive Word Display. These are **not** distributed through ReaPack; copy the text into a video processor instance directly.

## License

Provided as-is for creative use.

## Credits

Written by Thomas LeRoy Meier, with AI assistance from Claude. Where that assistance produced a specific change, it is recorded in the commit history rather than summarised here.

Approach to memory layout, filter topology and packaging is indebted to reading the published work of [Joep Vanlier (Saike)](https://github.com/JoepVanlier/JSFX), [Geraint Luff](https://github.com/geraintluff/jsfx) and [chokehold](https://github.com/chkhld/jsfx).
