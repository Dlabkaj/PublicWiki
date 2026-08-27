# Vlastnictví — kdo co vlastní v systému řad / přípojka

**Summary**: Zákon č. 274/2001 Sb. odděluje vlastnictví **vodovodního řadu** (obvykle obec / svazek / sdružení / VaK) od vlastnictví **přípojky** (osoba, která ji zaplatila — typicky odběratel). Přípojky se **nezapisují do katastru nemovitostí**.

**Sources**: 
- https://www.zakonyprolidi.cz/cs/2001-274 (§ 3 odst. 3, 6; § 5 odst. 1; § 7 odst. 7; § 8 odst. 5)
- https://www.zakra.cz/blog/komu-dle-zakona-patri-vodovodni-pripojka (Michal Kraus / ZAKRA s.r.o., 13.12.2021) — výklad vlastnictví, cizí pozemek a služebnost
- https://www.cevak.cz/cs/zakaznicky-servis/nova-pripojka/vlastnik-pripojky (ČEVAK a.s. — provozovatel) — provozovatelské shrnutí vlastnictví, vodoměr = vlastník řadu
- https://www.osmd.cz/faq/oprava-udrzba-a-vymena-vodovodni-a-kanalizacni-pripojky/ (JUDr. Jiří Odehnal, advokát Brno, OSMD, 14.10.2022) — NOZ § 506/509 jako právní rámec, asymetrie obnova vs. údržba ve veřejném prostranství
- https://www.zakra.cz/blog/vlastnictvi-pripojek-inzenyrskych-siti-komu-patri-vodovodni-a-kanalizacni-pripojka (Michal Kraus / ZAKRA s.r.o., 31.5.2023) — komplementární cross-source ke ZAKRA komu-patri, potvrzuje "přípojka je vaše po celém jejím úseku" + výměnu celé přípojky hradí majitel v plné výši (i pro veřejné prostranství)

**Last updated**: 2026-06-04

---

## Právní rámec: proč přípojka NENÍ součástí pozemku (NOZ § 506, § 509)

Od **1.1.2014** (účinnost NOZ č. 89/2012 Sb.) platí obecné pravidlo: **stavba je součástí pozemku** (superficies solo cedit). Pro podzemní stavby a inženýrské sítě však zákon obsahuje výjimky:

> "Pro podzemní stavby platí, že nejsou-li výslovně považovány za nemovitou věc, jsou součástí pozemku i tehdy, zasahují-li pod jiný pozemek." (source: § 506 NOZ, cit. OSMD/Odehnal)

> "Pro inženýrské sítě se výslovně stanoví, že **nejsou součástí pozemku** (§ 509 NOZ)." (source: § 509 NOZ, cit. OSMD)

Důsledek pro vodovodní/kanalizační přípojky:
- Inženýrské sítě (vč. vodovod, kanalizace, plyn, elektřina, telekomunikace) **nikdy** nejsou součástí pozemku, ani pod cizím pozemkem.
- ZVK to ještě dále specifikuje v § 3 odst. 1 + 2: vodovodní/kanalizační přípojka je **samostatnou stavbou**.

✓ Cross-source: § 509 NOZ (Odehnal/OSMD) + NS judikát 22 Cdo 1308/2003 (Epravo, řešen starý ObčZ) → kontinuita úpravy překlenuta. Settled. Viz [[VecnaBremena]].

## Klíčové pravidlo: kdo zaplatil, ten vlastní (§ 3 odst. 6)

> "Vodovodní přípojku a kanalizační přípojku pořizuje na své náklady odběratel, není-li dohodnuto jinak; **vlastníkem přípojky je osoba, která na své náklady přípojku pořídila**." (source: § 3 odst. 6)

Pro přípojky zřízené **přede dnem účinnosti** zákona platí presumpce: vlastníkem je **vlastník pozemku/stavby** připojené na vodovod, neprokáže-li se opak (§ 3 odst. 3).

**Předěl 1.1.2002** — do té doby vlastník = vlastník připojeného pozemku/stavby; od 1.1.2002 vlastník = investor, který přípojku zaplatil. (source: zakra.cz, cross-source potvrzení účinnosti zákona 274/2001)

✓ Cross-source potvrzení proti zakra.cz: pravidlo "kdo zaplatil, ten vlastní" — settled.

## Hranice řad / přípojka — odbočovací uzávěr

§ 3 odst. 1: "Odbočení s uzávěrem je součástí vodovodu." → odbočovací armatura (navrtávací pas / T-kus + uzávěr) **patří vlastníkovi řadu**, ne odběrateli (source: § 3 odst. 1).

§ 8 odst. 5: "**Materiál na odbočení přípojek a uzávěr vodovodní přípojky hradí vlastník vodovodu** nebo kanalizace." (source: § 8 odst. 5) → fyzické zhotovení odbočení obvykle provádí provozovatel (na své náklady materiálu, často s přefakturací práce odběrateli — praxe se liší, **needs second source** pro detaily).

## Schéma vlastnictví

```
   [VODOVODNÍ ŘAD]──[odbočovací uzávěr]──[přípojka]──[VODOMĚR]──[vnitřní vodovod]
   ▲                ▲                    ▲           ▲          ▲
   │                │                    │           │          │
   vlastník řadu    vlastník řadu        ten, kdo    "měřidlo"  vlastník
   (obec/VaK/...)   ("součást vodovodu") přípojku    provozo-   stavby
                    § 3 odst. 1          zaplatil    vatele*    (odběratel)
                                         § 3 odst. 6
```

*Vlastnictví vodoměru samotného — zákon to neurčuje explicitně v § 17; v praxi **hradí zpravidla vlastník hlavního vodovodního řadu** (města/obce/VaK), pokud není dohodnuto jinak. Stejné pravidlo platí pro **navrtávací pas** (odbočení). (source: ČEVAK — provozovatelské shrnutí; settles needs-second-source flag). Vlastnictví ≠ pouhé financování, ale typicky financování → vlastnictví v rámci provozovatelské praxe.

## Přípojky se nezapisují do KN (§ 5 odst. 1)

> "Vlastnické vztahy k vodovodům a kanalizacím, jakož i k vodovodním přípojkám a kanalizačním přípojkám **se nezapisují do katastru nemovitostí**. Na majetkovou evidenci vodovodů a kanalizací **se nevztahuje zákon o zápisech vlastnických a jiných věcných práv k nemovitostem**." (source: § 5 odst. 1)

Důsledky:
- vlastnictví přípojky se **neprokazuje výpisem z KN** — důkazem jsou stavební doklady (kolaudace, smlouvy, projektová dokumentace, faktury za zhotovení),
- pro převod vlastnictví přípojky **není potřeba vklad do KN**,
- **majetková evidence** vodovodů a kanalizací je samostatná povinnost vlastníka řadu (§ 5 odst. 1 první věta).

Tato úprava je často zdroj sporů — viz Epravo článek o vlastnictví přípojek a praxe ZAKRA/ČEVAK (doplnit v další iteraci).

## Odpovědnost za údržbu — výjimka pro veřejné prostranství

§ 3 odst. 7: opravy a údržbu **přípojky uložené v pozemcích tvořících veřejné prostranství** zajišťuje **provozovatel ze svých provozních nákladů** (source: § 3 odst. 7).

Praktický důsledek:
- část přípojky **v ulici / pod chodníkem / silnicí** → provozovatel,
- část přípojky **na soukromém pozemku** → odběratel.

Pojem "veřejné prostranství" odkazuje na obecní zřízení (**§ 34 zákona č. 128/2000 Sb. o obcích**): "**všechna náměstí, ulice, tržiště, chodníky, veřejná zeleň, parky a další prostory přístupné každému bez omezení, tedy sloužící obecnému užívání, a to bez ohledu na vlastnictví k tomuto prostoru**". (source: ČEVAK + cross-source NS 22 Cdo 1308/2003 viz [[VecnaBremena]])

✓ Cross-source potvrzení proti zakra.cz a ČEVAK: výjimka pro veřejné prostranství — settled.

### ⚠️ Vodoměrné šachty — výjimka NEPLATÍ

> "Opravy a údržbu **vodoměrných šachet hradí ve všech případech vlastník vodovodní přípojky, bez ohledu na to, na jakém pozemku je šachta umístěna**." (source: ČEVAK)

Praktický důsledek: i šachta v chodníku / veřejném prostranství → odběratel hradí opravu. Liší se od pravidla pro samotnou přípojku.

**Právní opora** (Odehnal/OSMD): vodoměrná šachta je podle § 2 odst. 7 ZVK součástí **vnitřního vodovodu** ("veškeré vodovodní potrubí za vodoměrem"), nikoli přípojky. Výjimka § 3 odst. 7 dopadá pouze na přípojku ve veřejném prostranství; vnitřní vodovod (vč. šachty) je vždy v majetku vlastníka připojeného pozemku/stavby. ✓ Cross-source: ČEVAK + OSMD + § 2 odst. 7 ZVK → settled.

### ⚠️ Obnova (výměna) přípojky — výjimka VP rovněž NEPLATÍ

Klíčové rozlišení (Odehnal/OSMD s odkazem na Výklad č. 25 MZe ze 7.2.2005):
- § 3 odst. 7 výjimka "veřejné prostranství" pokrývá pouze **údržbu a opravy**.
- **Obnova (výměna) přípojky vždy zůstává na vlastníkovi přípojky** — i pro úsek pod komunikací/chodníkem.
- Obnova zahrnuje: výkopové práce, uzavírku silnice, materiál, projektovou dokumentaci s veřejnoprávním projednáním → **významná investiční položka**.

Detail viz [[VodovodniPripojka#údržba--oprava--obnova--tři-pojmy-s-odlišným-režimem-odehnalosmd|VodovodniPripojka]].

### Spory o vlastnictví starších přípojek — kompetence (ZAKRA 2023)

> "U starších přípojek platí **právní fikce**, zákon předpokládá, že patří tomu, jehož nemovitosti slouží, **neprokáže-li se opak**. V případných sporech je tedy nutné obrátit se na **stavební úřad**." (source: https://www.zakra.cz/blog/vlastnictvi-pripojek-inzenyrskych-siti-komu-patri-vodovodni-a-kanalizacni-pripojka)

Tedy spor o vlastnictví "staré" přípojky (před 1.1.2002) řeší stavební úřad podle dokladů (kolaudace, smlouvy, faktury) — protože vlastnictví se nezapisuje do KN (§ 5 odst. 1).

### Starší přípojky (před 274/2001) — historický flag

ČEVAK upozorňuje: u stávajících (předchozích) přípojek mohlo dojít k převedení **veřejné části přípojky tehdejšímu správci vodohospodářské infrastruktury** dle **vyhlášky č. 144/1978 Sb.** (ve znění vyhl. č. 185/1988 Sb.) — zrušené, ale historicky uplatněné. Pro starší nemovitosti důležité pro určení skutečného vlastníka přípojky — ověřit v doložkách o vlastnictví / smlouvách z té doby.

Zakra dále upřesňuje: provozovatel provádí "rovněž osazení, údržbu a výměnu vodoměru" — soft cross-source pro vlastnictví vodoměru = provozovatel. *(formálně stále needs second source z provozovatelských zdrojů — ČEVAK/VAK)*

## Vlastnictví nového úseku řadu (prodloužení)

Při prodloužení řadu novým investorem:
- nový úsek si **postaví a vlastní investor** (§ 8 odst. 4: "Náklady na realizaci napojení vodovodu … hradí vlastník, jemuž je umožněno napojení"),
- vlastnictví nového úseku se po dokončení **typicky převádí na obec / provozovatele** smlouvou (kupní / darovací) — praxe se liší obec od obce. *(needs second source)* — doplnit z ZAKRA / projektvodovodnipripojky / SOVAK.

## Vztah k cizí přípojce na vlastním pozemku

Situace: soused má přípojku vedenou přes cizí (vaše) pozemek.
- **vlastníkem přípojky** zůstává soused (zaplatil ji),
- vlastník pozemku má vůči vlastníkovi přípojky práva → typicky řeší **věcné břemeno / služebnost inženýrské sítě** (občanský zákoník) — viz [[VstupNaPozemek]] a budoucí stránka VecnaBremena (po ingesci Verner Legal, MGMec, bezplatnapravniporadna).
- pokud věcné břemeno není zřízeno, lze řešit:
  - dohodu o jeho zřízení (odplatně),
  - vydržení (po splnění zákonných podmínek OZ),
  - žalobu na odstranění / náhradu — doplnit z článků právní poradny.

### Praktický výklad ZAKRA

> "Jestliže [přípojka] **není chráněna věcným břemenem, může po vás soused požadovat její odstranění**. Z toho důvodu doporučujeme zřídit k vodovodní přípojce věcné břemeno, konkrétně **služebnost inženýrské sítě**." (source: zakra.cz)

Klíčové parametry typické služebnosti dle zakra.cz:
- **Povinnosti vlastníka pozemku**: zdržet se všeho, co vede k ohrožení sítě; po předchozím projednání umožnit vstup oprávněné osobě k prohlídce/údržbě.
- **Náhrada**: vlastníkovi pozemku náleží **jednorázová nebo opakovaná náhrada** podle smlouvy.
- **Trvání**: zpravidla **doba neurčitá**.
- **Forma**: zpravidla **ve prospěch nemovitosti** (in rem) — ne osoby. → Při prodeji nemovitosti VB přechází automaticky na nového vlastníka oprávněné nemovitosti.
- **Cesta zřízení**: primárně **vzájemná dohoda**; v některých případech může o zřízení **rozhodnout soud**.

⚠️ Praktický postup (cizí přípojka souseda na pozemku):
1. Ověřit v KN, zda VB ve prospěch sousedovi nemovitosti existuje.
2. Pokud NE → návrh dohody (jednorázová náhrada za stávající uložení).
3. Pokud soused odmítá → zvážit žalobu na odstranění; pozor na institut **vydržení** (může soused argumentovat, je-li uložena dlouhodobě v dobré víře) — viz [[VstupNaPozemek]] a budoucí VecnaBremena.

## Related pages

[[Zakon274_2001]] · [[VodovodniPripojka]] · [[VodovodniRad]] · [[VstupNaPozemek]] · [[OchrannaPasma]]
