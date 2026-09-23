# Odstupová vzdálenost — výpočet a typické hodnoty pro RD

Jak se odstupová vzdálenost od RD prakticky počítá a jaké řády hodnot vycházejí podle materiálu obvodové stěny — z veřejně dostupného odborného článku (ne z placené normy přímo).


> **Ověřeno 2026-09-23:** vyhláška č. 23/2008 Sb. **platí i po novém stavebním zákoně** — e-Sbírka vydává její úplné znění účinné od **1. 1. 2025** a vyhláška č. 146/2024 Sb. ji nenahradila. Tagy `*(law-verify)*` níže, které se ptaly na aktuálnost samotné vyhlášky, jsou tím zodpovězené; zůstávají ty, které se ptají na obsah **placených norem** (ČSN 73 0802, 73 0833) a na **interní dokumenty HZS**, protože ty se z registru zjistit nedají. Doslovné znění § 4, § 10, § 11, § 15 a přílohy č. 3 je na stránce [[../../KontrolaVarianty/PozarniBezpecnostRD]].

Ověřeno: 2026-09-15

## Zdroj a jeho povaha

Zdroj je odborný článek ESTAV.cz „Požárně bezpečnostní řešení rodinného domu a odstupové vzdálenosti – díl I." (autorka Ing. Marie Rusinová, Ph.D., autorizovaný inženýr v oboru požární bezpečnost staveb, publikováno 12. 12. 2018) *(1 zdroj — sekundární odborný výklad, ne přímá citace placených ČSN norem, na které se odvolává: ČSN 73 0802, 73 0804, 73 0833, 73 0810)*. Číselné hodnoty níže pocházejí z tohoto veřejně dostupného článku, ne z normy samotné.

## RD jako požární úsek — budova skupiny OB1

Rodinný dům je z hlediska PBS budova skupiny **OB1**, která při dodržení podmínek tvoří jediný požární úsek *(1 zdroj)*:

- max. 3 užitná nadzemní podlaží (včetně využívaného podkroví) + 1 podzemní podlaží,
- max. 3 obytné buňky (samostatné byty),
- celková užitná plocha max. **600 m²** (shoduje se s hranicí 600 m² v § 15 odst. 2 vyhl. 23/2008 Sb., viz [[Predpisy]]),
- součástí požárního úseku může být i garáž pro max. 3 vozidla skupiny 1,
- součástí může být i provozovna do 50 m² s požárním rizikem max. 60 kg/m² bez rizikových výrobků — nad tyto parametry se odděluje do samostatného požárního úseku.

Pokud RD tyto parametry (rozloha, počet bytů, podlaží) překročí, posuzuje se jako budova skupiny **OB2** (bytový dům) *(1 zdroj)*.

## Kdo posuzuje výsledky PBŘS — hranice 200 m² zastavěné plochy

Podle článku *(1 zdroj)*:

- RD se zastavěnou plochou **nad 200 m²** — posuzuje PBŘS jako dotčený orgán **Hasičský záchranný sbor**.
- RD se zastavěnou plochou **do 200 m²** — výsledky PBŘS (a tím i dosah PNP) posuzuje přímo **stavební úřad**, bez HZS jako dotčeného orgánu.

⚠️ **Platnost pro rok 2026 neověřena** — právní vazba této hranice byla v r. 2018 (i v TP 1.7) navázána na zrušený zákon č. 183/2006 Sb.; náhradní ustanovení se v tomto běhu nepodařilo dohledat. Podrobně viz ⚠️ REPEALED na [[PozarneNebezpecnyProstor]] *(needs law verification)*.

**Oprava citace (tento běh):** hranice 200 m² **neplyne z § 41 vyhl. č. 246/2001 Sb.** — § 41 té vyhlášky upravuje pouze *obsah* požárně bezpečnostního řešení a žádnou hranici 200 m² neobsahuje (ověřeno proti znění § 41 účinnému od 1. 1. 2026, zdroj 6). Článek ESTAV.cz na § 41 odkazuje kvůli obsahu PBŘS a hranici 200 m² uvádí vedle toho, bez citace ustanovení. Nositelem pravidla je **§ 31 zákona č. 133/1985 Sb., o požární ochraně** (rozsah státního požárního dozoru) — tak ji cituje i TP 1.7 na [[PozarneNebezpecnyProstor]].

## Dvě složky odstupové vzdálenosti

PNP se vymezuje jako obalová plocha kolem hořícího objektu, kam hrozí přenesení požáru dvěma mechanismy *(1 zdroj)*:

1. **Sálání tepla** z požárně otevřených ploch (okna, dveře, celé stěny konstrukce DP3) — obvykle rozhodující vliv.
2. **Dopad hořících částí** odpadávajících z fasády (typicky dřevěný obklad) — obvykle menší vliv.

### Potvrzení hodnoty p_v = 40 kg/m² druhým zdrojem (TP 1.7 ČKAIT PROFESIS)

Technická pomůcka ČKAIT **TP 1.7 „Požární bezpečnost jednoduchých staveb"** (viz i [[PozarneNebezpecnyProstor]]) uvádí totéž číslo jako přímou normovou hodnotu, ne jako odvozený příklad: „Požární riziko rodinných domů, popř. rodinných rekreačních staveb a garáží lze uvést normovou hodnotou. Pro rodinné domy a rodinné rekreační stavby činí **p_v = 40 kg/m²**" (s odkazem na Přílohu B ČSN 73 0802) *(2 zdroje — TP 1.7 i ESTAV.cz díl I shodně uvádí 40 kg/m² pro RD, značka *(1 zdroj)* u tohoto konkrétního čísla výše se tímto ruší, hodnota je potvrzená)*. TP 1.7 dále uvádí i normové hodnoty pro garáže: garáž pro osobní/dodávková a jednostopá vozidla τ_e = 15 min (p_v = 15 kg/m²), pro nákladní automobily a samojízdné stroje τ_e = 40 min (p_v = 40 kg/m²), pro prostory ubytování p_v = 30 kg/m².

TP 1.7 také **potvrzuje hodnoty pro přístřešky** uvedené níže ze zdroje ESTAV.cz díl II: přístřešek z konstrukcí DP2 → τ_e = 25 min, výška požárně otevřené plochy 1 m; z konstrukcí DP3 → τ_e = 30 min, výška 1,5 m; obě se počítají s reálnou délkou stěny přístřešku. Přístřešek z konstrukcí DP1 nemusí mít odstup posuzován vůbec.

### Odstup od sálání — vliv materiálu obvodové stěny (výpočtové požární zatížení p_v)

Hustota tepelného toku z požárního úseku se u nevýrobních objektů vyjadřuje výpočtovým požárním zatížením p_v [kg/m²]. Podle článku (odkaz na ČSN 73 0802/73 0804) *(1 zdroj, hodnoty z placené normy citované sekundárně)*:

- **Nehořlavý konstrukční systém** (např. zděná stavba): p_v = 40 kg/m², se zohledněním stálého požárního zatížení p_v = 45,75 kg/m² — toto jsou už výsledné hodnoty pro určení odstupu.
- **Smíšený konstrukční systém**: hodnota se navyšuje o +5 kg/m² oproti nehořlavému.
- **Hořlavý konstrukční systém DP2**: navýšení o +10 kg/m².
- **Hořlavý konstrukční systém DP3** (např. srub): navýšení o +15 kg/m², výsledná hodnota p_v = 60,75 kg/m².
- **Střešní plášť** (pokud se pro něj odstup počítá): p_v = 50 kg/m² (typická hodnota pro RD, kdy jsou požadavky na požární odolnost střešní pláště nulové nebo naplněné).

**Praktický důsledek zmíněný přímo v článku**: RD srubové konstrukce (DP3) může mít odstupovou vzdálenost **kolem 10 m** — autorka doporučuje s tím počítat už při výběru velikosti pozemku *(1 zdroj, řádová hodnota, ne přesný výpočet konkrétního domu)*.

Celá obvodová stěna dřevostavby se považuje za **zcela požárně otevřenou plochu** (jako konstrukce DP3), pokud certifikát z požární zkušebny neprokáže druh konstrukční části DP2, nebo pokud certifikát nedeklaruje požární uzavřenost i pro DP3 *(1 zdroj)* — to zvyšuje odstupovou vzdálenost dřevostaveb oproti zděné stavbě se stejnou plochou oken.

### Vliv zateplení zděné stavby na požární otevřenost

U zděné stěny (DP1/DP2) s vnějším zateplením z hořlavého materiálu (např. polystyren, třída reakce na oheň E) se stěna může stát částečně nebo zcela požárně otevřenou plochou podle množství uvolněného tepla Q [MJ/m²] z 1 m² výrobku *(1 zdroj)*:

- Q < 150 MJ/m² → stěna zůstává požárně uzavřená.
- 150 ≤ Q ≤ 350 MJ/m² → částečně požárně otevřená plocha, odstup redukovaným postupem.
- Q > 350 MJ/m² → zcela požárně otevřená plocha, odstup se počítá pro celou plochu.

Posudek je podle článku nutné provádět od tloušťky izolantu **200 mm** — u pasivních RD s tlustou fasádní izolací se tak i zděná stavba může chovat jako zcela požárně otevřená plocha s odstupy srovnatelnými s konstrukcí DP3 *(1 zdroj)*.

### Odstup od dopadu hořících částí

Pro fasádní obklady, které mohou za požáru odpadávat (typicky dřevěné obložení), se počítá samostatná odstupová vzdálenost podle vzorce *(1 zdroj, s odkazem na TZB-info 2013 jako svůj pramen)*:

**d = 0,36 × h_c [m]**, kde h_c je výška horní hrany hořlavého obkladu na fasádě měřená od přilehlého terénu (v mezním případě rovna celkové výšce objektu h).

**Pozor na značení — zdroje si ho prohazují:** ESTAV.cz značí tuto vzdálenost od dopadu hořících částí jako d₂ a vzdálenost od sálání jako d₁; TP 1.7 ČKAIT (viz níže) používá opačné značení — d₁ = dopad hořících částí, d₂ = sálání. Vzorec i věcný obsah jsou v obou zdrojích stejné, liší se jen index. Dále na této stránce se drží značení TP 1.7.

Výsledná odstupová vzdálenost/PNP se stanovuje pro každou stranu objektu a každou požárně otevřenou plochu zvlášť — postup nesčítá jednotlivé vlivy dohromady do jedné vzdálenosti bez dalšího pravidla (zdroj toto explicitně nerozvádí, viz otevřená otázka o zákazu sčítání segmentů na jiné stránce).

## Číselný příklad: okno RD, výpočtové zatížení 40 kg/m²

Zdroj: internetová poradna J. Seidl & spol., s.r.o. (protipožární ochrana staveb), odpověď Ing. Petra Bohuslava, publikováno 22. 4. 2014 *(1 zdroj, hodnota z tabulky přílohy F ČSN 73 0802 citovaná sekundárně)*:

- Pro okno 1,5 × 1,5 m u rodinného domu (výpočtové požární zatížení p_v = 40 kg/m², resp. 45 kg/m² v obecném příkladu poradny) vychází podle tabulek přílohy F ČSN 73 0802 odstupová vzdálenost **cca 1,86 m**.
- Poradna doporučuje u projektanta PBS ověřit navíc odstup od střešního pláště zvlášť (závisí na konstrukci, typu střechy a krytině).

Toto je konkrétní číselný příklad potvrzující řádovou hodnotu p_v = 40 kg/m² pro RD s nehořlavým konstrukčním systémem uvedenou výše, a ukazuje, že i běžně velké okno u zděné stavby dává odstup výrazně pod 2 m — v kontrastu s cca 10 m u srubu (DP3) zmíněnými výše.

## Pergoly a přístřešky na pozemku RD

Zdroj: ESTAV.cz, „Požárně bezpečnostní řešení rodinného domu a odstupové vzdálenosti – díl II." (Ing. Marie Rusinová, Ph.D., publikováno 18. 12. 2018) *(1 zdroj, sekundární výklad s odkazem na ČSN 73 0804 a konzultační stanovisko www.pelcfrantisek.cz)*:

- Přístřešek s **nehořlavým konstrukčním systémem** se z hlediska odstupových vzdáleností dále neřeší.
- **Pergola** navazující na obytné prostory RD se považuje za stejnou hustotu tepelného toku jako RD samotný; pro výpočet odstupu lze výšku stavby redukovat na 0,3× a odstup se počítá od vnější hranice pergoly.
- **Přístřešek pro auto** se podle ČSN 73 0804 nepovažuje za garáž; stěnové konstrukce smí mít max. u poloviny svého obvodu. Pokud je celý z konstrukcí druhu DP1, odstupy se neřeší. Pro DP2 se počítá s ekvivalentní dobou trvání požáru t_e = 25 min a předpokládanou výškou 1,0 m; pro DP3 t_e = 30 min a výška 1,5 m (v obou případech se do výpočtu započítává skutečná délka a šířka přístřešku).
- RD a přístřešek pro auto tvořící jeden funkční celek se posuzují společně — jejich PNP se vzájemně neovlivňují, odstup se určuje od vnějšího obvodu celé skupiny staveb.

## Co smí a nesmí být v PNP, a jak řešit přesah na sousední pozemek (praktická pravidla)

Tentýž zdroj (ESTAV.cz díl II) shrnuje praktická pravidla pro výslednou situaci *(1 zdroj)*:

- V PNP téhož požárního úseku (např. jednoho RD) se otevřené plochy vzájemně neřeší — riziko přenesení požáru „na sebe" u jednoho úseku nehrozí.
- V PNP smí být obvodové stěny sousedních objektů/úseků **bez** požárně otevřených ploch (oken, dveří), konstrukce druhu DP1 (např. oboustranně omítnutá zděná stěna) nebo s povrchovou úpravou reakce na oheň A1/A2. Stěna druhu DP3 (hodnocená jako požárně otevřená) se v cizím PNP vyskytovat nesmí.
- Střešní pláště v PNP nesmí mít požárně otevřené plochy (střešní okna) a musí mít klasifikaci **B ROOF (t3)**.
- **Výsledné pravidlo k přesahu na sousední pozemek**: PNP posuzované stavby má zůstat na vlastním pozemku. Přesah na **veřejné prostranství bez staveb** (ulice, parkoviště, hřiště) se považuje za vyhovující bez dalšího řešení. Přesah na **pozemek souseda** je nutné řešit **smluvně** mezi vlastníky — jiné stavby se tam vyskytovat nesmí a soused nemusí přesah schválit (viz i praktický příklad s věcným břemenem na [[PozarneNebezpecnyProstor]]).
- Pokud soused nesouhlasí, možná opatření na vlastním pozemku: zmenšení oken v daném směru, vybudování zděného plotu dostatečné výše a požární odolnosti, nebo přerozdělení požárních úseků/snížení požárního rizika stavby.
- Stejně jako řešená stavba nesmí zasahovat na souseda, **ani sousední (i stávající) stavba nesmí svým PNP dosahovat na řešený RD** — platí to jak pro novostavby, tak pro adaptace.
- U **adaptace podkroví** (typický případ u RD) se může zvýšit požární výška stavby i při nezměněné celkové výšce objektu, což může změnit klasifikaci požárního úseku a stupeň požární bezpečnosti — nutné je nově posoudit nové otvory ve střešní rovině (střešní okna, vikýře, balkony) i případně změněné otvory ve stávající části.
- U **řadových RD** s nehořlavým konstrukčním systémem přesah PNP přes hranice pozemků typicky nastává na uliční frontě (řeší se dle uspořádání parcel, případně smluvně mezi sousedy) i na straně zahrady/terasy (řeší se na vlastním pozemku — zvětšení nárožního pilíře, zmenšení okenního otvoru, zděný plot).

## Metodika a číselné příklady z TP 1.7 ČKAIT (kapitola 13 „Odstupy a požárně nebezpečné prostory")

Zdroj: technická pomůcka ČKAIT **TP 1.7 „Požární bezpečnost jednoduchých staveb"** (PROFESIS ČKAIT), kapitola 13 — toto je **přímo metodická kapitola k tématu této stránky**, ne sekundární výklad; hodnoty a vzorce v ní jsou převzaty z ČSN 73 0802 a ČSN 73 0804, ale samotná kapitola je veřejně dostupná publikace ČKAIT *(1 zdroj co do celé kapitoly, ale shoduje se a doplňuje předchozí zdroje na této stránce a potvrzuje je)*:

### Definice a princip (potvrzení)

- PNP se vymezuje dvěma mechanismy: **a)** místa dopadu hořících částí, **b)** sálání tepla z požárně otevřených ploch. Pro oba se počítá odstupová vzdálenost, výsledná je ta větší; počítá se i odstup od sousedních domů — v daném směru rozhoduje větší ze zjištěných vzdáleností.
- Bezpečná (kritická) hustota tepelného toku **I_krit = 18,5 kW/m²** pro vymezení PNP mezi objekty (v ČR vztaženo ke smrkovému dřevu; v jiných zemích bývá nižší, tedy s vyššími odstupy — nedoporučuje se odstupy podceňovat). Pro dopad na osobu I_krit = 10,0 kW/m² (5 s expozice, rychlost pohybu 0,5 m/s), pro vznícení hořlavého materiálu v budově I_krit = 15,0 kW/m².
- **Přesah PNP na sousední pozemek**: TP 1.7 kap. 13 jej výslovně nezakazuje — přípustnost posuzuje stavební úřad s ohledem na možnost zastavění sousedního pozemku. Doslovnou citaci a celý rozbor (ČKA 2023, dopis GŘ HZS 2009, § 11 odst. 1 vyhl. 146/2024 Sb.) má [[PozarneNebezpecnyProstor]].
- V PNP se smí nacházet jiné budovy/požární úseky **stejného vlastníka**, pokud mají obvodové stěny DP1 s požadovanou odolností, otvory uzavřené požárními uzávěry EI-C DP1 a střešní pláště B ROOF (t3) — u jednoduchých staveb platí výjimky (viz garáž/přístřešek výše).
- V PNP se nesmí nacházet vnější požární hydranty (ztížil by se přístup hasičů).

### Vzorce a postup výpočtu (bez placených tabulkových hodnot)

- Odstup od dopadu hořících částí: **d₁ = 0,36 × h_c** [m] — shoduje se přesně se vzorcem uvedeným výše ze zdroje ESTAV.cz (nyní potvrzeno druhým zdrojem). Neposuzuje se u hořlavých střešních plášťů se sklonem do 45°, u oken, okenic, zábradlí a podobných drobných hořlavých konstrukcí.
- Odstup od sálání d₂: požární riziko p_v se zvyšuje oproti nehořlavému systému o +5 kg/m² (smíšený systém), +10 kg/m² (hořlavý DP2), +15 kg/m² (hořlavý DP3) — hodnoty shodné se zdrojem ESTAV.cz výše, nyní potvrzené i touto metodickou kapitolou.
- Postup: spočítá se plocha stěny S_p, požárně otevřená plocha S_po (se součiniteli k₂, k₃ pro částečně otevřené plochy a střechu), procento otevřených ploch p₀ = S_po/S_p × 100, a d₂ se vyhledá v tabulce (Příloha F ČSN 73 0802) — **tabulkové hodnoty samy jsou z placené normy a zde se nepřebírají**, jen postup a příklady níže (ty TP 1.7 uvádí přímo v textu, ne jen v placené tabulce).
- Minimální procento požárně otevřených ploch pro tabulkové vyhledání je **40 %** — méně otevřené plochy se počítají jednotlivě podle tab. F2 (potvrzuje pravidlo, které už je na [[Predpisy]] citováno přímo z § 11 odst. 2 vyhl. 23/2008 Sb.).
- Výsledný PNP je kolmo k požárně otevřené ploše vymezen odstupovou vzdáleností a do stran válcovou plochou ukončenou pod úhlem **160°** o poloměru rovném odstupové vzdálenosti.

### Konkrétní číselné příklady odstupů pro RD (přímo v textu TP 1.7, ne jen v tabulce)

Tyto příklady TP 1.7 uvádí přímo v textu kapitoly 13 jako ilustraci — hodnoty jsou pro nehořlavý konstrukční systém RD, p_v = 40 kg/m²:

- Jednopodlažní obvodová stěna (výška h_u = 3 m, délka l = 9 m): při **40 %** požárně otevřených ploch vychází odstup **2,8 m**; při **100 %** otevřených ploch **5,9 m**.
- Dvoupodlažní požární úsek (výška h_u = 6 m, stejná délka a p_v): při 40 % otevřených ploch odstup **4,5 m**; při 100 % otevřených ploch **8,8 m**.
- Závěr zdroje: odstupy rostou s délkou a výškou posuzované stěny, s procentem požárně otevřených ploch a s požárním rizikem (tedy s konstrukčním systémem).
- **Garáž pro osobní automobily** (nehořlavý systém, τ_e = 15 min, vrata 4 × 2,5 m): odstup od vrat cca **2,58 m**; u hořlavého systému s konstrukcemi DP3 se τ_e zvýší na 30 min a odstup na **3,39 m**. Od stěn bez otvorů s požadovanou odolností je odstup 0 m.

Tyto hodnoty jsou plně v souladu s řádem čísel ze zdrojů výše (Seidl.cz 1,86 m pro malé okno, ČVUT příklad 2,3–2,5 m pro okno/vrata dřevostavby s uzavřenou stěnou) a poskytují ucelenější obrázek: **běžné jednopodlažní RD se zděnou/nehořlavou stěnou a přiměřeným podílem oken (cca 40 %) vychází na odstup kolem 3 m, u dvoupodlažního domu kolem 4,5 m; celoprosklená stěna nebo dřevostavba bez opláštění DP2 zvyšuje odstup zhruba na dvojnásobek.**

### Zateplení RD a přístřešky — doplnění

- U RD platí zjednodušení oproti jiným nízkým objektům: **není požadován vodorovný ani svislý požární pás ve fasádě ani pruh vláknité izolace nad založením** (na rozdíl od jiných nízkých objektů). Podmínky: zateplovací systém ETICS B, izolant třídy reakce na oheň min. E, povrchová úprava i_s = 0. Při tloušťce hořlavé izolace **do 200 mm** není nutné vliv zateplení na odstupy posuzovat vůbec (potvrzuje hranici 200 mm uvedenou výše ze zdroje ESTAV.cz, nyní druhým zdrojem). Zateplení jen z nehořlavých materiálů A1/A2 s i_s = 0 PNP neovlivňuje vůbec.
- Vnější hořlavý obklad: stejné hranice Q jako u ESTAV.cz výše (< 150 MJ/m² uzavřená, 150–350 částečně otevřená, > 350 zcela otevřená plocha) — potvrzeno druhým zdrojem.
- ⚠️ CONFLICT — **650 m² vs. 600 m² u přístřešku jako součásti požárního úseku RD**:
  - TP 1.7 ČKAIT, kap. 13 (zdroj 5), doslovně: „Přístřešky mohou být součástí rodinného domu (jeden požární úsek), pokud půdorysná plocha všech podlaží nepřekročí **650 m²**."
  - § 15 odst. 2 vyhl. č. 23/2008 Sb. (doslovné znění z e-Sbírky, viz [[Predpisy]]): jednotlivá garáž **nebo přístřešek** je součástí požárního úseku RD, **není-li plocha tohoto požárního úseku větší než 600 m²**.
  - Rozdíl nevysvětluje ani jeden zdroj. **Pro návrh je rozhodující vyhláška (600 m²)** — TP 1.7 je metodická pomůcka, ne právní předpis. U běžného RD (řádově do 300 m²) je rozdíl bez praktického dopadu; u domu blížícího se 600 m² je nutné ověřit u zpracovatele PBŘ.

## Kompletní číselný příklad PBŘS RD (výukový materiál ČVUT)

Zdroj: výukový materiál Fakulty stavební ČVUT v Praze (předmět 125YPBZ), vzorové požárně bezpečnostní řešení „Rodinný dům RD Rýmařov s garáží", datováno 22. 8. 2005 *(příklad z výuky, ne aktuální projektová dokumentace — použita ČSN 73 0802:2000, dnes nahrazena novějším zněním; hodnoty berte jako ilustrační řád veličin, ne jako závaznou metodiku)*:

- Popis domu: přízemní RD s garáží, dřevěná rámová konstrukce (systém LORD) s izolací a opláštěním Fermacell/sádrokarton, sedlová/valbová střecha — **hořlavý konstrukční systém**, budova skupiny OB1 dle ČSN 73 0833. Dům tvoří 2 požární úseky: PÚ1 (obytná část, II. stupeň požární bezpečnosti) a PÚ2 (garáž, I. stupeň požární bezpečnosti).
- Výpočtové požární zatížení: obytná část p_v = 40 kg/m² (dle tab. B.1 přílohy B ČSN 73 0802), garáž p_v = 15 kg/m² (dle tab. B.1 přílohy B ČSN 73 0804).
- I přes hořlavý konstrukční systém jsou obvodové stěny (viz skladba: termofasáda + fermacell + dřevěný rám s izolací + fermacell + sádrokarton) posouzeny znaleckým posudkem jako **zcela požárně uzavřená plocha** (požární odolnost REW 60 proti požadavku REW 30) — příklad ukazuje, že vhodná skladba obvodové stěny dřevostavby může dosáhnout požárního uzavření i bez klasického zdiva.
- **Výsledné odstupové vzdálenosti v tomto konkrétním příkladu**:
  - od největšího okna (rozměr cca 1,69 × 2,105 m, 100 % požárně otevřená plocha): **2,48 m v přímém směru, 1,44 m radiálně do stran**;
  - od garážových vrat (2,25 × 2,0 m, 100 % otevřená plocha): **2,3 m v přímém směru, 1,3 m radiálně do stran**;
  - od stěn bez otvorů (posouzených jako zcela uzavřené): **0 m**.
- Závěr příkladu: PNP rodinného domku a garáže nepřesahuje hranice pozemku, pokud vzdálenosti k hranicím sousedních pozemků nejsou menší než uvedené odstupy; odstupy jsou počítány pro maximální možné otvory, u menších otvorů se odstup může zmenšit.

**Proč je tento příklad užitečný i s výhradou stáří**: ukazuje řádovou velikost odstupů pro **běžné okno/dveře u nehořlavě posouzené (i když konstrukčně dřevěné) obvodové stěny** — v rozmezí cca 1,3–2,5 m, tedy podobného řádu jako číselný příklad ze zdroje Seidl.cz výše (1,86 m pro okno 1,5×1,5 m). Obě čísla společně podporují závěr, že u RD s běžně velkými okny a požárně uzavřenou/kvalitně opláštěnou stěnou se odstupy pohybují v jednotkách metrů, zatímco u zcela požárně otevřené fasády (např. neopláštěný srub, DP3) mohou dosáhnout cca 10 m (viz výše).

## Otevřené otázky

- Přesné aktuální znění § 31 zákona č. 133/1985 Sb. (rozsah státního požárního dozoru) po nabytí účinnosti stavebního zákona č. 283/2021 Sb. — hranici 200 m² váže TP 1.7 na ohlášení podle § 104 odst. 1 písm. a) starého zákona č. 183/2006 Sb., jehož číslování dnes neplatí *(needs law verification)*.
- Přesný normový postup určení procenta požárně otevřené plochy (vzorec se součiniteli k₂, k₃) — článek uvádí jen princip, ne odvození součinitelů (ty jsou v placené ČSN 73 0802).
- Zda hranice 650 m² z TP 1.7 (přístřešek jako součást PÚ rodinného domu) skutečně stojí vedle hranice 600 m² z § 15 odst. 2 vyhl. 23/2008 Sb., nebo jde o chybu či starší znění — viz ⚠️ CONFLICT výše.

## Zdroje

1. https://www.estav.cz/cz/7020.pozarne-bezpecnostni-reseni-rodinneho-domu-a-odstupove-vzdalenosti-dil-i (Ing. Marie Rusinová, Ph.D., publikováno 12. 12. 2018)
2. https://www.estav.cz/cz/7028.pozarne-bezpecnostni-reseni-rodinneho-domu-a-odstupove-vzdalenosti-dil-ii (Ing. Marie Rusinová, Ph.D., publikováno 18. 12. 2018)
3. https://seidl.cz/pozarne-nebezpecny-prostor/ (poradna J. Seidl & spol., s.r.o., Ing. Petr Bohuslav, publikováno 22. 4. 2014)
4. https://tzb.fsv.cvut.cz/files/vyuka/125ypbz/cviceni/1_uloha/Pozarne_bezpecnostni_reseni_RD.pdf (výukový materiál ČVUT, předmět 125YPBZ, vzorové PBŘS datováno 22. 8. 2005)
5. https://profesis.ckait.cz/dokumenty-ckait/tp-1-7/ (TP 1.7 ČKAIT PROFESIS, kapitola 13 „Odstupy a požárně nebezpečné prostory", díl 4/5)
6. https://www.zakonyprolidi.cz/cs/2001-246#p41 (§ 41 vyhl. č. 246/2001 Sb., znění účinné od 1. 1. 2026 — ověřeno v tomto běhu, že hranici 200 m² neobsahuje)

<!-- nerd:links -->
## See also

- [[PozarneNebezpecnyProstor]]
- [[Predpisy]]
<!-- /nerd:links -->
