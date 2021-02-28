# Seeds Chord Organ
This is firmware for the [Ginkosynthese Seeds](https://www.ginkosynthese.com/product/1070494/seeds-assembled) that adds a chord organ as an extra voice.

The chord organ is composed of four slightly detuned sawtooth waves, able to be played in a variety of different chords.

This firmware was based upon V1.1 of the manufacturer's firmware.

## How to install

This firmware should be installed to the module by the standard method as found on the [Ginkosynthese website](https://www.ginkosynthese.com/firmware).

Once the firmware is uploaded, you should be able to access the chord organ via sound 9.

## Included Chords

Sound 9 includes the following chord qualities, listed in order from the counterclockwise knob position to the clockwise knob position:

 1. ![Octaves](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-03.png)
 2. ![Unison](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-04.png)
 3. ![Stacked Perfect Fourths](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-05.png)
 4. ![Sus4](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-06.png)
 5. ![Major](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-07.png)
 6. ![Major 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-08.png)
 7. ![Dominant 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-09.png)
 8. ![Minor 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-10.png)
 9. ![Minor Major 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-11.png)
 10. ![Augmented](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-12.png)

## Changing the Chords

If you would like to change the included chords in this module, you can do that by altering the `chords[][]` array in the `.ino` file. The non-equal-temperment version is set as the following:

```
const uint16_t chords[][4] = {
  { 256, 128, 256, 512},  // 8ves
  { 256, 256, 256, 256},  // unison
  { 256, 341, 455, 607},  // stacked perfect 4ths
  { 256, 384, 512, 683},  // sus4
  { 256, 384, 512, 640},  // major
  { 256, 384, 483, 640},  // major 7th
  { 256, 384, 455, 640},  // dominant 7th
  { 256, 384, 455, 614},  // minor 7th
  { 256, 384, 483, 614},  // minor major 7th
  { 256, 406, 512, 645},  // augmented
};
```

The data for each chord is represented by a sub-array of four numbers. You may alter these numbers to change the chord quality.
Each number controls the pitch of one voice. The number is the ratio between the frequency of the root of the chord and the frequency of the voice in question, multiplied by 256.
A list of these numbers for each of the 24 semitones above the root can be found above the array in the source code. Alternatively, you may work out the ratios mathematically, and use any tuning system that you want.

Though all of the chords included have the same root note, there is no requirement in the code for that to be the case, so you should be able to make chords have different roots.

You can also change the number of chords by adding or removing sub-arrays. In this case, be sure to update the `num_chords` variable to match the number of chords in the array.
