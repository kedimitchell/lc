# birds Piece Documentation

## 🎯 What I Did
This live-coded TidalCycles piece creates a layered and evolving atmospheric groove with glitchy textures, ambient soundscapes, and polymetric rhythmic patterns. It focuses on modulation, spatialization, and creative transitions between patterns using `xfade`, `off`, and `mask`. The performance explores ambient-to-groove evolution.

## 🛠️ How I Did It
I worked in cycles, layering different channels with distinct sonic roles:

### 🌿 Ambient Intro (d1)
```haskell
setcps(118/60/3.6)  -- Sets the tempo for triplet grid feel

d1 $ sound "birds"
   # gain 1.5
   # sustain 10
   # note "c'maj"
   # dry 1 # room 1 # size 1
   # cutoff (range 300 450 sine)
```
- Used a long-sustained "birds" sample for ambiance.
- Applied a sine-based filter sweep (`cutoff`) for movement.
- `room`, `size`, and `dry` create spatial reverb.

### 🎛 Glitch Texture (d2)
```haskell
d2 $ sound "glitch:5" # speed 0.2 # gain 0.5
   # delay 0.4 # delaytime (range 0.1 0.5 sine) # delayfeedback 0.9
   # dry 0.8 # room 0.8 # size 0.8
   # hcutoff 130
```
- Introduces glitch sounds with deep reverb and rhythmic delay.
- Modulates delay time using `sine`.
- High-passes slightly to avoid muddiness.

### 🏠 Rhythmic Groove (d8, d4, d6)
```haskell
d8 $ sound "house(5,12)" # gain 0.9

d4 $ sound "house:5" # gain 0.6

d6 $ sound "house:5?" # gain 0.8
```
- Euclidean house grooves add pulse (5 hits in 12 steps).
- Used multiple layers for thickening percussion.

### 🎚 Groove Modulation with `xfade` and `off`
```haskell
xfade 8 $ off 0.25 (|+| 2) $ sound "house(5,12?)" # gain 1
```
- Offsets pattern by 0.25 cycle and transposes up for a layered feel.
- `xfade` creates smooth transitions.

### 🔔 Bell & Melody Textures with Modulation (d7 and others)
```haskell
xfade 4
$ (# gain (range 0.6 0.9(slow 2 sine)))
$ mask "[110 101 101 010 101 011 011]"
$ note "[c3 c4 c5]" # "supergong"
+ up "[-7 -5 0 2 3 -5 -7 2 0 -5 3 2]"
```
- Uses `mask` to create rhythmic gates.
- Layered pitch movement via `up` and chord cycling.
- Gain modulated with `sine` for dynamic volume shifts.

### 🎹 Synth Melodic Layering
```haskell
d2 $ slow 2 $ struct "1(7,12)" $ note "c4" # "[gabor superfm superhammond]" + up "<0 3>/2"
```
- Slow-moving, structurally complex melody.
- Uses three synths in round-robin for evolving timbre.

### 🧨 Final Percussive Texture (d9)
```haskell
d9 $ sound "glitch:5" # speed 3 # gain 0.7 # delay 0.1 # delayfeedback 0.3
```
- Higher-speed glitch loop to add chaotic percussive energy toward the end.

## 🧩 Problems I Faced
### 1. Timing and Transition Issues
- `xfade` didn’t always transition smoothly. Some patterns clipped or cut out early.

### 2. Delay Feedback Loops
- Setting `delayfeedback` too high on glitch samples caused looping audio distortion.

### 3. Overlapping Reverbs
- Using multiple long-tail reverbs (`room`, `size`) on different channels caused buildup.


## ✅ How I Overcame Them
- I learned to preview patterns with `solo` before `xfade`.
- Lowered `delayfeedback` to avoid infinite feedback.
- Used `dry` values strategically to control reverb blend.
