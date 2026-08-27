# Specifika vytápění nízkoenergetického domu

**Summary**: Klíčové technické specifiky pro volbu a návrh otopné soustavy v nízkoenergetickém domě — zejména malá tepelná ztráta, nutnost akumulace, rekuperace, hydraulické poměry. Přímo aplikovatelné na slaměný dům.

**Sources**:
- https://vytapeni.tzb-info.cz/kotle-kamna-krby/9635-optimalni-volba-zdroje-pro-nizkoenergeticke-domy (TZB-info, Ing. Václav Helebrant STIEBEL ELTRON, recenzovaný, 2013-03-11, recenzent prof. Ing. Jiří Bašta Ph.D.)
- https://www.nazeleno.cz/jak-vybrat-vytapeni-do-nizkoenergetickeho-domu/ (Nazeleno.cz, Ing. Jiří Čech AB Atelier + Ing. Karel Srdečný EkoWATT, 2011-12-20)

**Last updated**: 2026-06-25

> ⚠️ Článek z 2013 — principy platí, konkrétní výkonové limity zařízení ověřit u aktuálních výrobců.

---

## Normy a definice

| Kategorie | Spotřeba tepla |
|-----------|----------------|
| Pasivní dům | do **15 kWh/m²/rok** *(zdroj: Nazeleno 2011 / ČSN 73 0540)* |
| Nízkoenergetický dům (ČSN 73 0540) | **15–50 kWh/m²/rok** *(zdroj: Nazeleno 2011 / ČSN 73 0540)* |
| Klasická novostavba | 80–140 kWh/m²/rok *(zdroj: Nazeleno 2011)* |

> Slaměný dům ~50 cm stěna → U ~ 0,1 W/m²K → pasivní standard (~10–15 kWh/m²/rok).

**Max. výkon zdroje tepla pro nízkoenergetický dům: do 10 kW** (výkonnější zdroj by přehřívával). *(needs second source — Nazeleno 2011)*

**Roční náklady na vytápění** (orientační):
- Pasivní dům: ~5 000 Kč/rok *(needs second source — Nazeleno 2011, staré ceny)*
- Nízkoenergetický dům: ~15 000–30 000 Kč/rok *(needs second source — Nazeleno 2011, staré ceny)*

---

## Větrání a rekuperace — de facto nutnost

Pro nízkoenergetické a pasivní domy platí: **bez řízeného větrání s rekuperací ztrácí dům smysl** — potřeba tepla na výměnu vzduchu může být více než **50 % roční tepelné bilance**.

- Větrání okny degraduje nízkou spotřebu energie
- Pro tepelné ztráty **do cca 3 kW** → vhodné teplovzdušné vytápění (vzduch pro přenos tepla relativně malý, větrací funkce převládá)
- Nevýhoda teplovzdušného: zdroj tepla nejčastěji elektřina (jiné zdroje nevhodné pro takto malé odběry)

---

## Tepelná ztráta slaměného domu — řádové hodnoty

**Tab. 1 — Tepelná ztráta [kW] při venkovní teplotě -12°C** *(zdroj: TZB-info Helebrant 2013, Tab. 1)*

| Plocha [m²] | 15 kWh/m²/rok | 20 kWh/m²/rok | 30 kWh/m²/rok | 40 kWh/m²/rok |
|-------------|----------------|----------------|----------------|----------------|
| 100 | 0,7 kW | 0,9 kW | 1,4 kW | 1,9 kW |
| 120 | 0,8 kW | 1,1 kW | 1,7 kW | 2,2 kW |
| 140 | 1,0 kW | 1,3 kW | 2,0 kW | 2,6 kW |
| 160 | 1,1 kW | 1,5 kW | 2,2 kW | 3,0 kW |
| 180 | 1,3 kW | 1,7 kW | 2,5 kW | 3,3 kW |

**Tab. 2 — Tepelná ztráta [kW] při +2°C** *(zdroj: TZB-info Helebrant 2013, Tab. 2)*

| Plocha [m²] | 15 kWh/m²/rok | 20 kWh/m²/rok | 30 kWh/m²/rok |
|-------------|----------------|----------------|----------------|
| 140 | 0,5 kW | 0,7 kW | 1,1 kW |
| 160 | 0,6 kW | 0,8 kW | 1,3 kW |

> **Aplikace na slaměný dům**: Slaměná stěna ≈ 50 cm tloušťky → U ~ 0,1–0,15 W/m²K → pasivní/nízkoenergetický standard 10–20 kWh/m²/rok. Pro dům 140 m² → tepelná ztráta při -12°C: **~1,0–1,3 kW**, při +2°C: **~0,5–0,7 kW**. Extrémně malé hodnoty!

---

## Klíčový problém: technologické minimum zdrojů tepla

**Průtok otopné soustavou** u nízkoenergetického domu je VÝRAZNĚ MENŠÍ než technologické minimum prakticky jakéhokoli tepelného zdroje.

Příklad: Dům 3 kW tepelné ztráty při -12°C → při +2°C ztráta 1,7 kW → průtok 300–400 l/h. *(zdroj: TZB-info Helebrant 2013, sekce E)*

**Následky**:
- Zdroj tepla pracuje pod svým minimálním výkonem → taktuje (start-stop cykly)
- Taktování = snižování účinnosti, zkracování životnosti
- **Řešení: akumulační zásobník** — hydraulické oddělení, eliminace taktování

---

## Hodnocení zdrojů tepla pro nízkoenergetický dům

### ✅ Tepelné čerpadlo (vzduch/voda nebo země/voda)
- Vhodné — přináší výraznou úsporu provozních nákladů
- **PODMÍNKA: akumulační zásobník** — povinný z hlediska:
  - Topného faktoru (SCOP) — zlepšení efektivity
  - Životnosti kompresoru — omezení počtu startů
- Vzduch/voda s reverzní funkcí → aktivní chlazení v létě (prací kompresoru)
- Země/voda → **pasivní chlazení** z vrtů (bez kompresoru) + přenos energie z chlazení do TUV

### ⚠️ Kotel na biomasu — PROBLEMATICKÝ pro nízkoenergetický dům
> **"Kotel na biomasu je pro tyto tepelné ztráty a obvyklou velikost domu nepřiměřeně velký a složitý z hlediska instalace."** *(zdroj: TZB-info Helebrant 2013, sekce C)*

Minimální výkon kotle na biomasu typicky 5–10 kW; tepelná ztráta slaměného domu 1–3 kW → kotel by pracoval v 10–30% výkonu → intenzivní taktování.
**Řešení pokud biomasa: velká akumulační nádoba** (~500–1000 l) eliminující taktování.

### ❌ Plynový kotel — problematický
- Minimální výkon kvalitního regulovaného kotle > tepelná ztráta → taktuje
- Provozní účinnost se snižuje (velká část provozu = starty, ne ustálený stav)
- Akumulační zásobník nutný, ale komplikuje soustavu

### ❌ Přímotopné konvektory
- Nejlevnější investice (~30 000 Kč pro ztrátu 3 kW), nejméně perspektivní
- "Přepalování vzduchu" u topných těles v režimu červeného žáru
- Uzavírá možnost změny zdroje tepla v budoucnu

### ✅ Solární systém + elektrický dotop
- Optimální kombinace pro nízkoenergetický dům
- 5 m² kolektorů pokryje při ztrátě 3 kW nejméně 25 % roční tepelné bilance *(zdroj: TZB-info Helebrant 2013, sekce D)*
- Zásobník solárního systému slouží zároveň jako akumulace pro otopnou soustavu

---

## Akumulační zásobník — klíčový prvek

**Pro nízkoenergetický dům je akumulační zásobník prakticky nutností** bez ohledu na zdroj tepla. *(zdroj: TZB-info Helebrant 2013, sekce E a H)*

Funkce:
- Hydraulické oddělení topných okruhů s malým průtokem
- Umožnění delší doby provozu zdroje v ustáleném stavu (vyšší účinnost)
- Pro TČ: omezení startů → delší životnost kompresoru
- Regulační armatury na topných okruzích fungují správně pouze se zásobníkem

> Regulační armatury na topných okruzích fungují POUZE pokud je v soustavě akumulační zásobník, jinak musí být plnoprůtočné (a nefungují). *(zdroj: TZB-info Helebrant 2013, sekce H)*

---

## Příprava TUV

- Je na stavebně-tepelných vlastnostech domu nezávislá → dimenzovat separátně
- **Pokud TČ: musí připravovat i TUV** *(zdroj: TZB-info Helebrant 2013, sekce G)*
- Pokud země/voda: v létě přenos energie z chlazení (vrtů) do TUV — synergie *(zdroj: TZB-info Helebrant 2013, sekce G)*
- Solár: 5 m² kolektorů pro TUV jako základ *(zdroj: TZB-info Helebrant 2013, sekce G)*

---

## Chlazení v létě

- U nízkoenergetického domu může přicházet do popředí paradoxně kvůli nízkému prosklení osluněných částí
- 2,5 kW chladu → cca 55–65 m zemního vrtu *(zdroj: TZB-info Helebrant 2013, sekce F)*
- TČ vzduch/voda s reverzní funkcí: aktivní chlazení (prací kompresoru)
- TČ země/voda: pasivní chlazení bez kompresoru — výhodnější, ale vyšší investice *(zdroj: TZB-info Helebrant 2013, sekce F)*

---

## Regulace a zónování

- Dům rozdělit na zóny podle oslunění (osluněná strana vs. severní místnosti)
- Bez zónování: jižní strana může způsobit vypnutí otopné soustavy při nadhřátí, severní místnosti pak chlad
- Na zpracování MaR by se měl podílet odborník s projektem *(zdroj: TZB-info Helebrant 2013, sekce H)*

---

## Závěr pro slaměný dům (aplikace)

| Zdroj | Vhodnost | Podmínka |
|-------|----------|----------|
| TČ vzduch/voda | ✅ Optimální | Akumulační zásobník + podlahové topení |
| TČ země/voda | ✅ Výborné (pasivní chlazení) | Vyšší investice (vrty) |
| Biomasa (kotel) | ⚠️ Možné s rezervacemi | Velká akumulace 500+ l; komfort–, obsluha+ |
| Solár + el. dotop | ✅ Dobrá kombinace | Zásobník, solár jako základ |
| Plynový kotel | ❌ Nevhodné | + není v scope (no gas) |
| Přímotop | ❌ Nevhodné | Nejméně perspektivní |

> **Klíčový poznatek**: Pro slaměný dům se tepelnou ztrátou ~1–2 kW platí, že kotel na biomasu je výkonově předimenzovaný a TČ je přirozenou volbou — ale i TČ potřebuje akumulační zásobník kvůli minimálnímu výkonu kompresoru.

---

## Související stránky

- [[SrovnaniZdroju]] — srovnání provozních nákladů biomasa vs. TČ
- [[Dotace]] — NZÚ 2026 dotace a bezúročné úvěry
- [[TeplotniCerpadlo]] — TČ pro slaměný dům (detaily)
- [[Biomasa]] — biomasa kotle a krbová kamna
- [[Index]] — přehled témat vytápění
