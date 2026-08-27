# Etapové rozdělení nákladů RD

**Summary**: Převod procentní struktury stavebních dílů RTS (obor 803) na chronologické etapy výstavby — základy, hrubá stavba, střecha, výplně otvorů, TZB, povrchy, dokončení — plus konfliktní údaje z ostatních zdrojů.

**Sources**: [cenovasoustava.cz — Cenové ukazatele ve stavebnictví pro rok 2026](https://www.cenovasoustava.cz/dok/ceny/thu_2026.html)

**Last updated**: 2026-08-13

---

## ⚠️ PŘEDPOKLAD: seskupení dílů do etap je vlastní předpoklad, ne údaj ze zdroje

RTS publikuje **strukturu stavebních dílů** (věcné třídění TSKP), **nikoli** rozdělení podle etap výstavby. Žádný zdroj neříká, který díl patří do které etapy. Následující mapování je **vlastní předpoklad této stránky**, provedený proto, aby šlo z cenového ukazatele vytvořit etapový rozpočet. Není to citovatelný fakt.

Výchozí data: sloupec „Průměr" oboru 803 Budovy pro bydlení — viz [[RtsCenoveUkazatele2026]].

## Mapování dílů na etapy (předpoklad této stránky)

| Etapa | Zahrnuté díly | % ZRN |
| --- | --- | --- |
| Zemní práce a základy | 1 Zemní práce (0,9) + 2 Základy (5,6) | **6,5** |
| Hrubá stavba | 3 Svislé konstrukce (21,2) + 4 Vodorovné konstrukce (10,9) + 9 Ostatní konstrukce, bourání (2,7) + 99 Přesun hmot (3,7) + 711 Izolace proti vodě (0,6) | **39,1** |
| Střecha | 762 Tesařské (0,9) + 764 Klempířské (0,9) + 765 Krytiny tvrdé (0,2) + 712 Živičné krytiny (0,7) | **2,7** |
| Výplně otvorů | 766 Truhlářské (7,4) + 767 Zámečnické (8,0) + 787 Zasklívání (0,3) | **15,7** |
| TZB / instalace | 721–726 (9,8) + 731–735 (3,0) + M21 (4,5) + M22 (0,9) + M24 (0,7) + M33 (2,2) + M36 (0,2) | **21,3** |
| Povrchy a podlahy | 6 Úpravy povrchu, podlahy (5,8) + 713 Izolace tepelné (1,6) + 771 (0,9) + 772 (0,1) + 776 (1,7) + 777 (0,9) + 781 (0,9) + 783 Nátěry (1,0) + 784 Malby (0,5) | **13,4** |
| Dokončení a ostatní | 5 Komunikace (0,1) + 8 Trubní vedení (0,1) + 761 (0,1) + 786 (0,6) + 793 (0,2) + M43 (0,1) + M99 (0,2) | **1,4** |
| | **Celkem** | **100,1** (zaokrouhlení) |

## Sporná místa v mapování

Několik rozhodnutí, která by šla udělat jinak a znatelně by posunula čísla:

- **711 Izolace proti vodě** dána do hrubé stavby (hydroizolace spodní stavby). Část jí ale patří ke koupelnám, tedy do povrchů.
- **713 Izolace tepelné (1,6 %)** dána do povrchů. Zateplení fasády by šlo stejně dobře řadit do hrubé stavby nebo do samostatné etapy „obálka budovy". U dnešních energetických standardů je to nezanedbatelná položka.
- **767 Konstrukce zámečnické (8,0 %)** dány do výplní otvorů — u bytových domů to jsou hlavně zábradlí a schodiště, ne okna. U bungalovu tato položka bude výrazně nižší. Etapa „výplně otvorů" je proto pravděpodobně **nadhodnocená**.
- **726 Instalační prefabrikáty (6,0 %)** dány do TZB. U individuálního RD je tento díl prakticky nulový, takže TZB je také **nadhodnoceno**.
- **9 Ostatní konstrukce, bourání (2,7 %)** a **99 Přesun hmot (3,7 %)** jsou průřezové položky, které se ve skutečnosti táhnou celou stavbou; přiřazení k hrubé stavbě je zjednodušení.

## Střecha vychází nesmyslně nízko

**2,7 % na střechu je u bungalovu se sedlovou střechou nepoužitelné.** Tabulka je za celý obor 803 včetně bytových domů s plochou střechou a bez krovu. U bungalovu s krovem, latěmi, pálenou/betonovou krytinou, klempířskými prvky a podstřešní fólií je reálný podíl podstatně vyšší.

⚠️ Pro etapový rozpočet bungalovu je tuto položku nutné nahradit číslem z jiného zdroje nebo z bottom-up odhadu. Zbývající etapy pak dopočítat proporcionálně.

## Druhý nezávislý rozpad — ESTAV.cz / Netdata software (2018)

Zdroj: [ESTAV.cz — Z čeho všeho se skládá cena rodinného domu](https://www.estav.cz/cz/6746.z-ceho-vseho-se-sklada-cena-rodinneho-domu), Ing. Pavel Vrána (Netdata software), 11. 10. 2018.

Tohle je **skutečně nezávislý zdroj** — nevychází z RTS, ale z cenové soustavy **RONET**. Uvádí modelové procentní rozložení nákladů běžného RD, který **není dřevostavbou**, neobsahuje tepelné čerpadlo, vzduchotechniku ani výtah a je v obvyklém standardu vybavení. To sedí na jednopodlažní zděný bungalov velmi dobře.

⚠️ **Rok 2018.** Struktura podílů je stabilnější než absolutní ceny, ale za osm let se poměry posunuly — hlavně u TZB (dnešní RD běžně má tepelné čerpadlo a rekuperaci, které tento model výslovně vylučuje) a u řeziva.

### Pozor na základnu procent

⚠️ **Procenta v tomto zdroji NEJSOU ze stejné základny jako u RTS.** Zde je 100 % = **ZRN + VRN včetně DPH**. Rozpad:

| Položka | % z celku s DPH |
| --- | --- |
| ZRN + VRN s DPH | 100 |
| DPH | 13,0 |
| ZRN + VRN bez DPH | 87,0 |
| **ZRN** | **83,9** |
| VRN | 3,1 |

RTS procenta jsou naproti tomu ze **ZRN**. Aby byla čísla porovnatelná, je nutné hodnoty z ESTAVu vydělit 0,839. Bez toho vypadá ESTAV systematicky o ~16 % nižší, což je ryze artefakt základny, ne skutečný rozdíl. (Kontrola: HSV + PSV + ZTI + montážní práce = 30,0 + 41,2 + 8,2 + 4,5 = 83,9 = ZRN. Sedí.)

Mimochodem — **VRN zde vychází na 3,1 %** ZRN+VRN. To je konkrétní číslo pro položku, kterou cenový ukazatel RTS neobsahuje vůbec. Text zdroje to potvrzuje slovně: VRN se obvykle pohybují v jednotkách procent ceny stavebního díla, u RD tedy v řádu desítek tisíc korun.

### Porovnání etap: RTS vs. ESTAV

Vpravo přepočteno na základnu ZRN (děleno 0,839), aby šlo srovnávat.

| Etapa | RTS 803 (% ZRN) | ESTAV (% ZRN) | Zahrnuté položky ESTAV |
| --- | --- | --- | --- |
| Zemní práce a základy | 6,5 | **4,4** | C1 (0,2) + C2 (3,5) |
| Hrubá stavba | 39,1 | **20,5** | C3 (8,6) + C4 (4,7) + C95 (1,1) + C99 (2,8) |
| Střecha | 2,7 | **12,2** | C762 tesaři/krov (4,6) + C764 klempíři (1,3) + C765 pokrývači (4,3) |
| Výplně otvorů | 15,7 | **18,9** | C766 truhláři (13,8) + C767 zámečníci (1,4) + C64 zárubně (0,7) |
| TZB / instalace | 21,3 | **15,1** | ZTI (8,2) + montážní práce (4,5) |
| Povrchy a podlahy | 13,4 | **28,2** | C61 (2,4) + C62 (0,9) + C63 (4,6) + C71 izolace (6,6) + C763 SDK (1,9) + C77 (5,6) + C781 (0,9) + C784 (0,8) |
| Ostatní (lešení) | 1,4 | **0,6** | C94 (0,5) |

## Nesrovnatelné definice: hrubá stavba 39 % vs. 20 %

> **Adjudikováno v REVIEW (2026-08-13): nejde o rozpor mezi zdroji.** Obě čísla jsou správná pro svou definici — měří jiný výsek stavby, ne stejnou veličinu s jiným výsledkem. Neblokuje; blokovalo by jen, kdyby dva zdroje tvrdily různé hodnoty téhož.

Rozdíl mezi 39,1 % (RTS) a 20,5 % (ESTAV) **není měřicí chyba — je to jiná definice pojmu.**

- Článek sám říká, že HSV „představuje především hrubou stavbu domu", a HSV je 30 % (tj. 35,8 % ZRN). Jenže do HSV řadí i vnitřní a vnější omítky, podkladní vrstvy podlah a dveřní zárubně — tedy věci, které by laik do hrubé stavby nedal.
- Skupina „hrubá stavba" z RTS obsahuje svislé + vodorovné konstrukce + přesun hmot + ostatní konstrukce + hydroizolaci.
- Podle toho, kam se položí hranice, vyjde stejná stavba na 20 %, 30 %, 36 % nebo 39 %.

**Nepočítat průměr těchto čísel.** Průměr dvou různých definic nedává třetí, lepší číslo — dává nesmysl. Při použití vždy uvést, které položky do „hrubé stavby" počítáme.

## Omezení zdroje: střecha 2,7 % vs. 12,2 %

> **Adjudikováno v REVIEW (2026-08-13): není to rozpor, je to omezení statistické základny RTS.** Obor 803 zahrnuje bytové domy s plochou střechou, takže průměr 2,7 % je pro tento vzorek správný — jen neplatí pro RD se sedlovou střechou. RTS zde není „vedle"; je jen za jinou populaci staveb. Řešení je doporučení níže (~10–12 % pro bungalov), ne verdikt o chybě.

Zde naopak **nejde o definici, ale o typ stavby**. Obě čísla pokrývají prakticky totéž (krov + krytina + klempířina), ale:

- RTS 2,7 % je průměr celého oboru 803 **včetně bytových domů s plochou střechou**.
- ESTAV 12,2 % je modelový **rodinný dům** — tedy přesně sledovaný případ.

**Pro bungalov se sedlovou střechou je ESTAV číslo (cca 12 % ZRN) výrazně důvěryhodnější.** Rozpor potvrzuje podezření z [[RtsCenoveUkazatele2026]], že střešní díly v průměru oboru 803 jsou pro RD nepoužitelně nízké.

Podobně **povrchy a podlahy** (13,4 vs. 28,2 %) — část rozdílu je způsobena tím, že jsme do ESTAV skupiny zařadili C71 izolace (6,6 %), zatímco v RTS mapování je izolace proti vodě v hrubé stavbě. Zbytek je reálný rozdíl.

## Třetí rozpad — DŘEVO&stavby (anketa realizačních firem)

Zdroj: [DŘEVO&stavby — Podrobný rozpočet domu aneb kolik co stojí?](https://www.drevoastavby.cz/o-drevostavbach/jak-na-financovani-stavby/podrobny-rozpocet-domu-aneb-kolik-co-stoji), redakce, publikováno 10. 5. 2025; článek původně vyšel v časopise **DŘEVO&stavby 4/2022**.

⚠️ **Metodika je jiná než u obou předchozích zdrojů, a je slabší.** Redakce sestavila „slepý rozpočet" o 15 položkách a **požádala tři realizační firmy a projekční ateliéry o odhad** procentního rozdělení. Jsou to tedy **odhady odborníků, ne vyhodnocená data z rozpočtů**. Uvedená čísla jsou průměry napříč respondenty.

⚠️ **Modelový objekt neodpovídá bungalovu**: **dvoupodlažní dům**, zastavěná plocha 100 m², podlahová plocha 160 m², **dřevostavba**, ve variantě „na klíč". Sledovaný typ je jednopodlažní zděný bungalov. U dvoupodlažního domu připadá na m² podlahové plochy méně základů a méně střechy než u bungalovu — a přesně tyto dvě položky jsou u bungalovu nejcitlivější.

| Položka | % z ceny na klíč |
| --- | --- |
| Základy domu | více než 10 |
| Nosná konstrukce | ~20 |
| Kompletní zateplení | 10 |
| Úprava vnitřních povrchů (výmalba, sádrokartony, podlahy, schody) | 10–15 |
| Zasíťování objektu | 7 |
| Vytápění a ohřev teplé vody | 7 |
| Vybavení a obložení koupelen | 6 |
| Okna a vstupní dveře | 6 |
| Střešní krytina | ~6 |
| Fasáda | ~5 |
| Vnitřní dveře | do 3 |
| Komín | do 2 |
| Kuchyňská linka | do 5 (většina dodavatelů považuje za nadstavbu) |
| Základní technologie (venkovní žaluzie, požární hlásiče, zabezpečení) | do 5 (obtížně odhadnutelné) |
| Úpravy kolem domu | 2–5 (nebývá v základní nabídce) |

⚠️ Součet horních hranic přesahuje 100 %. Jsou to nezávisle odhadnuté rozsahy, ne rozklad jednoho koláče — nelze je sčítat a očekávat 100.

## Hrubá stavba potřetí — a zase jinou definicí

> **Adjudikováno v REVIEW (2026-08-13):** tři definice a tři základny, ne tři měření. Nesrovnatelnost je zde závěrem, ne otevřeným rozporem.

Nyní máme tři čísla pro zhruba totéž:

| Zdroj | „Hrubá stavba" | Co tím myslí |
| --- | --- | --- |
| RTS 803 (seskupení této stránky) | **39,1 %** ZRN | svislé + vodorovné konstrukce + přesun hmot + ostatní konstrukce + hydroizolace |
| ESTAV / RONET | **20,5 %** ZRN (HSV celkem 35,8 %) | hrubé svislé + vodorovné konstrukce + ostatní práce + přesun hmot |
| DŘEVO&stavby | **~20 %** ceny na klíč | „nosná konstrukce domu" — bez základů, bez zateplení |

**Toto nejsou tři měření téže veličiny.** Jsou to tři různé definice pojmu „hrubá stavba", navíc počítané ze tří různých základen (ZRN / ZRN / cena na klíč včetně DPH a marže). **Zprůměrovat je by bylo hrubě zavádějící** — vzniklo by číslo, které neodpovídá žádné z použitých definic.

Článek sám k tomu poznamenává, že častým omylem stavebníků je předpoklad, že samotná konstrukce domu tvoří valnou většinu celkové ceny. To všechny tři zdroje shodně vyvracejí — nosná konstrukce je nanejvýš dvě pětiny, a podle užší definice jen pětina.

### Střecha: třetí zdroj potvrzuje ESTAV, ne RTS

DŘEVO&stavby uvádí **střešní krytinu ~6 %**, a to samotnou krytinu bez krovu a klempířiny (ty spadají pod „nosnou konstrukci"). ESTAV má krytinu (pokrývači) 4,3 % z celku, tj. 5,1 % ZRN — **tedy prakticky shodně**. Dva nezávislé zdroje se u střešní krytiny shodují na ~5–6 %, zatímco RTS má celou střechu včetně krovu na 2,7 %.

Jeden z dotazovaných odborníků navíc uvádí **cenu střechy jako položku, která klienty v rozpočtu nejvíc překvapí** — kvůli razantnímu navýšení ceny krytiny a hlavně práce. To dobře koresponduje s indexem latí 1,172 za rok 2025 (viz [[RtsCenoveUkazatele2026]]).

**Závěr pro bungalov: brát střechu jako ~10–12 % ZRN, ne 2,7 %.**

### Základy: DŘEVO&stavby vs. ostatní

Základy „více než 10 %" je výrazně nad RTS (5,6 %) i ESTAV (4,4 % ZRN). Pravděpodobné vysvětlení: u dřevostavby tvoří základová deska relativně větší podíl, protože nadzemní konstrukce je levnější, a položka zřejmě zahrnuje i přípojky (jeden respondent mluví o „spodní stavbě + přípojkách" jako jednom celku). ⚠️ **Pro zděný bungalov je tento údaj nepoužitelný přímo**, ale je varováním, že u nás jsou základy relativně dražší než u patrového domu — bungalov má při stejné podlahové ploše dvakrát větší základovou desku.

## Čtvrtý rozpad — RealFree.cz (2026)

Zdroj: [RealFree.cz — Stavba domu 2026](https://realfree.cz/blog/stavba-domu-2026), Pavel z RealFree, 24. 6. 2026.

⚠️ **Nejslabší zdroj v sadě. Používat jen jako orientaci na řádovou správnost, nikdy jako podklad pro číslo.** Důvody:

- Web sám uvádí: „Při tvorbě a úpravách tohoto článku byly použity nástroje umělé inteligence."
- Článek obsahuje **partnerské odkazy** (mj. na stavebniny) — má ekonomický zájem na obsahu.
- RealFree je realitní inzertní portál, ne stavební ani rozpočtářská autorita.
- Jako zdroje uvádí **jiné weby** (hypoindex.cz, estav.cz, nejremeslnici.cz aj.), tedy jde o kompilaci z druhé ruky, ne o vlastní data.

Přesto je to jediný nalezený rozpad s datem 2026, takže má cenu ho mít zapsaný — jako kontrolu, ne jako pramen.

| Etapa | % rozpočtu | Poznámka zdroje |
| --- | --- | --- |
| Projekt a inženýring | 3–5 | projektová dokumentace 150–300 tis. Kč |
| Základy a spodní stavba | 10–15 | závisí na svahu, spodní vodě, únosnosti podloží |
| Hrubá stavba — zdivo, stropy, **střecha** | 30–35 | konstrukční systém ovlivní cenu méně, než se čeká |
| Okna, dveře, izolace | 10–15 | |
| Instalace — voda, kanalizace, elektřina, topení | 15–20 | tepelné čerpadlo s podlahovkou 300–500 tis. |
| Dokončovací práce | 20–25 | omítky, podlahy, obklady, sanita, kuchyň |

⚠️ Součet horních hranic je 115 %, dolních 88 %. Opět rozsahy, ne rozklad koláče.

⚠️ **Pozor na základnu**: zdroj neuvádí, zda jde o ZRN, cenu na klíč nebo cenu včetně projektu. Vzhledem k tomu, že projekt je v seznamu, jde nejspíš o **celkový rozpočet stavebníka včetně DPH** — tedy zase jinou základnu než u předchozích tří.

**Definice hrubé stavby je zde počtvrté jiná**: 30–35 % **včetně střechy**, ale bez základů. To je jediný ze čtyř zdrojů, který střechu počítá do hrubé stavby — a proto jeho číslo nelze porovnávat s ostatními bez rozpadu, který zdroj neposkytuje.

## Základová deska — přímá sazba Kč/m²

Zdroj: [VEXTA DOMY — Ceny typových dřevostaveb v roce 2026](https://www.vextadomy.cz/novinka-ceny-typovych-drevostaveb-2026), 2026.

⚠️ **Marketingová stránka výrobce dřevostaveb.** Slouží k prodeji vlastních typových domů, čísla jsou nabídková, ne statistická. Přesto je jeden údaj přímo použitelný a nezávislý na všech ostatních zdrojích:

**Ceny základových desek pro typové dřevostavby: 4 000 – 6 000 Kč/m² zastavěné plochy** *(needs second source)*, v závislosti na skladbě podloží, svažitosti terénu, tvaru půdorysu, typu izolace a konstrukčním řešení.

Pro konkrétní dům stačí vynásobit zastavěnou plochou — dává kontrolní číslo pro etapu základů, spočitatelné nezávisle na procentech.

⚠️ Údaj je pro **dřevostavbu**. U zděného bungalovu bude deska nést těžší konstrukci, takže spíš horní hranice rozpětí nebo výše.

**Zdroj sám upozorňuje na jev přímo relevantní pro bungalov**: „V tomto parametru mají výhodu patrové domy, které oproti bungalovům mají menší zastavěnou plochu a tudíž levnější základovou desku." Bungalov má při dané užitné ploše zhruba dvojnásobnou zastavěnou plochu oproti patrovému domu — **základy i střecha jsou u něj systematicky dražší položkou**, než ukazují průměry počítané přes všechny typy RD. To je druhý nezávislý důvod (vedle střešního rozporu), proč etapová procenta z cizích zdrojů u bungalovu posouvat nahoru u základů a střechy.

Doplňkově, čistě pro řádovou kontrolu: metrová cena typových dřevostaveb vychází podle zdroje v průměru na **45 000 Kč/m²** bez základové desky a pozemku; typový bungalov 4+kk s užitnou plochou kolem 100 m² na klíč **za cca 5 mil. Kč včetně základové desky** *(needs second source)*. Jsou to nabídkové ceny jednoho výrobce dřevostaveb — nepoužívat jako benchmark pro zděnou stavbu.

## Souhrn: čtyři zdroje, čtyři definice

| Zdroj | Rok | „Hrubá stavba" | Základna | Střecha zvlášť? |
| --- | --- | --- | --- | --- |
| RTS 803 (seskupení této stránky) | 2026 | 39,1 % | ZRN | ano (2,7 %) |
| ESTAV / RONET | 2018 | 20,5 % (HSV 35,8 %) | ZRN | ano (12,2 %) |
| DŘEVO&stavby | 2022/2025 | ~20 % | cena na klíč | ano (krytina ~6 %) |
| RealFree | 2026 | 30–35 % | nejasná, spíš celkový rozpočet | **ne, je uvnitř** |

**Toto není rozptyl jednoho čísla — jsou to čtyři různé veličiny.** Kdokoli bude tato čísla používat, musí nejdřív říct, co do „hrubé stavby" počítá a z čeho procenta bere. Průměr přes tento sloupec by byl nesmysl.

## Použití

Pro rozpad ZRN na etapy: **ZRN × procento etapy**. ZRN vychází z obestavěného prostoru a sazby 10 475 Kč/m³ — viz [[RtsCenoveUkazatele2026]].

## Open questions

- Jaký je realistický podíl střechy u RD se sedlovou střechou? Potřebujeme nezávislý údaj.
- Jak moc snížit 767 Zámečnické a 726 Instalační prefabrikáty pro individuální RD?

## Related pages

- [[RtsCenoveUkazatele2026]]
- [[SvepomocKorekce]]
