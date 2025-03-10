//jacqmeus inspored score by Mitchell Kedi

const dot = slider(16,0,24,1)
//piano lead melody
$: n(irand(12).segment(16).ribbon(dot,1).degradeBy(.2).ribbon(0,1))
  .scale("f:major:pentatonic")
  .s("piano").velocity("[.50 [.79 | .75 | .66]]*2")
  .slow(2)
  .gain(1.5)
  .lpf(slider(290,0,900,10))
  .room("<1 3!4>/16")

//chord pads
$: chord("<F C C7 F>/4").anchor('F3')
.voicing()
.sound('gm_ocarina')
.off(.2, x=>x.velocity("<.4 .2 .3>*8"))
.room(.8)
.delay(.1)
.gain("< [.3 .4 .6] .7 .7!8>/16")
.mask("<1 1 1!8>/16".early(.05))
.lpf(550)

//more pads
$: n("[1 2 5 1]").chord("<F C>/4")
.voicing()
.sound("sine")
.fm("1 3 5")
.fmattack(".3 .7 2")
//.fmh("1 3 7 8")
.velocity(.66)
.room("<1 2!4>/16")
.mask("< 1 1!4>/16".early(.05))


/// sparkly thingy
$: n(rand.range(0,14).segment(6)) .scale("f4:major:pentatonic") .s("gm_guitar_harmonics").phaser("5")
.pan("<.5 1 .5 0>").crush(5).room("1").delay("1").postgain(".1").degradeBy("0.5").fast(2).gain(.4)



$: s("shaker_small").segment(8).sometimesBy(".14", x => x.ply("2 | 4")).gain(.9)



await initHydra()
//s0.initScreen()
//src(s0).out()
// above code is for fashion show "Jacqmeus Fall Winter 2024/2025"
//link to fashion show: https://youtu.be/u5D7qPC_wGQ?si=BMRWFBFDwnzgx0Ew

//filler visuals since couldn't find a way to upload video as background without glitching
// licensed with CC BY-NC-SA 4.0 https://creativecommons.org/licenses/by-nc-sa/4.0/
//Visuals by Olivia Jack
// https://ojack.github.io

osc(4, 0.1, 0.8).color(1.04,.1, -1.1).rotate(0.30, 0.1).pixelate(2, 20).modulate(noise(2.5), () => 1.5 * Math.sin(0.08 * time)).out(o0)


//const parts = [piano chords extra shaker]
//i tried to do the thing they showed us to cue parts without actually updating everytime but i got stuck 
//$: pick(parts,"<[piano chords shaker]*4")
