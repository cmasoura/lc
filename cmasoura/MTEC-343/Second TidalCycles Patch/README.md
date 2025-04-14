# **Second TidalCycles Patch**
## Christina Masoura - MTEC-343-001

This patch is a simple one containing a drum section, a bass, a chordal part, melody and a sound effect.

The bass is a simple 4 on the floor kick, with a slight change in timbre.
```javascript
d1 $ sound "bd*4" # n "<0 4>"
```
The hi-hat plays weak beats in 6/8 time.
```javascript
d2 $ s "~ hh ~ ~ hh*2"
```

The bass is a pedal note with a low pass filter controlled by a sine wave.
```javascript
d3 $ s "bass:0*8" # lpf (range 200 5000 $ sine) |-12

The chordal part is a C major - E minor progression.
```javascript
d4 $ slow "2" $ note "c'maj e'min" # s "gtr"
```

A repetitive melody.
```javascript
d5 $ note "0 4 7 5 4 9" # s "supermandolin"
```
And the fire sound effect!
```javascript
d6 $ slow 8 $ s "fire"
```
