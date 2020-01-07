# Learning PD with Instrument Maker

## Introduction

### What is PD (Pure Data)?

Pure Data (PD for short) is a free, open source [dataflow](https://en.wikipedia.org/wiki/Dataflow_programming) programming language. 

- Create and connect objects on-screen, rather than writing lines of text code.
- Pure Data is friendly to many musicians because it can feel similar to connecting instruments and effect pedals.
  - By changing the order in which the pedals (or objects) are connected, we can change the sound produced.
  - Sometimes this way of organising information can lead to a more playful approach.


#### Why use Pure Data?

Pure Data is free and open source, meaning that members of the community can edit the code and create their own versions of the software.

Pure Data code can be applied in a variety of music making contexts, including the web, audio apps for Android and iOS, and running on embedded computers like the Raspberry Pi and Bela.

### What is Instrument Maker?

Instrument Maker is a toolkit for making music quickly with sensors.  This includes a library for Pure Data: a set of objects that have been designed as an introduction to audio coding. 

The core aim is to enable beginners to make a wide range of sounds in a musical context, within a matter of minutes. The user should receive a basic idea of how dataflow programming works, but fulfil the goal of making sound with some commonly accepted musical qualities (e.g fitting to the notes of a scale) as soon as possible.  It is then up to the individual to decide whether they wish to dig deeper into the programming itself.

Instrument Maker objects can be used alongside regular Pure Data objects, so that the transition to usual Pure Data objects can take place gradually.

## Hardware resources

At present, the Instrument Maker code functions best with the following items:

- Arduino (made easier with an Instrument Maker shield)
- Touch Board
- Bela
- Raspberry Pi

Although these resources can be used to control motors, lights, and other outputs, at present the Instrument Maker library is designed to work one way: to convert sensor information into audio signals (whether you prefer to think of this as vibration, sound, or music). 

Therefore, apart from microphones and speakers any external connection mentioned below can be assumed to be a sensor input. 


## Anatomy of a Pure Data object

Each object has a **name**, **arguments**, **inlets**, and **outlets**.

<!--Name-->

<!--Arguments-->

<!--Inlets-->

<!--Outlets-->

All objects must have a name. Objects from the Instrument Maker library start with the letters im.

For people that have worked with other (text-based) programming languages, it might be useful to picture an object and its arguments like this: 

name(argument, argument) 

or, more concretely: 

sensor(1, 12)
scale(C, major)

Unlike contemporary languages like Swift, the names of arguments are not written down, meaning that the user must remember what each argument does (and the order in which they need to be written), or consult a reference.  

Information flows one way in Pure Data: downwards. Inlets can only be connected to outlets -- an inlet can not be connected to another inlet. 

Not all objects have the same numbers of inlets or outlets. Furthermore, some might only have an inlet or an outlet.  For example, the im.speaker object only has an inlet, because the output takes place in the physical world.

Multiple objects can be connected to each other -- so, for example, a single sensor input can be used to control several sounds or parameters. 

## Key concepts

### Signal flow

### Instrument elements

- Note/velocity vs. continuous controls
  - Flute
  - Piano
  - Theremin
  - Gamelan

## First steps in Pure Data 

### Creating and connecting objects 

Make a new object:

Press **ctrl** and **1** on the computer keyboard, or go to the **put** menu at the top of the window and choose **object**.

Type the name of the object into the box.

Type any arguments required.

Click outside the object to finish the box, or press **ctrl** and **1** to create another object — this will be connected automatically if your object has an outlet.

### Basics: connecting a microphone

Create a microphone object (im.microphone)

Create a speaker object (im.speaker)

Join the microphone and speaker with a cable

## Key objects

### im.sensor

***No inlet***

**Outlet:** sensor reading

**Arguments:**

1. the name or number of the input to read from
2. multiplier

The multiplier can be used to set how many notes are played (when combined with im.scale)

### im.speaker

**Inlet:** the signal to go to the speaker

**Outlet:** no outlet

***No arguments***

No 



## Examples

Depending on interest of the user, the following are recommended starting points for using Instrument Maker:

- "Theremin mode"
- Envelope follower
- Pitch tracker
- Loop pedal

## Making the transition from Instrument Maker

### Pure Data

- Sequencer

### Physical circuits

- Voltage divider circuit

## Glossary

- **Amplitude** — the strength of a signal (often equivalent to volume)
- **Arduino** — a circuit board computer that can be programmed to receive sensor data, control actuators, and  can be embedded in devices.
- **Bela** — 
- **Chord** —
- **Circuit** —
- **Controller** —
- **Crossfade** —
- **Dataflow** —
- **Distortion** —
- **Echo** —
- **Effect** —
- **Electrode** —
- **Envelope** —
- **Envelope follower** —
- **Fader** —
- **Feedback** —
- **Frequency** —
- **Filter** —
- **Granular synthesis** —
- **Inlet** —
- **Interval** —
- **Key** —
- **Loop** —
- **Looper** —
- **Major** —
- **Milliseconds** —
- **Minor** —
- **MIDI** —Musical Instrument Digital Interface
- **Mixer** —
- **Mode** —
- **Object** —
- **Open source** —
- **Noise** —
- **Parameter** --
- **Physical modelling** —
- **Patch** —
- **Pitch** —
- **Pitch tracker** —
- **Plugin** —
- **Reverb** —
- **Sampler** —
- **Sawtooth wave** —
- **Sensor** —
- **Signal flow** —
- **Sine wave** —
- **Speaker** —
- **Scale** —
- **Theremin** —
- **Touch Board** —
- **Triad** —a chord consisting of three notes.
- **White noise** —
- **Velocity** —
- **Volume** —

## References/learning resources

- [Programming electronic music in Pd](http://www.pd-tutorial.com/) (Johannes Kreidler)
- Designing Sound

## Notes for experienced PD users

The Instrument Maker set of objects/abstractions are almost exclusively based on audio connections.

There are only two elements available: objects and cables.  This reinforces a deliberate separation of interface and code. Users are not encouraged to use GUI objects (including messages) in the initial stages, which might feel counter-intuitive to some people!

Instrument Maker objects are created in Vanilla for maximum compatibility.

Input is roughly equivalent to "pin" on an Arduino or Bela board.