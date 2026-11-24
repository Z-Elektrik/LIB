## Hustota

Hustota určuje požadovanú úroveň zhustenia vývodov a spájkovacích plôch vzhľadom na mechanické rozmery komponentu.

Vychádza z IPC klasifikácie:

| Token | Názov | Význam |
|---|---|---|
| **L** | Least Density | nízka hustota |
| **N** | Nominal Density | štandardná hustota |
| **M** | Maximum Density | vysoká hustota |

---


## IPC-7351 Density Levels

Norma IPC-7351 definuje tri úrovne hustoty (Density Levels), ktoré určujú geometriu puzdra – predovšetkým veľkosť medených plôšok, solder filletov a courtyardu. Výber hustoty predstavuje kompromis medzi zabranou plochou DPS, spoľahlivosťou spájkovania a možnosťou opravy.

| IPC Density | Označenie | Charakteristika | Typické použitie |
|-------------|-----------|-----------------|------------------|
| **Level A** | **M** (Maximum / Most) | Najväčšie pady a najväčšie solder fillets. Poskytuje najrobustnejší spoj a najjednoduchší rework. | Prototypy, priemyselné zariadenia, aplikácie s vibráciami alebo mechanickým namáhaním. |
| **Level B** | **N** (Nominal / Median) | Kompromis medzi veľkosťou footprintu a spoľahlivosťou spájkovania. Predstavuje odporúčanú a najčastejšie používanú variantu. | Väčšina komerčných elektronických zariadení. |
| **Level C** | **L** (Least / Minimum) | Najmenšie pady a najmenšie solder fillets, umožňuje najvyššiu hustotu osadenia PCB. Vyžaduje presnejšiu výrobu a montáž. | Miniatúrne zariadenia, mobilná elektronika, vysoká hustota osadenia. |

---


### Rozdiel medzi jednotlivými hustotami

Prechod medzi jednotlivými úrovňami hustoty mení najmä:

- veľkosť medených plôšok (Land Pattern),
- veľkosť solder filletov (Toe, Heel, Side),
- veľkosť courtyardu.

Vo všeobecnosti platí:

| Parameter | Level A (M) | Level B (N) | Level C (L) |
|-----------|-------------|-------------|-------------|
| Veľkosť plôšok | najväčšia | stredná | najmenšia |
| Toe fillet | najväčší | stredný | najmenší |
| Heel fillet | najväčší | stredný | najmenší |
| Side fillet | najväčší | stredný | najmenší |
| Courtyard | najväčší | stredný | najmenší |
| Hustota osadenia | najnižšia | stredná | najvyššia |
| Možnosť reworku | najlepšia | dobrá | obmedzená |

### Poznámky

- **Level B (N)** je štandardná voľba pre väčšinu návrhov PCB.
- **Level A (M)** zvyšuje spoľahlivosť spojov za cenu väčšej plochy PCB.
- **Level C (L)** maximalizuje hustotu osadenia, ale kladie vyššie nároky na výrobu aj montáž.
- Niektoré puzdrá (napr. **BGA** a niektoré **QFN**) podľa IPC-7351 nemusia mať varianty L/M/N, pretože norma pre ne definuje iba nominálnu geometriu footprintu. :contentReference[oaicite:0]{index=0}