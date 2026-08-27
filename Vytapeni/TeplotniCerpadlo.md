# Tepelné čerpadlo vzduch/voda pro slaměný dům

**Summary**: Technické detaily tepelných čerpadel vzduch/voda — typy (fixspeed vs. invertor), taktování, akumulace, dimenzování, SCOP. Primárně z pohledu nízkoenergetického domu s malou tepelnou ztrátou.

**Sources**:
- https://vytapeni.tzb-info.cz/tepelna-cerpadla/8980-tepelna-cerpadla-vzduch-voda-a-akumulacni-nadoby (TZB-info, Ing. Jiří Honzík, AC Heating, 2012-08-28)
- https://vytapeni.tzb-info.cz/kotle-kamna-krby/9635-optimalni-volba-zdroje-pro-nizkoenergeticke-domy (TZB-info, Ing. Václav Helebrant, 2013)
- https://smartsolarenergy.cz/tepelne-cerpadlo/tepelne-cerpadlo-vzduch-voda/ (SmartSolarEnergy.cz, komerční instalatér, 2026)
- https://schlieger.cz/blog/srovnani-nakladu-na-vytapeni/ (Schlieger, komerční instalatér TČ/FVE, 2026) — sekundární potvrzení specifikací −25 °C / 75 °C
- https://www.obnovitelne.cz/clanek/4260/jak-zvolit-spravne-vytapeni-kdy-se-vyplati-cerpadlo-biomasa-hybrid-nebo-propan (Obnovitelně.cz, redakce + PR, 2025-11-12)

**Last updated**: 2026-06-25

---

## Dva typy TČ: fixspeed vs. invertor (klíčová volba)

| Vlastnost | Fixspeed (scroll) | Invertorové (modulace) |
|-----------|-------------------|------------------------|
| Regulace výkonu | Žádná (zap/vyp) | Plynulá (0–100%) |
| Taktovací nádoba | **Nutná** | Nepotřebná |
| Ekvitermní regulace | Volitelná | Zpravidla součást |
| Max. startů/h (scroll) | **6** | — |
| Vhodnost pro nizkoenergetický dům | Problematická | **Optimální** |
| Provozní náklady | Vyšší (topí na 55°C) | Nižší (topí na min. potřebnou teplotu) |

*(needs second source — pouze TZB-info Honzík/AC Heating 2012, výrobce má zájem na propagaci své modulace)*

---

## Proč invertorové TČ pro slaměný dům

Slaměný dům má tepelnou ztrátu ~1–3 kW. Fixspeedové TČ s minimálním výkonem 3–5 kW by taktovalo většinu topné sezóny → cyklování, zkrácená životnost kompresoru.

**Invertorové TČ** moduluje výkon podle aktuální potřeby → bez taktování i při malé ztrátě. *(needs second source — TZB-info Honzík 2012)*

---

## Taktovací nádoba u fixspeedového TČ — realita

Důležitý poznatek: akumulační nádoba u TČ **neslouží jako skutečná energetická akumulace**, ale jako **taktovací** (ochrana kompresoru). *(needs second source — TZB-info Honzík 2012)*

**Proč**: TČ max. výstupní teplota 55°C → malý ΔT → malá akumulovaná energie.

**Výpočet** (příklad — dům 10 kW tepelná ztráta, 500 l nádoba, ohřev na 55°C):

| Teplota výstupu topení | Energie v nádobě | Doba autonomie |
|------------------------|-----------------|----------------|
| 35°C (podlahové) | 11,7 kW | 70 min |
| 40°C (podlahové) | 8,7 kW | 52 min |
| 50°C (radiátory) | 2,9 kW | 17 min |
| 55°C (radiátory) | 0 kW | 0 min |

*(needs second source — Ing. Honzík AC Heating 2012, výpočet modelového případu)*

→ Pro nízkoteplotní soustavu (podlahové topení, výstup 35°C): 500 l nádoba dá ~70 min provoz bez TČ.
→ Pro radiátory (výstup 50°C): jen 17 min — taktovací nádoba prakticky nic neakumuluje.

---

## Dimenzování fixspeedového TČ

- **NEDIMENZOVAT na plnou tepelnou ztrátu** — jinak cyklování při nižší tepelné ztrátě (= většina topné sezóny) *(needs second source — TZB-info Honzík 2012)*
- Správné dimenzování: **75–85 % tepelné ztráty** *(needs second source — TZB-info Honzík 2012)*
- Zbytek krytý bivalentním zdrojem (elektrický přímotop)
- Bivalentní bod: typicky 0 °C až -5 °C (pod tuto teplotu se zapíná bivalent)

**Nevhodné dimenzování** → bivalentní zdroj se spíná již při 0°C → vysoké provozní náklady. *(needs second source — TZB-info Honzík 2012)*

---

## Akumulační zásobník vs. taktovací nádoba

| Typ nádoby | Funkce | Vhodné pro |
|------------|--------|------------|
| Akumulační nádoba (kotel na tuhá paliva) | Skutečná akumulace energie, ohřev na 90°C | Kotle na dřevo/pelety |
| Taktovací nádoba (TČ fixspeed) | Ochrana kompresoru, zajistit min. dobu běhu | Fixspeedové TČ |
| Bez nádoby | — | Invertorové TČ |

*(zdroj: TZB-info Honzík 2012; doplněno Biom.cz 2010 pro kotle na tuhá paliva)*

---

## Ekvitermní regulace

TČ s ekvitermní regulací ohřívá vodu na nejnižší možnou teplotu k pokrytí aktuální tepelné ztráty. *(needs second source — TZB-info Honzík 2012)*

- Výsledek: minimalizace provozních nákladů, vyšší SCOP v přechodném období
- Fixspeed bez ekvitermní: vždy ohřev na 55°C → zbytečně vyšší náklady
- Invertorové s ekvitermní: optimální provoz, nízká teplota vody = vyšší COP

---

## Aplikace na slaměný dům

### Tepelná ztráta
Slaměný dům 140–160 m², ~15 kWh/m²/rok → tepelná ztráta při -12°C: **~1–2 kW**.

### Doporučení
1. **Invertorové TČ vzduch/voda** — bez taktovací nádoby, moduluje na malou ztrátu
2. **Podlahové topení** — nízká teplota výstupní vody (35°C) → vysoký SCOP (4–5+) *(zdroj: TZB-info Lyčka 2022 — SCOP 4,5 pro TČpod)*
3. **Ekvitermní regulace** — povinnost pro maximální efektivitu
4. Pokud fixspeed: taktovací nádoba ~200–300 l (200 l zásobník TUV kombinovaný)
5. **Velká akumulační nádoba NENÍ potřeba** pro invertorové TČ v tomto domě

### Výkon TČ pro slaměný dům
- Tepelná ztráta ~1,5 kW při -12°C → TČ s min. výkonem 1,5–3 kW
- Invertorové TČ mohou modulovat dolů na <1 kW → vhodné
- Typický nejmenší vzduch/voda model: 3–5 kW jmenovitý výkon → pro slaměný dům na horní hranici dimenzování

> ⚠️ Riziko: dostupné TČ na trhu mají minimální výkon >1 kW, ale tepelná ztráta slaměného domu může být pod 1 kW při mírném počasí. **Invertorové TČ s modulací je nezbytné**, jinak by TČ taktovalo i přes taktovací nádobu.

---

## Provozní parametry (moderní TČ vzduch/voda)

- Min. teplota provozu: **-25°C** (kompresor bez elektrického dotopování) *(potvrzeno SmartSolarEnergy + Schlieger 2026, komerční — typické pro top-tier modely)*
- Max. výstupní teplota: **75°C** → použitelné i se starými radiátory *(potvrzeno SmartSolarEnergy + Schlieger 2026, komerční)*
- Hlučnost doporučená: akustický výkon **pod 50 dB** (zastavěné oblasti) *(needs second source — SmartSolarEnergy komerční)*
- Instalace: **2–3 pracovní dny** *(needs second source — SmartSolarEnergy komerční)*
- Monoblock vs. split: monoblock = revize doporučené; split = revize povinné **1× ročně** *(needs second source — SmartSolarEnergy komerční; ověřit u ČHMÚ / SZÚ regulace F-plyny)*
- Venkovní jednotka: min. **2 m** volného prostoru před čelní stranou *(needs second source — SmartSolarEnergy komerční)*

### Distribuční tarif pro TČ

TČ umožňuje využívat tarif **D57d** — dvoutarifní sazba s levnějším nízkým tarifem po dobu **20 hodin denně**. Levnou elektřinu lze využít i pro další spotřebiče v domácnosti. *(needs second source — citace M. Müller, Acond, přes Obnovitelně.cz 2025; doporučeno ověřit u distributora)*

> Poznámka: TZB-info 2022 modelový případ pracoval s tarifem D56d (8,50 Kč/kWh). D57d může mít jiné podmínky — ověřit aktuální ceník distributora.

### FV + TČ synergie
- Přebytky z FV → ohřev zásobníku TUV (alternativa k bateriím, bez ztráty efektivity) *(needs second source — SmartSolarEnergy komerční)*
- Inteligentní řízení: spínání TČ při nadbytku FV výroby *(needs second source — SmartSolarEnergy komerční)*

### Úspory oproti elektrickému vytápění
- Komerční tvrzení: **až 75%** úspora nákladů vs. přímotopné elektrické vytápění *(needs second source — SmartSolarEnergy komerční; Schlieger uvádí 70%)*

### Dotace — vyjasnění

Komerční instalátoři uvádějí různé částky podle programu/produktu:
- **NZÚ Light 2026 — výměna zdroje tepla / OZE: až 150 000 Kč** (pro nízkopříjmové domácnosti) — primární zdroj: portál NZÚ + ČSOB; potvrdil i Schlieger pro TČ vzduch/voda.
- SmartSolarEnergy uvádí "až 90 000 Kč" na TČ vzduch/voda *(needs second source — pravděpodobně reziduum staršího sazebníku NZÚ; nesouhlasí s aktuální NZÚ Light max 150k)*
- Schlieger uvádí na NZÚ Light pro solární ohřev vody **90 000 Kč** — různá kategorie OZE, ne TČ. *(needs second source — Schlieger komerční)*

⚠️ **CONFLICT — kotlíkové dotace na TČ**: SmartSolarEnergy uvádí **až 130 000 Kč**, Schlieger uvádí **až 180 000 Kč (až 95 % výdajů)**. Oba komerční. Ověřit u SFŽP / krajské výzvy podle aktuálního ročníku programu.

## Hybridní systém TČ + plynový kotel

Hybridní systém kombinuje TČ jako hlavní zdroj s plynovým kondenzačním kotlem jako zálohou při extrémně nízkých teplotách. *(needs second source — Thermona/Řezanina přes Obnovitelně.cz 2025)*

- TČ je primární zdroj, plynový kotel se zapíná automaticky jen při výkonu nedostatečném pro TČ
- Výhoda: plynový kotel má až 3× nižší náklady na energii než elektrický dotopový kotel ve vnitřní jednotce
- Dotace na TČ složku hybridního systému lze čerpat i při zachování plynového kotle *(needs second source — Obnovitelně.cz 2025)*
- **Pro slaměný dům**: hybridní systém není relevantní (neplánovaná plynová přípojka); případná záloha = krbová kamna na biomasu

## Ceny a investice (orientační)

*(viz [[SrovnaniZdroju]] — Viessmann data: TČ vzduch/voda od 300 000 Kč investiční náklady)*

---

## Výhody TČ vzduch/voda pro slaměný dům

| Pro | Proti |
|-----|-------|
| ✅ Vysoký SCOP (4–5+) při nízkoteplotní soustavě | ❌ Vyšší investice vs. biomasa |
| ✅ Automatický provoz — žádná obsluha | ❌ Závislost na elektřině |
| ✅ Dotace NZÚ (výměna zdroje tepla 150k Kč Light / bezúročný úvěr) | ❌ Výkon při -15°C klesá |
| ✅ Reverzní chod = chlazení v létě | ❌ Hluk venkovní jednotky |
| ✅ Ohřev TUV integrovaný | ❌ Nutná ekvitermní regulace + správná instalace |
| ✅ Kombinovatelné s FV | |

---

## SCOP hodnoty pro orientaci

*(z TZB-info srovnávacího článku — 2022)*

| Soustava | SCOP | Podmínka |
|----------|------|----------|
| TČ vzduch/voda + podlahové topení | **4,5** | Nízkoteplotní soustava, min. bivalent |
| TČ vzduch/voda + kvalitní soustava | **3,3** | Průměrný dům |
| TČ vzduch/voda + staré radiátory | **3,5 eff.** | Radiátory + 20% el. bivalent |

*(zdroj: TZB-info Lyčka 2022 — orientační, ověřit u konkrétního výrobce; oprava pass 2: raw + [[SrovnaniZdroju]] uvádějí 3,5, ne 2,8)*

---

## Související stránky

- [[NizkoenSpecifika]] — specifika nízkoenergetického domu (tepelné ztráty, hydraulika)
- [[SrovnaniZdroju]] — srovnání provozních nákladů TČ vs. biomasa
- [[Biomasa]] — alternativa k TČ pro slaměný dům
- [[Dotace]] — NZÚ 2026 dotace na TČ
- [[Index]] — přehled témat vytápění
