# Typické hodnoty A/V u rodinných domů — pásma z literatury a reálný příklad

Podle recenzovaného článku Ing. Romana Šubrta (VŠTE České Budějovice a Asociace energetických
specialistů, TZB-info, 1.7.2013) byl publikován konkrétní realizovaný rodinný dům s těmito
parametry:

- **dvoupodlažní rodinný dům s plochou střechou**, objem **647 m³**
- **objemový faktor tvaru A/V = 0,706 m²/m³** (v článku "tvarový faktor A/V")
- prosklení cca **18 %** podlahové plochy
- měrná potřeba tepla na vytápění: podle PHPP **17 kWh/(m².a)**, podle TNI **16 kWh/(m².a)**;
  ve výpočtu bylo uvažováno s tepelnými vazbami ΔUtbk = 0,0 W/(m²·K). **Pozor na vztažnou plochu:**
  při výpočtu podle TNI s podlahovou plochou z **vnějších** rozměrů klesne měrná potřeba tepla na
  **12,3 kWh/(m².a)** — tedy o čtvrtinu, při nezměněné hmotě domu. Autor z toho výslovně vyvozuje,
  že je nutné hlídat, jaké vztažné plochy byly použity.
- dům byl navržen a vyhodnocen jako **pasivní** (splňuje požadavky i pro budovu s téměř nulovou
  spotřebou energie při volbě přísnějších — "2. hranice dle normy" — hodnot součinitelů prostupu
  tepla jednotlivých konstrukcí)

Toto A/V = 0,706 m²/m³ leželo by v **historické** tabulce Uem,N (viz [[Definice|Definice pojmů]],
tabulka 9 komentáře k ČSN 73 0540, vydání 2011) mezi řádky 0,7 a 0,8; mezilehlá hodnota se
dopočítávala vztahem 0,30 + 0,15/(A/V), tj. cca 0,51 W/(m²·K).
⚠️ **Tento požadavek už není platný** — vydání ČSN 73 0540-2 ze srpna 2025 požadavky na průměrný
součinitel prostupu tepla budovy odstranilo (viz varování na stránce [[Definice]]). Odstavec je
zde pro orientaci v řádové velikosti, ne jako normový požadavek.

## Pásma A/V pro RD

Zdroje shromážděné k tomuto úkolu tabulku pásem **neobsahují** — dávají jen jednotlivé body
a jednu vlastnost ukazatele. Pásma doložená mimo tento úkol jsou v podsekci níž.

| Doložený bod | A/V | Zdroj |
|---|---|---|
| realizovaný dvoupodlažní RD s plochou střechou, V = 647 m³, pasivní standard | 0,706 m²/m³ | https://stavba.tzb-info.cz/pasivni-domy/10097-referencni-budova-a-pasivni-domy |
| malá krychlová budova (ilustrace citlivosti ukazatele na velikost) | ≈ 0,6 | https://www.tzb-info.cz/4709-tvary-budov-z-pohledu-spotreby-tepla-a-chladu |
| krychlový objekt velkého objemu (tentýž tvar, jiná velikost) | ≈ 0,2 | tamtéž |

Z toho plyne praktický závěr pro porovnávání hmotových variant: **A/V je citlivé na velikost
domu, ne jen na jeho tvar**, takže hodnoty A/V lze mezi variantami srovnávat jen při přibližně
stejném objemu; u malých objektů (typicky RD) vychází A/V nutně nepříznivěji než u velkých budov
a dosažení pasivní úrovně je proto obtížnější (viz [[VypocetPlochAObjemu]]).

### Pásma z literatury — existují, ale nejsou srovnatelná s výstupem `av.py`

Dva na sobě nezávislé prameny pásma uvádějí. **Ani jeden neplatí jako norma a ani jeden neměří `V`
tak, jak ho počítá `tools/av/av.py`** (obálka a objem vytápěné zóny z vnějších rozměrů).

| pramen | co uvádí |
|---|---|
| e-genius.at / GrAT (rakouský výukový modul „Energeticky účinné budovy", česká verze, CC BY-NC-ND 4.0, **bez autora a bez data**) | RD **obvykle 0,7–1,0**; pasivní RD „pokud možno nejvýše **0,8**"; větší budovy až **0,2**; kulový tvar < 0,3; krychle ≈ 0,5; členitá budova > 0,8; S-HOUSE Böheimkirchen, obestavěný prostor ≈ 1200 m³ → A/V **0,6** |
| Ing. arch. David Křeček, FA VUT Brno, „Energetická optimalizace architektonického konceptu", sborník doktorandské konference (nedatováno, nejnovější citovaný zdroj 2009), s. 46–51 — přebírá z NAGY, E.: *Nízkoenergetický a energeticky pasivní dům*, Jaga Group 2009 | výškové budovy **0,2–0,3**; deskové a bodové **0,4–0,5**; „nižší podlažností se poměr A/V zvyšuje na **0,6**"; pro dobrou energetickou kvalitu se doporučuje **nepřekročit 0,7** |

⚠️ **CONFLICT:** e-genius považuje 0,7–1,0 za běžné pásmo RD, Křeček/Nagy doporučuje 0,7
nepřekračovat. Podle prvního je typický RD nad doporučením druhého. Rozpor není vysvětlen ani
v jednom pramenu.

**Proč se pásma nesmí přebírat jako hodnotící mez:**

1. **Jiné `V`.** e-genius definuje `V` výslovně jako **obestavěný prostor** („velikost objemu budovy
   (obestavěnému prostoru) „V""). Obestavěný prostor je větší než objem vytápěné zóny (viz
   [[ObestavenyProstor]]), takže jejich A/V vychází **nižší** než A/V ze stejného domu spočítané
   nástrojem. Křeček definici neuvádí vůbec.
2. **Žádná normová opora.** Vyhl. č. 264/2020 Sb. mez A/V nestanoví a ČSN 73 0540-2 (8/2025)
   požadavek na Uem odstranila. Obě čísla jsou doporučení autorů, ne požadavek.
3. **Oba prameny jsou výukové/přehledové**, ne měření. Křeček čísla přebírá z knihy z r. 2009,
   e-genius je nepřipisuje nikomu.

**Jak s tím tedy pracovat:** pásma slouží jako kontrola řádu — vyjde-li variantě RD A/V 0,45 nebo
1,8, je pravděpodobně chyba ve vstupech. Rozhodnutí mezi variantami se dělá **porovnáním variant
mezi sebou** (a u variant různé velikosti přes RC), ne zatříděním do pásma. Viz
[[PorovnaniVariant]].

Doložený dopad tvaru: „při stejné kvalitě stavebních konstrukcí a technických prvků se
nízkoenergetické rodinné domy o různém poměru A/V mohou lišit o faktor 2,5, v případě pasivních
dokonce o faktor 7,5" (Křeček, přebírá z Nagy 2009) *(needs second source — jediný pramen, bez
uvedení rozsahu A/V, na kterém ten faktor platí)*.

(sources: https://www.e-genius.at/fileadmin/user_upload/lernfelder/energieeffiziente_gebaeudekonzepte/alt/cz/web/jak_tvar_objektu_je_pro_pasivn_dm_nejvhodnj.html ,
https://dspace.vut.cz/bitstream/handle/11012/56698/46-51_krecek.pdf)

## Poznámka k porovnatelnosti

Autor zdůrazňuje, že konečné zatřídění budovy do energetické třídy závisí kromě průměrného
součinitele prostupu tepla Uem (a tedy nepřímo A/V) i na dalších parametrech budovy (skladba
konstrukcí, tepelné vazby, technické systémy) — samotné A/V tedy nestačí k závěru o
energetické třídě budovy, jde jen o jeden ze vstupů referenčního výpočtu.

(source: https://stavba.tzb-info.cz/pasivni-domy/10097-referencni-budova-a-pasivni-domy)

<!-- nerd:links -->
## See also

- [[Definice]]
- [[PorovnaniVariant]]
- [[VypocetPlochAObjemu]]
<!-- /nerd:links -->
