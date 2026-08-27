# Živnost, odpovědnost a autorské právo — architektonická studie RD generovaná AI agentem

> ## ⚠️ TOTO NENÍ PRÁVNÍ STANOVISKO
>
> Tato složka je rešerše primárních právních předpisů a veřejně dostupných odborných výkladů. Není právní radou, právním stanoviskem ani doporučením pro konkrétní případ. Jednotlivé pasáže označené **[NÁZOR]** jsou výkladem zpracovatele této wiki, nikoli textem zákona ani judikaturou. Před spuštěním komerčního provozu agenta konzultuj advokáta se specializací na stavební a IT právo.
>
> Stav ke dni REVIEW: **2026-08-20**. Dvě otázky zůstávají **nevyřešené** — viz [Blokující otázky](#blokující-otázky).

Podstránky: [[Zivnost]] · [[StavebniZakon]] · [[AutorizovaneOsoby]] · [[AutorskeDiloAI]] · [[Licence]] · [[DiloAVady]] · [[OdpovednostZaSkodu]] · [[GDPR]]

---

## 1) Kdy je nutná vázaná živnost a kdy stačí živnost volná, obor 60

### Rozhodovací pravidlo

| Co agent produkuje | Režim | Ustanovení |
|---|---|---|
| Nezávazná architektonická/vizualizační studie RD — dispozice, hmota, vizualizace, orientační propočet; **bez** vazby na řízení podle stavebního zákona | **živnost volná**, obor č. 60 „Poradenská a konzultační činnost, zpracování odborných studií a posudků“ | § 25 + příloha č. 4 ŽZ; NV č. 278/2008 Sb., příloha 4, obor 60 |
| Územně plánovací dokumentace, **územní studie** (nástroj ÚP dle § 30 SZ), projektová dokumentace | **vázaná živnost** „Projektová činnost ve výstavbě“ **a zároveň** autorizace ČKA/ČKAIT | § 19 písm. b) + příloha č. 2 ŽZ; NV 278/2008 Sb., příloha 2; § 155 písm. a), § 156 odst. 1 SZ 283/2021 Sb.; § 2 odst. 4 a 5 zák. č. 360/1992 Sb. |
| Odborné vedení provádění stavby, dozor projektanta, ověřování zeměměřických činností | vybraná činnost — jen autorizovaná fyzická osoba | § 155 písm. b)–d) SZ 283/2021 Sb. |

### Opory v zákoně

- **§ 155 SZ č. 283/2021 Sb.** obsahuje **taxativní** výčet vybraných činností: zpracování ÚPD, územní studie a projektové dokumentace; odborné vedení provádění/odstraňování stavby; ověřování zeměměřických činností; výkon dozoru projektanta. **Architektonická studie stavby v tomto výčtu není.** „Územní studie“ v písm. a) je nástroj územního plánování („navrhuje, prověřuje a posuzuje možná řešení vybraných problémů v území“), nikoli studie rodinného domu.
- **§ 156 odst. 1 SZ**: ÚPD, územní studie a PD musí být zpracovány projektantem. **§ 156 odst. 2** dovoluje neautorizované osobě (VŠ/SŠ stavebního směru + 3 roky praxe) zpracovat dokumentaci jednoduchých staveb — **s výslovnou výjimkou jednoduchých staveb pro bydlení a rodinnou rekreaci**, tj. pro RD tato úleva neplatí.
- **NV č. 278/2008 Sb., příloha 4, obor 60** — obsahem jsou „poradenské služby technického charakteru … zejména ve stavebnictví a architektuře“ a „poskytování odborné pomoci, posudků, rad, doporučení a stanovisek k zabezpečení přípravy a realizace staveb“. Výslovné vyloučení: „Obsahem činnosti **není vlastní realizace technických činností, projektování staveb, ani jejich provádění**.“
- Pozor na sousední obor: **obor č. 62** („Příprava a vypracování technických návrhů, grafické a kresličské práce“ — zahrnuje zhotovování technických výkresů a náčrtků) je rovněž živností volnou a rovněž z něj je vyloučena „projektová činnost ve výstavbě“. Vizualizace a výkresy studie tedy spadají do živnosti volné, dokud se z nich nestane některý ze stupňů dokumentace podle SZ.
- **§ 3 odst. 1 písm. b) ŽZ** — živností není využívání výsledků duševní tvůrčí činnosti chráněných autorským zákonem **jejich autory**. Provozovatel AI agenta ale autorem není (§ 5 odst. 1 AZ vyžaduje fyzickou osobu, viz [[AutorskeDiloAI]]), takže se na něj tato výjimka nevztahuje. **[NÁZOR]**
- **§ 3 odst. 2 písm. i) ŽZ** — výjimka pro svobodné architekty/inženýry platí jen pro osoby s autorizací ČKA/ČKAIT vykonávající svobodné povolání, nikoli pro provozovatele nástroje.

### Sankce, pokud se hranice překročí

- **§ 303 odst. 1 a 5 SZ 283/2021 Sb.** — fyzická osoba, která v rozporu s § 155 provádí vybranou činnost bez oprávnění podle autorizačního zákona, se dopustí přestupku; pokuta až **400 000 Kč**.
- Odborná způsobilost pro vázanou živnost (příloha 2 ŽZ): autorizace/registrace dle zák. č. 360/1992 Sb.; nebo VŠ Mgr. stavebního/architektonického zaměření + 3 roky praxe; nebo VŠ Bc. / VOŠ / SŠ s maturitou v oboru + 5 let praxe. **Samotné naprogramování a provozování AI nástroje žádnou z těchto podmínek nesplňuje.**

### Praktický závěr **[NÁZOR]**

Provoz agenta je bezpečný v režimu **živnosti volné, obor 60**, pokud výstup (a) je označen jako nezávazná studie, (b) neobsahuje nic, co by šlo předložit stavebnímu úřadu jako dokumentaci podle SZ, (c) nenese autorizační razítko a (d) je ve smlouvě i v samotném dokumentu vymezen jako podklad, který musí přepracovat autorizovaná osoba. Jakmile by agent produkoval dokumentaci pro povolení záměru, jde o vybranou činnost podle § 155 SZ — a tu nemůže vykonávat právnická osoba ani software, jen autorizovaná fyzická osoba (§ 2 odst. 5 zák. č. 360/1992 Sb.). Nekomerční provoz nebo plugin zdarma **nemění nic na § 155 SZ** (ten oprávnění neváže na úplatnost); mění ale posouzení podle § 2 ŽZ, kde je znakem živnosti podnikání „za účelem dosažení zisku“ — bezúplatné nesoustavné poskytnutí živností být nemusí. Hranice soustavnosti a ziskovosti není v použitých zdrojích řešena. **[NÁZOR]**

---

## 2) Disclaimer a licenční doložka k vložení do výstupu studie

Text níže je **návrh k použití na vlastní riziko**, sestavený z ustanovení citovaných na podstránkách. Není právní radou; před nasazením nech zkontrolovat advokátem. **[NÁZOR]**

### 2a) Disclaimer

```
UPOZORNĚNÍ K POVAZE DOKUMENTU

1. Tento dokument je nezávazná architektonická studie vytvořená s použitím
   nástroje umělé inteligence. NENÍ dokumentací podle zákona č. 283/2021 Sb.,
   stavební zákon, v žádném jejím stupni, není územně plánovací dokumentací
   ani územní studií ve smyslu § 155 písm. a) téhož zákona a nelze jej použít
   jako podklad pro řízení před stavebním úřadem.

2. Dokument nebyl vypracován ani ověřen autorizovanou osobou podle zákona
   č. 360/1992 Sb. Neobsahuje statické posouzení, požárně bezpečnostní řešení,
   posouzení souladu s územně plánovací dokumentací ani ověření stavu pozemku
   a inženýrských sítí. Před jakýmkoli dalším krokem musí být obsah přepracován
   a ověřen autorizovaným architektem nebo autorizovaným inženýrem.

3. Rozměry, plochy, technická řešení a jakékoli cenové údaje jsou orientační
   a mohou být nesprávné. Objednatel bere na vědomí, že výstup generativního
   modelu může obsahovat věcné chyby, které nejsou na první pohled patrné.

4. Zhotovitel poskytuje tento dokument jako výsledek poradenské a konzultační
   činnosti v oboru č. 60 přílohy č. 4 nařízení vlády č. 278/2008 Sb.

5. Toto upozornění není jednostranným vyloučením odpovědnosti. Zhotovitel
   nevylučuje ani neomezuje svou zákonnou odpovědnost za újmu; k takovému
   jednostrannému oznámení by se podle § 2896 občanského zákoníku nepřihlíželo.
   Případné omezení náhrady újmy je upraveno výhradně smlouvou, a to v mezích
   § 2898 občanského zákoníku.
```

Bod 5 je podstatný: podle **§ 2896 OZ** se k jednostrannému oznámení o vyloučení nebo omezení povinnosti k náhradě újmy **nepřihlíží**; může být nanejvýš posouzeno jako varování před nebezpečím. Disclaimer tedy plní roli informační a důkazní (vymezuje účel díla a rozsah, v němž bylo plněno řádně), nikoli exonerační. **[NÁZOR]**

### 2b) Licenční doložka — s právem úpravy

```
LICENČNÍ UJEDNÁNÍ

1. Je-li tato studie autorským dílem podle zákona č. 121/2000 Sb., poskytuje
   zhotovitel objednateli licenci k jejímu užití podle § 2371 a násl.
   občanského zákoníku, a to:
   a) v rozsahu nevýhradním,
   b) územně neomezeně,
   c) časově na dobu trvání majetkových práv,
   d) množstevně neomezeně,
   e) ke všem způsobům užití známým v době uzavření smlouvy, zejména
      k rozmnožování, rozšiřování, vystavení a sdělování veřejnosti,
   f) k užití studie jako podkladu pro zpracování projektové dokumentace
      a pro provedení stavby.

2. PRÁVO ÚPRAVY. Objednatel je oprávněn studii i její název upravovat,
   zpracovávat, měnit, doplňovat, spojovat s jinými díly a zařazovat do díla
   souborného, a to i prostřednictvím třetích osob. Toto ujednání se sjednává
   výslovně pro účely § 2375 odst. 1 až 3 občanského zákoníku. Zhotovitel si
   nevyhrazuje svolení ke změnám podle § 2375 odst. 2 věty za středníkem.

3. PODLICENCE A POSTOUPENÍ. Objednatel je oprávněn poskytnout podlicenci
   třetí osobě (§ 2363 OZ), zejména navazujícímu projektantovi, zhotoviteli
   stavby a orgánům veřejné správy, a licenci postoupit (§ 2364 OZ);
   zhotovitel k postoupení uděluje souhlas již tímto.

4. Objednatel není povinen licenci využít; povinnost využití podle
   § 2372 odst. 2 OZ se vylučuje.

5. Odměna za licenci je zahrnuta v ceně díla.

6. Osobnostní práva autora podle § 11 zákona č. 121/2000 Sb. nejsou tímto
   ujednáním dotčena; autorských osobnostních práv se nelze vzdát
   (§ 11 odst. 4 téhož zákona).

7. Nejde-li o autorské dílo (zejména pro absenci tvůrčí činnosti fyzické
   osoby u výstupu generovaného umělou inteligencí), poskytuje zhotovitel
   objednateli tatáž oprávnění jako závazek smluvní povahy působící
   mezi stranami.
```

Proč je bod 2 nutný: **§ 2375 odst. 2 OZ** zakazuje nabyvateli dílo měnit, nebylo-li to ujednáno (výjimka jen pro úpravy, u nichž lze spravedlivě očekávat svolení autora). Bez výslovné doložky by navazující projektant neměl jistotu, že smí studii rozpracovat. **§ 61 odst. 1 AZ** sice u díla na objednávku zakládá licenci „k účelu vyplývajícímu ze smlouvy“ automaticky a dvě nezávislé advokátní kanceláře shodně uvádějí, že hospodářským účelem architektonické studie je zásadně následné zhotovení stavby — ale spoléhat na vyvratitelnou domněnku je zbytečné riziko. Bod 7 řeší situaci, kterou § 61 AZ nepokrývá vůbec: pokud výstup autorským dílem není (viz [[AutorskeDiloAI]] — autorem může být jen fyzická osoba dle § 5 odst. 1 AZ), není co licencovat a chránit lze jen smluvně, inter partes. **[NÁZOR]**

---

## 3) Kdo nese odpovědnost za chybu a jak daleko ji lze smluvně omezit

### Vrstvy odpovědnosti

| Vrstva | Vůči komu | Ustanovení |
|---|---|---|
| Odpovědnost za vady díla | objednateli (smluvnímu partnerovi) | § 2615 odst. 1 OZ — dílo má vadu, neodpovídá-li smlouvě; práva dle § 2106–2107 OZ |
| Náhrada škody z porušení smlouvy | objednateli | § 2913 OZ — **bez ohledu na zavinění**; nutno prokázat porušení povinnosti, škodu a příčinnou souvislost |
| Solidární odpovědnost dodavatele dokumentace | objednateli stavby | § 2630 OZ — vedle zhotovitele je zavázán i ten, kdo dodal stavební dokumentaci, neprokáže-li, že vadu nezpůsobila chyba v dokumentaci |
| Souběh vad a škody | — | § 1925 OZ — právo z vadného plnění nevylučuje právo na náhradu škody |
| Profesní odpovědnost autorizované osoby | veřejnoprávně | § 12 odst. 1 zák. č. 360/1992 Sb.; povinné pojištění dle § 16 odst. 1–2 |
| Řetězec dodavatelů | subdodavatel odpovídá svému objednateli, ne koncovému klientovi | ČKA FAQ (výklad komory, nikoli judikát) |

Lhůty: **§ 2618 OZ** — vady nutno oznámit bez zbytečného odkladu, nejpozději do **dvou let** od předání díla, namítne-li zhotovitel opožděnost. **§ 2629 odst. 1 OZ** — u skryté vady stavby a skryté vady stavební dokumentace **pět let od převzetí stavby**. Vzájemný vztah obou lhůt není v použitých zdrojích jednoznačně vyřešen — viz [[DiloAVady]].

### Meze smluvního omezení — § 2898 OZ

**Nepřihlíží se** k ujednání, které předem vylučuje nebo omezuje povinnost k náhradě újmy:
1. způsobené člověku na jeho **přirozených právech** (život, zdraví),
2. způsobené **úmyslně nebo z hrubé nedbalosti**,
3. **právo slabší strany** na náhradu jakékoli újmy.

Práva se v těchto případech nelze ani platně vzdát. Ustanovení je kogentní (§ 1 odst. 2 OZ — formulace „nepřihlíží se“). Dále: **§ 1814 písm. a) OZ** zvlášť zakazuje ujednání omezující práva **spotřebitele** na náhradu újmy.

**Kdo je slabší strana:** spotřebitel podle § 419 OZ (člověk uzavírající smlouvu s podnikatelem mimo rámec svého podnikání) bude prakticky vždy slabší stranou; i podnikatel jí může být podle vyvratitelné domněnky § 433 OZ, jedná-li mimo souvislost s vlastním podnikáním a je-li odborně závislý na poskytovateli.

### Co tedy zbývá **[NÁZOR]**

- **Klient-spotřebitel (typický objednatel studie RD):** prostor pro smluvní limitaci náhrady škody je **prakticky nulový**. Limit částkou, vyloučení ušlého zisku ani liberační důvody vůči spotřebiteli neobstojí (§ 1814 písm. a) OZ + § 2898 OZ). Reálnými nástroji řízení rizika jsou pojištění odpovědnosti, přesné vymezení předmětu plnění ve smlouvě (co studie je a co není — tím se určuje, co vůbec je vadou podle § 2615 OZ) a povinné přepracování autorizovanou osobou.
- **Klient-podnikatel, mimo režim slabší strany:** platně lze sjednat horní hranici náhrady, vyloučení ušlého zisku (hradí se jen skutečná škoda) a liberační důvody — vždy jen pro nedbalost prostou, nikdy pro úmysl a hrubou nedbalost.
- Vzdání se práva na náhradu škody na pozemku zapsané do katastru působí i vůči pozdějším vlastníkům (§ 2897 OZ) — pro tento provoz irelevantní, ale je to jediná forma s věcněprávními účinky.

---

## 4) Osobní údaje v `userInput/`

Podstránka [[GDPR]] stojí na výkladech ÚOOÚ a ČÚZK ke katastru nemovitostí. Právní tituly podle GDPR (nařízení (EU) 2016/679) nejsou v použitých zdrojích rozebrány; níže je jejich přiřazení k situaci agenta jako výklad zpracovatele. **[NÁZOR]**

### Co v `userInput/` typicky je

Jméno a adresa klienta; parcelní čísla a čísla LV; jména a adresy vlastníků sousedních pozemků z katastru; fotografie pozemku; případně rodné číslo, je-li ve výpisu nebo v listině ze sbírky listin.

### Doporučený režim

| Kategorie | Právní titul | Ustanovení |
|---|---|---|
| Údaje klienta (jméno, kontakt, adresa stavby) | plnění smlouvy | čl. 6 odst. 1 písm. b) GDPR |
| Jména a adresy vlastníků sousedních pozemků z katastru | oprávněný zájem (posouzení odstupů, věcných břemen, souhlasů sousedů) — nutný balanční test | čl. 6 odst. 1 písm. f) GDPR |
| **Rodné číslo** | **nezpracovávat** | viz níže |

Pravidla, která z toho plynou:

- **Rodné číslo z katastru se do `userInput/` nesmí dostat.** Podle ÚOOÚ platí, že nestanoví-li použití rodného čísla zákon, nemůže s ním osoba, která je z katastru získala, bez souhlasu nositele nakládat. Zpřístupnění RČ katastrálním úřadem je výkonem veřejné moci, což nezakládá titul pro navazující soukromoprávní zpracování. **Pipeline agenta musí RČ z nahraných výpisů a listin mazat nebo maskovat před uložením.** Použití listiny obsahující RČ k legitimnímu účelu není samo o sobě nakládáním s rodným číslem — ale jeho extrakce do datové sady ano. **[NÁZOR]**
- **Účelové omezení údajů z katastru.** ÚOOÚ uvádí, že s informacemi získanými z katastru nelze nakládat jinak než k naplnění účelů uvedených v katastrálním zákoně, bez ohledu na to, zda jde o osobní údaje; užití v rozporu s katastrálním zákonem může být správním deliktem projednávaným katastrálním úřadem. Konkrétní paragraf katastrálního zákona (č. 256/2013 Sb.) zdroj neuvádí — *(needs law verification)*. Prakticky: údaje z katastru použít pro zpracování konkrétní studie, nikoli budovat z nich databázi, profil vlastníka ani je použít jako trénovací data.
- **Zákaz použití pro trénink.** `userInput/` nesmí být zdrojem pro trénink ani fine-tuning modelu; to je jiný účel než ten, pro který byly údaje shromážděny (čl. 5 odst. 1 písm. b) GDPR — účelové omezení).
- **Minimalizace (čl. 5 odst. 1 písm. c) GDPR):** pro studii je potřeba geometrie pozemku, čísla parcel a odstupy — jména sousedů zpravidla nikoli. Pokud nejsou potřeba, neukládat je.
- **Doba uchování (čl. 5 odst. 1 písm. e) GDPR):** GDPR konkrétní lhůtu nestanoví; nutno ji určit a zveřejnit. Návrh: `userInput/` po předání studie **smazat nebo pseudonymizovat**, uchovat jen výstup studie a smluvní dokumentaci po dobu promlčecí lhůty pro nároky ze smlouvy (a účetní doklady dle daňových předpisů). **[NÁZOR]**
- **Informační povinnost (čl. 13 GDPR):** klientovi sdělit totožnost správce, účel, právní základ, příjemce (včetně poskytovatele LLM, je-li zpracování v cloudu), dobu uchování a jeho práva.
- **Předání do LLM = předání zpracovateli, případně do třetí země.** Odesílá-li agent obsah `userInput/` do cloudového modelu, je poskytovatel modelu zpracovatelem (nutná smlouva podle čl. 28 GDPR) a je nutné vyřešit předání mimo EU podle kapitoly V GDPR. Použité zdroje tuto otázku neřeší vůbec — **otevřená otázka.** **[NÁZOR]**
- Údaje ve výměnném formátu (VFK) jsou od 1. 1. 2019 pseudonymizované (šifrovaný identifikátor osoby) a posouzení zákonnosti a přiměřenosti získaného rozsahu je povinností koncového uživatele; běžných výpisů a Nahlížení do KN se to netýká.

---

## Blokující otázky

Tyto dvě otázky nejsou z použitých zdrojů zodpověditelné a REVIEW je nechal otevřené:

1. **Rozsah profesní odpovědnosti projektanta po rekodifikaci.** Zrušený § 159 odst. 3 zák. č. 183/2006 Sb. („projektant odpovídá za správnost, celistvost, úplnost a bezpečnost stavby…“) nemá v zák. č. 283/2021 Sb. výslovný protějšek; § 162 obsahuje jen povinnost zpracovat dokumentaci v souladu s právními předpisy. Zda tím veřejnoprávní odpovědnost projektanta zanikla, zúžila se, nebo ji plně pokrývá § 12 odst. 1 autorizačního zákona, musí posoudit právník. Zdroje ČKA (FAQ z 25. 4. 2023) i ČKAIT (PROFESIS A 3.5, nedatováno) stále citují zrušený předpis. Viz [[StavebniZakon]], [[OdpovednostZaSkodu]].
2. **Nesoulad NV č. 278/2008 Sb. s novým stavebním zákonem.** Obsahová náplň vázané živnosti „Projektová činnost ve výstavbě“ stále vyjmenovává „dokumentaci pro vydání územního rozhodnutí“ — stupeň dokumentace, který podle SZ 283/2021 Sb. neexistuje. Jak se vykládá rozsah živnosti přes tento nesoulad, žádný z použitých zdrojů neřeší.

Další otevřené otázky jsou na konci každé podstránky.

---

## Zdroje

Primární předpisy: [zák. č. 455/1991 Sb.](https://www.zakonyprolidi.cz/cs/1991-455) · [zák. č. 360/1992 Sb.](https://www.zakonyprolidi.cz/cs/1992-360) · [zák. č. 121/2000 Sb.](https://www.zakonyprolidi.cz/cs/2000-121) · [NV č. 278/2008 Sb.](https://www.zakonyprolidi.cz/cs/2008-278) · [zák. č. 89/2012 Sb.](https://www.zakonyprolidi.cz/cs/2012-89) · [zák. č. 283/2021 Sb.](https://www.zakonyprolidi.cz/cs/2021-283) · [nařízení (EU) 2016/679 (GDPR)](https://eur-lex.europa.eu/legal-content/CS/TXT/HTML/?uri=CELEX:32016R0679)

Odborné výklady a úřední zdroje jsou citovány u jednotlivých pasáží na podstránkách, vždy se jménem autora a povahou textu.
