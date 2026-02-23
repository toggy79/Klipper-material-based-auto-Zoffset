# Klipper-material-based-auto-Zoffset
This is klipper macro wich sets Z offset based on defined material values. Useffull for precise Zoffset tuning.
You need klipper and some type of probe.

In order this to work you need to parse material variable from Orca slicer to start_print macro.

PRINT_START BED_TEMP=[bed_temperature_initial_layer_single] EXTRUDER_TEMP=[nozzle_temperature_initial_layer] MATERIAL=[filament_type]

These are my Orca slicer printer, machine gcode. I use PRINT_START instead START_PRINT..IT IS OPTIONAL, NAME MUST BE SAME AS THE MACRO.
Last line MATERIAL sends material info to START_PRINT macro.

How to use:
copy or upload **mat_zofset.cfg** file to your klipper config.
add a include at start of your printer.cfg

<img width="253" height="42" alt="image" src="https://github.com/user-attachments/assets/a8dcaecb-01e4-45ec-82f8-805d04a102ce" />


at start of your start_print macro call it by this command:

DETECT_MATERIAL MATERIAL={MATERIAL}

<img width="545" height="300" alt="image" src="https://github.com/user-attachments/assets/c040225d-7deb-425c-9d2f-4c26010e1af9" />


That line just checks for material and displays info at terminal. It also checks for type of bed. Smooth or textured and adds correction for textured bed.
Real correction is done AFTER the bed mesh.

<img width="263" height="70" alt="image" src="https://github.com/user-attachments/assets/4addf427-6726-4721-9bd9-66fef2006117" />

After bed mesh line add command: APPLY_Z_OFFSET_MATERIAL
Turn of SET_GCODE_OFFSET Z=0.0 line if you got it inside startprint macro.

Command APPLY_Z_OFFSET_MATERIAL makes babby step adjustment to Z in order to get same Zoffset for same type of material. It displays info at terminal. Every PLA will have the same zofsset, PETG zofset will be same for all petg-s, etc...

You need to tune values from macro:

<img width="341" height="210" alt="image" src="https://github.com/user-attachments/assets/8f96483d-e029-4360-92b0-c0390b48ef52" />

Those values are based on your probe calibration. Not same for everyone.
Tip: zerro all the values and write new ones. Make some simple single layer object and print,adjust in real time zofset with klipper buttons

<img width="456" height="121" alt="image" src="https://github.com/user-attachments/assets/433a754c-e770-479c-9ee6-0741466643ff" />
and after succesfull first layer for given material write down that value to macro. Minus values are closer to the bed , positive are further, all based on your probe ofset.
Some people asks what is the point of this? You can fine tune Zofset, all is done in real time, no storing values, your probe calibratin holds same value.
I print on a mirror, so i can see the difference. 

Enjoy.

toggy79



