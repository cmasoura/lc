# Second Strudel Patch
## MTEC-343-001 Masoura

For the second Strudel patch, I wanted to create a loop that I could then present in a live coding setting, gradually building up its different parts.

I have separated the code in **three parts**, harmony, bass, and drums. I tried to use many different functions, and after finishing with the music, I wanted to add some simple pianoroll visualizers to make it prettier and more engaging.

In the **first part**, I have four different layers of harmony and melodies. I used different built-in samples. I also used room, delay, lpf, pan, phaser, gain, jux, range and palindrome functions.

```javascript
$: note("<c3 e3  d3 bb3>,<e3 g3*2 f3 d3>,<g3*2 b3 [a3 g3] [f3 d3]>,<b3 d4 c4 a3>")
  .sound('sawtooth').lpf(perlin.range(300,500)).lpq("<0 2 5 10>").pan(sine.slow(2)).color("magenta")._pianoroll()

$: n("0 <1 4> 2 3").palindrome().scale("<C:major E:phrygian d:dorian bb:lydian>")
  .sound("gm_electric_guitar_jazz").phaser("<1 2 4 8>").gain(1.5).delay(0.5)

$: n("<[0!6 1 0] 4*8 [0!6 [0 6] 0] [0 6 0 2]*2>").scale("<C:major E:phrygian d:dorian bb:lydian>")
  .sound("gm_epiano2").jux(rev).delay(0.5).lpf("<700 800 900 1000>").gain(0.7)

$: note("<[~ [c4,e4,g4,b4]] [~ [b3,d4,e4,g4]] [~ [d5,f5,a4]] [~ [d5,fb5,a4]]>")
  .sound("gm_electric_guitar_muted").delay(0.7).room(.5).color("#D6FF00")._pianoroll({ labels: 1 })`
```

In the **second part**, I have a tonic pedal bass, with some rhythmic interest. I also use some timbre differentiation with the low pass filter function.

```javascript
$: note("[C2 C3]!2 C2 [C2 C3]!2 C2 [C2 C3]!2").sound("gm_electric_bass_pick").lpf("<900 1200>").slow(2)
```

In the **third part**, I have a kick line, a hi-hat line, and one more elaborated drum line, to use in different parts of the loop.

```javascript
$: s("[bd bd] <[hh sh*2] [~ hh]> [~ rim|sd*3] <hh hh*2 - hh*3>").gain(0.9).bank("rolandcompurhythm1000").color("#7a015e")._pianoroll({ labels: 1 })
$: s("[hh*16?]").gain(perlin.range(0.1,0.3)).jux(rev).color("#a723b5").pianoroll()
$: s("bd*4").gain(0.5)
  ```

For this patch, the original idea was to have some sort of a spoken word sample, but I couldn't add it to my code from an external source. This is something that I want to have in a future edit. 
