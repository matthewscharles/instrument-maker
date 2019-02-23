# About Instrument Maker

This is an open source framework for digital instrument building with sensors, with improving access in mind. For [Bela](http://bela.io) / Raspberry Pi.  Currently developed by Charles Matthews through a series of collaborations - get in touch if you would like to contribute!

Distributed under the terms of the GNU Public license version 3 (for now  / not sure how appropriate / need to read up on this).

This is one of my first public repos and will definitely be messy for a little while.  The current version is not ready for public consumption (see the technical notes below); please feel free to explore the code, and download and try out the abstractions if you are familiar with Pure Data..but I recommend waiting a little while until everything's more coherent.



## How does it work?

Within Pure Data, create objects with the im. prefix to access building blocks: inputs, outputs, tuning systems. Upload to Bela, or Raspberry Pi with an Arduino-type device connected.  With Bela, choosing a setup should be a case of dragging and dropping into a browser; files can exist as "presets", no need to edit or look at the code unless desired.

Video demo (code): https://youtu.be/8AJMJq2P8Ko

Video demo (mobile): https://www.youtube.com/watch?v=jl020N0MZxk

Video demo (play): https://www.youtube.com/watch?v=ywEX0N6TpEA

An accompanying hardware component is in development, which adds crocodile clip access to the Bela platform.

### What's Pure Data, why use it this way?

Pure Data is a free, open source, visually oriented programming language. Otherwise known as dataflow ("the flowchart is the program").  Boxes that serve particular functions are joined together, sending messages back and forth, some of which can be sound that eventually gets sent out to speakers.

It's not a million miles away from the ["blocks"](https://en.wikipedia.org/wiki/Block_(programming))-type programming currently popular in education. I'm interested in how Pure Data can be used in a similar way, but without the complexity of trying to make everything from scratch: getting caught up in "spiders' webs" or a blank screen on day one — which are the experiences I often observe when teaching this.

Pure Data has an active online community with [forums](https://forum.pdpatchrepo.info/) and a [Facebook group](https://www.facebook.com/groups/4729684494/), where it's possible to discuss problems and ideas.

## Background

My intention is to help find a different entry point to instrument creation using sensors. I'm reluctant to use the term "accessible music technology" to describe this; while I respect others that do, I don't currently think it's all that helpful a term in abstract (I hope this will form a move toward Disabled artist-led music technology: essentially the same idea, but implies a different power relationship).  But that's certainly a context in which some of this project's output will fit. Access or accessibility tend to rely upon openness, and benefit from opportunities for input at every stage of the design process.

So, ideally, this should provide an opportunity/context for someone to approach the problem of creating an instrument, rather than (necessarily) learning a programming language. Conversely, it shouldn't remove access to the underlying code..whether that's through a nicely packaged GUI, or a closed source back end. That's not necessarily the easiest problem to solve!  We're starting to see a bit more of this appearing in commercial software; Max for Live is a good example.

A few considerations:

- remove obligation to code, but with opportunities to learn and dismantle 
- offer ways to create objects that feel like instruments, rather than controllers: devices that have a direct, local connection between physical input and output, without mediation from a keyboard and mouse (and added costs on that front)
- retain ability to make complex, difficult-to-master instruments
- options for expression beyond pitch, duration, and loudness by default; music is about more than playing notes and chords (obvious maybe, but AMT doesn't always look beyond this)
- integrate a variety of tuning systems
- expand access through ability to modify and create derivatives.

I don't identify as a coder, but I care enough about this stuff to want to make it. Plus I have pretty intense ADHD and find it difficult to let things go. Instrument Maker pulls together material from around fifteen years of lectures, collaborative projects, and artistic output ([Light Recorders](http://ardisson.net/a/?page_id=440) and [Augmented Gamelan](http://augmentedgamelan.com)). Portions of this work were developed with the support of Drake Music: the Kellycaster, DMLab innovation challenges, and the [Planted Symphony installation](http://www.drakemusic.org/our-work/artistic-development/projects-commissions/planted-symphony/).  I'm excited to think that this might form the basis for some much wider collaboration.

Some of this code was originally developed for Max/MSP, and can possibly be made available on request; it's a bit much to develop on the two platforms in parallel right now.  This sits alongside a couple of other projects that live in other repositories: the [Light Recorder Deck](https://github.com/matthewscharles/Light-Recorder-Deck) (for DMX light control), and Accessible Music Technology Framework (an Arduino library with similar aims, currently on hold).  

# Technical notes

At present, I anticipate that in order to use this framework effectively, you'll need to download an SD card image for a Bela or Raspberry Pi (available soon). This is in part due to reliance on external libraries, which would need better documentation to install from scratch. Furthermore, on the Raspberry Pi, we need instructions to boot directly to the software.

For the time being, the "source code" is available here.  If you want a disk image to test, just let me know.  Version tracking is kind of limited due to the nature of Pd files, but I'm trying to break it down enough that we can observe changes in units/abstractions.

## Interaction with sensors

Pure Data running on Bela is a thing of beauty: sensor inputs are treated as audio information.  Analog inputs are accessed through the `[im.input]` abstraction (with an argument matching the analog input), and connected directly to a virtual instrument.

At present, the most flexible way to recreate this experience with a Raspberry Pi (also a thing of beauty, in its own way, and a bit cheaper) appears to be through an affordable Arduino board running Firmata. In practical terms, this requires dropping in an `[im.firmata]` object, which tells the `[im.input]`objects to look at Arduino inputs rather than the Bela's audio ADC.

### Interaction with actuators?

No reason not to, and my initial attempt included a lot of this! But focussing on audio output keeps it simple for now.  

### MIDI output/what if I just want to make a controller?

As above..but there are lots of great things that do this already, and this was the focus of the accompanying AMT Arduino library.

## Objects/abstractions in current demo

| Name                         | Vanilla? | Needs (easy fixes in italics)                                |
| ---------------------------- | -------- | ------------------------------------------------------------ |
| im.generatescale             | y        |                                                              |
| im.input                     | y        |                                                              |
| im.key                       | y        |                                                              |
| im.midiin                    | y        |                                                              |
| im.output                    | y        |                                                              |
| im.reverb                    | n        | freeverb~ (yeah, I cheated for now)                          |
| im.sample                    | y        | -                                                            |
| im.scala & scala2 (internal) | n        | *counter*, *gate*, *tosymbol*, *fromsymbol*, zl: *iter*, *group*, *len*, *join*, sect, *reg*, *rev* |
| im.scale                     | n        | zl: *reg*, *len*, *lookup*                                   |
| im.sensor                    | y        |                                                              |
| im.tunedperc                 | n        |                                                              |
| im.tuning                    | n        |                                                              |

## Tuning/Scala

The framework uses the [Scala](http://www.huygens-fokker.org/scala/) format to retrieve tuning systems, which may be useful for storing scales as well.  This could fit into (or replace) JSON as described below.

Please note: if you got as far as reading this section, there's a possibility that I don't care about microtuning as intensely as you do.  I can dig that. Think I'm mishandling this stuff? Let me know :)

Tuning is transferred to a table accessible at audio rate with interpolation if needed (I think this has potential for some subtley freaky modulation sources).

## Reliance on Cyclone library/ current todo list

I would like to make this available to work on Pd Vanilla, to simplify the installation procedure and ensure compatibility with libpd-based contexts, e.g. [MobMuPlat](http://danieliglesia.com/mobmuplat/). At present, I use the Cyclone library as this makes Pd a lot more accessible to me coming from a Max background.  

I'm looking for ways to recreate the following objects using Vanilla.  Since the addition of new list functionality, some of this is more about breaking out of old habits, so I'll include this as something of a todo list for now. I guess it could form part of a useful resource for Max heads in the future. 

- **zl**: I'm pretty sure that all of the below can be handled with the generic list object, but some of these operations desperately need encapsulating
  - I've created a `[for]` object (with argument ++ or --), which takes in a list or integer to create a for loop based on the input/length..this makes patching a bit nicer and a bit more like text-oriented code
  - **zl reg**: more specifically, I use this to retrieve a symbol-based argument within an abstraction. Works fine with `[list store]`
  - **zl group**: (a bit more than) just `[append]` and bang
    - fixed by creating `[list.group]`
  - **zl join**: `[list append]` or `[list prepend]`
  - **zl lookup**: like `[list store]`, with a `get $ 1` message
  - **zl len**: `[list length]`
  - **zl sect**: `[list split]`? — not quite, need to compare..this is the sort of thing that usually gets quite complicated/frustrating in Pd.
  - **zl iter**: recursive `[list split]` with `[until]`? — see serialization example (3) in the help file
    - solved by creating `[list.iter]` - takes argument ++ or -- to iterate up or down through the list (only one entry at a time at present)
  - **zl rev**: probably a combination of `[list split]` and `[list prepend]` as above with iter
    - solved by creating `[list.rev]`
  - **zl rot**: as above
    - solved by creating `[list.rot]`
- **gate** and **switch**: with arguments for multiple inlets/outlets..should be ok but might need to establish a reasonable maximum number.
- **tosymbol**: is it really just a case of `[list prepend symbol] -> [list trim]`? Or is this stuff actually useful after all? Switching between types in Pd has been a thorn in my side..
- **fromsymbol**: this one is potentially tougher..maybe I don't yet understand how symbols and lists are processed differently in Pd yet.
- **counter**: should be easy enough, certainly the way I use it here. Pd 101 with added arguments.
- **rampsmooth~**: ugh..this one will be tough to live without, I use this for everything. Maybe look at [source code](https://github.com/porres/pd-cyclone/blob/master/cyclone_objects/binaries/audio/rampsmooth.c) and use something like `[fexpr~]`? Maybe there's another way.
- **svf~**: unfortunately this is an easy way to make filters with audio modulation that will be similarly difficult to let go.
- **scale**: I think this should be `[expr ($f1 * (($f5 - $f4) / ($f3 - $f2))) + $f4]` 
  - created `[im.map]` using the above.

Interested in using some Max-style attributes…some potentially useful info [here](https://forum.pdpatchrepo.info/topic/10892/collect-all-arguments-as-a-list/7).

## JSON file format

I'm keen for this to use the JSON format to promote compatibility with other platforms. I use the PuRestJson external available for Pd, which works OK. Considering writing a parser with Vanilla objects, but really, is that going to end well?  

Update: yes, turns out that the `[text]` object is great for this!! Nested structures now working in read mode (still a bit hacky), haven't attempted to format and write a JSON file yet.  The search function looks like it could be quite powerful.

## Accessibility/misc documentation

-Some instructions involving the help browser could be useful, as could Henri Bisognini's autocomplete plugin

-How do we make this screen reader compatible?

-How could we make a symbol-based version?