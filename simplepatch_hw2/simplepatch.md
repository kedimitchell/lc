//chords
$: chord("<F C Dm [Bb C]>").voicing()
.s("sine")
.lpf(250)
.lpd(.25)
.gain(1.5)

//bass
$: note("<[f2 f3] [c2 c3] >").sound("gm_synth_bass_2")
  .gain(1)
  .lpf(500)

//drums
$: sound("hh bd hh bd [bd rim]").bank("RhythmAce").gain(1.75)