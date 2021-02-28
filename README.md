# Seeds Chord Organ
This is firmware for the [Ginkosynthese Seeds](https://www.ginkosynthese.com/product/1070494/seeds-assembled) that adds a chord organ as an extra voice.

The chord organ is composed of four slightly detuned sawtooth waves, able to be played in a variety of different chords. You can change the root note of the chord via the "Tune" knob or "Pitch" input of your module, and alter the quality of the chords using the "Mod" knob.

This firmware was based upon V1.1 of the manufacturer's firmware.

## How to install

This firmware should be installed to the module by the standard method as found on the [Ginkosynthese website](https://www.ginkosynthese.com/firmware).

Once the firmware is uploaded, you should be able to access the chord organ via sound 9.

## Included Chords

Sound 9 includes the following chord qualities, listed in order from the counterclockwise knob position to the clockwise knob position:

| --- | --- | --- |
| 1. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q1.wav) | ![Octaves](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-03.png)  |
| 2. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q2.wav) | ![Unison](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-04.png) |
| 3. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q3.wav) | ![Stacked Perfect Fourths](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-05.png) |
| 4. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q4.wav) | ![Sus4](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-06.png) |
| 5. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q5.wav) | ![Major](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-07.png) |
| 6. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q6.wav) | ![Major 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-08.png) |
| 7. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q7.wav) | ![Dominant 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-09.png) |
| 8. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q8.wav) | ![Minor 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-10.png) |
| 9. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q9.wav) | ![Minor Major 7th](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-11.png) |
| 10. | [Audio](https://trainzack.github.io/seeds-chord-organ-pages/Demo/Q10.wav) | ![Augmented](https://trainzack.github.io/seeds-chord-organ-pages/Ginkosynthese%20Chords%20Diagram-12.png) |

## Altering the Tuning

By default, the chords are laid out in equal-temperment. However, there exists an option to use just intonation for the chords. Simply comment out the line `#define EQUAL_TEMPERAMENT` in the `.ino` file before uploading the firmware to the module, and it will use just intonation for the chords.

Note that the just intonation chords will sound more in tune with themselves, but might clash more with other notes.

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
