# AIArchitect — agent pro architektonickou studii RD

Rozcestník pro agenta, který zpracovává architektonickou studii rodinného domu v ČR ([repozitář `AIArchitect`](https://github.com/Dlabkaj/AIArchitect)). Tato složka drží **jen věci specifické pro agenta** — konvence psaní, log rešerší a mapu, která stránka wiki odpovídá na kterou fázi skillu. Samotná fakta leží v tématických složkách wiki, protože platí i mimo tohoto agenta.

Ověřeno: 2026-09-17

Konvence psaní: [[Conventions]] · Historie rešerší: [[Log]]

---

## Co agent čte a kdy

| Téma | Wiki složka | Fáze skillu |
|---|---|---|
| Legislativa a normy ČR | [[../Legislativa/Index]] | A2 (sběr regulace), B3 (osazení), B5 (kontrola) |
| Obecná pravidla a časté chyby RD | [[../ArchitekturaRDObecnaPravidlaACasteChyby/Index]] | B4 (dispozice), B5 |
| Metodika odhadu ceny | [[../CenovaMetodikaStaveb/Index]] | B6 (odhad ceny), B7 (konfrontace s rozpočtem), A3 |
| Podkladová čísla nákladů | [[../NakladyStavby/Index]] | B6, B7 |
| Nástroje pro kreslení a vizualizaci | [[../ArchitekturaNastroje/Index]] | B1–B4, B10, C (výkresová část) |
| Živnost, odpovědnost, licence, GDPR | [[../ZivnostOdpovednostCR/Index]] | D (licence pro projektanta), právní doložky |
| Sjezd a příjezdová cesta | [[../SjezdPrijezdovaCesta/Index]] | A2, B3 |
| Zasíťování pozemku | [[../ZasitovaniPozemku/Index]] | A2, B3 |
| Podklady k pozemku a postupy řízení | [[../ZasitovaniPozemku/PodkladyPozemku/Index]] | A2, B1 |
| Limity obálky mimo vyhl. 146/2024 (ochranná pásma, ZPF) | [[../Legislativa/StavebniObalka/Index]] | A2, B1, B3 |
| Požárně nebezpečný prostor a požární odstupy RD | [[../Legislativa/PozarniBezpecnostRD/Index]] | B1, B3, B5 |

## Stav rešerší

| Téma | Stav | Zdrojů |
|---|---|---|
| Legislativa a normy | zpracováno, s otevřenými body | 12 |
| Cenová metodika | zpracováno a zrevidováno | 28 |
| Nástroje pro kreslení | zpracováno a zrevidováno | 28 |
| Živnost a odpovědnost | zpracováno, 2 body blokované na právníka | 24 |
| Limity obálky mimo vyhl. 146/2024 | zpracováno 2026-09-17, 3 nedoložené údaje v OchranaZPF | 15 |
| Ochranná pásma sektorových zákonů | ověřeno 2026-09-17 přímo z e-Sbírky (dráhy, elektřina, teplo, vodovody, ZCHÚ, léčivé zdroje, pohřebnictví, rozhled) | 7 |
| Požárně nebezpečný prostor RD | zpracováno 2026-09-17, 2 rozpory otevřené | 20 |
| Podklady k pozemku a postupy řízení | zpracováno a zrevidováno 2026-09-17 | 16 |

## Rozhodnutí, která z rešerší vzešla

- **Kreslení** (revize 2026-09-18): jeden JSON model, N rendererů. Rychlé 2D schéma, Sweet Home 3D (generovaný `.sh3d`) a Blender/Cycles vizualizace se všechny odvozují z JSON. IFC je odvozený výstup pro předání a kontrolu IfcTester/IDS. Generátor obrázků (ControlNet) jen na náladu, nikdy jako výkres. Rozhodnutí: AIArchitect `docs/decisions/0001-one-model-n-renderers.md`. Odůvodnění: [[../ArchitekturaNastroje/Index]], strop kvality LLM: [[../ArchitekturaNastroje/StropKvalityLLM]].
- **Cena**: propočet podle cenových ukazatelů RTS (Kč/m³ obestavěného prostoru dle ČSN 73 4055), výstup jako rozpětí. Postup: [[../CenovaMetodikaStaveb/PostupOdhadu]].
- **Právo**: hotová doložka disclaimeru a licence včetně práva na úpravy je v [[../ZivnostOdpovednostCR/Index]]. **Není to právní stanovisko** — před komerčním provozem konzultovat s advokátem.

## Otevřené body napříč tématy

- Doslovný text § 11 odst. 3–7, § 20 a přílohy č. 4 vyhl. 146/2024 Sb. po novele 97/2026 — dosud jen z parafrází ([[../Legislativa/PozadavkyNaVystavbu]]).
- Obsah nového vydání ČSN 73 4301 (6/2026) — placená norma, nezískána. Do té doby se z ní nesmí citovat žádná hodnota ([[../Legislativa/NormyCSN]]).
- **Požární bezpečnost RD** — zpracováno ([[../Legislativa/PozarniBezpecnostRD/Index]]). Otevřené zbývají dva body: zda po rekodifikaci stále platí hranice 200 m² zastavěné plochy RD pro státní požární dozor (opora byla v zrušeném § 104 odst. 1 písm. a) zák. č. 183/2006 Sb.) a rozpor 650 m² (TP 1.7 ČKAIT) vs. 600 m² (§ 15 odst. 2 vyhl. č. 23/2008 Sb.) u přístřešků. Do rozhodnutí platí nižší, vyhláškou daná hodnota.
- Kterou novelou a k jakému datu bylo zrušeno ochranné pásmo veřejného pohřebiště (dříve 100 m) a jaký je režim pásem zřízených před zrušením — platné znění zák. č. 256/2001 Sb. institut nezná, přechodná ustanovení nebyla zpracována ([[../Legislativa/StavebniObalka/OchrannaPasma]]).
- Rozsah veřejnoprávní odpovědnosti projektanta po zrušení § 159 odst. 3 SZ 183/2006 — **BLOCKED**, chce právníka ([[../ZivnostOdpovednostCR/OdpovednostZaSkodu]]).
- Rozpad HSV/PSV stojí na jediném zdroji z r. 2018; podíl práce jen jako pásmo 35–60 % ([[../CenovaMetodikaStaveb/Index]]).
