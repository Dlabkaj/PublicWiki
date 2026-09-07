# Log rešerší — AIArchitect

Chronologicky, nejnovější nahoře.

## 2026-08-30 — sloučení `LLM_Wiki` do veřejné wiki

Složka `LLM_Wiki/` v repozitáři agenta byla samostatná wiki. Nahrazena klonem tohoto repozitáře (`PublicWiki`), obsah sloučen.

**Přeneseno beze změny obsahu**: `Legislativa/` (4 stránky, 12 zdrojů, ověřeno 2026-07-27) — nová složka v kořeni wiki. Upraveny jen odkazy na konvenci wiki (`[[Podtema]]` uvnitř složky, `[[../Tema/Podtema]]` mezi složkami) a odkaz do repozitáře agenta nahrazen textovou zmínkou, protože wiki je veřejná a klonuje se samostatně.

**Zahozeny 3 stub stránky** (`CenovaMetodika/Index.md`, `Nastroje/Index.md`, `ZivnostOdpovednost/Index.md`). Byly to rozcestníky ukazující na `MemoryVault/Wiki/Projects/AIArchitect/…` — cesta, která neexistuje. Skutečný obsah leží ve wiki jako [[../CenovaMetodikaStaveb/Index]], [[../ArchitekturaNastroje/Index]], [[../ZivnostOdpovednostCR/Index]]. Otevřené body z nich přesunuty do [[Index]].

**Ošetřen překryv**: § 11 vyhl. 146/2024 Sb. je popsán ve dvou stránkách — [[../Legislativa/PozadavkyNaVystavbu]] (znění vyhlášky včetně novely 97/2026) a [[../ArchitekturaRDObecnaPravidlaACasteChyby/UmisteniNaPozemku]] (praktický výklad, zná jen stav do novely). Obsah nesloučen; obě stránky mají navzájem odkaz s uvedením, která je pro citaci paragrafu autoritativní.

## 2026-08-20 — Cenová metodika, Nástroje, Živnost a odpovědnost — zpracováno

Tři rešeršní body ze `SKILL.md` zpracovány mimo tuto wiki a integrovány do tématických složek:

- **Cenová metodika** (28 zdrojů) → [[../CenovaMetodikaStaveb/Index]]. Výsledek: propočet podle cenových ukazatelů RTS v Kč/m³ obestavěného prostoru, výstup jako rozpětí. Otevřené body: rozpad HSV/PSV jen 1 zdroj (2018), čtvrtletní indexy ČSÚ ze sekundárního zdroje, podíl práce jen jako pásmo 35–60 %, neověřeno zapracování novely č. 523/2025 Sb.
- **Nástroje pro kreslení** (28 zdrojů) → [[../ArchitekturaNastroje/Index]]. Výsledek: IfcOpenShell-Python → IFC → výkresy z modelu → kontrola IfcTester/IDS; generátor obrázků jen na náladové vizualizace.
- **Živnost a odpovědnost** (24 zdrojů, převážně primární právní texty) → [[../ZivnostOdpovednostCR/Index]]. Výsledek: hotová doložka disclaimeru a licence včetně práva na úpravy. Otevřený bod (BLOCKED): zrušený § 159 odst. 3 SZ 183/2006 nemá výslovný protějšek v zák. 283/2021 Sb. — rozsah veřejnoprávní odpovědnosti projektanta chce právníka.

## 2026-07-27 — Legislativa — zpracováno (12 zdrojů)

Zpracován první bod z *Research needed* ve `SKILL.md`: aktuální legislativa ČR a normy.

**Nové stránky** — `Legislativa/` (4 soubory):
- `Index.md` — hierarchie předpisů, tři věci, které musí agent vědět nazpaměť, seznam nezpracovaných témat
- `PozadavkyNaVystavbu.md` — vyhl. č. 146/2024 Sb. účinná od 1. 7. 2024, novela č. 97/2026 Sb. účinná od 1. 7. 2026; § 11 odstupy, § 20 osvětlení/proslunění/stínění, § 38 světlé výšky, § 13 oplocení, § 18–19 větrání, § 61 dobíjecí body
- `NormyCSN.md` — § 4 odst. 1 zák. č. 22/1997 Sb. (ČSN nejsou závazné), tři typy odkazů dle výkladu MPO, § 94 vs. příloha č. 14 vyhl. 146/2024, ČSN 73 4301 nové vydání 6/2026
- `MestskePredpisy.md` — Praha 12/2024, Brno 14/2024, Ostrava od 1. 1. 2025; tabulka odchylek

**Tři zjištění, která mění dosavadní obsah `SKILL.md`:**
1. **Proslunění se u RD od 1. 7. 2024 nevyžaduje** (§ 20 vyhl. 146/2024). Prokazuje se denní osvětlení. Skill v B5 vyžadoval proslunění.
2. **Pravidlo „7 m mezi RD" zrušeno** spolu s vyhl. 501/2006 Sb. Zbyl jediný číselný odstup — 2 m od hranice pozemku (§ 11 odst. 2). Vzájemný odstup se řeší přes stínění, úhel 45°.
3. **ČSN 73 4301 má nové vydání účinné od 1. 7. 2026**, nahrazuje 22 let staré vydání 2004. Obsah nezískán (placená norma) — do té doby se z ní **nesmí citovat žádná hodnota**.

**Nevyřešeno**: doslovný text § 11 odst. 3–7 a přílohy č. 4 po novele (primární zdroj `zakonyprolidi.cz` vrací HTTP 403); paragrafy minimálních ploch místností; rozsah povinnosti dobíjecího bodu u RD; obsah přílohy č. 14; obsah nové ČSN 73 4301; požární bezpečnost RD vůbec nezpracována.

**Vyřazeno ze zadání wiki**: bod *Detailní podčeklisty jednotlivých fází* — není to rešerše externích fakt, ale autorská práce nad skillem. Patří vedle `SKILL.md`, ne do wiki.
