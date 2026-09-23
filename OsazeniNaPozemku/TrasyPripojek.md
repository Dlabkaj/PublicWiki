# Trasy přípojek na pozemku

Kolik místa přípojky zaberou a co se z toho dá ve fázi B3 skutečně rozhodnout. Odpověď je
skromnější, než se čeká: **pořadí a hloubky ano, vodorovné rozestupy ne.**

Prostorové uspořádání sítí technického vybavení upravuje **ČSN 73 6005**. Norma je placená;
níže je jen to, co je doložitelné z volně dostupných pramenů, a u každé hodnoty je uvedeno odkud.

## Pravidla, která jsou kvalitativní — a proto použitelná

Pořadí sítí v přidruženém prostoru od zástavby: silové kabely → plynovod → vodovod (vodovodní
potrubí se ukládá „v prostoru za plynovod směrem od zástavby").

Při **křížení** se ukládá:

| síť | nad | pod |
|---|---|---|
| vodovod a vodovodní přípojka | stoky jednotné soustavy, stoky oddílné splaškové kanalizace | silové a sdělovací kabely, plynovod, stoky oddílné dešťové kanalizace (s technickým ochranným opatřením) |
| plynovod | vodovodní přípojka, tepelné sítě, hloubkové kabelovody, stokové sítě a kanalizační přípojky | kabelová vedení silová a sdělovací |
| gravitační stoky (kromě dešťových) | — | vždy hlouběji než vodovodní potrubí |
| tlaková kanalizace | lze i nad vodovod, ale **po dohodě správců** dotčených vodovodních sítí | — |

Souběh v obousměrné zástavbě: při celkové šířce pásů **menší než 3 m** zpravidla jednostranně, při
šířce **větší než 3 m** oboustranně.
(source: https://hgf10.vsb.cz/546/PVH/prostorove_usporadani_siti.html)

> Pro osazení z toho plyne jedno použitelné pravidlo: **kanalizace je nejhlubší a nejméně ohebná.**
> Její spád od domu k bodu napojení určuje, jak nízko může jít ±0,000 — a to je vazba na § 18
> vyhl. č. 146/2024 Sb. řešený v B2.

## Nejmenší dovolené krytí

Z **4. návrhu revize ČSN 73 6005 (únor 2018)**, tabulka B.1. ⚠️ Je to **návrh, ne platné vydání** —
hodnoty slouží k odhadu prostorových nároků, nikdy jako podklad pro provedení:

| vedení | chodník | vozovka | volný terén |
|---|---|---|---|
| silové kabely do 1 kV | 500 mm | 1 000 mm | 350 / 700 mm |
| silové kabely do 10 kV | 500 mm | 1 000 mm | 700 mm |
| kabely elektronických komunikací, místní | 400 mm | 900 mm | 600 mm |
| plynovod do 0,4 MPa | 800 mm | 1 000 mm | 800 mm |

*(needs second source — 4. návrh revize z r. 2018, nikoli platné vydání normy; závazné hodnoty
jsou v placené ČSN 73 6005 a ve vyjádření správce sítě)*
(source: https://www.vnictp.cz/sites/default/files/content/article/jednani-o-4-navrhu-revize-normy-csn-73-6005-prostorova-norma/csn736005navrh5unor2018.doc)

Tentýž návrh dále uvádí, že v odůvodněných případech lze technologií řízeného protlaku ukládat
silové kabely NN a VN i pod nejníže uloženou síť; za bezpečnou vzdálenost pilotního vrtu od
vnějšího líce uloženého potrubí se přitom považuje **1,5 m** *(needs second source — návrh normy, ne platné vydání)*.

## Vodorovné rozestupy: proč tady žádná tabulka není

Matici nejmenších dovolených vodorovných odstupů (tabulka A.1 ČSN 73 6005) se z volně dostupných
zdrojů **nepodařilo získat v čitelné podobě**. Dostupné jsou dvě věci a ani jedna není použitelná:
návrh revize z r. 2018, jehož tabulka se ze souboru nevytáhla, a projektová dokumentace veřejné
zakázky, kde jsou čísla bez čitelných hlaviček sloupců — tj. nelze spolehlivě přiřadit hodnotu
k páru sítí.

🔴 **Vědomě nedoplněno.** Přepsat matici, u které si nejsem jistý osami, by bylo horší než ji
neuvádět: chybná hodnota v milimetrech vypadá stejně věrohodně jako správná.

Pro fázi B3 to nevadí tak, jak by se zdálo:

1. Studie **nedimenzuje rýhu**. Rozhoduje o **koridoru** — kudy trasy povedou, aby se nekřížily
   s vsakem, kořeny stromů, opěrnou zdí a základy vedlejších objektů.
2. Závazné podmínky souběhu a krytí stanoví **vyjádření vlastníka sítě** ke konkrétní přípojce,
   a to je stejně podmínka uzavření fáze B1 i B3 → viz
   [Vyjádření správců sítí](../ZasitovaniPozemku/PodkladyPozemku/VyjadreniSpravcuSiti.md).
3. Kde se koridor dostane do konfliktu s odstupem 2 m od hranice, platí § 11 odst. 3 písm. b)
   vyhl. č. 146/2024 Sb.: **sítě technické infrastruktury a zpevněné plochy odstup držet nemusí**
   → viz [Poloha a stavební čára](PolohaAStavebniCara.md).

## Co z toho platí pro fázi B3

1. Do situace se kreslí **koridor přípojek**, ne dimenze — a kontroluje se proti ploše pro vsak,
   proti stromům a proti vedlejším objektům.
2. Kanalizace určuje spád a tím i výšku podlahy; řeší se první.
3. Krytí se bere jako **odhad prostorových nároků** z návrhu normy, závazné je vyjádření správce.
4. Přípojky nemusí držet 2 m od hranice (§ 11 odst. 3 písm. b)) — a to se do studie napíše
   s odkazem na to písmeno, protože to je nejčastěji napadaná kóta.

## Zdroje

- VŠB HGF — Prostorové uspořádání sítí technického vybavení (výklad ČSN 73 6005)
  (https://hgf10.vsb.cz/546/PVH/prostorove_usporadani_siti.html)
- 4. návrh revize ČSN 73 6005, únor 2018 — tabulka B.1 (krytí), **návrh, ne platné vydání**
  (https://www.vnictp.cz/sites/default/files/content/article/jednani-o-4-navrhu-revize-normy-csn-73-6005-prostorova-norma/csn736005navrh5unor2018.doc)
- 146/2024 Sb., § 11 odst. 3 písm. b), ve znění účinném od 1. 7. 2026 (e-Sbírka)
