
# First Strudel Patch
## MTEC-343-001 Masoura

'''javascript
$: s(`<bd [bd hh]> <hh*2 [ht mt]> [rim|cp] <hh [hh oh] [~ hh]*1.5 hh*3>`)
.bank("RolandCompurhythm1000")

$: s("bd sd").delay(.5).gain(0.5).bank("CasioRZ1")

$: s("hh*16?").gain("[.15 1]*4").jux(rev).bank("RolandTR808").room(.3)

$: s(`rim ~ rim ~ rim rim ~ rim rim ~ rim rim ~ rim rim ~,
     ~ ~ cp ~ cp ~ ~ ~ cp ~ ~ cp ~ ~ cp ~
    `)
  .cpm(120/8).bank("RolandTR808")
  .ply("<1 2 2 1>").gain(0.5)

$: sound("<[[bd!110] [bd!131]] [[[bd!146.8]  [bd!164.6]]!2]>").lpf("<50 100>")
  '
