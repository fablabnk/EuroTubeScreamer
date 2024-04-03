This project is a Eurorack version of the [AionFX Stratus](https://aionfx.com/project/stratus-classic-overdrive/)

The original schematic can be found in the [PCB-Only Build Doc PDF](https://aionfx.com/app/files/docs/stratus_documentation.pdf)

The main issues in modifying the design to Eurorack format are:
- converting 12v to 9V (maybe using a LM7809)
- adding CV to the potis or using a 3.2 mini jack with an opener, so that CV would replace the Poti
- using smaller jacks and potentiometers

The ADC Inputs section of the [Daisy.patch schematics](https://daisy.nyc3.cdn.digitaloceanspaces.com/products/patch/ES_Daisy_Patch_Rev4.pdf)  might give some clue as to how to combine CV Inputs and pots.


See also: https://modwiggler.com/forum/viewtopic.php?t=87748