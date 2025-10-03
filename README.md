# Z Elektrik KiCad parts
Welcome to Z Elektrik KiCadv9 EDA Public library.

## Description
These libraries contains components, which are mostly used in the Z Elektrik, with additional fields as:
- MFG (Manufacturer name)
- MPN (Manufacturer Part Number). Libraries are atomic type (besides Generic library), due this even simple resistor have own MPN
- Device marking. Very Helpfull for small SMD devices as SOT-23.
- Technology. Field with filled values: SMD/THD/Mechanical/Graphical, which can create BOM more precise. Ex: Assembly THD only.
- Order code for LCSC, Mouser, RS, TME, Farnell, DigiKey, and SOS
- Unique Z Elektrik's internal stock ID. Use of this library for place assembly order to our company, make setup process in easy way :-) .

**Content**
All libraries listing with attributes in the open document format file, you can find here: [Library_Listing](https://docs.google.com/spreadsheets/d/176wO_S8_nby6Lyd8MGY-Abj0bwKNF8hLd7M2Ny2Cflg/edit?usp=sharing)

## Install
You can use git client to clone repository, or [download](https://github.com/Z-Elektrik/LIB/archive/refs/heads/main.zip) zip file and unpack content with folder structure to your KiCad library folder (e.g. "Documents/Zele-KiCad-Libs").

Open the KiCad->Menu->Preferences->"Configure Paths dialog" and add variables:
- Z_LIB_3D_DIR and set path to 3D folder of downloaded files
- Z_LIB_FOOTPRINT_DIR and set path to PCB folder of downloaded files
- Z_LIB_SYMBOL_DIR and set path to 3D folder of downloaded files

Next open "Manage symbol libraries" from same menu and click to small folder icon "Add existing library to table", point to inside downloaded SCH folder and select all files (CTRL+A).
Do same action for footprint libraries.
Enjoy!
 

## Refresh latest version from github
Due to the continually add a new elements to libs, is good refresh libs before use it.

Process is same as install, but itsn't need to add global variable to paths dialog, and before add library in the "Manage symbol/footprint library" dialog, is need to remove all libs with Z_LIB prefix in the path. 




## Details
### Symbols libraries
Library name convention like: **FUNCTION_PARAMETERS_MANUFACTURER**
- FUNCTION: Audio, Capacitor, EMI, Fuse, Header, IC, Inductor, Jumper, Mechanical, Opto, Power, Relay, Resistor, Sensor, Switch, Terminal,...
- PARAMETERS:
   - for capacitors can be technology (SMD/THD), Package size or LeadSpan, Voltage rating, tolerance and used material
   - for resistors can be technology (SMD/THD), Package size or LeadSpan, Power rating, tolerance, stability
- MANUFACTURER:
   - Name of manufacturer ex: Samsung, Panasonic etc. If part is not atomic (haven't MPN), as manufacturer can be entered "Generic"

**Used Reference Designators**
Used RefDes's letters should meet function's class code according to IEC/EN 81346-2. 
[Here is it](Library_Listing.ods)


