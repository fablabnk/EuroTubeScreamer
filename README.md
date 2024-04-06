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
- What do 'in' and 'out' represent? I guess the signal from the 1/4" jack tips?
	- I guess I need to replace these with 
	- In the 'wiring diagram' section we can see that there are two PCBs, a main board and a bypass board
	- Schematic for the bypass board is here: https://aionfx.com/app/files/docs/3pdt_bypass_documentation.pdf
	 
- 100R and 220R mean 100Ω and 220Ω respectively
- The diodes on the schematic don't a value, but they are 1N914's
- Why are there two LEDs in the main board schematic?
- In the bypass board schematic, we have a 3PDT footswitch, but no inbuilt schematic symbol or footprint for it
	- what will we replace this with in a eurorack context - guess just a normal 3PDT switch

https://github.com/benwis/SparkFun-Kicad-Libraries

For a couple of components there were no matching symbols i.e.
- for the 2N5088 transistor I am substituting 2N3904
- for the JRC4558D dual op amp I am substituting the RC4558
I will double check the details later to see if these subsitutions are appropriate.

## Power distribution

To create the RA and RB power sources the recommended approach is to first place a standard +9V power source (or any other named source), then edited its symbol and change both it's label (at the top) and pin name (right in the centre) to RA/RB.

To me, when deriving RA and RB from the +9V the power is an output, whereas in other parts of the circuit when I'm using it, it is an input. But for now I used the same symbols, all with Pin Properties -> Electrical type: Power input

# Next steps

1. [DONE] Assign footprints for the pots, jack inputs, switches and LEDs
2. Make a basic layout for the front panel and PCBs
	- There will likely be two PCBs, one for the front panel components and one for the
3. Complete the circuit by solving the main issues
	- Getting power from 12V down to 9V
	- Combining voltages from input pots + CV input jacks
	- Ensuring the inputs and outputs are at eurorack levels (10V)
4. Route the circuit

# Workflow

# Things I learned

- Two projects cannot be opened side by side in one instance of KiCad, instead to you have create a new instance e.g. right click on app icon and choose `New Window`
- Once the two projects are opened in this way, you can copy elements between them
- To wire the switches to the PCB using hookup wire I created a new footprint called `TwoHole_Connector` consisting simply of two pads

# Power

For now I'm:
- bringing in +12V from eurorack PSU
- connecting it to where the 9v came in, in the original circuit
- creating a 10V ref to be used to keep our CV input/pot in the right rack (10vpp)