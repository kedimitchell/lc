const dot = slider(13,0,24,1)

$: n(irand(12).segment(16).ribbon(dot,1).degradeBy(.2).ribbon(0,1))
  .scale("f:major:pentatonic")
  .s("piano").velocity("[.50 [.79 | .75 | .66]]*2")
  //.lpf("<100 200 300 400 500 600 700 800 900 1000 1100 1200 1300 1400 1300 1200 1100 1000 900 800 700 600 500 400 300 200>/4")
  .slow(2)
  .gain(1.5)
  .lpf(330)
  .room("<1 3!4>/16")

_$: chord("<F C C7 F>/4").anchor('F3')
.voicing()
.sound('gm_ocarina')
.off(.2, x=>x.velocity("<.4 .2 .3>*8"))
.room(.8)
.delay(.1)
.gain("< [.3 .4 .6] .7 .7!8>/16")
.mask("<1 1 1!8>/16".early(.05))
.lpf(550)

_$: n("[1 2 5 1]").chord("<F C>/4")
.voicing()
.sound("sine")
.fm("1 3 5")
.fmattack(".3 .7 2")
//.fmh("1 3 7 8")
.velocity(.66)
.room("<1 2!4>/16")
.mask("< 1 1!4>/16".early(.05))


/// sparkly 
$: n(rand.range(0,14).segment(6)) .scale("f4:major:pentatonic") .s("gm_guitar_harmonics").phaser("5")
.pan("<.5 1 .5 0>").crush(5).room("1").delay("1").postgain(".1").degradeBy("0.5").fast(2).gain(.4)


_$: s("bd!16?").gain(0.3).bank("RhythmAce")
  .decay(0).sustain(0)
  .coarse(32)
  .distort("10:.3")
  .postgain(.3)

_$: s("shaker_small").segment(8).sometimesBy(".14", x => x.ply("2 | 4")).gain(.6)

await initHydra()
//s0.initScreen()
//src(s0).out()

// licensed with CC BY-NC-SA 4.0 https://creativecommons.org/licenses/by-nc-sa/4.0/
//visuals by Asdrúbal Gomez

noise(3,0.1,7)
.rotate(1,-1,-2).mask(shape(20))
.colorama(0.5)
.modulateScale(o0)
.modulateScale(o0,1,)
.blend(o0)
.blend(o0)
.blend(o0)
.blend(o0)
.out(o0)
//s(white!16).gain(0.5).decay(sine.mul(0.015).fast())

//const parts = [piano chords extra shaker]


//$: pick(parts,"<[piano chords shaker]*4")
