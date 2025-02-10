# **First Strudel Patch**
## Christina Masoura - MTEC-343-001

For this first project, I tried to incorporate as many features of the basic Strudel syntax we covered in class, as well as certain other functions I found in the [strudel.cc](https://strudel.cc/workshop/first-sounds/).

The **first line** of my code is the basic drum pattern, which I tried to elaborate with some differentiation per cycle. For this, I am using the Roland CR-1000 sound bank, as I figured it sounded realistic and had a good balance in all its sounds.
```javascript
    $: s(`<bd [bd hh]> <hh*2 [ht mt]> [rim|cp] <hh [hh oh] [~ hh]*1.5 hh*3>`)
    .bank("RolandCompurhythm1000")
```
In my **second line** I am adding a second kick and snare, this time from the Casio RZ1 soundbank. I have lowered its gain with the .gain() function, so that it doesn't sound as loud as the main drum idea. I also added a delay effect using .delay(), so that the final patch sounds deeper.
```javascript
$: s("bd sd").delay(.5).gain(0.5).bank("CasioRZ1")

```
In the **third line**, I wanted 16th value beats, with a hi-hat. Here, I wanted a different sound than that of hi-hat of the first line, so I'm using the Roland TR808 soundbank. Here I used the ? function, so that sometimes the 16th beat is silent. I also used the .gain() function, so that I could achieve some dynamics variation. The .jux(rev) function is also very interesting, as it reverses the order of the sequence (which here doesn't make much difference, only in the dynamics) and also pans the sound.

```javascript
$: s("hh*16?").gain("[.15 1]*4").jux(rev).bank("RolandTR808").room(.3)
```

For similar results, we could also write this line like this, using the .pan(sine).
```javascript
  $: s("hh*16?").gain("[.15 1]*4").pan(sine).bank("RolandTR808").room(.3)
```
I didn't choose this however cause I couldn't find a way to make it sound like the jux but without reversing it. On the other hand, I still don't know how to use the jux() with something different than a rev argument.

The **fourth line** is a latin american Cáscara pattern, together with the 2/3 clave pattern. The pattern changes a little bit, with the doubling of the number of beats by the ply() function, but the pulse remains the same.

```javascript
$: s(`rim ~ rim ~ rim rim ~ rim rim ~ rim rim ~ rim rim ~,
     ~ ~ cp ~ cp ~ ~ ~ cp ~ ~ cp ~ ~ cp ~
    `)
  .cpm(120/8).bank("RolandTR808")
  .ply("<1 2 2 1>").gain(0.5)
```

The **fifth** and final **line** was the one I seriously considered to omit, but decided to put it here with a warning. It was my way of creating a bass line but only with the drum sounds. I took advantage of the great number of repetitions this interface can do, and made it play in pitch frequencies. However, this caused my session to crash several times, so it's definitely not the best thing to do.

```javascript
  $: sound("<[[bd!110] [bd!131]] [[[bd!146.8]  [bd!164.6]]!2]>").lpf("<50 100>")
```
