# Konstrukční proveditelnost dispozice

Co se dá poznat na půdorysu, než se dispozice pošle statikovi. **Nic z této stránky není statický
výpočet** — je to sada červených vlajek, které má fáze B5 umět vyvěsit sama.

## Rozpony: kam který strop dosáhne

Konkrétní čísla z technického listu výrobce (inženýrská data, ne článek):
[Porotherm strop, Wienerberger](https://www.wienerberger.cz/content/dam/wienerberger/czech-republic/marketing/documents-magazines/technical/technical-product-info-sheet/wall/CZ_POR_TEC_Pth_strop.pdf).

| nosník POT | světlé rozpětí | výška nosníku |
|---|---|---|
| 1 750 mm | 1 500 mm | 175 mm |
| … stupňuje se po 250 mm … | vždy **délka − 250 mm** | 175 mm do délky 6 250 mm |
| 8 250 mm | **8 000 mm** | 230 mm od délky 6 500 mm |

Z toho dvě pravidla pro půdorys:

> **Keramický vložkový strop (MIAKO) dosáhne světlého rozpětí nejvýš 8,0 m**, a to už s nosníkem
> výšky 230 mm. Uložení je 125 mm na každé straně (rozdíl mezi délkou nosníku a rozpětím).
> Tloušťka stropu se volí podle rozpětí: 210 mm (MIAKO 15), 250 mm (MIAKO 19), 290 mm (MIAKO 23).

> **Nad světlým rozpětím 6 m** technický list doporučuje **uprostřed rozpětí příčné ztužující žebro**
> šířky jedné vložky (250 mm) se čtyřmi pruty výztuže. To je pro dispozici důležité: takové žebro je
> nosný prvek napříč místností a nese ho podhled, takže hluboká otevřená denní zóna má konstrukční
> cenu i uvnitř.

Monolitické železobetonové stropy podle [ASB Portal](https://www.asb-portal.cz/stavebnictvi/strop-a-podlaha/stropni-system/stropy-a-vodorovne-konstrukce):

| konstrukce | rozpětí |
|---|---|
| deska uložená na dvou protilehlých stranách prostě (kloubově) | do **3 m** |
| deska uložená vetknutím | **4,5–6 m** |
| deska podepřená po obvodu stěnami nebo průvlaky | do **7,2 × 7,2 m** i více |
| deska bodově podepřená (sloupy) | od **5 m**, spíš pro menší zatížení |
| skelet, hřibové stropy | **5–12 m** |
| trámové a žebrové stropy | 12 m a více |

Dřevěný trámový strop: stropnice v osových vzdálenostech **0,9–1,2 m**, běžně pro místnosti do
**6 m** šířky; na větší rozpony kombinace s ocelí nebo lepené hranoly
([Venkovský dům](https://venkovskydum.cz/druhy-stropu/),
[nejremeslnici.cz](https://www.nejremeslnici.cz/blog/stropy-v-rodinnem-dome-co-musi-splnovat-a-z-jakych-konstrukci-mate-na-vyber/) —
dva zdroje, shodně).

⚠️ Jeden z těch článků uvádí, že konce trámů se zapouštějí do zdiva „minimálně po **200 cm**". To je
zjevná chyba v jednotkách (běžné uložení je řádu 200 mm) a **nepřebírá se**.

**Vodorovná tuhost.** ASB i nejremeslnici dělí stropy na tuhé (monolit, filigrán, panely,
ocelobeton) a **vodorovně netuhé** (dřevěný, hurdiskový). Netuhý strop neroznáší vodorovné síly, což
u domu s dlouhými štítovými stěnami nebo s velkými otvory v nosných stěnách mění celý statický
koncept — a to je právě ten případ, kdy dispozice musí ke statikovi už ve studii.

## Červené vlajky na půdorysu

Studie je má umět najít sama a napsat je do verdiktu:

1. **Světlé rozpětí nad 6 m** u vložkového stropu → ztužující žebro; **nad 8 m** → jiný systém.
2. **Nosná stěna, pod níž v dolním podlaží nosná stěna není.** Musí ji nést průvlak nebo stěna
   dispozičně jinde. Nástroj to hlásí jako blokující nález pro statika.
3. **Otvor v nosné stěně širší než ~2,5 m** — překlad se mění v průvlak s uložením a s prostupem do
   podhledu; u zděného domu to jde na výšku parapetu a nadpraží.
4. **Konzola** (vyložené podlaží, arkýř, balkon bez podpory) — vždy statik.
5. **Schodišťový otvor napříč nosným směrem stropu** — deska se přerušuje v nejhorším místě.
6. **Sloup uprostřed obytného prostoru** — obvykle důsledek toho, že rozpon nikdo nezkontroloval,
   ne autorský záměr.

> **Co studie netvrdí:** dimenze. Ani jedna z hodnot výše není návrh — jsou to hranice, za kterými
> je odpověď „na tohle potřebujeme statika" (B8). Přesně tak to má být napsané i v textu varianty.

## Related pages

- [Požární bezpečnost RD](PozarniBezpecnostRD.md)
- [Přístupnost a výjimky](PristupnostAVyjimky.md)
- [Konstrukční zásady](../ArchitekturaRDObecnaPravidlaACasteChyby/KonstrukcniZasady.md)
