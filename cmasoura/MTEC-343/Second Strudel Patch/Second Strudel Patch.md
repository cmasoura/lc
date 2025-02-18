# Second Strudel Patch
## MTEC-343-001 Masoura

'''javascript
$: note("<c3 e3  d3 bb3>,<e3 g3*2 f3 d3>,<g3*2 b3 [a3 g3] [f3 d3]>,<b3 d4 c4 a3>")
  .sound('sawtooth').lpf(perlin.range(300,500)).lpq("<0 2 5 10>").pan(sine.slow(2)).color("magenta")._pianoroll()

$: n("0 <1 4> 2 3").palindrome().scale("<C:major E:phrygian d:dorian bb:lydian>")
  .sound("gm_electric_guitar_jazz").phaser("<1 2 4 8>").gain(1.5).delay(0.5)

$: n("<[0!6 1 0] 4*8 [0!6 [0 6] 0] [0 6 0 2]*2>").scale("<C:major E:phrygian d:dorian bb:lydian>")
  .sound("gm_epiano2").jux(rev).delay(0.5).lpf("<700 800 900 1000>").gain(0.7)

$: note("<[~ [c4,e4,g4,b4]] [~ [b3,d4,e4,g4]] [~ [d5,f5,a4]] [~ [d5,fb5,a4]]>")
  .sound("gm_electric_guitar_muted").delay(0.7).room(.5).color("#D6FF00")._pianoroll({ labels: 1 })

//bass
$: note("[C2 C3]!2 C2 [C2 C3]!2 C2 [C2 C3]!2").sound("gm_electric_bass_pick").lpf("<900 1200>").slow(2)



//drums
$: s("[bd bd] <[hh sh*2] [~ hh]> [~ rim|sd*3] <hh hh*2 - hh*3>").gain(0.9).bank("rolandcompurhythm1000").color("#7a015e")._pianoroll({ labels: 1 })
$: s("[hh*16?]").gain(perlin.range(0.1,0.3)).jux(rev).color("#a723b5").pianoroll()
$: s("bd*4").gain(0.5)
  '
