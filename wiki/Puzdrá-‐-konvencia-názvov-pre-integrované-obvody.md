# IC –  puzdrá pre integrované obvody

Prefix `IC` označuje polovodičové puzdrá určené pre integrované obvody.
Nasledujúca časť názvu určuje mechanickú skupinu puzdra podľa konštrukcie, nie podľa
obchodného názvu výrobcu.


SMD puzdra sú zaradené do skupín podľa jednoduchého kľúča:

```
                              IC puzdrá
                                  |
                    +-------------+--------------+
                    |                            |
                   THD                          SMD
                    |                            |
             Vývody do DPS               Spôsob kontaktu
                    |                            |
             +------+-----+              +-------+--------------+
             |            |              |                      |
        jeden rad     dva rady       s vývodmi           bez vonkajších vývodov
             |            |              |                      |
           ICSIP        ICDIP       +----+----+          +------+------------+
                                    |         |          |                   |
                                 2 str.    4 str.     po obvode        spodná mriežka
                                    |         |          |                   |
                                  ICDP      ICQP     +----+----+        +----+----+
                                                     |         |        |         |
                                                  2 str.   4 str.     plôšky  guľôčky
                                                     |         |        |         |
                                                   ICDN      ICQN     ICLGA     ICBGA
```


---



| Skupina | Popis | Zaradené |
| -- | -- | -- |
| ICDIP | Dual In-line Pins. THD puzdro s dvomi paralelnými radmi vývodov prechádzajúcimi cez DPS. | PDIP, CERDIP, MDIP a podobné puzdrá s dvomi radmi priebežných vývodov. |
| ICSIP | Single In-line Pins. THD puzdro s jedným radom vývodov. | SIP a podobné jednoradové puzdrá pre IC, regulátory alebo moduly. |
| ICDP | Dual Lead Pins. SMD puzdro s vývodmi na dvoch protiľahlých stranách tela. | SOP, SO, SOIC, SSOP, TSSOP, MSOP, VSSOP, MiniSO a podobné dvojstranné vývodové puzdrá. |
| ICQP | Quad Lead Pins. SMD puzdro s vývodmi na všetkých štyroch stranách tela. | QFP, PQFP, LQFP, TQFP, PLCC a podobné štvorstranné vývodové puzdrá. |
| ICDN | Dual No-lead. Bezvývodové SMD puzdro s kontaktmi iba na dvoch protiľahlých stranách tela. | SON, DFN, MicroDFN, MLPD a podobné dvojstranné no-lead puzdrá. |
| ICQN | Quad No-lead. Bezvývodové SMD puzdro s kontaktmi na všetkých štyroch stranách tela. Často obsahuje stredový exposed pad. | QFN, VQFN, TQFN, MLPQ a podobné štvorstranné no-lead puzdrá. |
| ICLGA | Land Grid Array. Puzdro bez vonkajších vývodov a bez spájkovacích guľôčok. Kontakty sú tvorené kovovými plôškami na spodnej strane puzdra. | LGA, µLGA a CSP/WLCSP s plochými spodnými kontaktmi bez spájkovacích guľôčok. |
| ICBGA | Ball Grid Array. Puzdro bez vonkajších vývodov, ktorého spodná strana obsahuje pole spájkovacích guľôčok. | BGA, FBGA, µBGA, WFBGA a podobné puzdrá s guľôčkovými kontaktmi. |


---

### Pravidlo zaradenia

Pri zaradení puzdra rozhoduje mechanická konštrukcia puzdra:
* spôsob montáže (THD/SMD).
* počet strán s kontaktmi alebo vývodmi,
* typ kontaktu (vývod, plôška, guľôčka),

_Tvar vývodov (napr. Gull-wing, J-Lead) sám o sebe neurčuje samostatnú skupinu_


---



Obchodné označenie výrobcu (napr. SOIC, PowerPAD, MLP, VQFN) neurčuje samostatnú skupinu, pokiaľ nemení základnú mechanickú konštrukciu. 

Toto označenie môže byť/je pridané pred názvom výrobcu.
