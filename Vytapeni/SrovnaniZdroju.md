# Srovnání zdrojů tepla — provozní náklady

**Summary**: Technické srovnání provozních nákladů biomasy (pelety, kusové dřevo) vs. tepelné čerpadlo vzduch/voda pro rodinné domy, včetně SCOP faktorů a spotřeby na GJ.

**Sources**:
- https://vytapeni.tzb-info.cz/vymeny-kotlu/24178-biomasa-vs-tepelne-cerpadlo-srovnani-mernych-provoznich-nakladu (TZB-info, Ing. Zdeněk Lyčka APTT, 2022-08-09)
- https://www.viessmann.cz/cs/rady-a-tipy/technologie/vytapeni-elektrikou/porovnani-nakladu-na-vytapeni.html (Viessmann CZ, komerční — data z tzb-info kalkulačky)
- https://schlieger.cz/blog/srovnani-nakladu-na-vytapeni/ (Schlieger, komerční instalatér TČ/FVE, 2026)

**Last updated**: 2026-06-28

> ⚠️ **Pozor**: Ceny energonosičů v tabulkách jsou z **2022**. Používat jako metodický rámec, ne jako aktuální čísla. Aktuální ceny ověřit u jiných zdrojů.

---

## Uvažované zdroje tepla (TZB-info model)

| Označení | Popis | SCOP |
|----------|-------|------|
| TČpod | TČ vzduch/voda, nízkoteplotní soustava, podlahové topení, min. bivalent | **4,5** |
| TČ3,3 | TČ vzduch/voda, kvalitní soustava, průměrný dům | **3,3** |
| TČrad | TČ vzduch/voda, starší radiátory, teplota vody >55°C + 20% el. bivalent | **3,5 eff.** |
| Kotel pelety | Kotel na dřevní pelety | — |
| Kotel dřevo | Kotel na kusové dřevo | — |

*(zdroj: TZB-info Lyčka 2022, recenzovaný odborný článek)*

---

## Spotřeba na výrobu 1 GJ energie dodané do otopné soustavy

| Energonosič | Měrná jednotka | Spotřeba [mj/GJ] |
|-------------|----------------|------------------|
| Pelety | kg | **66,8** |
| Kusové dřevo | prmr (prostorový metr rovnaný) | **0,217** |
| Elektřina — TČpod (SCOP 4,5) | kWh | **61,6** |
| Elektřina — TČ3,3 (SCOP 3,3) | kWh | **84** |
| Elektřina — TČrad (SCOP 3,5 eff.) | kWh | **123** |

*(zdroj: kalkulátor TZB-info, citováno v Lyčka 2022)*

---

## Srovnávací hranice výhodnosti (ceny energonosičů)

Tabulka ukazuje, za jakou cenu elektřiny/paliva jsou náklady **srovnatelné** s danou cenou pelet:

| Cena pelet (Kč/kg) | Hranice el. TČpod | Hranice el. TČ3,3 | Hranice el. TČrad | Hranice dřevo (Kč/prmr) |
|--------------------|--------------------|--------------------|--------------------|--------------------------|
| 10 | 10,80 | 8,00 | 5,40 | 3 083 |
| 11 | 11,90 | 8,70 | 6,00 | 3 382 |
| 12 | 13,00 | 9,50 | 6,50 | 3 696 |
| 13 | 14,00 | 10,30 | 7,10 | 4 000 |
| 14 | 15,20 | 11,10 | 7,60 | 4 308 |
| 15 | 16,30 | 11,90 | 8,10 | 4 617 |

*(zdroj: TZB-info Lyčka 2022 — data z 2022, peletová cena jako referenční osa)*

**Jak číst**: Pokud cena elektřiny pro TČpod je NIŽŠÍ než hranice ve sloupci → TČpod je výhodnější než pelety. Pokud VYŠŠÍ → pelety jsou výhodnější.

---

## Modelový případ (RD, roční potřeba tepla 80 GJ, ceny 7/2022)

Při ceně pelet 12 Kč/kg a elektřiny cca 8,50 Kč/kWh (tarif D56d):

| Zdroj | Efektivní cena el. vč. jistič | Vs. referenční hranice | Výsledek |
|-------|-------------------------------|------------------------|----------|
| TČpod | 9,35 Kč/kWh | < 13,00 | ✅ TČ výhodnější než pelety |
| TČ3,3 | 9,10 Kč/kWh | < 9,50 | ✅ mírně výhodné (blízko parity) |
| TČrad | 8,90 Kč/kWh | > 6,50 | ❌ pelety levnější |

*(zdroj: TZB-info Lyčka 2022 — ceny 2022, dnes jinak)*

**Dřevo**: Ceny kusového dřeva v 7/2022 pod 2000 Kč/prmr → dřevo jednoznačně nejlevnější. *(zdroj: TZB-info Lyčka 2022)*

---

## Závěry autora (Ing. Lyčka, 2022)

1. **Nejlevnější zdroj**: kotel na kusové dřevo (pokud dostupné za cenu <3000 Kč/prmr)
2. **Nízkoenergetický dům + podlahové topení**: TČ s SCOP 4,5+ jasně výhodné
3. **Starý dům + staré radiátory** (výměna plynového kotle bez rekonstrukce soustavy): pelety lepší než TČ
4. **Nová otopná soustava + výkonné TČ**: náklady TČ a pelety srovnatelné
5. **Ideální kombinace**: mít k dispozici TČ + spalovací zdroj na biomasu, kombinovat dle aktuální ekonomické výhodnosti

*(přímé závěry z TZB-info Lyčka 2022)*

---

## Aplikace na nízkoenergetický slaměný dům

Slaměný novostavba patří do kategorie **nízkoenergetický dům s podlahovým topením** → profil TČpod:

- SCOP 4,5 (nebo vyšší u nových TČ)
- Podlahové vytápění jako primární systém
- Minimální potřeba bivalentního elektrického zdroje díky nízké tepelné ztrátě domu
- Malý výkon potřebného TČ (~3–5 kW) → riziko taktování → nutná akumulační nádoba

→ **Závěr pro slaměný dům**: TČ vzduch/voda s podlahovým topením je provozně nejekonomičtější varianta, pokud cena elektřiny nepřesáhne ~13–14 Kč/kWh při ceně pelet 12–13 Kč/kg.

---

## Orientační provozní náklady 2026 (Schlieger, komerční instalatér)

Orientační roční náklady na vytápění pro běžný RD (~140–160 m²):

| Zdroj tepla | Roční náklady vytápění | Poznámka |
|-------------|------------------------|----------|
| TČ vzduch/voda + nízkoteplotní soustava | **20–35 tis. Kč** | Při správném návrhu |
| Tuhá paliva — kusové dřevo | **20–35 tis. Kč** | Závisí na ceně a množství |
| Tuhá paliva — pelety | **35–45 tis. Kč** | Závisí na kvalitě paliva a účinnosti kotle |
| Plynový kondenzační kotel | **35–55 tis. Kč** | Závisí na regionu a distribučních poplatcích |
| Elektrický kotel (přímotopy) | **110–150 tis. Kč** | Při spotřebě ~18 MWh/rok |

*(needs second source — Schlieger.cz, komerční instalatér TČ a FVE, 2026)*

> ⚠️ Data z komerčního zdroje prodávajícího TČ — TČ varianty mohou být optimisticky hodnoceny.

### Investiční náklady TČ vzduch/voda (Schlieger, 2026)

- Hrubá investice: **250–350 tis. Kč** *(needs second source — Schlieger komerční)*
- Cena po dotaci (Schlieger interní nabídka): **od 117 tis. Kč** *(needs second source — komerční, závisí na konkrétní dotaci)*

### Scénáře "před a po" přechodu na TČ (Schlieger, orientační, 2026)

| Scénář | Výchozí stav | Nové řešení | Náklady před | Náklady po | Dostupná dotace |
|--------|--------------|-------------|--------------|------------|-----------------|
| 1 | Elektrokotel, RD ~150 m² | TČ 9 kW + FVE 7,2 kWp + solár TUV | 120–150 tis./rok | 28–35 tis./rok | 230–300 tis. Kč |
| 2 | Plynový kondenzační, RD ~140 m² | TČ 8 kW + FVE 6 kWp | 40–50 tis./rok | 20–28 tis./rok | 200–260 tis. Kč |
| 3 | Smíšený provoz, RD ~160 m² | TČ 10 kW nízkoteplotní + solár TUV | 55–65 tis./rok | 30–38 tis./rok | 150–190 tis. Kč |

*(needs second source — Schlieger komerční, 2026, "orientační")*

> ⚠️ Dotace uváděné Schliegerem (150–300k) zahrnují kombinaci programů (NZÚ + kotlíkové dotace + FVE) — ne jen TČ.

---

## Roční náklady celkem — modelový dům (Viessmann, tzb-info kalkulačka)

**Model**: dům 150 m², potřeba tepla 7 kW, 4-členná rodina, ceny 2022.
**Složky**: vytápění + TUV + amortizace investice (reinvestiční fond).

| Zdroj tepla | Vytápění Kč/rok | TUV Kč/rok | Investice Kč/rok | **Celkem Kč/rok** |
|-------------|-----------------|------------|------------------|-------------------|
| Zplyňovací kotel dřevo | 9 882 | 2 668 | 14 393 | **~54 000–64 000** ✅ Nejlevnější |
| TČ vzduch/voda | 20 032 | 5 408 | 22 433 | **~72 000–83 000** |
| Kotel na brikety | 30 656 | 8 277 | 13 773 | **~80 000–88 000** |
| Plynový kondenzační | 31 596 | 8 531 | 12 143 | **~84 000–93 000** |
| El. podlahové topení | 56 757 | 18 028 | 3 600 | **~102 000–104 000** |
| El. kotel s akumulací | 68 388 | 18 464 | 11 990 | **~125 000–130 000** ❌ Nejdražší |

*(needs second source — Viessmann CZ, komerční, data z tzb-info kalkulačky, ceny 2022)*

> ⚠️ Ceny 2022, dnes elektřina/plyn/dřevo jinak. Použít jako porovnávací rámec.

### Investiční náklady na realizaci (orientační, 2022)

| Zdroj tepla | Investiční náklady |
|-------------|-------------------|
| El. podlahové topení | od 90 000 Kč |
| El. kotel | od 180 000 Kč |
| Plynový kondenzační kotel | od 255 000 Kč |
| Štěpkový kotel | od 310 000 Kč |
| Peletový kotel | od 320 000 Kč |
| **TČ vzduch/voda** | **od 300 000 Kč** |

*(needs second source — Viessmann CZ, 2022)*

> **Poznámka Viessmann**: "Vytápění elektřinou má místo v pasivních nebo nízkoenergetických domech, kde by byla návratnost investice do TČ nebo drahého kotle na biomasu příliš dlouhá." *(needs second source — komerční tvrzení)*

---

## Doplňkové faktory úspory (Schlieger, 2026)

### Zateplení jako první páka úspory

Zateplení fasády a střechy, utěsnění oken a hydraulické vyvážení otopné soustavy přinese orientačně **až −40 % energie na vytápění** bez ohledu na typ zdroje tepla. *(needs second source — Schlieger.cz, komerční, 2026)*

> Platí univerzálně pro všechny zdroje: menší tepelné ztráty domu = menší potřebný výkon TČ/kotle → nižší investice i provoz. Pro slaměný novostavbu (nízkoenergetický standard) to znamená výchozí výhodu oproti starším domům.

### Solární termický ohřev vody

Správně navržený termický solární systém (vakuové kolektory) pokryje **50–70 % roční energie na TUV** ze slunce. V létě zvládá TUV prakticky samostatně, v přechodných měsících snižuje zátěž hlavního zdroje. *(needs second source — Schlieger.cz, komerční, 2026)*

> Schlieger uvádí, že vakuové kolektory s technologií heat-pipe fungují i při −20 °C a nižším slunečním osvitu díky uzavřenému okruhu se solární kapalinou. *(needs second source — komerční tvrzení)*

### Komfort obsluhy — srovnání zdrojů

| Zdroj tepla | Obsluha | Komfort |
|-------------|---------|---------|
| Dřevo / pelety | Manuální plnění, sklad, pravidelná obsluha | Nízký |
| Plyn | Plně automatický, nutný komín + servis | Vysoký |
| TČ vzduch/voda | Plně automatický, dálkové ovládání | Velmi vysoký |
| TČ + FVE + chytré řízení | Automatická optimalizace (priorita vlastní výroby) | Nejvyšší |

*(needs second source — Schlieger.cz, komerční, 2026)*

### Technické specifikace TČ vzduch/voda (Schlieger Premium Pro, 2026)

- Funkční až do **−25 °C** venkovní teploty *(potvrzeno SmartSolarEnergy 2026, komerční — typické pro top-tier modely)*
- Výstupní teplota vody až **75 °C** → vhodné i pro starší domy s radiátory *(potvrzeno SmartSolarEnergy 2026, komerční)*
- Tichý provoz pod **35 dB** *(needs second source — Schlieger Premium Pro komerční; SmartSolarEnergy uvádí "pod 50 dB" obecně)*
- Funkce Multizone: dva nezávislé okruhy (podlahové topení + radiátory) *(needs second source — Schlieger Premium Pro komerční)*

> ⚠️ Specifikace Schlieger Premium Pro jsou z komerčního marketingu — ověřit technický list konkrétního modelu.

---

## Související stránky

- [[Dotace]] — NZÚ 2026 dotace a bezúročné úvěry
- [[TeplotniCerpadlo]] — TČ pro slaměný dům
- [[Biomasa]] — kotle na biomasu
- [[Index]] — přehled témat vytápění
