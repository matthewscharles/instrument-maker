The instrument maker library is meant to be used by beginners in workshops and hackathons.  

Please bear this in mind when adding or modifying documentation.

Here are some of the broader conventions (work in progress):

# Naming objects

Object names should be as short and intuitive as possible.  Avoid technical jargon unless this is necessary to understand the object, or a key concept for a beginner to learn.  

Consider creating "synonyms" for common variations.  See the files for im.tunedperc and im.tunedpercussion for an example of how to wrap this.

At present, all objects use the prefix `im.` and are entirely lower case

If creating an object, consider checking the list of existing Pd objects to avoid clashes, in case we decide to drop this prefix at a later date.

## "Utility" objects

There is a small selection of utilities I have written to emulate externals within vanilla (see for example the `list` files, `stof`). I haven't yet established a naming convention for these, but if an object needs to be added without inclusion in the main object list, the help file template used should be im.utils.helptemplate.pd (see below)

# Help files

Files should be saved in im.objects with the same name as  `(objectname)-help.pd`

See the help-templates folder for examples of the help files.

## Including sound/media

Sounds are currently stored in /sounds/ within the im.objects folder.

## Modifying multiple files

Consider using Atom to find and replace across the entire project folder:

<https://flight-manual.atom.io/using-atom/sections/find-and-replace/>

I am working on some templates and scripts to automate help file generation — get in touch if there's something you feel needs automating or would be interested in contributing to this side of things.

## Graph on parent

Open the object in a text editor and add this line to make sure the user does not open the source patch by accident:

`#X coords 0 -1 1 1 15 15 1 0 800;`

In the first line, remove the font size (the fifth number following canvas) e.g.

`#N canvas 0 23 450 300` **10**`;`

Please don't make these modifications to the corresponding help files.



# Indexing

## Deken object list

The objectlist file `instrument-maker.txt` should be updated for inclusion in the Deken release.

After the object name, include a description of the object within the context of Pd, to complement the more accessible descriptions in the main flow.