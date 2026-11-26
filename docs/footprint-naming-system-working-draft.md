# ZElektrik LIB – Pracovný návrh systému označovania footprintov

> **Stav:** pracovný dokument na diskusiu. Nejde o finálnu normu ani o aktualizáciu Wiki. Existujúce názvy footprintov sa nemenia.

## 1. Základný princíp

Cieľom je jednotný systém označovania pre SMD aj THD.

**Základné pravidlo: HODNOTA + KVALIFIKÁTOR.**

Rozmer sa zapisuje číselnou hodnotou v stotinách milimetra, za ktorou nasleduje kvalifikátor. Rozmery sa uvádzajú v metrických jednotkách.

Príklady zápisu:

- `50W` – 0,50 mm, šírka THD vývodu
- `254P` – 2,54 mm, rozteč vývodov
- `1250X` – 12,50 mm, rozmer tela v osi X
- `508Y` – 5,08 mm, rozmer tela v osi Y
- `800OZ` – 8,00 mm, celkový rozmer v osi Z

Poradie kvalifikátor + hodnota (napr. `W50`) sa v ZElektrik konvencii nepoužíva.

## 2. Počet vývodov a hustota

Počet vývodov a hustota osadenia sa zapisujú na konci názvu:

`-<POČET VÝVODOV><HUSTOTA>`

| Označenie | Význam |
|---|---|
| `L` | Least |
| `N` | Nominal |
| `M` | Most |

Príklady:

- `-2N` – 2 vývody, Nominal
- `-8N` – 8 vývodov, Nominal
- `-40N` – 40 vývodov, Nominal

Tento zápis sa používa pre SMD aj THD, vrátane pasívnych sietí. Počet vývodov a hustota tvoria jeden koncový údaj. Samostatný kvalifikátor `Q` pre počet vývodov sa preto v tomto návrhu nepoužíva.

Príklad rodiny rezistorovej siete (iba ilustračný tvar, nie definícia rozmerov):

`RESCxxxxx-8N`

## 3. Predbežný zoznam kvalifikátorov

### Geometrické rozmery

| Kvalifikátor | Zamýšľaný význam |
|---|---|
| `X` | Rozmer samotného tela v osi X |
| `Y` | Rozmer samotného tela v osi Y |
| `Z` | Rozmer samotného tela v osi Z |
| `D` | Priemer samotného tela |
| `OX` | Celkový vonkajší rozmer komponentu v osi X |
| `OY` | Celkový vonkajší rozmer komponentu v osi Y |
| `OZ` | Celkový vonkajší rozmer komponentu v osi Z |
| `OD` | Celkový vonkajší priemer komponentu |
| `P` | Rozteč vývodov / vzdialenosť osí otvorov alebo terminálov |
| `W` | Šírka THD vývodu |

Hodnoty X, Y a Z predstavujú tri priestorové osi. V tomto návrhu sa nepoužívajú samostatné rozmerové kvalifikátory `H` (height), `L` (length) ani `S` (span). Výška je rozmer v osi Z; dĺžka a šírka sa vyjadrujú podľa orientácie komponentu osami X a Y. Pri kruhovom tele sa používa `D`.

Kvalifikátory s prefixom `O` označujú Overall – maximálny vonkajší rozmer celého komponentu vrátane vývodov, kontaktov a mechanických častí, ktoré presahujú samotné telo. Používajú sa rovnaké osi ako pri rozmeroch tela: X/Y/Z, prípadne priemer D.

Kvalifikátor `W` je vyhradený pre šírku THD vývodu. Jeho prítomnosť v názve zároveň rozlišuje THD footprint od SMD footprintu. Preto sa `W` nesmie používať na označenie šírky SMD terminálu. Samostatný kvalifikátor pre šírku SMD terminálu zatiaľ neurčujeme.

### Pravidlo pre rozmery BODY a OVERALL

- `X/Y/Z/D` vždy označujú rozmery samotného tela komponentu.
- `OX/OY/OZ/OD` vždy označujú maximálne vonkajšie rozmery celého komponentu.
- Ak je pre identifikáciu puzdra alebo výber footprintu potrebný iba jeden druh rozmeru, uvedie sa iba tento rozmer.
- Ak sú dôležité oba druhy rozmerov, uvedú sa samostatne. Celkový rozmer sa nesmie zamieňať s rozmerom tela.
- Pri kruhovom tele sa používa `D`; ak je celkový vonkajší obrys kruhový, použije sa `OD`. Ak vývody alebo mechanické časti vytvárajú obdĺžnikový obrys, použijú sa `OX` a `OY`.

Kvalifikátory musia mať stabilný význam bez ohľadu na rodinu súčiastky. Názov má byť čitateľný človekom a zároveň jednoznačne strojovo dekódovateľný; preto sa význam nesmie meniť podľa poradia tokenov v konkrétnej rodine.

## 4. Telo puzdra verzus celkový vonkajší rozmer

**Všeobecné pravidlo:** Názov footprintu má obsahovať iba tie geometrické parametre, ktoré sú potrebné na jednoznačné rozlíšenie konkrétneho puzdra alebo jeho land patternu. Rozsah uvádzaných parametrov sa môže líšiť podľa rodiny súčiastok.

Rozmery BODY a OVERALL sa preto uvádzajú samostatne iba pri rodinách, pri ktorých má toto rozlíšenie praktický význam. Nie je potrebné mechanicky uvádzať oba rozmery pri každej súčiastke.

Pri jednoduchých pasívnych SMD súčiastkach, ako sú rezistory a kondenzátory (napr. rodiny `RESC` a `CAPC`), spravidla postačuje bežné označenie veľkosti puzdra. Samostatné rozmery tela a celkového obrysu by názov zbytočne komplikovali bez pridania užitočnej rozlišovacej informácie.

### Rozmery tela (BODY)

Rozmery označené `X`, `Y`, `Z` a `D` opisujú samotné telo komponentu. Nezahŕňajú vývody, kontakty ani iné časti, ktoré z tela vyčnievajú.

### Celkové rozmery (OVERALL)

Rozmery označené `OX`, `OY`, `OZ` a `OD` opisujú maximálny vonkajší obrys celého komponentu. Nezáleží na tom, či presahujúce časti vyčnievajú na jednej strane, na protiľahlých stranách alebo v niekoľkých smeroch.

Z tohto dôvodu sa nepoužíva samostatný kvalifikátor `SPAN`. Pri symetricky vyčnievajúcich vývodoch môže byť Lead Span číselne rovnaký ako celkový rozmer; pri jednostranných alebo nepravidelne rozmiestnených vývodoch by však Span nevyjadroval všeobecný vonkajší obrys. `OVERALL` je univerzálnejšie označenie.

### Výška a referenčné plochy

Rozmer v osi Z sa musí určovať podľa skutočných fyzických referenčných plôch, nie podľa názvu parametra použitého výrobcom v datasheete.

Napríklad pri SOIC môže byť parameter `A1` celkovou výškou od dosadacej roviny vývodov po hornú plochu puzdra. Ak tento rozmer predstavuje celkovú výšku komponentu, v našom názvosloví sa označí `OZ`, aj keď ho datasheet opisuje ako rozmer súvisiaci s telom. Samotná výška tela sa označí `Z`, ak je potrebná a známa.

### Výška osadenia (Standoff Height)

Výška osadenia `SH` je samostatný parameter polohy tela voči referenčnej rovine PCB. Nie je náhradou za rozmer tela ani za celkový rozmer komponentu. Môže byť potrebná napríklad pri umiestnení priradeného 3D modelu.

Preto sa `SH` zachováva ako samostatný doplnkový údaj a nezamieňa sa s `Z` ani `OZ`.

### Šírka SMD terminálov

Šírka vývodu má pri THD priamy význam pre návrh otvoru a jeho tolerancie. Pri SMD je situácia odlišná: šírka terminálu môže ovplyvniť geometriu plošky, ale nie je automaticky potrebná v názve footprintu.

- **Čipové súčiastky (RESC, CAPC):** samostatnú šírku terminálu spravidla netreba uvádzať; obvykle postačuje označenie veľkosti puzdra.
- **Gull-wing puzdrá (napr. SOIC, QFP):** šírka vývodu môže byť dôležitým geometrickým parametrom, ale do názvu patrí iba vtedy, ak pomáha rozlíšiť puzdro alebo land pattern.
- **QFN a podobné puzdrá:** rozmery terminálov môžu byť dôležité pre geometriu plošiek; ich uvádzanie v názve sa posúdi podľa konkrétnej rodiny a potreby rozlíšenia.

Kvalifikátor `W` sa pri SMD nepoužíva, pretože je vyhradený pre THD a jeho použitie by narušilo rozlíšenie technológie footprintu. Samostatný kvalifikátor pre šírku SMD terminálu zatiaľ neurčujeme.

## 5. Inšpirácia: Thomas Hausherr / PCB Libraries

PCB Libraries Footprint Expert oddeľuje rozmery tela od geometrie vývodov. V jeho konvencii sa podľa rodiny puzdra uvádzajú napríklad:

- rozmery tela (Body Length, Width, Height),
- rozteč vývodov (Pin Pitch),
- rozpätie vývodov (Lead Span),
- rozmery terminálov (Lead Length × Width),
- rozmery tepelnej plošky (Thermal Tab Length × Width).

Dôležité je, že PCB Libraries nepoužíva jeden univerzálny zoznam tokenov bez ohľadu na rodinu puzdra. Štruktúra názvu sa prispôsobuje fyzickej geometrii danej rodiny. Uvedenie parametra v technickom opise alebo v konvencii výrobcu však samo osebe neznamená, že ho musíme uvádzať aj v názve ZElektrik footprintu.

### Čo z toho chceme prevziať

Nie nevyhnutne Thomasovu syntax, ale jeho rozlíšenie fyzických veličín:

- telo nie je to isté ako vývody;
- rozteč vývodov nie je to isté ako rozpätie vývodov;
- rozmery terminálu nie sú to isté ako rozmery tela;
- celkový mechanický obrys nemusí byť automaticky jediným vhodným identifikátorom land patternu.

ZElektrik si zachová vlastné jednotné poradie **HODNOTA + KVALIFIKÁTOR**. Na rozdiel od rodinne závislej interpretácie tokenov chceme, aby každý kvalifikátor mal stabilný geometrický význam.

## 6. Ilustračné príklady

Príklady zobrazujú aktuálny pracovný smer. Nie sú ešte finálnou syntaxou všetkých rodín.

### THD axiálny rezistor 0207

Pôvodný názov:

`RESAD1524W60L650D230-0207`

Navrhovaný názov:

`RESAD60W230D650X1524P-2N_0207`

- `60W` – šírka THD vývodu 0,60 mm
- `230D` – priemer tela 2,30 mm
- `650X` – dĺžka tela 6,50 mm
- `1524P` – rozteč vývodov 15,24 mm
- `-2N` – 2 vývody, hustota Nominal
- `0207` – komerčné označenie veľkosti

Celkový rozmer vrátane vývodov sa neuvádza, pretože v tomto príklade nie je potrebný na identifikáciu puzdra.

### SOIC-16

Pracovný príklad:

`SOIC127P400X800OX175OZ-16_SOIC-16N`

- `127P` – Pitch 1,27 mm
- `400X` – šírka samotného tela 4,00 mm
- `800OX` – celková šírka komponentu vrátane vývodov 8,00 mm
- `175OZ` – celková výška komponentu 1,75 mm, ak ide o rozmer od dosadacej roviny po hornú plochu puzdra (napr. príslušný rozmer A1)

Ak sa uvádza samostatná výška tela, označí sa `Z`. Klasifikácia rozmeru ako BODY alebo OVERALL sa riadi skutočnými referenčnými plochami, nie iba označením v datasheete.

### Radiálna LED

Pracovný príklad s telom s priemerom 3 mm a samostatne definovanou výškou osadenia:

`LEDRD50W254P300D500Z-2N_CVX_FD_LL500_SH102_Red_HueyJann`

- `50W` – šírka THD vývodu 0,50 mm
- `254P` – rozteč vývodov 2,54 mm
- `300D` – priemer tela 3,00 mm
- `500Z` – výška samotného tela 5,00 mm
- `SH102` – Standoff Height 1,02 mm

Ak je potrebné uviesť aj celkovú výšku komponentu, použije sa `OZ`. `SH` zostáva samostatným údajom o výške osadenia a polohe 3D modelu.

### Kruhový komponent s kruhovým rozmiestnením vývodov

Pri kruhovom tele a kruhovom vonkajšom obryse možno uviesť napríklad:

- `D1800` – priemer tela 18,00 mm
- `OD2200` – maximálny vonkajší priemer 22,00 mm

Ak vývody alebo mechanické časti vytvárajú skôr obdĺžnikový obrys, použijú sa `OX` a `OY` namiesto `OD`.

## 7. Otvorené otázky

- [ ] Potvrdiť, či `P` označuje rozteč aj pri dvojvývodových súčiastkach a THD.
- [ ] Potvrdiť globálnu orientáciu osí X/Y/Z a spôsob určovania orientácie komponentu.
- [ ] Presne definovať referenčné plochy pre rozmery Z a OZ.
- [ ] Určiť, ktoré doplnkové údaje (napr. `SH`, `LL`, farba, výrobca) majú zostať v samostatnej časti názvu a aké bude ich poradie.
- [ ] Preveriť kruhové a valcové telá (`D`, `OD`) a orientované montáže.
- [ ] Preveriť LED, rezistorové siete, konektory, DIP, SOIC/QFP, BGA a ďalšie rodiny.
- [ ] Overiť, či každý podstatný geometrický rozdiel vedie k odlišnej identifikácii footprintu.
- [ ] Preveriť jednoznačnosť a strojovú dekódovateľnosť všetkých tokenov vrátane viacpísmenových kvalifikátorov `OX/OY/OZ/OD`.

## 8. Zdroje

- [PCB Libraries – Footprint Expert: Design Options](https://www.pcblibraries.com/Products/FPX/UserGuide/Console%20Options/3.2%20Design.asp)
- [PCB Libraries – Footprint Expert Naming Convention](https://www.pcblibraries.com/Products/FPX/UserGuide/default.asp?ch=4)
- [PCB Libraries – Surface Mount naming convention](https://www.cskl.de/fileadmin/csk/dokumente/produkte/pcbl/pcb-footprint-expert-guideline/pcb-footprint-expert-guidline-csk_files/part84.htm)
- [PCB Libraries – aktuálna tabuľka konvencie (fórum)](https://www.pcblibraries.com/forum/pcbl-footprint-naming-convention_topic3681.html)

---

**Poznámka:** Tento dokument slúži na priebežné pracovné rozhodnutia. Do oficiálnej Wiki sa prenesú až potvrdené pravidlá. Existujúce footprinty sa v tejto fáze nepremenúvajú.
