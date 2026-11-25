# Konvencia názvov puzdier

Táto stránka opisuje pravidlá pomenovania puzdier používaných v knižniciach ZElektrik.

Názvy vychádzajú z odporúčaní IPC, ktoré boli rozšírené o ďalšie informácie potrebné pre moderný návrh elektroniky.

IPC normy vznikli v období, keď puzdro predstavovalo najmä návrh medených plôch. Moderné návrhové nástroje však používajú puzdro aj ako nositeľa informácie o:

- mechanickom vyhotovení komponentu,
- spôsobe montáže,
- väzbe na 3D model,
- zdrojových parametrických dátach.
---


## Všeobecné názvoslovie
Názvoslovie každého puzdra vychádza z formátu:

        '<Predpona><Parametre><PrimárnyRozmer>-<PočetVývodov><Hustota>_<VlastnostiNávrhu>_<SpôsobMontáže>_<OznačenieVýrobcom>_<Výrobca>'

### Poradie hodnoty a kvalifikátora

Všetky číselné rozmerové údaje sa zapisujú v poradí **HODNOTA + KVALIFIKÁTOR**. Najprv sa uvedie číselná hodnota v stotinách milimetra a za ňou písmeno určujúce druh rozmeru.

Príklady: **50W** (0,50 mm), **254P** (2,54 mm), **1250X** (12,50 mm), **508Y** (5,08 mm), **780H** (7,80 mm).

Opačné poradie, napríklad **W50**, **P254** alebo **X1250**, sa nepoužíva.

---

### Predpona puzdra

Určuje základnú kategóriu komponentu prípadne aj podkategóriu daného prvku.

Napríklad: **CAP**C1608, **RES**AH60768W250P250D630L, **CONHDR**VF64W254P1200X508Y780H-12N, ...

Zoznam je na stránke [[Puzdrá ‐ Základné predpony]]

---


### Parametre

Parametre sú doplnkové informácie k typom puzdier, špecifické pre každú kategóriu.

Napríklad: Typ puzdra, rozmer vývodov, rozteč vývodov, orientácia (horizontal, vertical), Typ (Male, Female, Genderless), atď...

Napríklad: CAP**C**1608, RES**AH60W768P**250D630L, CONHDR**VF64W254P**1200X508Y780H-12N, ...

---



**Typ puzdra**

Tokeny: **C, M, P, AE, B, ...**

* _Chip, Molded, Polarised, Aluminum Electrolytic, Button, ..._

---



**Orientácia vývodov**

Tokeny: **A, R**

* _Axial, Radial_

Viac: [[Puzdrá ‐ Všeobecná definícia orientácie vývodov]]

---



**Rozmer vývodov**

Token: **W**

* _Width_

Viac: [[Puzdrá ‐ Všeobecný rozmer vývodov]]

---



**Rozteč vývodov**

Token: **P**

* _Pitch_

Viac: [[Puzdrá ‐ Všeobecná rozteč vývodov]]

---




### Primárny rozmer

Tokeny: **X, Y, H, D, L**

* _Rozmer X a Y, výška, priemer, dĺžka_

Primárny rozmer určuje fyzické rozmery tela komponentu bez spájkovacích vývodov.

Napríklad: CAPC**1608**, RESAH60W768P**250D630L**, CONHDRVF64W254P**1200X508Y780H**-12N, ...

Viac: [[Puzdrá ‐ Všeobecný primárny rozmer]]

---


### Počet vývodov

Udáva celkový počet vývodov puzdra, alebo pri symetrických počet radov X počet vývodov v rade (napr. niektoré konektory)

Napríklad: CAPC1608, RESAH60768W250P250D630L, CONHDRVF64W254P1200X508Y780H**-12**N, ...

Viac: [[Puzdrá ‐ Všeobecný počet vývodov]]

---


### Hustota
Tokeny: **L, N, M**

* _Least, Nominal, Most_

Hustota určuje požadovanú úroveň zhustenia vývodov a spájkovacích plôch vzhľadom na mechanické rozmery komponentu.

Napríklad: CAPC1608, RESAH60768W250P250D630L, CONHDRVF64W254P1200X508Y780H-12**N**, ...

Viac: [[Puzdrá ‐ Všeobecná definícia hustoty]]

---


### Vlastnosti Návrhu
Tokeny: **C, R, O, D, H**

* _Circular, Rectangle, Oblong, D-Shape, Hole size_

Vlastnosť návrhu dodatočne špecifikuje dané puzdro. Môže obsahovať napríklad tvar a veľkosť použitých otvorov.

Napríklad: CONHDRVF64W254P1200X508Y780H-12N_**R150H90**, ...

Viac: [[Puzdrá ‐ Všeobecná definícia plôšok]]

---


### SpôsobMontáže

---


### Výrobca

---

Názvoslovie, ktoré svoje špecifické definície je detailnejšie popísané nižšie.

---

* [[Puzdrá ‐ konvencia názvov pre integrované obvody]]
* [[Puzdrá ‐ konvencia názvov pre konektory]]