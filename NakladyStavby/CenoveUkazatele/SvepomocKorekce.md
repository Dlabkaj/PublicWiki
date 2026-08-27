# Korekce na svépomoc — poměr práce a materiálu

**Summary**: Jak snížit top-down odhad podle cenových ukazatelů, pokud se část prací dělá svépomocí — poměr práce/materiál v ceně, hodinové zúčtovací sazby a obvyklá úspora.

**Sources**: [ESTAV.cz — Z čeho všeho se skládá cena rodinného domu](https://www.estav.cz/cz/6746.z-ceho-vseho-se-sklada-cena-rodinneho-domu)

**Last updated**: 2026-08-13

---

## Proč korekce vůbec potřebujeme

Cenový ukazatel RTS je odvozen z dodavatelsky realizovaných staveb — obsahuje tedy plnou cenu práce včetně režií a **přiměřeného zisku dodavatelské firmy** (viz [[RtsCenoveUkazatele2026]]). Svépomocná stavba tuto složku částečně odstraňuje. Otázka je, jak velká ta složka je.

## Rozdělení ZRN na práci a materiál

ZRN lze členit podle toho, zda jde o práci nebo o materiál. Hodinová zúčtovací sazba (cena práce) se podle cenové soustavy **RONET** pro rodinné domy pohybovala **ve 2. pololetí 2018 v rozmezí 250–350 Kč/hod** *(needs second source)*, podle toho, jak kvalifikované pracovní síly daná práce vyžaduje.

⚠️ **Údaj je z roku 2018 a je pro dnešek nepoužitelný jako absolutní číslo.** Za osm let ceny práce ve stavebnictví výrazně vzrostly. Slouží jen jako doklad, že se sazba liší podle kvalifikace — což je přesně to, co rozhoduje o tom, které práce má smysl dělat svépomocí a které ne.

⚠️ **Konkrétní procentní poměr práce : materiál tento zdroj neuvádí.**

Jiný zdroj ([DŘEVO&stavby](https://www.drevoastavby.cz/o-drevostavbach/jak-na-financovani-stavby/podrobny-rozpocet-domu-aneb-kolik-co-stoji), DŘEVO&stavby 4/2022, publ. 10. 5. 2025) uvádí, že u objednávky **„domu na klíč" je výsledná cena půl na půl tvořená materiálem a prací** *(needs second source)*. To je maximální teoretický strop úspory ze svépomoci — 50 %.

## Proč se plná polovina ušetřit nedá

Tentýž zdroj to hned koriguje: **při kompletní svépomocné výstavbě není možné počítat s tím, že ušetříte plnou polovinu nákladů.** Důvody:

1. **Horší marže na materiálu** — jako jednotlivec nezískáte takové ceny stavebního materiálu jako firma.
2. **DPH** — u dodávky na klíč se na celý dům vztahuje jednotná snížená sazba, zatímco při vlastním nákupu materiálu platíte základní sazbu. Zdroj uvádí 15 % vs. 21 %; **ověřeno v REVIEW 2026-08-13: snížená sazba je od 1. 1. 2024 12 %, nikoli 15 %** (základní zůstává 21 %, pro rok 2026 beze změny). Mechanismus platí dál a systematicky užírá část úspory.
3. **Doprava a režie** — neodpadají, jen se přesunou na stavebníka.
4. **Čas** — ohromné množství hodin strávených na stavbě, které se v rozpočtu neobjeví.

⚠️ **Konkrétní číslo obvyklé úspory tento zdroj neuvádí** — říká jen „ne celých 50 %". Rozsah je potřeba doplnit odjinud, viz Open questions.

## Konkrétní čísla — G SERVIS

Zdroj: [G SERVIS — Orientační ceny stavby rodinných domů SVÉPOMOCÍ](https://www.gservis.cz/rady-a-tipy/ceny-domu/orientacni-ceny-stavby-rodinnych-domu-svepomoci/). G SERVIS CZ, s.r.o. je projekční kancelář prodávající typové projekty RD; web nese copyright DEK a.s. a G SERVIS CZ, s.r.o. z roku 2022.

Toto je jediný nalezený zdroj s **explicitní kvantifikací úspory ze svépomoci**:

| Typ domu | Cena na klíč (Kč/m³ OP, bez DPH) | Svépomocí | Implikovaná úspora |
| --- | --- | --- | --- |
| Běžný dům | 9 775 | **60 %** ceny na klíč | 40 % |
| Pasivní dům | 10 400 | **70 %** ceny na klíč | 30 % |

Metodicky vychází z „průměrných nákladů na stavební práce a materiál, které aktuálně platí u rodinných domů", odvozených ze stavebních standardů.

Modelový výpočet zdroje pro dům s obestavěným prostorem 700 m³: 700 × 9 775 = cca 6,84 mil. Kč na klíč, z toho 60 % = **cca 4,1 mil. Kč svépomocí**. To je přímo použitelné schéma pro jakýkoli RD — stačí dosadit jeho OP.

⚠️ **Chyba ve zdroji**: v modelovém výpočtu je použito 9 755 Kč, zatímco text i výsledek pracují s 9 775 Kč. Zjevný překlep, rozdíl je zanedbatelný, ale ukazuje na úroveň redakční péče.

⚠️ **Není uveden rok cenové úrovně.** Copyright webu je 2022. Bez roku je sazba Kč/m³ v podstatě nepoužitelná jako absolutní číslo — použitelné je z toho hlavně **procento úspory**, které stárne pomaleji.

### ⚠️ Tato sazba NENÍ nezávislým potvrzením RTS

Vypadá to lákavě — 9 775 Kč/m³ vedle 10 475 Kč/m³ od RTS. **Není to však cross-check, a to ze dvou důvodů:**

1. **Jiný obsah ceny.** G SERVIS uvádí cenu **na klíč**, tedy včetně VRN, režií a zisku dodavatele. RTS uvádí **ZRN** bez VRN a bez rezervy. Ceny na klíč by měla být *vyšší* než ZRN, ne nižší — takže rozdíl nelze číst jako „shodují se v rámci ±15 %".
2. **Neznámý původ.** Zdroj neuvádí, ze které datové základny čísla pochází. Provozovatelem je DEK a.s., což je zároveň vlastník ÚRS — pokud jde o data ÚRS, je to zajímavé, ale zdroj to netvrdí a nelze to ověřit. Viz [[UrsAlternativa]].

**Nepoužívat jako potvrzení sazby RTS.** Použitelné je procento úspory a struktura výpočtu.

### ⚠️ Druhý výskyt „60 %" není druhý zdroj

[Svépomocí.cz — Cena stavby svépomocí](https://projekty.svepomoci.cz/stranka/cena-stavby-svepomoci/) (Stavební Postupy s.r.o.) uvádí totéž číslo: „cena stavby rodinného domu svépomocí tvoří **60 % z ceny stavby domu na klíč**". Sám to označuje za „všeobecně přibližný odhad" a ceny za stanovené „na základě obecných stavebních odhadů".

**Nepočítat to jako potvrzení.** Kromě shodného čísla se u obou zdrojů shoduje i seznam vyloučených položek — projekt, napojení na sítě, skrývka a uložení ornice, individuální podmínky zakládání, zpevněné plochy a přístupové komunikace, zahradní úpravy a oplocení, zařízení staveniště, kuchyňská linka a krb, nadstandardní materiály — **v prakticky stejném pořadí a stejné formulaci**. Stejně tak seznam faktorů ovlivňujících cenu. To je převzatý text, ne nezávislý odhad. Obě stránky jsou navíc marketingové weby prodávající typové projekty, které mají zájem na tom, aby stavba vypadala dostupně.

Reálně tedy máme pro „60 %" **jeden zdroj, ne dva** — a ten se sám hlásí k tomu, že jde o hrubý odhad.

### Co orientační cena svépomocí nepokrývá

Zdroj explicitně vyjmenovává, co je nutné připočíst navíc — cenný checklist, protože se to kryje s tím, co vynechává i cenový ukazatel RTS:

- projekt rodinného domu,
- vybudování inženýrských sítí a napojení na přípojky,
- skrývka a uložení ornice,
- individuální podmínky zakládání,
- zpevněné plochy a přístupová komunikace,
- zahradní, terénní a sadové úpravy, oplocení,
- zařízení staveniště,
- kuchyňská linka a krb,
- nadstandardní materiály a speciální prvky.

Zdroj upozorňuje, že tyto náklady **nejdou obecně vyčíslit** — na pozemku po předchozím domě většina odpadá, zatímco na nové parcele několik set metrů od přípojek můžou být významné.

Cenu dále ovlivňuje výběr materiálů a vybavení, **místo výstavby** (ve větších městech a atraktivních lokalitách vyšší), specifické požadavky, ceny konkrétních firem a **množství vlastní práce**.

## ⚠️ CONFLICT (NEVYŘEŠENO — blokuje stránku): úspora 40 % vs. 10–20 %

> **Adjudikováno v REVIEW (2026-08-13): tento rozpor NELZE odepsat na jinou definici.** Obě čísla popisují touž veličinu — kolik procent ceny na klíč ušetří stavebník svépomocí — a liší se čtyřnásobně. Ani jeden zdroj neuvádí metodiku a oba mají zájmový motiv opačným směrem. Zůstává otevřené; číslo úspory se nesmí použít jako jediná hodnota.

[RealFree.cz — Stavba domu 2026](https://realfree.cz/blog/stavba-domu-2026) (24. 6. 2026) tvrdí pravý opak G SERVISu: **„Stavba svépomocí ušetří reálně 10–20 %, ne polovinu."**

| Zdroj | Rok | Úspora ze svépomoci |
| --- | --- | --- |
| G SERVIS (a Svépomocí.cz, převzato) | ~2022 | **40 %** (60 % ceny na klíč) |
| DŘEVO&stavby | 2022/2025 | „ne plná polovina" — bez čísla |
| RealFree | 2026 | **10–20 %** |

**Rozdíl je čtyřnásobný. Nezprůměrovat.** Zdroje mají navíc protichůdné motivace: G SERVIS prodává typové projekty pro svépomocnou výstavbu (zájem na tom, aby svépomoc vypadala výhodně), RealFree je AI-asistovaný kompilát s partnerskými odkazy. Ani jeden neuvádí, z čeho své číslo odvodil.

⚠️ **Kvalita zdroje RealFree je nízká** — viz varování v [[EtapoveRozdeleni]] (obsah tvořen s pomocí AI, partnerské odkazy, zdrojem jsou jiné weby). Uvádíme ho proto, že jeho argumentace je konkrétní a ověřitelná, ne proto, že by to byla autorita.

Argumenty RealFree pro nízkou úsporu jsou přitom věcné a shodují se s DŘEVO&stavby:

- Materiál nakoupí jednotlivec **o 10–20 % dráž** než firma.
- U svépomocné stavby **zákon vyžaduje odborný stavební dozor** (u jednoduchých staveb) nebo stavbyvedoucího. Dobrý dozor stojí **kolem 3–4 % z ceny stavby**.
- Stavba se protáhne z 8–14 měsíců na **2–4 roky** (stavíte večery a víkendy).
- Složitější dokládání prostavěnosti pro banku a záruka jen na jednotlivé dodávky, ne na celé dílo.

**Praktický závěr**: 40 % je marketingový strop za předpokladu, že děláte skoro všechno sám a váš čas nemá cenu. 10–20 % je realističtější pro běžný scénář. Pro propočet bungalovu doporučuji počítat obě varianty jako rozpětí a **nevydávat žádnou za očekávanou hodnotu**.

## Rozptyl, ne rozpor: poměr materiál : práce

> **Adjudikováno v REVIEW (2026-08-13):** dva hrubé odhady bez metodiky, jejichž rozpětí (50–60 % na práci) se překrývá v jednom řádu. Stránka to už uzavírá rozpětím, ne jedním číslem — neblokuje.

Zdroje si protiřečí i v tom, která složka je větší:

| Zdroj | Tvrzení |
| --- | --- |
| DŘEVO&stavby | u domu na klíč je cena **půl na půl** materiál a práce |
| RealFree | **„práce tvoří až 60 % celkových nákladů, materiál zbytek"** |

Rozdíl 50:50 vs. 60:40 ve prospěch práce. Ani jeden zdroj neuvádí, jak k číslu došel, ani zda počítá režii a zisk dodavatele jako „práci". **Bezpečný závěr: práce je zhruba polovina až tři pětiny ceny na klíč** — to stačí k pochopení, proč je svépomoc lákavá, a nestačí k přesnému výpočtu úspory.

## Kde se svépomoc vyplatí a kde ne

RealFree to shrnuje způsobem, který se shoduje s výpověďmi realizačních firem výše:

- **Vyplatí se**: dokončovací práce — malování, pokládka podlah, montáž kuchyně, obklady. Tady jde ušetřit i stovky tisíc bez rizika poškození statiky nebo hydroizolace. Podle rozpadu tvoří dokončovací práce 20–25 % rozpočtu, takže je to největší dostupný balík.
- **Nevyplatí se**: základy, hrubá stavba, střecha, elektřina a rozvody. Chyba v hydroizolaci nebo elektroinstalaci se předělává řádově dráž, než kolik jste ušetřili.

## Rezerva

RealFree doporučuje držet **rezervu 10–15 %** rozpočtu na skryté náklady (základy, přípojky, terén) *(needs second source)*. Shodou okolností to odpovídá běžné odchylce ±15 %, se kterou počítá i RTS u cenových ukazatelů (viz [[RtsCenoveUkazatele2026]]) — ale jsou to dvě různé věci: jedna je nejistota odhadu, druhá jsou nepředvídané vícepráce. **Pro propočet je namístě počítat obě, ne jednu místo druhé.**

## Mezivarianta: investor jako generální dodavatel

Zdroj popisuje běžnou střední cestu: investor je sám sobě generálním dodavatelem — sám realizuje jen některé **méně technicky náročné práce** a na jednotlivé úkoly si sjednává firmy nebo specialisty. Dvě upozornění, která k tomu zdroj přidává:

- Nepodcenit **technický dozor**, který dohlíží na řádnost jednotlivých profesí po celou dobu výstavby.
- **Ztrácí se záruka** od jednoho hlavního dodavatele; vznikají sporné body mezi dodavateli dílčích celků.

Podle jednoho z dotazovaných dodavatelů se pro variantu „na klíč" rozhodne **zhruba 75 % klientů** *(needs second source)*.

## Kde se svépomocí šetřit nevyplácí

Praktické poznatky realizačních firem z téhož zdroje — užitečné při rozhodování, které etapy si nechat:

- **Nikdy nešetřit** na nosné konstrukci, obvodovém a střešním plášti a na technologii vytápění/rekuperace. Naopak sanita, podlahy, dveře a finální vybavení jdou měnit či doplňovat postupně bez zásahů do konstrukce.
- **Spodní stavba a přípojky** — nejčastější místo falešné úspory. Špatně provedená základová deska vyvolá vícepráce, které rozdíl v ceně snadno vyrovnají.
- **Základy obecně** — projektová dokumentace často řeší statiku jen jednoduchým výpočtem a výkres základů neudává skutečnou hloubku základové spáry, což výrazně ovlivní finální cenu. Bez průzkumu se cena základů zjišťuje až nad výkopem.
- **Elektro a voda** — subdodavatelé neznalí konkrétní technologie (u dřevostaveb výslovně) působí finanční problémy.
- **Výmalba** je klasická „udělám si sám" volba; podle dodavatele nedosáhly klientem vymalované domy kvality profesionála.

## Co se svépomocí ušetřit nedá

Zdroj upozorňuje, že do ZRN patří i práce a dodávky, které po dokončení nejsou fyzicky „hmatatelné", ale platí se za ně. Soukromý investor je systematicky opomíjí:

- vodorovná a svislá doprava vytěžené zeminy, uložení, případný poplatek za skládkování,
- manipulace se sutí a vybouranými hmotami včetně odvozu a skládkovného,
- veškeré potřebné **lešení**,
- veškeré **bednění** monolitických konstrukcí (odpadá, pokud se základ lije přímo do rýh nebo do ztraceného bednění),
- **přesun hmot** — přemístění materiálu z místa složení na stavbě do místa pracovního úkonu,
- úklid a kompletní vyčištění objektu před předáním,
- provizorní ochrana stavby před dokončením střechy a opatření proti krádežím.

U svépomoci se část z toho promění z peněz na čas, ale nezmizí. Lešení a skládkovné se platí tak jako tak.

## Vedlejší rozpočtové náklady (VRN)

VRN se obvykle pohybují **v jednotkách procent** ceny stavebního díla — u rodinných domů tedy v řádu desítek tisíc korun *(needs second source)*. Modelový rozpad téhož zdroje uvádí **VRN = 3,1 %** z celku ZRN+VRN s DPH (viz [[EtapoveRozdeleni]]).

Typicky sem patří zábory veřejných komunikací, ztížené prostorové podmínky pro zařízení staveniště, provizorní oplocení, rozsáhlé dočasné staveništní komunikace, ztížený dopravní přístup, práce v památkových zónách nebo doprava pracovníků ze vzdálených lokalit. **U běžného RD na volné parcele bude většina těchto vlivů nulová** — 3,1 % je tedy spíš horní odhad.

## DPH

Zdroj (2018) uvádí u bytové výstavby **sníženou sazbu 15 %** ze součtu ZRN+VRN, zatímco drobné stavební objekty (přípojky, oplocení, komunikace, sadové úpravy) jsou zatíženy **základní sazbou 21 %**.

**Aktualizováno v REVIEW 2026-08-13:** snížená sazba byla od 1. 1. 2024 sloučena na **12 %**; pro rok 2026 se sazby nemění. Uplatní se v režimu **stavby pro sociální bydlení** podle § 48 a § 48a zákona o DPH — u rodinného domu je limit **celková podlahová plocha do 350 m²** (u bytu 120 m²). Běžný bungalov okolo 110 m² tento limit splňuje s velkou rezervou, takže **pro propočet platí 12 % na hlavní objekt a 21 % na drobné objekty okolo**. Princip, že hlavní objekt má nižší sazbu než drobné objekty, tedy zůstává — jen s jiným číslem.
([sazby DPH 2026](https://www.taxorio.cz/blog/sazby-dph-2026), [režim sociálního bydlení](https://www.arbolux.cz/dph-pro-socialni-bydleni/))

## Členění, které stojí za zapamatování

Rozpočet stavebního objektu se člení podle druhu prací na:

- **HSV** — hlavní stavební výroba (především hrubá stavba),
- **PSV** — přidružená stavební výroba, tj. dokončovací řemeslné obory,
- **ZTI** — zdravotně technické instalace (vodoinstalace a ústřední vytápění),
- **montážní práce** — elektroinstalace, slaboproud, měření a regulace, případně vzduchotechnika a výtahy.

Rozhodnutí „co dělám svépomocí" se v praxi dělá po těchto skupinách, takže je to užitečnější dělení než stavební díly.

## Nezapomenout na drobné objekty

Cena domu není cena stavby. Kromě hlavního stavebního objektu je u RD obvykle několik drobných objektů vně domu: **přípojky, oplocení, příjezdové a pěší komunikace, sadové úpravy, venkovní osvětlení**. Cenový ukazatel Kč/m³ obestavěného prostoru je **nepokrývá** — počítají se zvlášť a mají vyšší sazbu DPH.

Stejně tak zdroj upozorňuje, že projektová příprava a zpracování rozpočtu se mohou pohybovat **v řádu až stovek tisíc korun** a zpravidla **nebývají zahrnuty do ceny stavby** *(needs second source)*.

## Open questions

- Jaký je procentní poměr práce vs. materiál v ZRN u RD? Klíčové číslo, které zatím nemáme.
- Jaká je obvyklá celková úspora při svépomoci a při jakém rozsahu vlastní práce?
- Aktuální hodinové zúčtovací sazby (2026), ne 2018.

## Related pages

- [[RtsCenoveUkazatele2026]]
- [[EtapoveRozdeleni]]
