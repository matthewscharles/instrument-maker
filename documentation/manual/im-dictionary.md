# Instrument maker Dictionary 

Notes by Robyn Steward 22/11/19

***Common Terms*** 

**Tone** is used instead of thee word sound as sound implies you can hear it however instrument maker supports other ways of sensing the output of audio.

**Instrument maker is** a more user friendly way of accessing a  compute programming language called **pure data,** 

**when you write a programme  it will save as a .pd file** 

 **a programme is code to tell a computer what too do**

Anything that start im. Is called a object in this  context

To make a new object click put object or CTRL + 1 

When you create a object it will have inlets and inlets  this is so yu can  connect your objects together inlets are at the top outlets are at the bottom the number of inlets and outlets varies object to object

##  

## **Inputs**

**im.microphone** = line in or mic in NOT sensors

**im.linein** = same as above but may be easier to remember

**im.sensor =** input from a sensory including buttons , light sensors ,potentiometer, sensor pads anything that can be connected with crocodile clips

**im.electrode =** when using the instrument maker touchboard

## **Outputs**

**Ia tm.output =** mono audio

**im.speaker =** mono speaker

**im.belt or im.stap =** output to vibration source

##  

## **Sound Generators**

### **Basic sounds and oscillators**

Oscillator = a sound that changes between two or more tones.

**Im.noise or im.whitenoise** = white noise = every frequency at once at equal volume

**im.sinewave** = a sinewave is a continuous ohh sound like a teest tone  en the TV.

**im.sawtooth**= buzzing tone

### **Complex sound sources**

**im.hollow**= a fm oscillator  (frequency modulation) 

**Im.grains**  = a granular synthesizer means that sounds are cut up and rearranged quickly to make a new tone.

### **Instrument Maker Synthesisers** 

**Ready made tones**

**Im.fizzy** = fizzy 80”s sound

**Im.tunedperc** = Gamelan type sound (Gamalab is music from indonesia) 

**Im.acid** = acid house style synthesiser ( no connection to psychedelic drugs its a kind of music)

## **Signal processors** = something that can changes a sound

**im.filter** = low pass filter which means that only low sounds on the audio spectrum can pass through it meaning you want hear higher sounds from the instrumentor input you apply it to.

**im.echo** = echo’s/repeats the sound sometimes called a delay it has feedback

​		When using im.echo put a space between words and numbers **delay time**  (measured in  milliseconds e.g 5000= 5 seconds) feedback (how much of the echo is sent back into itself e.g100% would feedback 50% would be repeat in a relaxed manner)

**im.fader** = changes the volume of the signal  this can be putin different places e.g to the output speaker or to a effect , it can also be controlled by a sensor.

**im.volume =** put the % oof the volume you want e.g  im.volume 50% will make the sound going into it 50% quieter

**im.distort =** distorts sound like a distortion pedal e.g Boss SD1

**im.chorus** = Squeachey sound

**im.crossfade** = being able to alter the volume of 2 sounds being played at the same time in relation to each other e.g when you reduce the volume of ne sound the other sound playing will get louder and vica versa.

## **Audio triggers**

**im.envelopefollower** = uses the volume of a sound to control other parameters

**im.pitchtracker** = finds pitches in a sound connected to the input and uses this to control another oscillator or synthesiser

## **Samplers** = recording sounds or using pre recorded sounds to make music

**Im.looper** = recording a sound that will then repeat it can be turned on or off 

​	Used with a sensor to play or stop recorded sound repeating 

**Im.player =** plays a sound file e.g im.player string.wav file would need to be uploaded not a microcontroller in the same folder as the .pd file the files supported ar .wav or .aiff 

## Note generators = makes notes that adhere to musical rules 

**Im.scale =**   applies rules about what sounds are created so they adhere to weestern music theory.

-you need to use this with a input to change notes,sound generator but im.noise

-(  type note you want to start with C,C#,D,D#,E,Eb,F,F#,G,G#,Ab,A#,B,Bb)

-Then type type of scale major,minor, ionian, dorian, phrygian, lydian, mixolydian, aeolian and locrian blues and pentatonic scale 

-Starting octave 1,2 = sub woofers or vibration strap only)3,4,,5 or 6

example

**Im.scale** C minor 5

**Im.triads** = coming soon 