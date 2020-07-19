**Instrument Maker** is an open source framework for digital instrument building with sensors, for [Pure Data](http://puredata.info/) running on embedded computers such as [Bela](http://bela.io) or [Raspberry Pi](https://www.raspberrypi.org/) + [Arduino](https://www.arduino.cc/).  

<!--Some rough documentation is being generated here: <https://instrumentmaker.org/im-reference/>.-->

# Key pages:

- [**Learning Pd through Instrument Maker**](documentation/manual/learning-pd-through-im.md) (work in progress)
- [**GitHub repo**](https://github.com/matthewscharles/instrument-maker/)
- [**Instrument Maker Communication Symbols**](https://instrumentmaker.org/instrument-maker-symbols/)
- [**Wiki: development notes.**](https://github.com/matthewscharles/instrument-maker/wiki)  
<!-- - **[Education Makers version](https://github.com/educationmakers/instrument-maker)** (development in an education technology context with Milieux Institute). -->

Distributed under the terms of the **GNU Public license version 3**.

Instrument Maker is a tool for rapidly creating what is often described as accessible music technology (AMT), by using established programming languages and affordable hardware to create standalone instruments.  Its parameters have been chosen to reflect the options usually requested in music workshop settings: easily assignable musical scales or key, flexibility around root notes and available ranges of notes, and input from a range of interfaces such as distance sensors and switches.

Through this framework, we hope to ensure more people have direct access to the act of coding and customisation.  All too often in instrument development settings such as hackathons, it is assumed that the setup of a new instrument will be the domain of a specialist separate from a musician as an end user.. more specifically in accessibility contexts, this maintains the divide between non-disabled specialists creating resources for disabled people.

This is not an attempt to make the process easier in a way that detracts from artistic integrity, nor is it an attempt to force independence — rather, our intention is to establish options for more people to engage with the creation of music technology from a more accessible starting point.  

The core code was developed by [Charles Matthews](http://ardisson.net/), initially through workshops in collaboration with [Gift Tshuma](http://www.utchoir.com/) and [Roybn Steward](https://www.robynsteward.com/music). Follow [Blurring the Boundaries](http://www.blurringtheboundaries.org/) for news of future events.  

<!--Thanks to [Roybn Steward](https://www.robynsteward.com/music), [Education Makers](http://www.educationmakers.ca/), and [Dave Darch](http://alittlelearning.org/) (+ many more) for testing the code and helping generate documentation.-->

---

Read more about the philosophy behind this framework on the [Bela.io blog](https://blog.bela.io/2019/08/20/towards-disabled-artist-led-music-technology-charles-matthews/).

---

![The key ingredients of the instrument maker framework are sensors, musical scales, effects, and code.](documentation/readme-images/im-sensors.png)

---

## How does it work?

Although Instrument Maker was designed as a complete workshop package including hardware, the main resource is a library of objects for [Pure Data](http://puredata.info/) that can be used independently.  We are currently looking for users to test and use the code before returning to a more integrated approach.

Having downloaded the library, create and connect building blocks in the form of obects with the `im.` prefix: e.g. inputs, outputs, tuning systems, processors, and synthesisers. 

Upload this code to Bela, or use a Raspberry Pi with an Arduino-type device connected.  

![The Instrument Maker objects in Pure Data sit on a white screen, featuring minimal outlined boxes with black connecting lines. The boxes are labelled: input, scale, sinewave, volume, and they are connected to further boxes labelled echo and output. The lines are drawn from the top, through each of the boxes in various inlets and outlets, into a box labelled output.](documentation/readme-images/im-scale.png)

## How does it differ from regular Pd?

Our focus is on a separation between graphical interface and interactions - there are no on-screen objects that act as sliders or buttons, as we encourage users to work toward physical outcomes.  Of course, this decision in itself represents more access barriers, but we're working on something a bit more integrated.

Instrument Maker objects are named through something we feel is a bit closer to "plain English", or rather the kind of language we might expect to use in a workshop setting with non-specialists.  That's not to say there is anything wrong with the abbreviations found in Pure Data and similar language, we're just trying to cut down on explanations for that initial experience.

Pure Data code relies on a user placing arguments immediately after an object name, in a particular order. Our latest updates introduce the idea of non-case-sensitive parameters that can be placed in any order.  We are also introducing more conventional units such as Hz, ms, and note names.

All Instrument Maker objects run at audio rate, and we have deliberately omitted the tilde (~) usually used to distinguish this process. However, for people running later versions of Pd, many objects will accept "control"-style messages.

Note: Instrument Maker is designed to run on Pd Vanilla — all of our objects are based on recombinations of the core Pd objects rather than C code, and so should work on libPd based platforms such as Bela without the need for any external libraries.  This also means that the back end should provide a field day for people learning to patch in more depth in Pd — but the legibility at this level is a longer term project!!

----

# Installation

***This is for our current demo setup for desktops/RPi- Deken release and instructions for Bela coming soon!***

We recommend using [Patchbox OS](https://blokas.io/patchbox-os/) for Raspberry Pi.

## **Recommended: clone this repo**

- Clone the repo to a local folder by opening a terminal:
  - `git clone https://github.com/matthewscharles/instrument-maker`
  - *On a Mac, you might be required to download developer tools. There is no need to install Xcode if prompted.*
  - Keep up to date by periodically typing `git pull` within the folder in terminal.

## **Alternative: direct download**

Click the green Clone or Download icon at the top of the [GitHub repo](https://github.com/matthewscharles/instrument-maker) to download a zip file.  If you choose this option, you will need to download updates manually in the future.

## **Installation**

- Install [Pure Data](http://puredata.info/downloads) Vanilla

  - *On a Mac, you may need to right-click on the downloaded application to open it.*

- Add the instrument-maker folder to the search path in Pure Data: click new, and browse to the folder you cloned to.

  ![](documentation/readme-images/add-path.png)

  ![](documentation/readme-images/add-path2.png)

- Find a list of objects by opening `_im-current-objects.pd` from the main folder

- Right-click on the objects found here to open help files.  Make sure you press `ctrl-E` to enter edit mode before clicking on any boxes!

![a list of current objects](documentation/readme-images/current-objects-pd.png)
