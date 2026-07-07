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
- alebo stiahnutím ZIP archívu, jeho rozbalením do adresára a zachovaním pôvodnej štruktúry priečinkov.

V KiCade nastavte:

**Preferences → Configure Paths**

nasledujúce premenné:

| Premenná | Cesta |
|---|---|
| `Z_LIB_3D_DIR` | váš priečinok s rozbalenými 3D modelmi |
| `Z_LIB_FOOTPRINT_DIR` | váš priečinok s rozbalenými footprintmi |
| `Z_LIB_SYMBOL_DIR` | váš priečinok s rozbalenými symbolmi |

Potom pridajte knižnice:

**Preferences → Manage Symbol Libraries**  
→ pridajte všetky knižnice zo zložky `symbols`

**Preferences → Manage Footprint Libraries**  
→ pridajte všetky knižnice zo zložky `footprints`


## Licencia

Z-Elektrik/LIB je licencovaná pod licenciou  
[CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P v2)](https://ohwr.org/cern_ohl_p_v2.txt).

Knižnicu môžete používať, upravovať a ďalej distribuovať v súlade s podmienkami tejto licencie.


## Obsah tretích strán

Niektoré 3D modely v tejto knižnici môžu pochádzať priamo od výrobcov komponentov alebo z verejne dostupných zdrojov.

Tieto súbory sa naďalej riadia pôvodnými licenciami a podmienkami použitia.

Licencia CERN-OHL-P sa vzťahuje iba na pôvodný obsah vytvorený pre Z-Elektrik/LIB.
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
| `Z_LIB_3D_DIR` | your folder with unpacked 3D models |
| `Z_LIB_FOOTPRINT_DIR` | your folder with unpacked footprints |
| `Z_LIB_SYMBOL_DIR` | your folder with unpacked symbolsy |

Then add the libraries:

**Preferences → Manage Symbol Libraries**  
→ add all libraries from the `symbols` folder

**Preferences → Manage Footprint Libraries**  
→ add all libraries from the `footprints` folder



## License

Z-Elektrik/LIB is licensed under the  
[CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P v2)](https://ohwr.org/cern_ohl_p_v2.txt).

You are free to use, modify and distribute this library according to the terms of the license.


## Third-party content

Some 3D models included in this library may originate from component manufacturers or publicly available sources.

Such files remain subject to their original licenses and usage terms.

The CERN-OHL-P license applies only to original Z-Elektrik/LIB content.
---

Maintained by **Z-Elektrik**