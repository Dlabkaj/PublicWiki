# AIArchitect — agent pro architektonickou studii RD

Rozcestník pro agenta, který zpracovává architektonickou studii rodinného domu v ČR ([repozitář `AIArchitect`](https://github.com/Dlabkaj/AIArchitect)). Tato složka drží **jen věci specifické pro agenta** — konvence psaní, log rešerší a mapu, která stránka wiki odpovídá na kterou fázi skillu. Samotná fakta leží v tématických složkách wiki, protože platí i mimo tohoto agenta.

Ověřeno: 2026-09-21

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
| **Osazení domu na pozemku** | [[../OsazeniNaPozemku/Index]] | **B3** |
| **Dispoziční varianty** | [[../DispozicniVarianty/Index]] | **B4** |
| **Kontrola varianty** | [[../KontrolaVarianty/Index]] | **B5** |
| **Cenová metodika a náklady** | [[../CenovaMetodikaStaveb/Index]] | **B6–B7** |
| Sjezd a příjezdová cesta | [[../SjezdPrijezdovaCesta/Index]] | A2, B3 |
| Zasíťování pozemku | [[../ZasitovaniPozemku/Index]] | A2, B3 |
| Podklady k pozemku a postupy řízení | [[../ZasitovaniPozemku/PodkladyPozemku/Index]] | A2, B1 |
| Limity obálky mimo vyhl. 146/2024 (ochranná pásma, ZPF) | [[../Legislativa/StavebniObalka/Index]] | A2, B1, B3 |
| Požárně nebezpečný prostor a požární odstupy RD | [[../Legislativa/PozarniBezpecnostRD/Index]] | B1, B3, B5 |
| Hmotové řešení RD — podlažnost, tvar hmoty | [[../HmotoveReseniRD/Index]] | B2 |
| Příklady dobrého návrhu RD (oceněné domy, kritéria hmota/dispozice/světlo/materiál, anti-vzory) | [[../DobryNavrhRD/Index]] | B2, B4, B10 |
| Poměr A/V, obestavěný prostor, porovnání variant | [[../HmotoveReseniRD/PomerAV/Index]] | B2, B6 |
| Tvar a sklon střechy, osazení k terénu | [[../HmotoveReseniRD/StrechaATeren/Index]] | B2, B3 |

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
| Hmotové řešení RD — podlažnost a tvar hmoty | zpracováno 2026-09-21 | 11 |
| Tvar a sklon střechy, osazení k terénu | zpracováno a zrevidováno 2026-09-21 | 12 |
| Poměr A/V a porovnání variant | zpracováno a zrevidováno 2026-09-21, 1 blokující rozpor | 7 |
| Osazení na pozemku — doprava, přípojky a vsak, poloha a proslunění | zpracováno a zrevidováno 2026-09-22, 0 nedoložených údajů | 24 |
| Dispozice — plochy, zónování, komunikace a schodiště, jádra a okna | zpracováno a zrevidováno 2026-09-23, 12 otevřených údajů s tagem | 29 |
| DPH u stavby pro bydlení a podíl práce | zpracováno 2026-09-23; DPH z primárního textu, podíl práce zůstává na jediném zdroji | 2 |
| Kontrola varianty — požární bezpečnost, konstrukce, přístupnost a výjimky | zpracováno 2026-09-23; požární úloha zůstává STOP_NEEDS_WORK, protože zbylé tagy uzavřou jen placené normy | 11 |

## Rozhodnutí, která z rešerší vzešla

- **Kreslení** (revize 2026-09-18): jeden JSON model, N rendererů. Rychlé 2D schéma, Sweet Home 3D (generovaný `.sh3d`) a Blender/Cycles vizualizace se všechny odvozují z JSON. IFC je odvozený výstup pro předání a kontrolu IfcTester/IDS. Generátor obrázků (ControlNet) jen na náladu, nikdy jako výkres. Rozhodnutí: AIArchitect `docs/decisions/0001-one-model-n-renderers.md`. Odůvodnění: [[../ArchitekturaNastroje/Index]], strop kvality LLM: [[../ArchitekturaNastroje/StropKvalityLLM]].
- **Cena**: propočet podle cenových ukazatelů RTS (Kč/m³ obestavěného prostoru dle ČSN 73 4055), výstup jako rozpětí. Postup: [[../CenovaMetodikaStaveb/PostupOdhadu]].
- **Poměr A/V** (2026-09-21): A/V se ve studii uvádí jako **srovnání hmotových variant**, ne jako průkaz energetické náročnosti — ČSN 73 0540-2 (8/2025) požadavek na Uem zrušila a vyhl. č. 264/2020 Sb. žádnou mez A/V nestanoví. Pásma A/V pro RD existují ve dvou nezávislých výukových pramenech, ale vzájemně si odporují a e-genius měří `V` jako obestavěný prostor — slouží proto jen jako kontrola řádu, ne jako hodnocení ([[../HmotoveReseniRD/PomerAV/TypickaPasmaAV]]). Vedle A/V se počítá RC (vůči krychli stejného objemu), protože A/V klesá i jen s velikostí domu. Ve vyhl. č. 264/2020 Sb. A/V nevystupuje vůbec. Nástroj: AIArchitect `tools/av/av.py`. Podklad: [[../HmotoveReseniRD/PomerAV/Index]].
- **Odhad ceny** (2026-09-23): o **sazbě DPH rozhoduje dispozice**. RD s podlahovou plochou do
  **350 m²** je stavba pro sociální bydlení (§ 48a odst. 1 písm. b) zák. č. 235/2004 Sb.), takže na
  stavební práce jde **12 % místo 21 %** (§ 49 odst. 1); plocha se počítá podle
  **vyhl. č. 163/2025 Sb.**, která nezapočítává schodiště, lodžii ani půdu, u šikmin měří v 1,2 m
  nad podlahou, ale garáž uvnitř domu započítává. Hranice 120 m² z téhož paragrafu se týká obytného
  prostoru, ne RD. Cenový ukazatel je **ZRN** (bez VRN, rezervy, soft costs a DPH) s odchylkou běžně
  ±15 %, takže výstup B6 je **rozpětí**. Nástroj: AIArchitect `tools/cena/cena.py` s cenovými
  ukazateli v `tools/cena/ukazatele.json` (hladina 2026/I, hlásí zastarání).
  Podklad: [[../CenovaMetodikaStaveb/DphUStavbyProBydleni]].
- **Kontrola varianty** (2026-09-23): tři pravidla, která mění dosavadní postup fáze B5.
  (1) **Seznam prominutelných požadavků je uzavřený.** § 95 vyhlášky jmenuje mj. počet stání
  (§ 7 odst. 1 a 3), **odstup 2 m a stavební čáru** (§ 11 odst. 1, 2 a 4) a podjezdnou výšku garáže
  (§ 38 odst. 3). **Světlou výšku 2,5 m (§ 38 odst. 1), denní osvětlení a zastínění (§ 20), šířky
  (§ 39), schodiště (§ 31) ani „1 záchod a 1 koupelna" prominout nelze** — a výjimku povoluje
  stavební úřad za podmínek § 138 odst. 1 SZ, ne projektant. (2) **Vyhláška č. 23/2008 Sb. platí
  i po novém stavebním zákoně** (znění od 1. 1. 2025) a pro RD odkazuje na ČSN 73 0833 jako na
  určenou normu: běžný RD je **jeden požární úsek včetně garáže** (plocha úseku do 600 m²), musí
  mít **autonomní detekci a signalizaci**, a **dřevostavba je jiný režim** (§ 15 odst. 4).
  (3) **Od 1. 1. 2026 nesmí PBŘ u staveb kategorie I a II zpracovat projektant pozemních staveb** —
  musí to být autorizovaná osoba pro PBS. Navíc: **běžný RD nemusí splnit požadavky na přístupnost**
  (§ 29 odst. 1 a 3). Nástroj: AIArchitect `tools/verdikt/verdikt.py`.
  Podklad: [[../KontrolaVarianty/Index]].
- **Dispoziční varianty** (2026-09-23): čtyři pravidla, která mění dosavadní postup fáze B4.
  (1) **Nejmenší plochy místností od 1. 7. 2026 nestanoví nic** — vyhláška je nikdy neměla a revize
  **ČSN 73 4301** (červen 2026) je zrušila včetně 12 m² na dvoulůžkovou ložnici; 8 m² je *definice*
  obytného prostoru (§ 2 písm. b), ne požadavek. Velikost se prokazuje **zaříditelností** podle
  ČSN 73 4305, jinak programem klienta. Hodnota 16 m² je rodinný standard nové ČSN, ne předpis.
  (2) **Pro RD nepředepisuje vyhláška žádný rozměr schodiště ani šířku chodby** — § 31 žádá jedno
  hlavní schodiště na podlaží a stejné stupně v rameni, § 39 odst. 3 dává 1,2 m chodbě *bytového*
  domu a odst. 2 rodinné domy z přepravy předmětů výslovně vyjímá. Číslo 900 mm je z vyhl.
  268/2009 Sb. Geometrie je z ČSN 73 4130, jejíž splnění je podle § 94 presumpce souladu.
  (3) **Poměr okna 1 : 10 není průkaz denního osvětlení** — požadavek je v § 13 písm. l) zák. č.
  283/2021 Sb. a měří se činitelem denní osvětlenosti (ČSN 73 0580-2: ≥ 0,7 % ve dvou bodech
  v polovině hloubky, nejdále 3 m od okna). Při stejné ploše okna rozhoduje jeho **šířka**.
  (4) **Hygienický požadavek na byt je jedna věta** — příloha č. 3 bod 1: 1 záchodová mísa
  a 1 koupelna. Nástroj: AIArchitect `tools/dispozice/dispozice.py`.
  Podklad: [[../DispozicniVarianty/Index]].
- **Osazení na pozemku** (2026-09-22): pět pravidel, která mění dosavadní postup fáze B3.
  (1) Dvoumetrový odstup **neplatí k hranici veřejného prostranství** (§ 11 odst. 2 in fine) —
  směrem do ulice rozhoduje **stavební čára** podle § 11 odst. 1, a ta platí i bez územního plánu.
  (2) **Proslunění obytných místností není požadavek**; zbylo denní osvětlení jako poměr 1 : 10
  (§ 20 odst. 1), a ve stavební proluce se místo úhlu 45° porovnává s hypotetickou souvislou
  zástavbou (§ 20 odst. 5). (3) **Počet parkovacích stání** se nepočítá podle ČSN 73 6110, ale
  podle přílohy č. 1 vyhlášky — 1 stání na 120 m² podlahové plochy, u typického RD tedy jedno;
  rozměry stání dál platí podle ČSN 73 6056. (4) Povinnost k srážkové vodě je v **§ 5 odst. 3
  zák. č. 254/2001 Sb.** a má pořadí akumulace → vsak → výpar → řízené odvádění. (5) Pravidlo
  „50 % pozemku schopno vsakovat" je podmínka **drobné stavby** podle přílohy č. 1 SZ, ne limit
  zastavěnosti; **garáž drobnou stavbou není nikdy**. Nástroj: AIArchitect
  `tools/pozemek/pozemek.py`. Podklad: [[../OsazeniNaPozemku/Index]].
- **Právo**: hotová doložka disclaimeru a licence včetně práva na úpravy je v [[../ZivnostOdpovednostCR/Index]]. **Není to právní stanovisko** — před komerčním provozem konzultovat s advokátem.

## Otevřené body napříč tématy

- ~~Doslovný text § 11 odst. 3–7 a § 20 vyhl. 146/2024 Sb.~~ — **získán 2026-09-22** z úplného znění e-Sbírky (znění účinné od 1. 7. 2026, konsolidované — text odkazuje na vyhl. č. 43/2025 Sb. a nař. vl. č. 162/2025 Sb.). Doslovné citace jsou v [[../OsazeniNaPozemku/PolohaAStavebniCara]] a [[../OsazeniNaPozemku/OsvetleniAProsluneni]]. **Otevřená zůstává jen příloha č. 4** — je to grafika a z textového exportu registru ji vytáhnout nelze.
- Obsah nového vydání ČSN 73 4301 (6/2026) — placená norma, nezískána. Do té doby se z ní nesmí citovat žádná hodnota ([[../Legislativa/NormyCSN]]).
- **Požární bezpečnost RD** — zpracováno ([[../Legislativa/PozarniBezpecnostRD/Index]]). Otevřené zbývají dva body: zda po rekodifikaci stále platí hranice 200 m² zastavěné plochy RD pro státní požární dozor (opora byla v zrušeném § 104 odst. 1 písm. a) zák. č. 183/2006 Sb.) a rozpor 650 m² (TP 1.7 ČKAIT) vs. 600 m² (§ 15 odst. 2 vyhl. č. 23/2008 Sb.) u přístřešků. Do rozhodnutí platí nižší, vyhláškou daná hodnota. *(Doplněno 2026-09-22: hranice 200 m² se objevila i v odborném článku k sjezdům, tedy podruhé a nezávisle — ale ani jeden z obou výskytů není právní předpis, takže bod zůstává otevřený.)*
- **Podíl práce v ceně díla (35–60 %)** — jediný dohledaný zdroj; hledáno znovu 2026-09-23 a druhý
  zdroj se nenašel. Strop úspory ze svépomoci proto zůstává pásmem, ne číslem.
- **Pásma VRN a soft costs** v `tools/cena/ukazatele.json` jsou z praxe, ne z citovatelného zdroje.
- **Doslovná dikce povinnosti PBŘ u rodinného domu** — doloženo jen články ČKAIT a ESTAV
  ([[../KontrolaVarianty/PozarniBezpecnostRD]]).
- **Odstupové vzdálenosti podle ČSN 73 0833 / 73 0802** a **ČSN 73 4001** — placené normy; hodnoty
  se do studie nepřebírají. Proto zůstává úloha `pozarni-bezpecnost-rd` ve stavu STOP_NEEDS_WORK:
  její zbylé tagy nejde uzavřít z veřejných zdrojů.
- **Které vydání ČSN 73 4130 platí** — Strand uvádí 2024, karta TZB-info a přednáška ČVUT
  2010-03. Ve studii se cituje bez roku ([[../DispozicniVarianty/Schodiste]]).
- **Které normy jsou pro § 31 určeny ve Věstníku ÚNMZ** a co obsahuje **příloha č. 14** vyhlášky
  (odchylky geometrických parametrů) — příloha je grafická, z textového exportu registru ji
  vytáhnout nelze. Je to stejná překážka jako u přílohy č. 4 v B3.
- **Rozsah vydané ČSN 73 4301 (2026)** — popis revize jmenuje bytové domy, obytné části jiných
  budov, nástavby a *hromadnou* výstavbu individuálního bydlení; jednotlivý RD na míru v předmětu
  normy nefiguruje. Ověřit na vydaném znění ([[../DispozicniVarianty/PlochyAMinimalniRozmery]]).
- **Rok zrušené edice ČSN 73 4301** — týž článek Z+i mluví v prose o roku 2004 a v citaci Věstníku
  ÚNMZ 6/2026 o červnu 2024.
- **Sazba DPH u RD do 350 m² podlahové plochy** — hranice doložena (ČKAIT A 3.20), procento
  v dohledaném zdroji je zastaralé.
- **Sklon sjezdu a vyrovnávací rampy do garáže** — nedoloženo. Indicie ČSN 73 6057 (17 %) je
  z rešeršního souhrnu, ne z normy ani technického listu. Do té doby se ve studii žádné procento
  netvrdí ([[../OsazeniNaPozemku/ParkovaniAVjezd]]).
- **Vodorovné odstupy sítí — tabulka A.1 ČSN 73 6005** — nezískána v čitelné podobě (dostupný je
  jen 4. návrh revize z r. 2018 a projektová dokumentace bez hlaviček sloupců). Vědomě nedoplněno;
  nahrazeno pravidlem „koridor, ne dimenze, a vyjádření správce sítě" ([[../OsazeniNaPozemku/TrasyPripojek]]).
- **Postup pro stavební proluku podle § 20 odst. 5** — v proluce se odstupový úhel 45° nepoužije
  a porovnává se s hypotetickou souvislou zástavbou. Referenční hmotu model nezná; skill
  `odstupovy-uhel-zastineni` na to nemá postup ([[../OsazeniNaPozemku/OsvetleniAProsluneni]]).
- Kterou novelou a k jakému datu bylo zrušeno ochranné pásmo veřejného pohřebiště (dříve 100 m) a jaký je režim pásem zřízených před zrušením — platné znění zák. č. 256/2001 Sb. institut nezná, přechodná ustanovení nebyla zpracována ([[../Legislativa/StavebniObalka/OchrannaPasma]]).
- Rozsah veřejnoprávní odpovědnosti projektanta po zrušení § 159 odst. 3 SZ 183/2006 — **BLOCKED**, chce právníka ([[../ZivnostOdpovednostCR/OdpovednostZaSkodu]]).
- Rozpad HSV/PSV stojí na jediném zdroji z r. 2018; podíl práce jen jako pásmo 35–60 % ([[../CenovaMetodikaStaveb/Index]]).
- Ztráta výnosu FVE při orientaci východ/západ místo jihu — 20 % (Acetex) vs. 5–10 % (Viessmann CZ); procento se neuvádí, jen pořadí ([[../HmotoveReseniRD/StrechaATeren/OrientaceHrebeneAFotovoltaika]]).
- Bezpečné sklony skládaných krytin podle aktuální ČSN 73 1901-2:2020 — dostupná tabulka je z článku z r. 2007 citujícího nahrazené znění; placený text ([[../HmotoveReseniRD/StrechaATeren/TvarASklonStrechy]]).
- ~~Kterým ustanovením vyhl. č. 264/2020 Sb. se dnes stanoví Uem,N~~ — **vyřešeno 2026-09-21** z úplného textu e-Sbírky (znění od 1. 9. 2024): žádné Uem,N ve vyhlášce není, požadavek je Uem ≤ Uem,R (§ 6 odst. 1, příloha č. 1 odst. 4) a **A/V se ve vyhlášce nevyskytuje vůbec** ([[../HmotoveReseniRD/PomerAV/Definice]]).
- ~~Bezpečné sklony krytin podle ČSN 73 1901-2:2020~~ — **částečně vyřešeno 2026-09-21**: 30° a 22° u tašek potvrzeny třemi zdroji; 7° u falcované krytiny patří **dvojité stojaté drážce** a plyne z ČSN 73 3610, ne z 73 1901-2; asfaltové šindele sporné (20° vs. 18°). Zbytek tabulky z r. 2007 nepotvrzený — ověřitelný jen z placené normy nebo technických listů ([[../HmotoveReseniRD/StrechaATeren/TvarASklonStrechy]]).
- ~~Publikovaná rozhodovací matice pro hmotové varianty RD neexistuje~~ — **neplatí, dohledána 2026-09-21**: Juodagalvienė et al. (2017), EDAS + SWARA, CC BY — náklady na materiál 0,33, bezpečnost 0,29, variabilita dispozice 0,21, kompaktnost 0,16; v jejím výpočtu vyhrál čtvercový bungalov, protože bezpečnost převážila kompaktnost patra. Litva, 7 expertů, neřeší střechu ani terén ([[../HmotoveReseniRD/PomerAV/PorovnaniVariant]]).
- **Terénní úpravy a opěrné zdi ve schématu modelu** — není to rešeršní otázka, ale **chybějící funkce**: `site.json` zná jen zaměřený terén, takže `check.py` i `av.py` počítají § 18 a odstupový úhel proti stavu před úpravami. Vyžaduje rozšíření `site`/`design` schématu, ne zdroj.
- **Zadaná rešerše (2026-09-21): náklady podle podlažnosti** — kdy je patro dražší a kdy levnější než bungalov o stejné užitné ploše, co je víc svépomoc-friendly, jaké jsou reálné rozdíly nákladů a za jakých podmínek. Zdroje z r. 2019 si protiřečí ve znaménku; přednost mají cenové ukazatele ÚRS/RTS a rozpočty, ne magazíny ([[../HmotoveReseniRD/BungalovVsPatrovyDum]]).
- Cenový podklad pro B2 **chybí**. Rozporné sazby (výkop 5 000 Kč/m³, opěrná zeď 10–15 tis. Kč/bm bez výšky) byly 2026-09-21 z wiki odstraněny; zbývá jen jeden komerční ceník *(needs second source)*. Doplnit z cenových ukazatelů ÚRS/RTS s cenovým obdobím — do té doby se cena v B2 jako kritérium nepoužívá ([[../HmotoveReseniRD/StrechaATeren/VykopoveANasypovePrace]]).
