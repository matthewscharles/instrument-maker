This file describes the set of PD examples found in this folder.

[Link to Synthesiser](#Synthesiser)

# Synthesiser

---



## scale

**Inputs**: 

1. continuous control (light sensor or dial)

Objects: `im.sensor`,`im.scale`, `im.sawtooth`, `im.speaker`

`im.sensor` reads data from the analog inputs on our control board (in this case sensor number 1).

Use the `im.scale` object to output a set of notes within a particular key and/or [musical mode](https://blog.landr.com/music-modes/).

The `im.sawtooth` object creates a sawtooth oscillator: a constant, buzzing tone. The pitches at which it plays are determined by the output of `im.scale`.  The number of pitches to played is determined by the second argument of `im.sensor`.

The sawtooth object must be connected to `im.speaker` to produce a sound.

___



## scale + volume

**Inputs**: 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: `im.sensor`,`im.scale`, `im.sawtooth`, `im.volume`,`im.speaker`

By placing an `im.volume` object in-between `im.sawtooth` and `im.speaker`, we can use a second sensor input to turn the intensity of the sound up or down.

If we use a button, the sound will be turned on or off (like pressing a key on a piano).  With a continuous control like a light sensor, the sound will turn up and down smoothly (like a theremin).

------



## scale + filter

**Inputs**: 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: `im.sensor`,`im.scale`, `im.sawtooth`, `im.filter`,`im.speaker`, `sig~`

------



## scale + filter + lfo

**Inputs**: 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: `im.sensor`,`im.scale`, `im.sawtooth`, `im.filter`,`im.speaker`, `im.lfo`

------



## scale + filter + lfo + controls

**Inputs:** 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: `im.sensor`,`im.scale`, `im.sawtooth`, `im.filter`,`im.speaker`, `im.lfo`

------



## (coming soon: envelopes)

------



# Looper