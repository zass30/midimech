# linnstrument-wholetone

"Alternating Whole-tone" layout and visualizer for the Linnstrument.  I consider this to be one of the most accessible and playable musical note layouts, and once you learn how it works, you'll realize why I've made it my primary layout.

This program is a work-in-progress so some things are only partially working.

Note: So far, this has only been tested on the LinnStrument 128 version.  If you own the 200-note version,
please let me know how this works for you and if there are any issues.

License: MIT

![Screenshot](https://i.imgur.com/F0VQU4F.png)

## Setup

- First create a midi loopback device.  You can do this easily with LoopMidi on Windows or using "Audio MIDI Setup / MIDI Studio" on Mac.  Then set your DAW to use this device instead of the linnstrument.  Make sure the virtual device you set up has "loopmidi" in its device name, since this is how its detected by the program.

- Set your LinnStrument to use ChPerRow mode.  (Or alternatively, see the section *MPE* for getting the full MPE mode working).

- Download the project by typing the following commands in terminal:
```
git clone https://github.com/flipcoder/linnstrument-wholetone
```

- Switch to the new project folder:
```
cd linnstrument-wholetone
```

- Install the dependencies:
```
pip install -r requirements.txt
```

- Run app.py.  You should see a window pop up with the layout.

- If this works, your linnstrument will show the colors of the wholetone layout and be playable in your DAW.

- If you're using the larger (200-note) version of the LinnStrument, click "SIZE" to use the full layout (experimental).

- Set your virtual instruments' pitch bend range to double the LinnStrument's value.

## How to Play

### Layout

Each row consists of a whole tone scale, separated by 4ths, which cause the rows to alternate.  It sounds strange at first but because of the layout's relation to the circle of 5ths, it makes a number of things easier to play and remember than the default chromatic layout.  It's much easier to demonstrate than it is to explain, so let's begin!

### Basic Scales

The major/minor scales are shaped with the "3-4" pattern.  3 notes on first row, then 4 notes on next row, then repeat moving over 1 space, making runs fit across the fingers easily.
Here's what it looks like:

```
4567
123
```

All the modes for this, (such as lydian, dorian, etc.) are accessible by picking a different starting note.

For example, if you start the scale on 6, it becomes a minor scale.

### Pentatonic Scales

Similarly, the pentatonic scale modes fit the "2-3" pattern:

```
345
12
```

### Melodic Minor Scale

Melodic minor has a "2-5" pattern:

```
34567
 12
```

You may notice that based on your starting note, the further left you go, the brighter the scale, and the further right,
the darker the scale.  This is because the alternating whole tone layout resembles a staggered circle of 5ths which corresponds with musical brightness.

## Basic Chord Shapes

The symbol 'o' is used for a pressed note to show the shape:

```
Major:
 o
o o

Minor:
o o
 o

Dim:
o
 o
  o
  
Aug:
o o o

Sus2:
 o
oo

Sus4:
oo
o
 
Maj7:
 o o
o o

m7:
 o
o o
 o
 
7:
o
 o
o o
```

Another interesting thing about this layout on the Linnstrument is you can walk up and down while holding major and minor 3rd intervals within a scale without lifting your fingers.
This technique is most useful for a piano sound or something where pitch shifting is disabled.

## More Scales

Once you become comfortable with this layout, you can introduce the harder scales into your playing:

### Blues Scale

```
4 6
 235
  1
```

Or:

```
 6
235
 1  4
```

### Harmonic Major Scale

This is the same 3-4 pattern, but the 6th note is flat:

```
6
 45 7
 123
```

Or:

```
 45 7
 123  6
```

### Harmonic Minor Scale

This one is a little tricky at first:

```
 6
345 7
 12
```

Or:

```
7
 6
 345
  12
```

You might prefer to think about this as a mode of Ionian Augmented intead, which is the 3-4 shape but with a sharp 5:

```
5
 4 67
 123
```

Or:

```
 4 67
 123 5
```

## Visualizer

Using this program, you can visualize the midi playing in your DAW on both the screen and LinnStrument.
You do this by creating another device in LoopMidi called "visualizer" then use a Midi Out plugin
on the track you want to visualize and set the plugin to use the visualizer midi device.

## MPE

(Note: This mode currently only works on LinnStrument 128)

To use ChPerNote/MPE mode, set your LinnStrument to "NO OVERLAP" with a transposition of -3 octaves and +6 pitch.
Then, set `no_overlap=true` in your settings.ini file (if you don't have one, copy it from settings.ini.example).
For some reason, these settings are required to get note 0 to be the lower left pad and the upper right to be 127.
Due to the midi note range being 0-127, this only works for the LinnStrument 128.  If you know of a workaround to this limitation, let me know.

## Pitch Bend

To get pitch bending working properly, you'll need to set your virtual instruments' pitch bend range to exactly double the amount
of the LinnStrument's range.
