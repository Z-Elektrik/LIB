# ZElektrik LIB – Pracovný návrh systému označovania footprintov

> **Stav:** pracovný dokument na diskusiu. Nejde o finálnu normu ani o aktualizáciu Wiki. Existujúce názvy footprintov sa nemenia.

## 1. Základný princíp

Cieľom je jednotný systém označovania pre SMD aj THD.

**Základné pravidlo: HODNOTA + KVALIFIKÁTOR.**

Rozmer sa zapisuje číselnou hodnotou v stotinách milimetra, za ktorou nasleduje kvalifikátor. Rozmery sa uvádzajú v metrických jednotkách.

Príklady zápisu:

- `50W` – 0,50 mm, šírka vývodu/terminálu
- `254P` – 2,54 mm, rozteč
- `1250X` – 12,50 mm, rozmer v osi X
- `508Y` – 5,08 mm, rozmer v osi Y
- `800H` – 8,00 mm, výška

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

| Kvalifikátor | Zamýšľaný význam | Stav |
|---|---|---|
| `W` | Šírka THD vývodu | Návrh – vyhradené pre THD |
| `P` | Rozteč vývodov / vzdialenosť osí otvorov alebo terminálov | Návrh – treba potvrdiť použitie aj pri dvojvývodových a THD súčiastkach |
| `X` | Rozmer tela v osi X | Otvorená definícia |
| `Y` | Rozmer tela v osi Y | Otvorená definícia |
| `H` | Výška tela/komponentu | Otvorená definícia referenčných plôch |
| `D` | Priemer tela alebo kruhového prvku | Otvorená definícia |
| `L` | Dĺžkový rozmer; potenciálne aj dĺžka terminálu | Treba presne rozlíšiť podľa kontextu |
| `S` | Rozpätie radov vývodov (Lead Span) | Kandidát, zatiaľ nepotvrdený |

Kvalifikátor musí mať stabilný význam. Nemal by meniť význam podľa toho, či ide o SMD alebo THD. Ak sa rovnaký fyzický parameter v rôznych rodinách označuje odlišne, treba najskôr preveriť možnosť zjednotenia.

Kvalifikátor `W` je vyhradený pre šírku THD vývodu. Jeho prítomnosť v názve zároveň rozlišuje THD footprint od SMD footprintu. Preto sa `W` nesmie používať na označenie šírky SMD terminálu.

## 4. Telo puzdra verzus rozmery vývodov a celkový obrys

**Všeobecné pravidlo:** Názov footprintu má obsahovať iba tie geometrické parametre, ktoré sú potrebné na jednoznačné rozlíšenie konkrétneho puzdra alebo jeho land patternu. Rozsah uvádzaných parametrov sa môže líšiť podľa rodiny súčiastok.

Rozmery tela a celkový vonkajší rozmer sa preto uvádzajú samostatne iba pri rodinách, pri ktorých má toto rozlíšenie praktický význam – napríklad pri LED alebo konektoroch. Nie je potrebné mechanicky uvádzať oba rozmery pri každej súčiastke.

Pri jednoduchých pasívnych SMD súčiastkach, ako sú rezistory a kondenzátory (napr. rodiny `RESC` a `CAPC`), spravidla postačuje bežné označenie veľkosti puzdra. Samostatné rozmery tela a celkového obrysu by názov zbytočne komplikovali bez pridania užitočnej rozlišovacej informácie.

Pri rozmeroch X a Y treba jednoznačne rozlíšiť, čo sa meria. Podľa potreby rodiny puzdier možno rozlišovať:

1. **Rozmery tela (Body dimensions)** – rozmery samotného puzdra bez vývodov.
2. **Rozmery vývodov/terminálov (Lead/Terminal dimensions)** – rozmery a poloha kovových vývodov alebo terminálov.
3. **Celkový vonkajší rozmer (Overall envelope)** – maximálny obrys komponentu vrátane vývodov, ak presahujú telo.

Tieto údaje nie sú zameniteľné. Napríklad 3 mm radiálna LED má telo s priemerom 3 mm, ale jej ohnuté vývody môžu vytvárať väčší vonkajší obrys. Informácia o priemere tela je pritom užitočná na identifikáciu komponentu a nemala by sa stratiť v celkovom rozmere.

### Predbežný smer

Odporúča sa nepreberať automaticky jeden všeobecný rozmer X/Y pre celý komponent. Namiesto toho treba podľa konkrétnej rodiny najskôr určiť, ktoré z nasledujúcich údajov sú skutočne potrebné:

- rozmery tela,
- rozteč alebo rozpätie vývodov,
- rozmery vývodov/terminálov,
- celkový vonkajší obrys, ak je odlišný a dôležitý,
- prípadné ďalšie rozmery, ktoré skutočne odlišujú geometriu footprintu.

Samostatné kvalifikátory pre celkový obrys X/Y zatiaľ **nie sú navrhnuté ani schválené**. Treba zistiť, či je celkový obrys potrebný v názve, alebo či ho možno jednoznačne odvodiť z rozmerov tela, polohy vývodov a ich geometrie.

### Šírka SMD terminálov

Šírka vývodu má pri THD priamy význam pre návrh otvoru a jeho tolerancie. Pri SMD je situácia odlišná: šírka terminálu môže ovplyvniť geometriu plošky, ale nie je automaticky potrebná v názve footprintu.

- **Čipové súčiastky (RESC, CAPC):** samostatnú šírku terminálu spravidla netreba uvádzať; obvykle postačuje označenie veľkosti puzdra.
- **Gull-wing puzdrá (napr. SOIC, QFP):** šírka vývodu môže byť dôležitým geometrickým parametrom, ale do názvu patrí iba vtedy, ak pomáha rozlíšiť puzdro alebo land pattern.
- **QFN a podobné puzdrá:** rozmery terminálov môžu byť dôležité pre geometriu plošiek; ich uvádzanie v názve sa posúdi podľa konkrétnej rodiny a potreby rozlíšenia.

Kvalifikátor `W` sa pri SMD nepoužíva, pretože je vyhradený pre THD a jeho použitie by narušilo rozlíšenie technológie footprintu. Samostatný kvalifikátor pre šírku SMD terminálu zatiaľ neurčujeme. Ak sa neskôr ukáže, že tento údaj musí byť súčasťou názvu niektorej SMD rodiny, treba navrhnúť iný, jednoznačný kvalifikátor.

## 5. Inšpirácia: Thomas Hausherr / PCB Libraries

PCB Libraries Footprint Expert oddeľuje rozmery tela od geometrie vývodov. V jeho konvencii sa podľa rodiny puzdra uvádzajú napríklad:

- rozmery tela (Body Length, Width, Height),
- rozteč vývodov (Pin Pitch),
- rozpätie vývodov (Lead Span),
- rozmery terminálov (Lead Length × Width),
- rozmery tepelnej plôšky (Thermal Tab Length × Width).

Pri SMD čipových súčiastkach sa uvádzajú rozmery tela a samostatne rozmery terminálu. Pri SOIC/QFP sa používa Lead Span, pretože ten lepšie opisuje rozstup/rozpätie vývodov než samotná šírka tela. Pri THD sa prvý rozmer často vzťahuje na Lead Spacing alebo vzdialenosť otvorov; ďalšie rozmery opisujú vývody a telo.

Dôležité je, že PCB Libraries nepoužíva jeden univerzálny zoznam tokenov bez ohľadu na rodinu puzdra. Štruktúra názvu sa prispôsobuje fyzickej geometrii danej rodiny. Uvedenie parametra v technickom opise alebo v konvencii výrobcu však samo osebe neznamená, že ho musíme uvádzať aj v názve ZElektrik footprintu.

### Čo z toho chceme prevziať

Nie nevyhnutne Thomasovu syntax, ale jeho rozlíšenie fyzických veličín:

- telo nie je to isté ako vývody;
- rozteč vývodov nie je to isté ako Lead Span;
- rozmery terminálu nie sú to isté ako rozmery tela;
- celkový mechanický obrys nemusí byť automaticky najvhodnejším identifikátorom land patternu.

ZElektrik si zachová vlastné jednotné poradie **HODNOTA + KVALIFIKÁTOR**.

## 6. Ilustračné príklady

Príklady zámerne používajú zástupné znaky tam, kde ešte nie je uzavreté kódovanie rozmerov. Nevyjadrujú finálnu syntax všetkých rodín.

### Rezistorová sieť

`RESCxxxxx-8N`

Rezistorová sieť s ôsmimi vývodmi, hustota Nominal. Rozmerová časť zatiaľ nie je definovaná.

### Radiálna LED s telom 3 mm

Finálny názov zatiaľ neurčujeme. Pri návrhu musí byť možné zachovať samostatnú informáciu o priemere tela LED (3 mm) a zároveň odlíšiť rozteč/umiestnenie vývodov a prípadnú geometriu ohnutých vývodov. Ak je dôležitý aj celkový obrys, môže sa uviesť samostatne.

### DIP

Názov musí vedieť rozlíšiť minimálne rozteč vývodov v rade, vzdialenosť medzi radmi vývodov, rozmery tela a rozmery samotných vývodov. Konkrétne poradie a kvalifikátory ešte treba potvrdiť.

## 7. Otvorené otázky

- [ ] Potvrdiť, či `P` označuje rozteč aj pri dvojvývodových súčiastkach a THD.
- [ ] Rozhodnúť, či je pre vzdialenosť medzi radmi vývodov potrebný samostatný kvalifikátor `S`, alebo sa dá použiť existujúci parameter.
- [ ] Presne definovať `X` a `Y` ako rozmery tela, nie automaticky celkového obrysu.
- [ ] Rozhodnúť, či a ako označovať celkový vonkajší obrys komponentu.
- [ ] Presne definovať `L` a ďalšie prípadné rozmery SMD terminálov; `W` zostáva vyhradené pre šírku THD vývodu.
- [ ] Definovať referenčné plochy pre výšku `H`.
- [ ] Preveriť kruhové a valcové telá (`D`) a orientované montáže.
- [ ] Preveriť LED, rezistorové siete, konektory, DIP, SOIC/QFP, BGA a ďalšie rodiny.
- [ ] Overiť, či každý podstatný geometrický rozdiel vedie k odlišnej identifikácii footprintu.

## 8. Zdroje

- [PCB Libraries – Footprint Expert: Design Options](https://www.pcblibraries.com/Products/FPX/UserGuide/Console%20Options/3.2%20Design.asp)
- [PCB Libraries – Footprint Expert Naming Convention](https://www.pcblibraries.com/Products/FPX/UserGuide/default.asp?ch=4)
- [PCB Libraries – Surface Mount naming convention](https://www.cskl.de/fileadmin/csk/dokumente/produkte/pcbl/pcb-footprint-expert-guideline/pcb-footprint-expert-guidline-csk_files/part84.htm)
- [PCB Libraries – aktuálna tabuľka konvencie (fórum)](https://www.pcblibraries.com/forum/pcbl-footprint-naming-convention_topic3681.html)

---

**Poznámka:** Tento dokument slúži na priebežné pracovné rozhodnutia. Do oficiálnej Wiki sa prenesú až potvrdené pravidlá. Existujúce footprinty sa v tejto fáze nepremenúvajú.
