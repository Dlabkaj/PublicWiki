# Klima / zateplení / vytápění mobilheimu (celoroční obyvatelnost v ČR)

**Summary**: Co musí splňovat mobilheim pro celoroční bydlení v ČR klimatu (léto až +40 °C, zima pod −10 °C). Klíč: skladba zateplení (podlaha + stěny + střecha + okna trojsklo + tepelné mosty), volba vytápění, technické minimální parametry (světlá výška, plocha místnosti, energetická náročnost). Rozdíl mezi **rekreačním** a **celoročním** mobilheimem je v konstrukčních detailech.

**Sources**:
- https://www.mobilni-domy-prodej.cz/blog/celorocni-mobilheimy-co-musi-splnovat-abyste-v-nich-mohli-zit-po-cely-rok (STERAUTO s.r.o., Olomouc, 7.10.2022) — vendor blog (mobilheim prodejce), pre-NSZ. První zdroj v této wiki pro klima. **Cross-source verification čeká na další iterace klimatického clusteru.**
- https://www.mobilni-domy-prodej.cz/zatepleni-mobilnich-domu (STERAUTO s.r.o., Olomouc, sales page bez data publikace) — **stejný vendor jako výše**, marketing pro retrofit zateplení. **Necountí jako nezávislý cross-source.** Doplňuje pouze konkrétní materiály a postup retrofit revitalizace.
- https://www.novymobilheim.cz/inpage/celorocni-zateplene-mobilni-domy-usporne-bydleni-bez-kompromisu/ (Novymobilheim / mobilnydom.eu, Brno, bez data publikace) — **nezávislý vendor** (jiný subjekt než STERAUTO), výrobce řady **Super Arktik®**. Konkrétní technické parametry (λ, R, tloušťky) pro model Super Arktik® FAMILY. **První nezávislý cross-source v klimatickém clusteru.**
- https://www.mobilheimcentrum.cz/blog/mobilni-domy-celorocni-zateplene (Mobilheimcentrum.cz, prodejce, bez data publikace) — **třetí nezávislý vendor** v klimatickém clusteru. Krátký blog, ale potvrzuje 3 atomy ze STERAUTO 2022 a doplňuje praktický bod o protizamrzání rozvodů.
- https://www.drevostavitel.cz/clanek/mobilni-domy-k-trvalemu-bydleni (Ing. Petr Novák, redaktor Drevostavitel.cz, 10.6.2015) — **nezávislý editorial zdroj** (ne vendor). ⚠️ **Pre-NSZ kontext** (odkazuje na starý SZ 183/2006 a novelu 350/2012); klimatická a typologická část (mobilheim vs. modulový dům) zůstává relevantní.

**Last updated**: 2026-06-08

---

## Klíčové technické parametry (pro povolení celoročního obyvatelného mobilheimu)

⚠️ **Single-sourced STERAUTO 2022** *(needs second source — verify ve vyhl. 146/2024 / 268/2009 znění)*:

| Parametr | Limit | Poznámka |
| -------- | ----- | -------- |
| **Světlá výška obytné místnosti** | **≥ 2 500 mm** | ✓ settled (STERAUTO × Píšová § 40 odst. 2 vyhl. 268/2009 × SÚ Orlová). **Kritická překážka pro většinu mobilheimů** (typicky 2,2–2,4 m). |
| **Šířka chodby** | **≥ 900 mm** | single-sourced STERAUTO 2022. *(needs second source — vyhl. 268/2009 § neověřeno; SÚ Orlová ani Píšová konkrétní šířku neuvádějí, jen § 10 odst. 6 hyg. požadavek na WC)* |
| **Energetická náročnost (PENB)** | **třída ne horší než C** | single-sourced STERAUTO 2022. Standardní požadavek na novostavby v ČR. *(needs second source pro mobilheim — Píšová pouze zmiňuje PENB nutný > 50 m², bez třídy)* |
| **Plocha obytné místnosti** | **≥ 8 m²** | single-sourced STERAUTO 2022. *(needs second source — vyhl. 268/2009 / 146/2024; SÚ Orlová zmiňuje "předepsané plochy obytných místností" bez čísla)* |
| **Pokud jen 1 místnost (studio)** | **plocha ≥ 16 m²** | single-sourced STERAUTO 2022. *(needs second source — vyhl. 268/2009 / 146/2024 neověřeno)* |
| Mechanická odolnost, požární bezpečnost, hygiena | dle obecných požadavků na výstavbu | ✓ settled (vyhl. 146/2024) |

**Cross-source potvrzení z legislativní wiki** ([[Legislativa]]):
- Světlá výška 2500 mm — Píšová cit. § 40 odst. 2 vyhl. 268/2009 / SÚ Orlová → ✓ **fully settled**.
- WC nesmí být přístupné přímo z obytné/pobytové místnosti, je-li jediné v bytě (§ 10 odst. 6 vyhl. 268/2009) — chodba **min. 90 cm** je proto pravděpodobně technicky nutná (Píšová single-sourced šířku, ale STERAUTO ji dává jako konkrétní 90 cm). ✓ konzistentní.

→ **Důsledek pro výměnek**: pokud mobilheim 3+kk 40 m² (typická velikost) — pravděpodobně splní 8 m² místnost. Problém spíše **světlá výška** (typický mobilheim 2,2–2,4 m, limit 2,5 m) a **PENB třída C** (slabě zateplená dovozová repas zařízení selže).

## Zateplení (kritické komponenty)

⚠️ Single-sourced STERAUTO 2022 *(needs second source — drevostavitel.cz, novymobilheim.cz, mobilheimcentrum.cz)*:

Celoroční mobilheim musí mít:

1. **Izolace podlahy** — ⚠️ *podceňovaný problém*. Nezateplená/špatně izolovaná podlaha:
   - chlad od nohou (komfort),
   - vyšší spotřeba energie,
   - **zvýšené riziko kondenzace vlhkosti** (= dlouhodobá degradace konstrukce — vazba na [[Zivotnost]]).
2. **Izolace stěn** — primární tepelná ochrana.
3. **Izolace střechy** — únik tepla horní polovinou.
4. **Okna s izolačními trojskly** — nikoli dvojskla (běžná u rekreačních modelů).
5. **Vyřešené tepelné mosty** — kritické pro PENB i kondenzaci. ⚠️ konstrukce mobilheimu (ocelový rám + dřevěný panel) má **inherentní tepelné mosty** v rámu — speciální detaily nutné.

> "Rozdíl mezi rekreačním a mobilním domem celoročním tak často spočívá právě v **konstrukčních detailech**, které na první pohled nemusí být patrné, ale v praxi hrají zásadní rozdíl." *(source: STERAUTO 2022)*

→ **Důsledek pro výměnek**: **nelze koupit rekreační mobilheim a "dozateplit ho"** plně do celoročního standardu — některé konstrukční detaily (tepelné mosty v rámu, podlahový sendvič) **vyžadují kompletně jinou konstrukci od výroby**. Pro celoroční bydlení od počátku **koupit celoroční celosezónní model** (drahší), ne rekreační. Cross-source potvrzeno [[PraktickeOtazky#Katalog skrytých vad (zejména repasované / dovozové)|Preuss]]: dovozové repas mobilheimy ze západu se projevují nedostatečnou izolací **po první zimě**.

### Materiály pro retrofit zateplení (revitalizace starého mobilheimu)

*(source: STERAUTO sales page — same-vendor supplement to STERAUTO 2022; needs independent cross-source — drevostavitel.cz, mobilheimcentrum.cz, novymobilheim.cz)*

STERAUTO uvádí jako **běžně používané materiály** pro retrofit revitalizaci celoroční obyvatelnosti:

| Materiál | Charakteristika | Pozn. |
| -------- | --------------- | ----- |
| **Minerální vata** | klasický stavební materiál | Standard, dobrá tepelná i akustická izolace, paropropustná. |
| **Polystyren (EPS)** | klasický stavební materiál | Levný, dostupný; nižší paropropustnost, **riziko kondenzace** pokud chybí parozábrana. |
| **PIR panely** | moderní izolační materiál | **Vyšší účinnost** při menší tloušťce — výhoda pro mobilheim, kde každý cm tloušťky stěny ubírá z interiéru. |
| **Fenolická pěna** | moderní izolační materiál | Velmi nízká tepelná vodivost, **požárně odolnější** než polystyren. |
| **Lupotherm folie** | speciální reflexní izolační folie | Marketing vendor; **single-sourced**, *(needs verification — funguje primárně proti radiačním ztrátám, ne kondukci; samostatně nestačí)*. |

**Komponenty pro retrofit**:
- **Stěny** (primární)
- **Podlaha** (kritická — viz výše)
- **Stropy / střecha** — STERAUTO uvádí "popř. konstrukce nové střechy" → naznačuje, že **při hluboké revitalizaci se někdy mění celá střešní konstrukce** (potvrzuje, že původní střecha rekreačního mobilheimu je často nedostatečná).
- **Výměna oken a dveří** — STERAUTO doporučuje paralelně s zateplením, "výměna jednoduchých oken" → tj. původní mobilheimy mají často **jednoduchá skla** (ne dvojskla, natož trojskla). Cross-confirms claim z předchozí sekce, že okna trojsklo jsou kritická pro celoroční standard.
- **Plastový venkovní obkladový systém** (imitace dřeva, fasáda, omítka) — kosmetické, ale součást revitalizace.

**Implicitní claim**: revitalizace "prodlouží životnost stavby" — viz [[Zivotnost]], single-sourced, *(needs verification — kvantifikovat o kolik let, jaký interval údržby)*.

> ⚠️ **Konflikt s předchozí sekcí**: STERAUTO sales page implikuje, že retrofit lze plně provést u jakéhokoli mobilheimu ("Mobilní dům lze přizpůsobit parametrům trvalého bydlení... i extrémním klimatickým podmínkám"). **Ale STERAUTO 2022 (stejný vendor, blog sekce)** explicitně varuje, že **konstrukční detaily nelze dozateplit** (tepelné mosty v rámu, sendvič podlahy). → **Resolution**: sales page je marketing (přeprodá službu), blog sekce je technicky přesnější. Retrofit lze udělat **částečně** — sníží spotřebu, zlepší komfort, ale **nedosáhne PENB třídy C u původně rekreačního modelu**. Pro doložení povolení jako RD (cesta C, viz [[Legislativa]]) je nutný **od výroby celoroční model**, ne retrofit rekreačního.
