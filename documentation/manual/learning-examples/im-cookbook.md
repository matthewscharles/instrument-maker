This file describes the set of PD examples found in this folder.

[Synthesiser](#Synthesiser)

For all examples, buttons can be substituted with outputs from `im.keypress` or `im.makeymakey`

# Synthesiser

---



## scale

**Inputs**: 

1. continuous control (light sensor or dial)

Objects:[ `im.sensor`](im-objects.md#imsensor),[`im.scale`](im-objects.md#imscale), `im.sawtooth`, `im.speaker`

`im.sensor` reads data from the analog inputs on our control board (in this case **sensor 1**).

Use the `im.scale` object to output a set of notes within a particular key and/or [musical mode](https://blog.landr.com/music-modes/).

The `im.sawtooth` object creates a sawtooth oscillator: a constant, buzzing tone. The pitches at which it plays are determined by the output of `im.scale`.  The number of pitches to played is determined by the second argument of `im.sensor`.

The sawtooth object must be connected to `im.speaker` to produce a sound.

___



## scale + volume

**Inputs**: 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: [ `im.sensor`](im-objects.md#imsensor),[`im.scale`](im-objects.md#imscale), `im.sawtooth`, `im.volume`,`im.speaker`

By placing an `im.volume` object in-between `im.sawtooth` and `im.speaker`, we can use a second sensor input to turn the intensity of the sound up or down.

If we use a button, the sound will be turned on or off (like pressing a key on a piano).  With a continuous control like a light sensor, the sound will turn up and down smoothly (like a theremin).

------



## scale + filter

**Inputs**: 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: [ `im.sensor`](im-objects.md#imsensor),[`im.scale`](im-objects.md#imscale), `im.sawtooth`, `im.filter`,`im.speaker`, `sig~`

------



## scale + filter + lfo

**Inputs**: 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**: [ `im.sensor`](im-objects.md#imsensor),[`im.scale`](im-objects.md#imscale), `im.sawtooth`, `im.filter`,`im.speaker`, `im.lfo`

------



## scale + filter + lfo + controls

**Inputs:** 

1. continuous control (light sensor or dial)
2. continuous control or button

**Objects**:[ `im.sensor`](im-objects.md#imsensor),[`im.scale`](im-objects.md#imscale), `im.sawtooth`, `im.filter`,`im.speaker`, `im.lfo`

------



## (coming soon: envelopes)

------



# Looper

Make sure a microphone or line is plugged in for these examples!

## plain looper

**Inputs:** 

1. button
2. button

**Objects**:[ `im.sensor`](im-objects.md#imsensor), im.microphone, im.looper, im.speaker

This example sends a microphone into the looper to record. Press and hold the button attached to **sensor 1** to record, and press and hold the button attached to **sensor 2** to play back.  These buttons will record and play back for amount of time they are held down.

For "glitchy" loop effects, try pressing button 1 while button 2 is held down!

------



## looper + pitch

**Inputs:** 

1. button
2. button
3. continuous control (dial or light sensor)

**Objects**:[ `im.sensor`](im-objects.md#imsensor), im.microphone, im.looper, im.speaker

Add a dial or light sensor to **sensor 3** to change the pitch.  Since the pitch starts at 0, the sound will not be audible until the sensor receives some information.

* note - the pitch control might be quite slow, only reaching about half speed — try the next example to speed it up!

------

## looper + extremepitch

02c-looper+extremepitch.pd

**Inputs:** 

1. button
2. button
3. continuous control (dial or light sensor)

**Objects**:[ `im.sensor`](im-objects.md#imsensor), im.microphone, im.looper, im.speaker

This time, using the second argument (multiplier) on `im.sensor 3`, the changes in pitch should be quite extreme!  In this version, the pitch dial is multiplied by . Try replacing this with higher or lower numbers.

------

