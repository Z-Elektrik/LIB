# Z-Elektrik KiCad Libraries

## Jazyk / Language

- [Slovensky](#slovensky)
- [English](#english)

---

# Slovensky

Vitajte v **Z-Elektrik/LIB** — verejnej knižnici komponentov pre [KiCad](https://www.kicad.org/).

Knižnica obsahuje súčiastky používané pri návrhu elektroniky so zameraním na praktické použitie vo výrobe. Obsahuje nielen symboly a púzdra, ale aj výrobné a nákupné informácie:

- výrobca a objednávacie číslo (MFG / MPN)
- označenie súčiastky (Device marking)
- typ technológie (SMD, THD, Mechanical...)
- objednávacie kódy pre distribútorov
- interný identifikátor Z-Elektrik

Kompletný popis štruktúry knižnice, pravidlá pomenovania a ďalšie informácie nájdete vo Wiki:

[Z-Elektrik/LIB Wiki](https://github.com/Z-Elektrik/LIB/wiki)

Zoznam aktuálne dostupných prvkov knižnice:

[Library Element List](https://docs.google.com/spreadsheets/d/176wO_S8_nby6Lyd8MGY-Abj0bwKNF8hLd7M2Ny2Cflg/edit?usp=sharing)

Otázky, návrhy alebo všeobecnú diskusiu môžete riešiť v GitHub Discussions:

[Z-Elektrik/LIB Discussions](https://github.com/Z-Elektrik/LIB/discussions)

Problémy v knižnici alebo požiadavky na doplnenie nových prvkov môžete nahlásiť cez GitHub Issues:

[Z-Elektrik/LIB Issues](https://github.com/Z-Elektrik/LIB/issues)


## Inštalácia

Knižnicu môžete nainštalovať:

- klonovaním repozitára pomocou Git,
- alebo stiahnutím ZIP archívu a zachovaním pôvodnej štruktúry priečinkov.

V KiCade nastavte:

**Preferences → Configure Paths**

nasledujúce premenné:

| Premenná | Cesta |
|---|---|
| `Z_LIB_3D_DIR` | priečinok s 3D modelmi |
| `Z_LIB_FOOTPRINT_DIR` | priečinok s footprintmi |
| `Z_LIB_SYMBOL_DIR` | priečinok so symbolmi |

Potom pridajte knižnice:

**Preferences → Manage Symbol Libraries**  
→ pridajte všetky knižnice zo zložky `SCH`

**Preferences → Manage Footprint Libraries**  
→ pridajte všetky knižnice zo zložky `PCB`


## Licencia

Z-Elektrik/LIB je licencovaná pod licenciou  
[CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P v2)](https://ohwr.org/cern_ohl_p_v2.txt).

Knižnicu môžete používať, upravovať a ďalej distribuovať v súlade s podmienkami tejto licencie.

---

Udržiava **Z-Elektrik**


---

# English

Welcome to **Z-Elektrik/LIB** — a public component library for [KiCad](https://www.kicad.org/).

The library contains components used for electronics design with a focus on practical manufacturing use. It provides not only symbols and footprints, but also production and purchasing information:

- manufacturer and part number (MFG / MPN)
- device marking information
- technology classification (SMD, THD, Mechanical...)
- distributor ordering codes
- internal Z-Elektrik identification

Complete documentation, naming rules, library structure, and usage information are available in the Wiki:

[Z-Elektrik/LIB Wiki](https://github.com/Z-Elektrik/LIB/wiki)

A complete list of available library elements:

[Library Element List](https://docs.google.com/spreadsheets/d/176wO_S8_nby6Lyd8MGY-Abj0bwKNF8hLd7M2Ny2Cflg/edit?usp=sharing)

Questions, suggestions, or general discussions can be handled through GitHub Discussions:

[Z-Elektrik/LIB Discussions](https://github.com/Z-Elektrik/LIB/discussions)

Issues in the library or requests for adding new components can be submitted through GitHub Issues:

[Z-Elektrik/LIB Issues](https://github.com/Z-Elektrik/LIB/issues)


## Installation

The library can be installed:

- by cloning the repository using Git,
- or by downloading the ZIP archive while preserving the original folder structure.

In KiCad open:

**Preferences → Configure Paths**

and add:

| Variable | Path |
|---|---|
| `Z_LIB_3D_DIR` | 3D model directory |
| `Z_LIB_FOOTPRINT_DIR` | footprint directory |
| `Z_LIB_SYMBOL_DIR` | symbol directory |

Then add the libraries:

**Preferences → Manage Symbol Libraries**  
→ add all libraries from the `SCH` folder

**Preferences → Manage Footprint Libraries**  
→ add all libraries from the `PCB` folder



## License

Z-Elektrik/LIB is licensed under the  
[CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P v2)](https://ohwr.org/cern_ohl_p_v2.txt).

You are free to use, modify and distribute this library according to the terms of the license.

---

Maintained by **Z-Elektrik**