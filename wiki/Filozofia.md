# Filozofia

Cieľom Z-Elektrik/LIB bolo a je vytvoriť jednotnú, konzistentnú a dlhodobo udržiavateľnú knižnicu elektronických komponentov pre KiCad.

Nezameriava sa iba na počet dostupných komponentov. Hlavným cieľom bolo a je vytvorenie systému, v ktorom majú všetky časti komponentu jasne definované pravidlá a vzájomné väzby.

## Komponent ako celok

Každý komponent predstavuje jeden logický celok pozostávajúci z:

- symbolu,
- puzdra,
- 3D modelu,
- zdrojového parametrického modelu.

Jednotlivé časti komponentu nie sú chápané ako samostatné objekty, ale ako vzájomne prepojené časti jedného fyzického prvku.

## Konzistentnosť

Všetky časti knižníc používajú jednotné pravidlá pomenovania a organizácie.

Cieľom je, aby bolo možné z názvu alebo štruktúry súborov čo najjednoduchšie určiť ich význam bez potreby ďalšieho hľadania.

## Parametrické modelovanie

Ak je to možné, mechanické modely sú vytvárané parametrickým spôsobom.

Zdrojový model zostáva súčasťou projektu a umožňuje ďalšie úpravy alebo opätovné generovanie odvodených formátov.

## Automatizácia

Štruktúra knižníc je navrhnutá s ohľadom na možnosť automatizovaného spracovania, kontroly a publikovania.