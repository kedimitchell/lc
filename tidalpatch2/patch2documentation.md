Patch2 Documentation

```haskell
setcps(40/60) --tempo configuration
```
- Sets the clock speed to 40 BPM (beats per minute), creating a slower and more spacious groove.
- TidalCycles uses cycles per second, so 40 BPM is equivalent to 40/60 cycles per second.

---

## 🎸 Track `d1` – Bass Pattern

```haskell
d1 $ n"[d2(3,8) f2(3,8) c2(3,8) a2]" # s "pluck" # gain 0.7
```
- Defines a bassline using Euclidean rhythms.
- Notes: `d2`, `f2`, `c2`, `a2` give a mix of D minor and F major tonality.
- `(3,8)` means 3 notes are played evenly across 8 steps.
- `s "pluck"` selects a plucky, string-like synth.
- `gain 0.7` adjusts the volume level.

---

## 🎹 Track `d2` – Melodic Texture
```haskell
d2 $ n"[f3(3,7) a3(3,8) c3 e3(3,8)]" # s "gabor" # gain 0.8
```
- Adds a melodic texture with airy, glassy sounds.
- Uses `f3`, `a3`, `c3`, `e3` to create harmony and variation.
- `s "gabor"` provides a soft, synthetic sound.

---

## 🥁 Track `d3` – Drum Pattern
```haskell
d3 $ "bd*4 sn*2 hh*2" # gain 0.8
```
- Simple drum beat using kick, snare, and hi-hat.
- `bd*4` creates a four-on-the-floor feel.
- `sn*2` and `hh*2` fill out the rhythm.
- `gain 0.8` keeps the drums balanced with other layers.

---

## 🎶 Track `d4` – Melodic Accent with Rhythmic Masking
```haskell
d4 $ mask "[110 101 111 010]"
$ note "f6" # "pluck" #gain 0.8
+ up "[-7 -5 0 2 3 -5 -7 2 0 -5 3 2]"
```
- `note "f6"` defines the starting pitch.
- `+ up [...]` shifts the pitch in semitones, creating a melodic contour.
