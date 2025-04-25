# TidalCycles Live Set Documentation

## 🎯 What I Did
This project is a rhythmic and melodic live coding piece built using TidalCycles. I programmed and layered various drum, synth, and melodic patterns

## 🛠️ How I Did It
I used TidalCycles and SuperDirt to construct the following elements:

### Drums:
```haskell
d1 $ s "bd*8?" # gain 1.1           -- Kick

d2 $ s "sn*2?" # gain 1.2           -- Snare

d3 $ s "hh*16?" # gain 1.5          -- Hi-hats
```
All drums use pattern randomness (`?`) to avoid static repetition and increase rhythmic variation.

### Rhythmic Synth sounds:
```haskell
d5 $ chunk' 3 (hurry 2) $ n "7 2 [3 2] ~" # s "print" # gain 1
```
This line creates fast, syncopated synth hits with note/chord groupings and rhythmic subdivision using `chunk'` and `hurry`.

### Harmony:
```haskell
d7 $ n "f'maj a'min" # s "superhammond" # gain 0.8 # octave 3 # voice 2
```
An organ-style pad plays a two-chord progression: F major and A minor.

### Melody:
```haskell
d8 $ jux rev $ chunk 5 (fast 2 . (|- n 12)) $ off 0.5 (|+ 7) $ struct (iter 4 "t(5,8)")
  $ n (scale "hexMajor7" "0 .. 7") # sound "gabor" # gain 0.8 # octave 5
```
This melody pattern involves transformations like:
- `jux rev`: mirrored copy
- `chunk` and `fast`: faster sub-patterns
- `(|- n 12)`: transposition
- Euclidean rhythms and custom scale mapping

## 📚 Code I Used from Others
1. **TidalCycles Documentation**:
   - https://tidalcycles.org/docs/reference/scale
