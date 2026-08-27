# Postup propočtu ceny stavby podle cenových ukazatelů (JKSO)

Zdroj: Ing. Lukáš Janda, Ing. Tomáš Varmus (RTS, a.s.), Z+i ČKAIT 2025/01 (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/).

## Kroky propočtu

1. **Zatřídění objektu dle JKSO** — první trojčíslí = obor stavebnictví, čtvrtá pozice = skupina/charakter užívání.
2. **Výběr konstrukčně materiálové charakteristiky** — sloupec matice odpovídající převažující nosné konstrukci; obecný sloupec se používá v raných fázích, před studií/PD.
3. **Výpočet výměry účelové měrné jednotky** — u pozemního stavitelství m³ obestavěného prostoru, výpočet dle **ČSN 73 4055** — "Výpočet obestavěného prostoru pozemních stavebních objektů".
4. **Práce s cenou** — rozpad ceny do stavebních nebo funkčních dílů (funkční díly = dle stavebních konstrukcí, vhodnější pro práci s cenovým ukazatelem); umožňuje ověřit/upravit cenu podle nadstandardu konkrétního řešení.

Rozdíl mezi prvním cenovým odhadem (dle ukazatele) a výslednou cenou navrženého objektu může být podle zkušeností autorů vyšší než *25 %* (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/). Toto číslo se shoduje s horní hranicí odchylky uvedenou přímo na cenovasoustava.cz (viz [CenoveUkazatele.md](CenoveUkazatele.md)).

Cena ukazatele je bez DPH, neobsahuje vedlejší rozpočtové náklady (VRN) a vztahuje se pouze k oceňovanému objektu, ne k celé stavbě (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/).

## Rozpad ceny do funkčních dílů — příklad JKSO 803.5:1

Ukazatel "Domy bytové netypové, řadové bez občanského vybavení", zdivo z cihel/tvárnic/bloků (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/):

| Funkční díl | Podíl (%) | Kč/m³ |
|---|---|---|
| 01 Zemní práce | 1,7 | 151,90 |
| 02 Základové konstrukce | 8,3 | 741,61 |
| 03 Svislé konstrukce | 13,8 | 1 233,03 |
| 04 Vodorovné konstrukce | 9,0 | 804,15 |
| 05 Střešní konstrukce | 6,7 | 598,65 |
| 06 Povrchy vnitřních a vnějších konstrukcí | 12,5 | 1 116,88 |
| 07 Výplně otvorů | 10,5 | 938,18 |
| 08 Podlahové konstrukce | 7,7 | 688,00 |
| 09 Zařízení budov | 7,1 | 634,39 |
| 10 Ostatní | 5,1 | 455,69 | — jedná se o jeden konkrétní ukazatel, hodnoty se liší dle JKSO/konstrukce.

## Ilustrační příklad postupného zpřesňování ceny (RD, rok 2025)

Jednopodlažní RD 2+1, plochá střecha, zastavěná plocha 75 m², obestavěný prostor 273 m³, JKSO 803.6 sloupec 1 (zděná), venkovní komunikace JKSO 822.2 sloupec 3 (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/):

| Fáze | Postup | Výsledná cena |
|---|---|---|
| 1. Investiční záměr | 273 m³ × 9 775 Kč/m³ (dům) + 35 m² × 1 438 Kč/m² (komunikace) + 2 % VRN | *2 773 283 Kč* |
| 2. Studie | + nadstandard (vegetační střecha, venkovní schodiště, zábradlí) dopočtený z agregovaných položek RTS, + 2 % VRN | *3 006 255 Kč* |
| 3. Povolení stavby | agregované položky + technická zařízení dopočtená ukazatelem | *3 065 636 Kč* |
| 4. Realizace (položkový rozpočet) | prováděcí dokumentace, položky prací a materiálů | *3 225 119 Kč* |

Nárůst z fáze 1 (investiční záměr) do fáze 4 (realizace) u tohoto konkrétního příkladu: z 2 773 283 Kč na 3 225 119 Kč, tj. přibližně *+16 %* — v souladu s deklarovanou odchylkou propočtu podle ukazatelů (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/).

## Meziroční nárůst cen (kontext)

Cenové ukazatele pro 1. pololetí 2025 vzrostly nejčastěji o *14 %* oproti předchozímu období; v letech 2021–2022 (energie, covid, válka na Ukrajině) šlo o nárůst přes *30 %* za účelovou jednotku, v roce 2023 se nárůst ustálil (source: https://zpravy.ckait.cz/vydani/2025-01/jak-pracovat-s-cenovymi-ukazateli/, autor Ing. Tomáš Varmus, RTS). Novější zdroj téhož autora (Z+i ČKAIT 2026/01) potvrzuje, že jde o růst jiného období: nárůst pro rok 2025 (~14 %) byl výrazně vyšší než nárůst pro rok 2026 (u staveb pro bydlení *6,5 %*), tempo cenového růstu se tedy meziročně zpomaluje — soulad, ne rozpor, s meziročním nárůstem +6,5 % dopočteným z JKSO 803.6 (viz [CenoveUkazatele.md](CenoveUkazatele.md)) (source: https://zpravy.ckait.cz/vydani/2026-01/jake-ceny-budou-ve-stavebnictvi-v-roce-2026/).

## ČSN 73 4055 — identifikační údaje

Norma "Výpočet obestavěného prostoru pozemních stavebních objektů" byla schválena *30. 6. 1962* a nabyla účinnosti *1. 1. 1963*; rozsah *16 stran formátu A5* *(needs second source)* (source: https://shop.normy.biz/detail/5566 — katalog distributora norem; ČSN není právní předpis, kontrola „právní currency“ se na ni nevztahuje, platnost normy potvrzuje odkaz vyhlášky č. 359/2011 Sb., viz [ObestavenyProstor.md](ObestavenyProstor.md)). Norma platí pro výpočet obestavěného prostoru objektů, jejichž rozsah lze vyjádřit v m³, pro účely projektové přípravy a porovnání/hodnocení staveb; jde čistě o techniku výpočtu (obsahuje příkladové nákresy), bez cenových údajů (source: https://shop.normy.biz/detail/5566).

## Souhrnný výpočetní postup pro fázi B6 (jeden spočitatelný postup)

Sestaveno REVIEW 2026-08-20 z hodnot doložených na ostatních stránkách této složky; každý krok odkazuje na zdrojovou stránku, nová čísla se zde nezavádějí.

1. **OP** — spočítej obestavěný prostor podle ČSN 73 4055 (viz [ObestavenyProstor.md](ObestavenyProstor.md)); jednotka m³.
2. **Zatřídění JKSO + konstrukční charakteristika** — kroky 1–2 výše (RD jednobytový = 803.6, sloupec dle nosné konstrukce).
3. **ZRN = OP × cenový ukazatel** — ukazatele pro cenovou hladinu 2026/I viz [CenoveUkazatele.md](CenoveUkazatele.md) (803.6: zděná *10 410*, monolit *10 470*, montovaná *11 100*, dřevo *9 920*, průměr *10 475* Kč/m³ bez DPH).
4. **+ VRN** — ukazatel VRN neobsahuje. V ilustračním příkladu RTS se použily *2 %* ze ZRN (viz tabulka fází výše); rozpad RD dle ESTAV.cz uvádí VRN *3,1 %* (viz [StrukturaNakladu.md](StrukturaNakladu.md)).
5. **+ vedlejší objekty** — komunikace, zpevněné plochy, přípojky se oceňují vlastním ukazatelem (např. JKSO 822.2 *3 440* Kč/m², hladina 2026/I — [CenoveUkazatele.md](CenoveUkazatele.md)); ukazatel hlavního objektu je pouze k objektu, ne k celé stavbě.
6. **+ soft costs (hlava I)** — projektové, inženýrské a průzkumné práce; sazby a orientační ceny viz [StrukturaNakladu.md](StrukturaNakladu.md) (studie, povolení záměru, prováděcí dokumentace, kolaudace).
7. **+ rezerva investora** — u novostaveb *7–10 %* ze součtu stavební + technologické části (VP 800-0 ÚRS, viz [StrukturaNakladu.md](StrukturaNakladu.md)). Je to samostatná hlava rozpočtu, nepřekrývá se s VRN z kroku 4.
8. **+ DPH** — snížená sazba *12 %* pro stavbu pro sociální bydlení (RD do 350 m² podlahové plochy), jinak *21 %*; ověřeno proti § 47 a § 48a zákona č. 235/2004 Sb. (viz [StrukturaNakladu.md](StrukturaNakladu.md)). Ukazatele v kroku 3 jsou bez DPH.
9. **Pásmo nejistoty** — výsledek uváděj jako rozpětí: běžně *±15 %*, maximálně až *25 %* odchylky od skutečné ceny ([CenoveUkazatele.md](CenoveUkazatele.md)); ilustrační příklad výše skončil na *+16 %* mezi fází záměru a realizací.
10. **Svépomoc (volitelná korekce)** — pokud se počítá se svépomocnou výstavbou, uplatni srážku *10–20 %* (konzervativně) až *30 %* z ceny stavby a **přičti zpět** povinný stavební dozor a další skryté náklady; odvození a meze viz [Svepomoc.md](Svepomoc.md).

Pořadí je závazné: DPH (krok 8) se počítá až z částky včetně VRN, vedlejších objektů, soft costs a rezervy.

## Otevřené otázky

- Text jednotlivých pravidel výpočtu (co se do obestavěného prostoru počítá/nepočítá) nebyl v žádném dosud zpracovaném zdroji citován, pouze katalogové údaje o normě.
