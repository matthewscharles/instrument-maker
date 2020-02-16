Thanks to Robyn Steward for creating this list of currently used IM objects:



Explanations will be added below as time goes on.

# `im.sensor`

`im.sensor` reads data from the analog inputs on our control board.

**Arguments:** sensor number, multiplier

1. **sensor number**: the sensor number to try, 
2. **multiplier** *(optional)*: by default the sensor outputs a range of 0-1.  Use the multiplier to expand this range. For example, type 10 for a range from 0-10.  When connected to im.scale, the multiplier used will equal the number of notes possible to produce. 

**Examples:** 

- `im.sensor 3 1`: read the values from input number 2 with a range from 0-1
- `im.sensor 1 100`: read the values from input number 1 with a range from 0-100
- `im.sensor 6` : read the values from input number 6, with a range from 0-1.

____

# `im.scale`

Use the `im.scale` object to play a set of notes within a particular key and/or [musical mode](https://blog.landr.com/music-modes/).

**Arguments**: root note, scale/mode, starting octave

1. root note: 

___

`Blank object` description

**Arguments:** -

1. 

**Examples**:

- `im.` : description