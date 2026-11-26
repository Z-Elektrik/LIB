# ZElektrik LIB – Pracovný návrh systému označovania footprintov

> **Stav:** pracovný dokument na diskusiu. Nejde o finálnu normu ani o aktualizáciu Wiki. Existujúce názvy footprintov sa nemenia.

## 1. Základný princíp

Cieľom je jednotný systém označovania pre SMD aj THD.

**Základné pravidlo: HODNOTA + KVALIFIKÁTOR.**

Rozmer sa zapisuje číselnou hodnotou v stotinách milimetra, za ktorou nasleduje kvalifikátor. Rozmery sa uvádzajú v metrických jednotkách.

Príklady zápisu:

- `50W` – 0,50 mm, šírka THD vývodu
- `254P` – 2,54 mm, rozteč vývodov
- `1250L` – 12,50 mm, najdlhší rozmer tela
- `508W` – 5,08 mm, druhý rozmer tela
- `800OH` – 8,00 mm, celková výška komponentu

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

Rozmerové označenia rozdeľujeme na **mechanické rozmery tela** a **celkové vonkajšie rozmery komponentu**. Nezávisia od natočenia footprintu v súradnicovom systéme KiCadu.

| Kvalifikátor | Zamýšľaný význam |
|---|---|
| `L` | Najdlhší rozmer samotného tela |
| `W` | Druhý rozmer samotného tela |
| `H` | Výška samotného tela |
| `D` | Priemer samotného kruhového tela |
| `OL` | Najdlhší celkový vonkajší rozmer komponentu |
| `OW` | Druhý celkový vonkajší rozmer komponentu |
| `OH` | Celková výška komponentu |
| `OD` | Celkový vonkajší priemer komponentu |
| `P` | Rozteč vývodov / vzdialenosť osí otvorov alebo terminálov |
| `W` | Šírka THD vývodu – vyhradené použitie v kontexte geometrie vývodov |
| `SH` | Standoff Height – výška osadenia tela voči referenčnej rovine PCB |

Hodnoty sa zapisujú v stotinách milimetra, bez desatinnej bodky. Naďalej platí poradie **HODNOTA + KVALIFIKÁTOR**. Napríklad `650L` znamená 6,50 mm a `800OL` znamená 8,00 mm.

- `L` je vždy dlhší z dvoch pôdorysných rozmerov tela; `W` je kratší. Pri štvorcovom tele platí `L = W`.
- `H` označuje výšku samotného tela.
- Pri kruhovom pôdoryse sa namiesto `L/W` používa `D`.
- `OL/OW` opisujú dva pôdorysné rozmery maximálneho vonkajšieho obrysu celého komponentu. `OL` je dlhší alebo rovnaký ako `OW`.
- `OH` označuje celkovú výšku komponentu vrátane častí presahujúcich telo.
- Pri kruhovom celkovom obryse sa používa `OD`; ak vývody alebo mechanické časti vytvárajú obdĺžnikový obrys, použijú sa `OL/OW`.

**L/W/H a OL/OW/OH nie sú osi KiCadu.** L a W sa určujú podľa veľkosti mechanických rozmerov, nie podľa toho, či ležia pozdĺž osi X alebo Y footprintu. Orientácia vývodov preto nemení význam L a W. Napríklad bežný rezistor 1206 a rezistorová sieť s rovnakým rozmerom tela môžu mať rovnaké L/W, aj keď je rozloženie vývodov otočené o 90°.

Kvalifikátor `W` sa používa aj pre šírku THD vývodu, napr. `60W`. Kontext názvu a poradie geometrických tokenov musia umožniť jednoznačné dekódovanie; prípadné riziko kolízie medzi `W` ako šírkou tela a `W` ako šírkou THD vývodu treba vyriešiť pri finalizácii syntaxe. Pre SMD sa `W` nesmie používať na označenie šírky terminálu.

### Pravidlo pre rozmery BODY a OVERALL

- `L/W/H/D` vždy označujú rozmery samotného tela komponentu.
- `OL/OW/OH/OD` vždy označujú maximálne vonkajšie rozmery celého komponentu.
- Ak je pre identifikáciu puzdra alebo výber footprintu potrebný iba jeden druh rozmeru, uvedie sa iba tento rozmer.
- Ak sú dôležité oba druhy rozmerov, uvedú sa samostatne.
- Celkový rozmer sa nesmie zamieňať s rozmerom tela.

Rozmery L/W a OL/OW sú zoradené podľa veľkosti, nie podľa orientácie v CAD. Pri štvorcovom obryse sú príslušné rozmery rovnaké a ich vzájomné priradenie nemá praktický význam.

### Výška a referenčné plochy

Rozmer H a OH sa musí určovať podľa skutočných fyzických referenčných plôch, nie podľa názvu parametra použitého výrobcom v datasheete.

Napríklad pri SOIC môže byť parameter A1 celkovou výškou od dosadacej roviny vývodov po hornú plochu puzdra. Ak tento rozmer predstavuje celkovú výšku komponentu, v našom názvosloví sa označí OH, aj keď ho datasheet opisuje ako rozmer súvisiaci s telom. Samotná výška tela sa označí H, ak je potrebná a známa.

### Výška osadenia (Standoff Height)

Výška osadenia SH je samostatný parameter polohy tela voči referenčnej rovine PCB. Nie je náhradou za rozmer tela ani za celkový rozmer komponentu. Môže byť potrebná napríklad pri umiestnení priradeného 3D modelu.

Preto sa SH zachováva ako samostatný doplnkový údaj a nezamieňa sa s H ani OH.

### Šírka SMD terminálov

Šírka vývodu má pri THD priamy význam pre návrh otvoru a jeho tolerancie. Pri SMD je situácia odlišná: šírka terminálu môže ovplyvniť geometriu plošky, ale nie je automaticky potrebná v názve footprintu.

- **Čipové súčiastky (RESC, CAPC):** samostatnú šírku terminálu spravidla netreba uvádzať; obvykle postačuje označenie veľkosti puzdra.
- **Gull-wing puzdrá (napr. SOIC, QFP):** šírka vývodu môže byť dôležitým geometrickým parametrom, ale do názvu patrí iba vtedy, ak pomáha rozlíšiť puzdro alebo land pattern.
- **QFN a podobné puzdrá:** rozmery terminálov môžu byť dôležité pre geometriu plošiek; ich uvádzanie v názve sa posúdi podľa konkrétnej rodiny a potreby rozlíšenia.

Samostatný kvalifikátor pre šírku SMD terminálu zatiaľ neurčujeme.

## 4. Telo puzdra verzus celkový vonkajší rozmer

**Všeobecné pravidlo:** Názov footprintu má obsahovať iba tie geometrické parametre, ktoré sú potrebné na jednoznačné rozlíšenie konkrétneho puzdra alebo jeho land patternu. Rozsah uvádzaných parametrov sa môže líšiť podľa rodiny súčiastok.

Rozmery BODY a OVERALL sa preto uvádzajú samostatne iba pri rodinách, pri ktorých má toto rozlíšenie praktický význam. Nie je potrebné mechanicky uvádzať oba rozmery pri každej súčiastke.

Pri jednoduchých pasívnych SMD súčiastkach, ako sú rezistory a kondenzátory (napr. rodiny RESC a CAPC), spravidla postačuje bežné označenie veľkosti puzdra. Samostatné rozmery tela a celkového obrysu by názov zbytočne komplikovali bez pridania užitočnej rozlišovacej informácie.

### Rozmery tela (BODY)

Rozmery označené L, W, H a D opisujú samotné telo komponentu. Nezahŕňajú vývody, kontakty ani iné časti, ktoré z tela vyčnievajú. L a W sú zoradené podľa veľkosti; nevyjadrujú osi footprintu.

### Celkové rozmery (OVERALL)

Rozmery označené OL, OW, OH a OD opisujú maximálny vonkajší obrys celého komponentu. Nezáleží na tom, či presahujúce časti vyčnievajú na jednej strane, na protiľahlých stranách alebo v niekoľkých smeroch.

Z tohto dôvodu sa nepoužíva samostatný kvalifikátor SPAN. Pri symetricky vyčnievajúcich vývodoch môže byť Lead Span číselne rovnaký ako celkový rozmer; pri jednostranných alebo nepravidelne rozmiestnených vývodoch by však Span nevyjadroval všeobecný vonkajší obrys. OVERALL je univerzálnejšie označenie.

### Výška a referenčné plochy

Rozmer OH sa musí určovať podľa skutočných fyzických referenčných plôch, nie podľa názvu parametra použitého výrobcom v datasheete.

Napríklad pri SOIC môže byť parameter A1 celkovou výškou od dosadacej roviny vývodov po hornú plochu puzdra. Ak tento rozmer predstavuje celkovú výšku komponentu, v našom názvosloví sa označí OH. Samotná výška tela sa označí H, ak je potrebná a známa.

### Výška osadenia (Standoff Height)

Výška osadenia SH je samostatný parameter polohy tela voči referenčnej rovine PCB. Nie je náhradou za rozmer tela ani za celkový rozmer komponentu. Môže byť potrebná napríklad pri umiestnení priradeného 3D modelu.

Preto sa SH zachováva ako samostatný doplnkový údaj a nezamieňa sa s H ani OH.

### Šírka SMD terminálov

Šírka vývodu má pri THD priamy význam pre návrh otvoru a jeho tolerancie. Pri SMD je situácia odlišná: šírka terminálu môže ovplyvniť geometriu plošky, ale nie je automaticky potrebná v názve footprintu.

- **Čipové súčiastky (RESC, CAPC):** samostatnú šírku terminálu spravidla netreba uvádzať; obvykle postačuje označenie veľkosti puzdra.
- **Gull-wing puzdrá (napr. SOIC, QFP):** šírka vývodu môže byť dôležitým geometrickým parametrom, ale do názvu patrí iba vtedy, ak pomáha rozlíšiť puzdro alebo land pattern.
- **QFN a podobné puzdrá:** rozmery terminálov môžu byť dôležité pre geometriu plošiek; ich uvádzanie v názve sa posúdi podľa konkrétnej rodiny a potreby rozlíšenia.

Kvalifikátor W pre šírku THD vývodu zostáva vyhradený pre THD; nepoužíva sa na označenie šírky SMD terminálu. Samostatný kvalifikátor pre šírku SMD terminálu zatiaľ neurčujeme.

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

## 6. Orientácia footprintov – IEC 61188-7:2017, Level B

Pre orientáciu komponentov v knižnici sa prijíma **IEC 61188-7:2017, Level B** ako základná konvencia. Norma v druhom vydaní z roku 2017 výslovne uvádza Level B ako preferovanú orientáciu pre nové CAD knižnice.

Toto pravidlo sa týka nulovej orientácie komponentu v CAD knižnici (pohľad zhora), nie orientácie súčiastky na výrobnej páske, v zásobníku alebo v podávači osadzovacieho stroja.

### Základné pravidlá

- Footprinty a komponenty sa zobrazujú v pohľade zhora.
- Poloha referenčného vývodu PAD1 musí zodpovedať polarizačnej/orientačnej značke na fyzickom puzdre.
- Ak výrobca namiesto čísel používa funkčné označenia vývodov (napr. cathode, anode, base, emitter, collector), knižničný opis musí priradiť príslušný vývod k referenčnej pozícii PAD1.
- Skutočné názvy PADov v KiCade sa zachovávajú. PAD označený napr. `C` alebo `K` sa nepremenúva na `1`; musí však obsadiť polohu, ktorá podľa IEC zodpovedá PAD1.
- Orientácia sa určuje podľa pravidiel Level B pre konkrétnu rodinu puzdra. Nie je správne aplikovať polohu PAD1 vľavo dole mechanicky na všetky typy komponentov.
- Pri dvojvývodových súčiastkach zostáva PAD1 vľavo; Level A a Level B sa pri týchto príkladoch zhodujú.
- Pri viacvývodových súčiastkach je PAD1 na ľavej alebo ľavej dolnej pozícii podľa konkrétneho typu puzdra a tabuliek normy.
- Level použitý v knižnici musí byť jednoznačne deklarovaný v dokumentácii knižnice ako Level B.

### Príklady podľa IEC

| Rodina / puzdro | Orientácia Level B |
|---|---|
| Čipový rezistor, kondenzátor, induktor | PAD1 vľavo, PAD2 vpravo |
| Tvarované polarizované puzdro / dióda | PAD1 podľa polarizačnej značky, spravidla vľavo |
| Hliníkový elektrolytický kondenzátor | PAD1 podľa značky polarity, v príklade normy vľavo |
| SOT23-3 | PAD1 vľavo dole |
| SOT23-5, SOT343, SOT223 | Orientácia podľa príslušného diagramu Level B |
| SOIC, SOP, SSOP | PAD1 vľavo dole; dlhá os puzdra vodorovne |
| TSSOP | PAD1 vľavo dole; dlhá os puzdra zvisle |
| TO252 / DPAK | Veľká ploška hore; PAD1 a PAD2 dole |

Tabuľka je orientačný výber, nie úplný zoznam. Pri ostatných rodinách sa musí skontrolovať príslušný diagram v IEC 61188-7:2017.

### Fyzická značka a názov PADu

Referenčný PAD1 sa určuje podľa značky, ktorá na puzdre identifikuje príslušný vývod, napríklad:

- IC – jamka alebo iná značka vývodu 1;
- THT LED – orezaný okraj označujúci katódu;
- elektrolytický kondenzátor – značka polarity (napr. pásik označujúci záporný vývod);
- SMD dióda – pásik označujúci katódu.

Pri písmenových označeniach sa zachová funkčný názov PADu. Napríklad pri dióde môže byť referenčným PADom `C` (cathode), pri tranzistore príslušný vývod podľa fyzickej značky a dokumentácie výrobcu.

Ak puzdro nemá jednoznačnú polarizačnú značku, orientácia a referenčný vývod sa určia podľa príslušného diagramu IEC a dokumentácie výrobcu. Nesmie sa svojvoľne predpokladať, že ľubovoľný vývod je PAD1.

### Vzťah mechanických rozmerov a orientácie footprintu

Mechanické rozmery L/W/H a OL/OW/OH sú nezávislé od osí L/W/H v KiCade. L je vždy najdlhší pôdorysný rozmer tela a W druhý rozmer; ich priradenie sa nemení podľa natočenia footprintu ani podľa orientácie vývodov.

IEC 61188-7:2017 Level B určuje nulovú orientáciu footprintu podľa konkrétnej rodiny puzdra. Preto môže dlhšia os tela ležať v KiCade pozdĺž X pri jednej rodine a pozdĺž Y pri inej. To nie je rozpor: názov footprintu opisuje mechanickú geometriu, zatiaľ čo IEC určuje CAD orientáciu.



Naša rozmerová konvencia predbežne stanovuje:
- X = vždy dlhší rozmer pôdorysu samotného tela;
- Y = vždy kratší rozmer pôdorysu samotného tela.

Zároveň sme uvažovali, že dlhší rozmer X bude vždy ležať na vodorovnej osi X footprintu. To však **nie je univerzálne kompatibilné s orientáciami Level B**. Napríklad IEC uvádza SOIC v horizontálnej a TSSOP vo vertikálnej orientácii dlhej osi.

Preto zatiaľ platí:
- význam X ako dlhšieho rozmeru tela zostáva zachovaný;
- Level B sa dodržiava podľa rodiny puzdra;
- vzťah medzi pomenovaním rozmerov X/Y a fyzickými osami kreslenia footprintu sa musí ešte rozhodnúť;
- nesmieme otočiť footprint proti Level B len preto, aby dlhší rozmer tela ležal vodorovne.

Tento konflikt je otvorenou otázkou systému a nesmie sa považovať za vyriešený.

### Kontrola doterajších rozhodnutí voči IEC 61188-7:2017

Táto kontrola sa týka iba rozsahu IEC 61188-7 – nulovej orientácie komponentov pre tvorbu CAD knižníc. Norma neurčuje syntax názvov footprintov ani všeobecný systém pomenovania mechanických rozmerov. Preto nemožno samotnú syntax ZElektrik označiť za odklon od tejto normy.

| Doterajšie pravidlo ZElektrik | Výsledok kontroly |
|---|---|
| PAD1 určuje fyzická polarizačná/orientačná značka | **V súlade.** IEC požaduje zhodu polohy PAD1 so značkou polarity; pri funkčných označeniach (katóda, anóda, báza, emitor, kolektor) sa má priradiť zodpovedajúce označenie PAD1. |
| Zachovanie písmenových názvov PADov | **Bez rozporu v princípe.** Názov PADu môže zostať funkčný; treba jednoznačne určiť, ktorý funkčný vývod zodpovedá referenčnej pozícii PAD1. |
| PAD1 vždy vľavo pri dvojvývodových súčiastkach | **V súlade s príkladmi normy.** Level B pri bežných dvojvývodových diskrétnych súčiastkach nemení orientáciu voči Level A. |
| PAD1 vľavo dole pri viacvývodových súčiastkach | **Všeobecne správny smer, nie univerzálne pravidlo pre každú rodinu.** Norma uvádza polohu vľavo alebo vľavo dole a konkrétne orientácie v tabuľkách podľa typu puzdra. |
| L/W/H a OL/OW/OH opisujú mechanické rozmery | **Mimo rozsahu tejto normy.** IEC 61188-7 neurčuje syntax pomenovania mechanických rozmerov. |
| L/W sa neurčujú podľa osí X/Y footprintu | **Bez konfliktu.** Mechanické rozmery sú nezávislé od CAD orientácie určenej podľa Level B. |
| BODY/OVERALL: L/W/H a OL/OW/OH | **Mimo rozsahu tejto normy.** IEC 61188-7 neurčuje túto nomenklatúru rozmerov. |
| HODNOTA + KVALIFIKÁTOR; P, W, D, OD, SH | **Mimo rozsahu tejto normy.** Ide o vlastnú syntax ZElektrik; táto norma ju ani nepredpisuje, ani nezakazuje. |
| Hustota L/N/M a koncový zápis počtu vývodov | **Mimo rozsahu tejto normy.** IEC 61188-7 nedefinuje hustotu ani syntax názvov. |
| Nepoužívanie samostatného SPAN | **Bez konfliktu s IEC 61188-7.** Norma neurčuje tokeny názvov footprintov ani povinnosť používať označenie Span. |

### Ďalšie body normy, ktoré zatiaľ nemáme v konvencii doriešené

- **Počiatok (origin):** Pri SMD norma všeobecne odporúča stred obrysovej oblasti/courtyard; pri konektoroch a pohyblivých častiach uvádza osobitné podmienky. Pri THD môže byť počiatkom ťažisko alebo terminál; ak sa použije terminál, je to stred ľavého terminálu pri horizontálnom zobrazení a nezávisí od jeho elektrickej funkcie.
- **Jednovývodové komponenty:** Norma má osobitné pravidlá pre SMD aj THD. Napríklad pri THD má vývod smerovať od tela komponentu a počiatkom je tento vývod. Tieto prípady treba preveriť samostatne.
- **Konektory a pohyblivé časti:** Počiatok sa určuje aj podľa mechanického stavu, napr. uzamknutá poloha konektora alebo dodaná poloha pohyblivej časti.
- **Courtyard a land pattern:** Norma požaduje koordináciu polohy komponentu, land patternu a obrysovej oblasti v knižnici. Samotné pravidlá geometrie land patternov odkazujú na sériu IEC 61188-5; ich súlad treba preveriť samostatne.

**Záver auditu:** Z doterajších rozhodnutí je jediným priamo identifikovaným konfliktom s IEC 61188-7 požiadavka, aby dlhšia os tela (X) bola vždy vodorovná. Ostatné pravidlá pomenovania nie sú predmetom tejto normy; pravidlo PAD1 podľa fyzickej značky je s ňou v súlade. Pred vyhlásením úplného súladu knižnice treba ešte preveriť konkrétne rodiny podľa tabuliek Level B, počiatky footprintov a súvisiace požiadavky IEC 61188-5.

### Ďalšie pravidlá IEC relevantné pre knižnicu

IEC 61188-7:2017 okrem nulovej orientácie uvádza aj tieto zásady:
- komponent, land pattern a obrysová/courtyard oblasť majú byť v knižnici navzájom súradnicovo zhodné;
- počiatok land patternu môže byť odlišný od počiatku použitého pri osádzaní; pri SMD sa všeobecne odporúča stred courtyard, pri THD možno použiť ťažisko alebo stred ľavého terminálu;
- odporúča sa počiatok v ťažisku tela komponentu;
- orientácia a poloha vývodov sú nezávislé od spôsobu dodania komponentu (páska, zásobník, trubica).

Tieto body budú predmetom samostatnej kontroly pri audite existujúcich footprintov.

## 7. Ilustračné príklady

Príklady zobrazujú aktuálny pracovný smer. Nie sú ešte finálnou syntaxou všetkých rodín.

### THD axiálny rezistor 0207

Pôvodný názov:

`RESAD1524W60L650D230-0207`

Navrhovaný názov:

`RESAD60W230D650X1524P-2N_0207`

- `60W` – šírka THD vývodu 0,60 mm
- `230D` – priemer tela 2,30 mm
- `650L` – najdlhší rozmer tela 6,50 mm
- `1524P` – rozteč vývodov 15,24 mm
- `-2N` – 2 vývody, hustota Nominal
- `0207` – komerčné označenie veľkosti

Celkový rozmer vrátane vývodov sa neuvádza, pretože v tomto príklade nie je potrebný na identifikáciu puzdra.

### SOIC-16

Pracovný príklad:

`SOIC127P400W800OL175OH-16_SOIC-16N`

- `127P` – Pitch 1,27 mm
- `400W` – kratší rozmer samotného tela 4,00 mm
- `800OL` – najdlhší celkový pôdorysný rozmer komponentu vrátane vývodov 8,00 mm
- `175OH` – celková výška komponentu 1,75 mm, ak ide o rozmer od dosadacej roviny po hornú plochu puzdra (napr. príslušný rozmer A1)

Ak sa uvádza samostatná výška tela, označí sa `Z`. Klasifikácia rozmeru ako BODY alebo OVERALL sa riadi skutočnými referenčnými plochami, nie iba označením v datasheete.

### Radiálna LED

Pracovný príklad s telom s priemerom 3 mm a samostatne definovanou výškou osadenia:

`LEDRD50W254P300D500Z-2N_CVX_FD_LL500_SH102_Red_HueyJann`

- `50W` – šírka THD vývodu 0,50 mm
- `254P` – rozteč vývodov 2,54 mm
- `300D` – priemer tela 3,00 mm
- `500H` – výška samotného tela 5,00 mm
- `SH102` – Standoff Height 1,02 mm

Ak je potrebné uviesť aj celkovú výšku komponentu, použije sa `OH`. `SH` zostáva samostatným údajom o výške osadenia a polohe 3D modelu.

### Kruhový komponent s kruhovým rozmiestnením vývodov

Pri kruhovom tele a kruhovom vonkajšom obryse možno uviesť napríklad:

- `D1800` – priemer tela 18,00 mm
- `OD2200` – maximálny vonkajší priemer 22,00 mm

Ak vývody alebo mechanické časti vytvárajú skôr obdĺžnikový obrys, použijú sa `OX` a `OY` namiesto `OD`.

## 8. Otvorené otázky

- [ ] Potvrdiť, či `P` označuje rozteč aj pri dvojvývodových súčiastkach a THD.
- [ ] Vyriešiť vzťah medzi normalizovanými rozmermi X/Y (X je dlhší rozmer tela) a orientáciou footprintov podľa IEC Level B; napr. SOIC a TSSOP majú odlišnú orientáciu dlhej osi.
- [ ] Presne definovať referenčné plochy pre rozmery H a OH.
- [ ] Určiť, ktoré doplnkové údaje (napr. `SH`, `LL`, farba, výrobca) majú zostať v samostatnej časti názvu a aké bude ich poradie.
- [ ] Preveriť kruhové a valcové telá (`D`, `OD`) a orientované montáže.\n- [ ] Definitívne vyriešiť prípadnú kolíziu kvalifikátora `W` (druhý rozmer tela verzus šírka THD vývodu) a zabezpečiť jednoznačné strojové dekódovanie.
- [ ] Preveriť orientáciu každej používanej rodiny podľa tabuliek IEC 61188-7:2017 Level B (LED, rezistorové siete, konektory, DIP, SOIC/QFP, TSSOP, BGA a ďalšie).
- [ ] Overiť, či každý podstatný geometrický rozdiel vedie k odlišnej identifikácii footprintu.
- [ ] Preveriť jednoznačnosť a strojovú dekódovateľnosť všetkých tokenov vrátane viacpísmenových kvalifikátorov `OL/OW/OH/OD`.

## 9. Zdroje

- [PCB Libraries – Footprint Expert: Design Options](https://www.pcblibraries.com/Products/FPX/UserGuide/Console%20Options/3.2%20Design.asp)
- [PCB Libraries – Footprint Expert Naming Convention](https://www.pcblibraries.com/Products/FPX/UserGuide/default.asp?ch=4)
- [PCB Libraries – Surface Mount naming convention](https://www.cskl.de/fileadmin/csk/dokumente/produkte/pcbl/pcb-footprint-expert-guideline/pcb-footprint-expert-guidline-csk_files/part84.htm)
- [PCB Libraries – aktuálna tabuľka konvencie (fórum)](https://www.pcblibraries.com/forum/pcbl-footprint-naming-convention_topic3681.html)\n- [IEC 61188-7:2017 – Electronic component zero orientation for CAD library construction (preview PDF)](https://cdn.standards.iteh.ai/samples/22959/72e624a1b6b2487e9759fa0a309144d1/IEC-61188-7-2017.pdf)\n- [PCB Libraries – Footprint Expert: predvolená orientácia PAD1 podľa IEC 61188-7](https://www.pcblibraries.com/Products/FPX/UserGuide/Component%20Options/default.asp?ch=11.10)

---

**Poznámka:** Tento dokument slúži na priebežné pracovné rozhodnutia. Do oficiálnej Wiki sa prenesú až potvrdené pravidlá. Existujúce footprinty sa v tejto fáze nepremenúvajú.
