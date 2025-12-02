# TLM-JSFX 
My JSFX plugins for REAPER. I am commited long term to improving these tools and creating new fx in my pursuit to make more music. 
repo link: https://raw.githubusercontent.com/ThomasListens/TLM-JSFX/main/index.xml
## Retro Codec Suite

Authentic emulation of retro compression formats. Add charcter to your audio with the signature sound of classic gaming hardware.

![Retro Codec Suite Interface](https://i.imgur.com/55v0koi.png)

### Features
- **4 Codec Types:** N64 VADPCM, IMA ADPCM, 4-bit PCM, PSX ADPCM
- **Period-Accurate Settings:** Sample rates (11-44kHz), bit depths (4-24 bit)
- **Creative Controls:** Saturation, artifacts intensity, dry/wet mix, output gain
- **Optional Filters:** Anti-aliasing pre-filter and lo-fi character filter

### Codec Types

**N64 VADPCM** - Nintendo 64's Vector-Adaptive Differential PCM, the signature sound of Ocarina of Time and GoldenEye.

**IMA ADPCM** - Interactive Multimedia Association standard, widely used in early CD-ROM games and multimedia.

**4-bit PCM** - Simple 4-bit pulse code modulation with aggressive lo-fi digital artifacts.

**PSX ADPCM** - PlayStation 1's format that defined an era of gaming with Final Fantasy VII and Metal Gear Solid.

### Controls

- **Codec Type** - Select compression format (N64 VADPCM, IMA ADPCM, 4-bit PCM, PSX ADPCM)
- **Sample Rate** - Choose from 11kHz, 16kHz, 22kHz, 32kHz (default), or 44kHz
- **Bit Depth** - Select 4-bit, 8-bit, 16-bit (default), or 24-bit
- **Saturation** - Soft saturation for subtle harmonic warmth
- **Artifacts** - Control codec-specific compression artifacts intensity
- **Mix** - Blend processed and dry signals (100% wet default)
- **Output** - Master output level with ±12dB range (0dB default)
- **Anti-Aliasing** - Pre-filter to reduce aliasing (enabled by default)
- **Lo-Fi Filter** - Character filter matching target sample rate (enabled by default)

### Usage Tips

- **Double-Click** any slider to reset it to default value
- Start with default settings (32kHz, 16-bit, N64 VADPCM) for instant retro character
- Use the Artifacts slider to add period-authentic compression artifacts
- Experiment with Mix control to blend vintage character with clean signal
- Perfect for chiptune, lo-fi beats, retro game soundtracks, or experimental sound design

---

## SEED_DELAY

A multi-tap delay plugin featuring creative, musical, and organically-inspired algorithms to produce 12 unique delay timings.

![Seed Delay Interface](https://i.imgur.com/kbfxQ4Y.png)

### Features
- 12-tap delay matrix with individual control over each tap
- 8 unique timing algorithms inspired by nature, music theory, and mathematics
- Per-tap volume and pan controls with visual envelope editing
- Intuitive grid-based interface

### Algorithms
- **Seed Random** - Generates unpredictable, organic delay patterns
- **Quantum Shuffle** - Timing variations based on quantum probability concepts
- **Perlin Noise** - Smooth, natural variations using noise algorithms
- **Spiral Wave** - Creates spiraling, evolving delay patterns
- **Chromatic** - Delays based on chromatic scale intervals
- **Harmonic** - Musically-consonant delays following harmonic series
- **Fibonacci** - Nature-inspired timing using the golden ratio
- **L-System** - Fractal-based patterns for complex rhythms(used to model plant growth)

### Controls
#### Grid Interface
- **Click** any square to enable/disable individual taps
- **[VOL & PAN]** Click to set volume/pan for specific tap
- **[VOL & PAN]** Shift-click to enable/disable modulation
- **[VOL & PAN]** Control-click to reset to default
- **[VOL & PAN]** Click and drag through row to draw envelopes

---

## Tap Timing Utility

A timing measurement plugin for REAPER that helps you set delays and time-based effects "by hand" using your mouse or keyboard

![Tap Timing Utility Interface](https://i.imgur.com/xSkC0bt.png)

### Features
- Measures intervals between clicks with millisecond accuracy
- Real-time conversion to Hz, ms, and samples at current sample rate
- Tempo-aware beat division calculations
- Audio click feedback for rhythmic accuracy
- History tracking of recent measurements

### Use Cases
- Setting delay times by tapping along with music
- Finding the tempo of audio material
- Calculating LFO rates and modulation speeds
- Measuring rhythmic intervals for precise timing

### Usage
1. Click the main button to mark timing points
2. View instant conversion to useful time formats
3. Use measurements to dial in perfect delay times

---

## Installation

### Via ReaPack (Recommended)
1. Install [ReaPack](https://reapack.com/) if you haven't already
2. In REAPER: Extensions → ReaPack → Manage repositories
3. Click "Import repositories..."
4. Add this repository URL: `https://raw.githubusercontent.com/ThomasListens/TLM-JSFX/main/index.xml`
5. Click OK, then close the Manage repositories window
6. Extensions → ReaPack → Synchronize packages
7. Extensions → ReaPack → Browse packages
8. Search for "TLM-JSFX" and install the plugins you want

### Manual Installation
1. Download the .jsfx files from this repository
2. Place them in your REAPER Effects folder:
   - Windows: `%APPDATA%\REAPER\Effects`
   - macOS: `~/Library/Application Support/REAPER/Effects`
   - Linux: `~/.config/REAPER/Effects`
3. Restart REAPER or scan for new plugins

### Using JSFX in Other DAWs
Not using REAPER? You can still use JSFX plugins! Check out [this guide for running JSFX in other DAWs](https://github.com/JoepVanlier/JSFX?tab=readme-ov-file#what-if-i-want-to-use-the-plugins-in-another-daw).

---

## License
These plugins are provided as-is for creative use.

## Credits
Created by Thomas Meier with AI assistance from Claude.
