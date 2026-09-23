# Porovnávání hmotových variant — kritéria a meze ukazatele A/V

## Slabina objemového faktoru tvaru A/V při porovnávání variant různé velikosti

Podle článku **Ing. Petra Kotka** (uveden jako "Ing.Petr Kotek", EkoWATT — Centrum pro
obnovitelné zdroje a úspory energie; článek je částí jeho disertační práce na ČVUT FSv, katedra
TZB, školitel prof. Karel Kabele; TZB-info, 17. 3. 2008, označeno "Recenzovaný" — autor, datum
i afiliace ověřeny ve zdroji 2026-09-20) je faktor tvaru FT = A/V velmi citlivý na absolutní objem stavby, nikoli jen na
její geometrický tvar — se stoupajícím objemem stejně "tvarované" budovy hodnota A/V klesá.
Autor uvádí příklad: malá krychlová budova může mít FT = 0,6, zatímco krychlový objekt velkého
objemu bude mít FT = 0,2, ačkoli jde o stejný (krychlový) tvar. (Citováno doslova ze zdroje;
souhlasí i s geometrií — A/V klesá s rostoucím charakteristickým rozměrem jako 1/L. Týž příklad
je uveden i na stránce [[TypickaPasmaAV]].)

**Praktický důsledek pro porovnávání hmotových variant RD:** srovnání A/V mezi variantami
o výrazně odlišném obestavěném prostoru je zavádějící — nízké A/V může být důsledkem většího
objemu, nikoli kompaktnějšího tvaru. Pro čisté porovnání "tvarové" efektivity variant o
podobném objemu je srovnání A/V přímočaré; při odlišných objemech je potřeba tento efekt
zohlednit nebo použít objemově nezávislý ukazatel.

## Alternativní ukazatele geometrie tvaru (RC, RCW)

Autor dále popisuje ukazatel **relative compactness (RC)** ze zahraniční literatury — poměr
vztažený k referenční krychli stejného objemu. Podle autora platí, že **objekt s RC = 0,9 je
tvarově optimalizován a má nejmenší ochlazovanou plochu konstrukcí** (žádné zbytečné výčnělky,
konzoly), a to shodně pro všechny objemy stejně tvarovaných staveb; **RC má opačný trend než
FT** — čím tvarově složitější objekt, tím nižší RC a vyšší FT. (Pozn.: tentýž článek na jiném
místě uvádí, že hledaným ukazatelem by byl takový, u kterého "objekt s koeficientem 1 je krychle,
0,7 obdélníková hala" — hodnoty 1 a 0,9 pro krychli/optimum jsou tedy ve zdroji uvedeny
nekonzistentně; pro rozhodování o variantách je podstatný jen trend, ne přesná kalibrace.)

V rámci disertační práce autora (ČVUT, 2008) byl dále navržen ukazatel **RCW**, který místo
celkové ochlazované plochy A pracuje s plochou obvodových stěn A_stěn — reakce na zjištění, že
u budov s vysokým podílem prosklení ovlivňuje spotřebu tepla a chladu především plocha a kvalita
zasklení, ne celková ochlazovaná plocha. Studie byla provedena na **69 modelových objektech
stejného objemu a různého tvaru** (skládaných z 27 shodných kostek, zařazených do 24 kategorií;
čísla FT na obrázcích platí pro objem 729 m³) s dynamickou simulací v IES<VE> — celkem 690
simulací a 2760 hodnot, klimatická databáze Prague.epw, obálka se součiniteli prostupu tepla na
doporučené úrovni podle ČSN 730540-2/2007; výsledné závislosti autor označuje za charakteristické
pro administrativní budovy; autor sám uvádí, že jde o dílčí výsledek disertační práce, ne finální
normovou metodiku, a ukazatel RCW nebyl v době článku zaveden do žádné normy či vyhlášky.

Poznámka k relevanci pro RD: studie a ukazatel RCW cílí primárně na budovy s vysokým podílem
prosklení (administrativní budovy); pro běžné rodinné domy s podíly zasklení v obvyklém rozsahu
autor přímé doporučení nahradit A/V jiným ukazatelem neuvádí — jde spíše o upozornění na meze
zjednodušeného odhadu podle A/V (viz výše zmíněná citlivost na objem a na skutečné vlastnosti
zasklení).

## Shrnutí — na co si dát pozor při porovnávání variant podle A/V

- A/V dobře porovnává tvarovou (ne)kompaktnost mezi variantami **podobného objemu**.
- Mezi variantami s výrazně odlišným obestavěným prostorem srovnání A/V samo o sobě zavádí
  k mylným závěrům — nízké A/V může být jen důsledek velikosti, ne tvaru.
- Ukazatel nezohledňuje podíl a kvalitu prosklení ani orientaci ke světovým stranám — pro reálný
  odhad tepelných ztrát/zisků je třeba tyto parametry posuzovat vedle A/V, ne místo něj.
- Ze simulací téhož autora: při vysokém podílu zasklení přestává být pořadí variant podle
  ochlazované plochy vypovídající — "krychlový objekt" s nejnižší ochlazovanou plochou nemá
  nutně nejnižší potřebu chladu.
- Porovnávat A/V variant vždy při stejné definici A a V (vnější rozměry, systémová hranice
  vytápěného prostoru) a nezaměňovat V s obestavěným prostorem — viz [[VypocetPlochAObjemu]]
  a [[ObestavenyProstor]].

## Publikovaná sada porovnávacích kritérií (doplněno 2026-09-21)

Zdroje původního úkolu žádnou rozhodovací matici neobsahovaly. Dohledána je jedna
**recenzovaná a otevřeně licencovaná** (CC BY 4.0):

> Juodagalvienė, B.; Turskis, Z.; Šaparauskas, J.; Endriukaitytė, A. (2017): *Integrated
> multi-criteria evaluation of house's plan shape based on the EDAS and SWARA methods.*
> Engineering Structures and Technologies 9(3), 117–125. DOI 10.3846/2029882X.2017.1347528
> (source: https://journals.vilniustech.lt/index.php/EST/article/view/594)

Model vybírá **základní tvar půdorysu RD**. Kritéria a jejich váhy (metoda SWARA, 7 expertů —
5 architektů a 2 konstruktéři):

| # | kritérium | směr | váha |
|---|---|---|---|
| c1 | náklady na materiál hlavních konstrukčních prvků [na m²] | min | **0,3344** |
| c2 | bezpečnost (bodově — zejména absence vnitřního schodiště) | max | **0,2943** |
| c3 | variabilita dispozice prostor | max | **0,2074** |
| c4 | kompaktnost tvaru | max | **0,1639** |

Srovnávaných variant bylo osm: tvar **obdélníkový, čtvercový, L a kříž**, každý jako
**jednopodlažní a dvoupodlažní**, při **stejné celkové ploše** a se šikmou střechou u všech.
Vítězem vyšel **čtvercový jednopodlažní dům** — a to výslovně proto, že kritérium bezpečnosti
(odstranění vnitřního schodiště) převážilo **výrazně lepší kompaktnost dvoupodlažních variant**.

Čtyři věci, které to o naší tabulce kritérií v B2 říkají:

1. **Kompaktnost je nejlehčí ze čtyř kritérií** (0,16). To podpírá pravidlo, že se podlažnost
   nerozhoduje podle A/V.
2. **Bezpečnost / bezbariérovost je těžké kritérium** (0,29) a v tomto modelu porazila
   kompaktnost. Odpovídá to pořadí kritérií v skillu `hmotove-reseni` (J1), kde je
   bezbariérovost vynucující kritérium.
3. **Náklady jsou nejtěžší kritérium** (0,33) — tedy přesně ta věc, kterou naše cenová báze
   dosud neumí spočítat, a proto je z tabulky v J5 vynechaná. To není nesoulad metodiky, ale
   chybějící vstup: dokud není rozpočtový podklad, je tahle váha nezaplněná. Viz zadaná rešerše
   k nákladům podle podlažnosti.
4. **Estetika byla z modelu vyřazena** s odůvodněním, že je příliš subjektivní — v architektonické
   studii pro klienta to takhle odmítnout nelze, takže model nepokrývá celé rozhodnutí.

⚠️ Omezení, se kterými se to musí citovat: Litva 2017, ekonomická třída domů 80–250 m², váhy jsou
**expertní úsudek sedmi lidí**, ne měření, a „bezpečnost" je bodované subjektivní kritérium. Model
také **neřeší tvar střechy, orientaci hřebene ani osazení k terénu** — tedy tři z pěti témat B2.
*(needs second source — jediná publikovaná sada, jedna autorská skupina)*

<!-- nerd:links -->
## See also

- [[ObestavenyProstor]]
- [[TypickaPasmaAV]]
- [[VypocetPlochAObjemu]]
<!-- /nerd:links -->
