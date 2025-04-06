# **First TidalCycles Patch**
## Christina Masoura - MTEC-343-001


This week was oriented more on learning the syntax of TidalCycles and its differences and similarities to Strudel, rather than being more creative on the patch.
I've made a simple pattern with a drums, bass, and two lead elements.

First, setting the cycles per second (60 bpm).

```javascript
setcps 1
```
Then, here's the simple bass pattern, and a delayed clap in triple time.
```javascript
--drums
d1 $ sound "[[bd*2],[~ sd],[hh/2]]" # gain 1.5
d2 $ sound "cp" # delay 0.8 # delaytime (1/6) # delayfeedback 0.6 # lock 1 # gain 0.8
```

The bass with a simple quarter pattern.
```javascript
--bass
d3 $ note "c2!2 g2 as2" # sound "superreese"
```

And finally, the two lead elements, one using the sampled numbers in different speed and pan orientations, and the otherone using the iter and run functions, playing part of a c minor pentatonic scale. 
```javascript
--1234
d4 $ every 4 (hurry 2) $ sound "numbers:1 numbers:2 numbers:3 numbers:4" # pan "0 0.5 1 0.5"

--synth
d5 $ iter 8 $ n (run 4)  # sound "arpy"  |-12
```
