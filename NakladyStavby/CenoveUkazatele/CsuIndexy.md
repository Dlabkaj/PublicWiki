# ČSÚ indexy cen stavebních prací a děl

**Summary**: Čtvrtletní indexová řada ČSÚ pro ceny stavebních prací, stavebních děl a náklady stavební výroby — nástroj pro eskalaci a pro ověření *pohybu* cen, nikoli pro ověření *úrovně* sazby Kč/m³.

**Sources**: [ČSÚ — Indexy cen stavebních prací, indexy cen stavebních děl a indexy nákladů stavební výroby, čtvrtletní časové řady, 1. čtvrtletí 2026](https://csu.gov.cz/produkty/indexy-cen-stavebnich-praci-indexy-cen-stavebnich-del-a-indexy-nakladu-stavebni-vyroby-ctvrtletni-casove-rady-1-ctvrtleti-2026)

**Last updated**: 2026-08-13

---

## ⚠️ K čemu indexy jsou a k čemu nejsou

ČSÚ indexy **potvrzují pohyb cen v čase, nikoli úroveň sazby RTS Kč/m³**. Tuhle hranici je nutné držet ostrou:

- ✅ Použitelné: převod sazby z jedné cenové úrovně do jiné (eskalace), ověření, zda meziroční nárůst deklarovaný RTS odpovídá nezávisle měřenému vývoji trhu.
- ❌ Nepoužitelné: jako důkaz, že 10 475 Kč/m³ je správné číslo. Index je bezrozměrný poměr; nezná absolutní Kč/m³ obestavěného prostoru.

Nezávislé potvrzení *výše* sazby RTS z veřejných zdrojů nemáme — viz [[RtsCenoveUkazatele2026]].

## Metadata publikace

- **Vydavatel**: Český statistický úřad — nezávislý na RTS i ÚRS.
- **Kód produktu**: 011041-26
- **Datum vydání**: 20. 5. 2026 (edice za 1. čtvrtletí 2026)
- **Kadence**: čtvrtletní, souvislá archivní řada minimálně od 1. čtvrtletí 2010; starší ročníky vycházely pod kódem 700144 (do 2013) a w-7001 (do 2010).
- Publikace je volně ke stažení včetně datové přílohy a metodických vysvětlivek.

Čtvrtletní kadence je pro nás výhodná: sazba RTS je roční (2026/I), ČSÚ dovoluje dopočítat posun uvnitř roku.

## Struktura tabulek

Publikace obsahuje tyto tabulky — užitečné vědět, kde co hledat:

| Tab. | Obsah |
| --- | --- |
| 1 | Indexy cen stavebních konstrukcí a prací podle **TSKPstat** |
| 2 | Indexy cen **stavebních děl** podle klasifikace **CZ-CC** |
| 3 | Indexy cen stavebních děl podle číselníku druhů staveb |
| 4 | Indexy nákladů stavební výroby podle číselníku druhů staveb |
| 5 | Indexy cen **materiálových vstupů** stavební výroby |
| 6 | **Průměrné ceny vybraných stavebních prací** |
| 7–10 | Tytéž řady za rok 2025 |

Pro propočet ceny RD jsou nejzajímavější:

- **Tab. 2 (CZ-CC)** — obsahuje třídu budov jednobytových, tedy přímý protějšek JKSO 803.6.
- **Tab. 1 (TSKPstat)** — členění podle stavebních konstrukcí a prací je stejná logika jako díly v RTS tabulce; umožňuje eskalovat jednotlivé etapy různým tempem, ne celý rozpočet plošně.
- **Tab. 5** — odděluje materiálové vstupy od celkové ceny práce. To je přímo relevantní pro korekci na svépomoc, kde jde právě o poměr materiál/práce (viz [[SvepomocKorekce]]).

## Hodnoty — 1. čtvrtletí 2026 (Tab. 2, CZ-CC)

Báze: **průměr roku 2015 = 100**.

| CZ-CC | Název | Stálá váha | 2015 = 100 | Předchozí obd. = 100 | Stejné obd. min. roku = 100 |
| --- | --- | --- | --- | --- | --- |
| — | Stavební díla celkem | 10000 | 154,5 | 101,2 | 103,1 |
| 1 | Budovy | 5180 | 155,1 | 101,4 | 103,1 |
| 11 | Budovy bytové | 1581 | 154,8 | 101,4 | 103,2 |
| **111 / 1110** | **Budovy jednobytové** | **296** | **156,4** | **101,5** | **103,4** |
| 1121 | Budovy dvoubytové | 45 | 156,5 | 101,6 | 103,4 |
| 1122 | Budovy tří a vícebytové | 1048 | 154,6 | 101,4 | 103,2 |

**Budovy jednobytové (CZ-CC 1110) jsou přímý protějšek JKSO 803.6** — to je hledaný řádek.

Čtení hodnot pro budovy jednobytové v 1Q 2026:

- **156,4** — ceny jsou o 56,4 % výše než průměr roku 2015.
- **101,5** — mezičtvrtletně +1,5 %.
- **103,4** — meziročně +3,4 %.

Poznámka ČSÚ pod tabulkou: index „Stavební díla" je **obsahově totožný s indexem cen stavebních prací**.

Doplňkově Tab. 3 (podle číselníku druhů staveb) uvádí pro **Budovy bytové (kód 010)** shodně 154,8 / 101,4 / 103,2 a pro opravy a údržbu celkem 156,6 / 101,5 / 103,6.

## Dvě různá měřítka: ČSÚ +3,4 % vs. RTS +6,5 % meziročně

> **Adjudikováno v REVIEW (2026-08-13): NEJDE o rozpor mezi zdroji — měří se dvě různé veličiny.** Původně zde stál `⚠️ CONFLICT`; snížen na metodický rozdíl, protože pro rozpor by obě čísla musela být pokusem změřit totéž.
>
> Rozhodující je sloupec **„Stálá váha"** přímo v tabulce ČSÚ. Index cen stavebních děl je **index s pevnými vahami** (báze průměr roku 2015 = 100): drží skladbu díla konstantní a měří **čistý cenový pohyb** reprezentativních položek zjišťovaný u dodavatelů. Naproti tomu meziroční změna cenového ukazatele RTS je **rozdíl dvou ročníků průměrné jednotkové ceny přepočteného modelového objektu** — nese v sobě jak cenový pohyb, tak jakoukoli změnu skladby a standardu modelu a změnu vlastní datové základny RTS. RTS své číslo nikde neoznačuje za cenový index.
>
> Index s pevnými vahami a meziroční posun znovu odvozeného modelového průměru se **rozcházet mají**; shoda by byla shodou okolností. Časová okna se navíc nekryjí (RTS „cenová úroveň 2026/I" zveřejněná koncem ledna 2026 vs. ČSÚ 1. čtvrtletí 2026).
>
> Zůstává v platnosti pravidlo z úvodu stránky: **ČSÚ potvrzuje pohyb cen, nikoli úroveň sazby RTS.** A zůstává i praktický dopad níže — pro eskalaci se dvě různé řady nemají míchat na dlouhý horizont.

Obě čísla se týkají téhož typu stavby a zhruba téhož období, ale **nejsou touž veličinou**:

| Zdroj | Veličina | Meziroční růst |
| --- | --- | --- |
| ČSÚ, CZ-CC 1110 Budovy jednobytové, 1Q 2026 | index cen stavebních děl, **pevné váhy**, 2015 = 100 | **+3,4 %** |
| RTS, JKSO 803.6 Domky rodinné jednobytové, 2025/I→2026/I | meziroční posun **průměrné jednotkové ceny modelového objektu** Kč/m³ | **+6,5 %** |

Rozdíl je téměř dvojnásobný, ale je to rozdíl konstrukce ukazatele, ne neshoda o faktu. Co k němu přispívá:

- ČSÚ drží skladbu díla konstantní a měří ceny reprezentativních položek zjišťované u dodavatelů; RTS znovu přepočítává **modelový rozpočet** z vlastní datové základny, takže do jeho meziročního rozdílu vstupuje i změna skladby a standardu modelu.
- RTS mohl v ročníku 2026 změnit skladbu modelového objektu, ne jen ceny — to by se v indexu s pevnými vahami z definice neprojevilo.
- Časová okna se nekryjí — „cenová úroveň 2026/I" u RTS a „1. čtvrtletí 2026" u ČSÚ nejsou totožné okno.

**Praktický dopad (platí i po adjudikaci)**: pokud budeme sazbu RTS eskalovat do budoucna pomocí ČSÚ indexů, míchají se dvě různě konstruované řady. Pro krátké posuny (jedno dvě čtvrtletí) to je přijatelné, pro delší období vzniká systematická chyba — a ta roste tím rychleji, čím víc RTS mění skladbu modelu. Do doby, než RTS metodiku svého meziročního přepočtu zveřejní, je namístě eskalaci na horizontu delším než rok považovat za orientační a raději sáhnout po novém ročníku ukazatelů než po indexovaném starém.

## Použití pro eskalaci

Sazba RTS má vždy uvedený rok cenové úrovně (aktuálně 2026/I). Pro převod do jiného období:

```
sazba(cílové období) = sazba(2026/I) × index(cílové období) / index(1Q 2026)
```

kde index(1Q 2026) = **156,4** pro budovy jednobytové. Až ČSÚ vydá další čtvrtletí, stačí dosadit novou hodnotu z Tab. 2, řádek CZ-CC 1110.

⚠️ Vzorec platí jen díky tomu, že báze obou hodnot je stejná (2015 = 100). **Nemíchat s hodnotami z jiné báze.**

## Open questions

- Konkrétní hodnoty z Tab. 1 (TSKPstat, po dílech) a Tab. 5 (materiálové vstupy) zatím nemáme — byly by potřeba pro eskalaci jednotlivých etap různým tempem a pro poměr materiál/práce.
- Jakou váhu má v meziročním posunu ukazatele RTS (+6,5 %) změna skladby modelového objektu oproti čistému cenovému pohybu? RTS metodiku přepočtu nezveřejňuje; bez toho nelze říct, o kolik přesně se obě řady na delším horizontu rozejdou.

## Related pages

- [[RtsCenoveUkazatele2026]]
- [[EtapoveRozdeleni]]
- [[SvepomocKorekce]]
