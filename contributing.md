The instrument maker library is meant to be used by beginners in workshops and hackathons.  

Please bear this in mind when adding or modifying documentation.

Here are some of the broader conventions (work in progress):

# Naming objects

Object names should be as short and intuitive as possible.  Avoid technical jargon unless this is necessary to understand the object, or a key concept for a beginner to learn.  

Consider creating "synonyms" for common variations.  See the files for im.tunedperc and im.tunedpercussion for an example of how to wrap this.

At present, all objects use the prefix `im.` and are entirely lower case.

If creating an object, consider checking the list of existing Pd objects to avoid clashes, in case we decide to drop this prefix at a later date.

## "Utility" objects

There is a small selection of utilities I have written to emulate externals within vanilla (see for example the `list` files, `stof`). I haven't yet established a naming convention for these, but if an object needs to be added without inclusion in the main object list, the help file template used should be im.utils.helptemplate.pd (see below)

# Conventions and saving

Save all objects to the `im.objects` folder.

## Inlets and outlets

 Add `fwd` as the first argument to inlets to enable the new outlet for messages in Pd 0.51+

Include functions of inlets and outlets as additional arguments (purely for descriptive purposes - Pd ignores these). 

e.g. 

`inlet~ fwd 1 trigger in`

`outlet~ 1 signal out`

Try to match inlet numbering with arguments where possible.

## Arguments and parameters

Instrument Maker uses a custom argument/parameter system. At present, this involves manually copying and pasting a block of code at the top-right of most patches (documentation tbc, as I hope to move this into an abstraction and/or update to the new pdcontrol system in version 0.5x).

Instead of using $x variables directly, please include the utils.get.args object with the following format

`utils.get.args $0 [argument number starting at 1] [parameter name]`

For example, these three objects could form parameters for a filter delay:

`utils.get.args $0 1 cutoff`

`utils.get.args $0 2 resonance`

`utils.get.args $0 3 delaytime`

All case differences and dots will be stripped from the parameter, so the user can type delaytime, delayTime, delay.time (or even dE.L.A.Y.T.i.M.e) as preferred.

## Graph on parent

Open the object in a text editor.  Add this line to the end of the file to make sure the user does not open the source patch by accident:

`#X coords 0 -1 1 1 15 15 1 0 800;`

Every time you are ready to commit, in the first line, remove the font size (the fifth number following canvas) e.g.

`#N canvas 0 23 450 300` **10**`;`

This is probably unworkable for now, so I'll try to make a script to automate the process.

Please don't make these modifications to the corresponding help files.

# Help files

Help files should be saved in `im.objects` with the same name as  `(objectname)-help.pd`

See the help-templates folder for examples of the help files.

## Position

Save files viewed on your main screen if working on two monitors, as this information is saved to the patcher (I'm not sure if this can be an issue with other platforms, but I think sometimes the window position will not be compensated on Linux).

## Including sound/media

Sounds are currently stored in /sounds/ within the im.objects folder.

## Modifying multiple files

Consider using Atom to find and replace across the entire project folder:

<https://flight-manual.atom.io/using-atom/sections/find-and-replace/>

I am working on some templates and scripts to automate help file generation — get in touch if there's something you feel needs automating or would be interested in contributing to this side of things.

# Indexing

## Deken object list

The objectlist file `instrument-maker.txt` should be updated for inclusion in the Deken release.

After the object name, include a description of the object within the context of Pd, to complement the more accessible descriptions in the main flow.