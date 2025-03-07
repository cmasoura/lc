# Strudel + Hydra Patch
## MTEC-343-001 Masoura

For this third assignment we had to produce a code that could be performed live. Therefore, this code is not supposed to be played with all parts being active simultaneously.

In this first line, we set the tempo (in cycles per second).

```javascript
setcps(0.5)
```

The next line is the basic harmony, same throughout the track, played by a muted electric guitar sample with a delay effect.
```javascript
$: chord("<Cm*2 [Ab Fm]>/2").voicing().room(.5).sound("gm_electric_guitar_muted").delay(0.5)
```

This line is the main riff of the song, and I'm using different values of a low pass filter to add some change in timbre.
```javascript
$: note("<[c3 d3 eb3 f3]*2 [c3 d3 eb3 f3 g3 eb3 f3 d3] [c3 d3 eb3 f3]*2 [ab3 g3 f3 eb3 d3 c3 b2 g2]>")
  .sound("gm_pad_warm").lpf("700 800 900 1000 1100 1200 1300 1200 1100 1000 900 800 ").gain(2).adsr("0:1:1:0.1").delay(0.2)
```

In the end of the song, this main riff line is substituted by the following, in order to give the feeling of a final cadence.
```javascript
_$: note("<[c3 d3 eb3 f3]*2 [c3 d3 eb3 f3 g3 eb3 f3 d3] [c3 b2 c3 d3 eb3 f3 eb3 d3] [c3 b2 c3 d3 g3 f3 eb3 d3] c2>").sound("gm_pad_warm").lpf("700 800 900 1000 1100 1200 1300 1200 1100 1000 900 800 ").gain(2).adsr("0:1:1:0.1").delay(0.2)
```

Here's our rhythm section (bass, drums, and two hi-hats). Jade Rose who listened to my performance, suggested the idea of the white noise hi-hat for a more vintage vibe, which was a great addition (so credits to her for that).
```javascript
$: note("<[C2 C3]*8 [[Ab1 Ab2]*4 [F1 F2]*4]>/2").sound("gm_synth_bass_2").gain(1.2)

$: s("bd*4").bank('RolandTR909').dist("1:1")

$: s("~@14 hh hh").bank('RolandTR808').gain(0.7)
$: s("white*8").decay(0.07).gain(0.7)
```


In many parts of the song, there are also secondary elements that can be added: a sequence, a "helicopter" effect that enforces the beat, and a static tonic chord.
```javascript
$: note("[C5 Bb4 Ab4 g4]*4").sound(" z_triangle").gain(1).pan(sine).phaser("<1 2 4 8>")


$: note("<c>*16").sound("< gm_helicopter>").gain(3)


$: note("c4,c6,g6,c7").sound("zzfx").gain(0.1)
```

And last, but not least, this is the main melody (with its variation), and a guitar solo that plays before the final bead drop (something like a bridge).
```javascript
$: note("<[c4@3 [d4 eb4]] [c4@3 [d4 eb4]] [c4@3 [d4 eb4]] [bb4@3 g4] [f4@3 [g4 f4]]  eb4 ~ d4>*2").sound("gm_fx_atmosphere").gain(1.4)
_$: note("<[c4@3 [d4 eb4]] [c4@3 [d4 eb4]] [g4 eb4 ~ eb4] [ab4 eb4 g4 eb4] [c4@3 [d4 eb4]] c4@3 >*2").sound("gm_fx_atmosphere").pan(sine).gain(1.2)


$: note("<eb4 g3 c4 [c4|d4|g4]>").gain(0.5).sound("gm_distortion_guitar")
```


I also used two different visual patches on Hydra and changed their scale parameters (0.899-0.999) to create different shapes. For these two amazing patches I am crediting their two creators, Marianne Teixido and Flor de Fuego.

```javascript
await initHydra()

voronoi(8,1)
.mult(osc(10,0.1,()=>Math.sin(time)*3).saturate(3).kaleid(200))
.modulate(o0,0.5)
.add(o0,0.8)
.scrollY(-0.01)
.scale(0.89)
.modulate(voronoi(8,1),0.008)
.luma(0.3)
.out()

src(o0)
 .saturate(1.01)
 .scale(.899)
 .color(1.11,1.01,1.01)
 .hue(.01)
 .modulateHue(src(o1).hue(.3).posterize(-1).contrast(.7),2)
  .layer(src(o1)
         .luma()
         .mult(gradient(1)
               .saturate(.9)))
  .out(o0)

noise(1, .2)
  .rotate(2,.5)
  .layer(src(o0)
  .scrollX(.2))
  .out(o1)

render(o0)
  ```
