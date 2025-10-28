# Z Elektrik KiCad Parts

Welcome to the Z Elektrik KiCad v9 EDA Public Library.

## Description

These libraries contain components that are mostly used in Z Elektrik projects, with additional fields such as:

* **MFG** (Manufacturer name)
* **MPN** (Manufacturer Part Number). The libraries are of the *atomic* type (except the Generic library), therefore even a simple resistor has its own MPN.
* **Device marking.** Very helpful for small SMD packages such as SOT-23.
* **Technology.** A field with values like SMD / THD / Mechanical / Graphical, which helps generate a more precise BOM (e.g., “Assemble THD only”).
* **Order codes** for LCSC, Mouser, RS, TME, Farnell, Digi-Key, and SOS.
* **Unique Z Elektrik internal stock ID.** Using this library when placing an assembly order with our company makes the setup process much easier. :-)

**Content**
A complete list of all libraries with attributes (in OpenDocument format) can be found here:
[Library_Listing](https://docs.google.com/spreadsheets/d/176wO_S8_nby6Lyd8MGY-Abj0bwKNF8hLd7M2Ny2Cflg/edit?usp=sharing)

## Installation

You can use a Git client to clone the repository, or [download](https://github.com/Z-Elektrik/LIB/archive/refs/heads/main.zip) the ZIP file and extract its contents (keeping the folder structure) to your KiCad library folder (e.g., “Documents/Zele-KiCad-Libs”).

Then open **KiCad → Menu → Preferences → Configure Paths** and add the following variables:

* `Z_LIB_3D_DIR` — set the path to the 3D folder of the downloaded files
* `Z_LIB_FOOTPRINT_DIR` — set the path to the PCB folder of the downloaded files
* `Z_LIB_SYMBOL_DIR` — set the path to the SCH (symbols) folder of the downloaded files

Next, open **Manage Symbol Libraries** from the same menu, click the small folder icon **“Add existing library to table”**, navigate to the downloaded SCH folder, and select all files (Ctrl+A).
Repeat the same for the footprint libraries.
Enjoy!

## Updating to the Latest Version from GitHub

Since new elements are continuously being added, it’s a good idea to refresh the libraries before use.

The process is the same as installation, but there is no need to re-add global variables in the Paths dialog.
Before adding the library in the “Manage Symbol/Footprint Library” dialog, remove all libraries with the `Z_LIB` prefix from the list.

## Details

### Symbol Libraries

The naming convention is:
**FUNCTION_PARAMETERS_MANUFACTURER**

* **FUNCTION:** Audio, Capacitor, EMI, Fuse, Header, IC, Inductor, Jumper, Mechanical, Opto, Power, Relay, Resistor, Sensor, Switch, Terminal, etc.
* **PARAMETERS:**

  * For capacitors: technology (SMD/THD), package size or lead span, voltage rating, tolerance, and material.
  * For resistors: technology (SMD/THD), package size or lead span, power rating, tolerance, stability, etc.
* **MANUFACTURER:**

  * Manufacturer name, e.g., Samsung, Panasonic, etc.
  * If the part is not atomic (has no MPN), “Generic” can be used as the manufacturer.

### Reference Designators

Reference designators should follow the functional class codes according to **IEC/EN 81346-2**.
[You can find them here.](https://docs.google.com/spreadsheets/d/e/2PACX-1vSQrfTI6g8CGJz_kQ2h6NA4STcINRSNWpEIgMftyWNZnPfuyPHBXPfnJIhNQU6JdZVPvYBZkwLYq0Yu/pubhtml?gid=1922460605&single=true)
