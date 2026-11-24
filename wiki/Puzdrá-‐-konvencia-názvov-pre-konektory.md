# Puzdrá - konektory

Názvy vychádzajú zo všeobecných konvencií.

Špecifické pre túto kategóriu sú len predpony puzdier a typ konektora.
---


# Predpony puzdier

Prefix začína **CON** a pokračuje kategóriou konektora.

| Prefix | Popis kategórie |
|---|---|
| **CONHDR** | PCB pin/socket headers (male/female), breakaway alebo pevné, bez mechanického vedenia alebo polarizácie protikusu (unshrouded).<br>Príklad: _Pin Header, Female Header, Machine Pin Header_ |
| **CONIDC** | IDC box headers (shrouded headers) určené pre ploché káble.<br>Príklad: _IDC Box Header_ |
| **CONB2B** | Konektory určené výhradne na spojenie dvoch PCB.<br>Príklad: _Mezzanine connectors, Board stacking connectors (Samtec, Hirose DF12)_ |
| **CONW2B** | Wire-to-board konektory s vlastným párovacím systémom určené pre krimpované vodiče v plastovom housingu.<br>Príklad: _JST PH, JST XH, Molex PicoBlade, MicroFit_ |
| **CONFFC** | FFC/FPC konektory pre ploché flexibilné káble.<br>Príklad: _FFC, FPC ZIF_ |
| **CONFSTN** | Faston konektory a kontakty. |
| **CONUSB** | USB konektory všetkých štandardov. |
| **CONRJ** | Modulárne telekomunikačné konektory RJxx. |
| **CONJACK** | Audio a DC jack konektory pre zasúvacie cylindrické kontakty.<br>Príklad: _3.5 mm audio jack, DC barrel jack_ |
| **CONRF** | Koaxiálne RF konektory. |
| **CONTERM** | Svorkovnice, kde sa vodič upína priamo skrutkou alebo pružinou.<br>Príklad: _Phoenix Contact, Weidmüller, WAGO PCB Terminal_ |
| **CONDSUB** | D-Sub konektory. |
| **CONCIRC** | Kruhové konektory.<br>Príklad: _XLR, DIN, M8, M12, GX_ |
| **CONCARD** | Konektory pre pamäťové alebo identifikačné karty.<br>Príklad: _SD, microSD, SIM_ |
| **CONPWR** | Špecializované napájacie konektory, ktoré netvoria samostatnú mechanickú rodinu.<br>Príklad: _XT60, Anderson, IEC_ |
| **CONPCB** | Pripojovacie rozhrania vytvorené priamo na DPS bez dodatočne osadeného mechanického prvku. Elektrické a mechanické vlastnosti sú definované geometriou medených plôšok, otvorov, kontaktov alebo hranou DPS.<br>Príklad: _PCIe, M.2, ISA, SO-DIMM, Card Edge_ |
---


## Pravidlo určovania kategórie

Kategória sa určuje podľa **fyzického spôsobu spojenia**, nie podľa elektrickej funkcie.

Príklady:

| Nesprávne | Správne |
|---|---|
| JST napájanie → CONPWR | JST → CONWTB |
| USB-C PD → CONPWR | USB-C → CONUSB |
| Phoenix 2-pin pre 24 V → CONPWR | Phoenix → CONTERM |
| SWD pady → CONHDR | SWD pady → CONPCB |
---


## Typ konektora
* **F** - female (dutinky)
* **M** - male (kolíky)
* **G** - neurčené, resp. hermafroditné

Príklad: _CONHDRVF64W254P..._


