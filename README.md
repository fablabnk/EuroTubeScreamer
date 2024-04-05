This project is a Eurorack version of the [AionFX Stratus](https://aionfx.com/project/stratus-classic-overdrive/)

The original schematic can be found in the [PCB-Only Build Doc PDF](https://aionfx.com/app/files/docs/stratus_documentation.pdf)

The main issues in modifying the design to Eurorack format are:
- converting 12v to 9V (maybe using a LM7809)
- adding CV to the potis or using a 3.2 mini jack with an opener, so that CV would replace the poti

The ADC Inputs section of the [Daisy.patch schematics](https://daisy.nyc3.cdn.digitaloceanspaces.com/products/patch/ES_Daisy_Patch_Rev4.pdf)  might give some clue as to how to combine CV Inputs and pots.

See also: https://modwiggler.com/forum/viewtopic.php?t=87748

# Reproducing the Schematic

See `EuroTubeScreamer.kicad_sch` for the intial reproduction.

Some questions and answers:
- What do 'in' and 'out' represent? I guess the signal from the 1/4" jack tips? In the 'wiring diagram' section we can see that there are two PCBs, a main board and a bypass board
- 100R and 220R mean 100Ω and 220Ω respectively
- The diodes on the schematic don't a value, but they are 1N914's
- Why are there two LEDs?

For a couple of components there were no matching symbols i.e.
- for the 2N5088 transistor I am substituting 2N3904
- for the JRC4558D dual op amp I am substituting the RC4558
I will double check the details later to see if these subsitutions are appropriate.

# Power distribution in the schematic

To create the RA and RB power sources the recommended approach is to first place a standard +9V power source (or any other named source), then edited its symbol and change both it's label (at the top) and pin name (right in the centre) to RA/RB.

To me, when deriving RA and RB from the +9V the power is an output, whereas in other parts of the circuit when I'm using it, it is an input. But for now I used the same symbols, all with Pin Properties -> Electrical type: Power input

# Next steps

- assign footprints for the pots, jack inputs, switches and LEDs
- try to make a basic layout for the front panel and PCB