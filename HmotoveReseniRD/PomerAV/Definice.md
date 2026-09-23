# Definice pojmů

## Systémová hranice

Vyhláška č. 264/2020 Sb., o energetické náročnosti budov, definuje **systémovou hranici** jako
povrch konstrukcí budovy, které souvisle obalují objem ucelené části budovy při uplatnění pravidel
podle české technické normy upravující energetickou náročnost budov (§ 2 písm. p) vyhlášky).

Vyhláška dále definuje **obálku ucelené části budovy** jako soubor všech teplosměnných konstrukcí
na hranici ucelené části budovy, které jsou vystaveny přilehlému prostředí (venkovní vzduch,
přilehlá zemina, vnitřní vzduch v přilehlém nevytápěném prostoru nebo v sousední budově/zóně)
(§ 2 písm. m) vyhlášky).

Právní aktuálnost ověřena 2026-09-20: vyhláška č. 264/2020 Sb. je v platnosti (účinnost od
1. 9. 2020, poslední konsolidované znění k 1. 9. 2024), nebyla zrušena; sama nahradila vyhlášky
č. 78/2013 Sb. a č. 230/2015 Sb. (§ 11). Znění § 2 písm. m) a p) odpovídá citaci výše.

Poznámka: samotný poměr **A/V** (objemový faktor tvaru) není v této vyhlášce definován ani zmíněn —
jeho definici stanovuje ČSN 73 0540-2, na kterou vyhláška v této otázce odkazuje. Vyhláška se
většinově zabývá metodikou výpočtu energetické náročnosti budovy (dodaná energie, primární energie,
klasifikační třídy), což je mimo rozsah tohoto tématu.

(source: https://www.zakonyprolidi.cz/cs/2020-264)

## Objemový faktor tvaru budovy A/V

> ⚠️ **NEAKTUÁLNÍ NORMOVÝ POŽADAVEK — celá tato sekce popisuje stav podle vydání
> ČSN 73 0540-2:2011 (resp. 2002/2005).** Od **1. 9. 2025** platí nové vydání
> **ČSN 73 0540-2 (srpen 2025)**, které nahrazuje vydání z října 2011 a ve kterém byly
> **požadavky na průměrný součinitel prostupu tepla budovy Uem odstraněny** (spolu
> s energetickým štítkem obálky budovy), a to kvůli kolizi s vyhláškou č. 264/2020 Sb.
> Nové vydání nemá kapitolu 9 „Prostup tepla obálkou budovy" ani přílohu C — obsah normy
> končí kapitolou 8 (tepelná stabilita) a informativní přílohou A.
> Doloženo oficiálním volným náhledem normy (předmluva, „Změny proti předchozí normě":
> odstraněny požadavky na průměrný součinitel prostupu tepla budovy) —
> https://www.normservis.cz/download/view/csn/73/520674/520674_nahled.pdf — a shodně
> TZB-info, https://stavba.tzb-info.cz/prostup-tepla-stavebni-konstrukci/28808-nova-csn-73-0540-2-tepelna-ochrana-budov-cast-2-pozadavky-vydana
>
> **Důsledek pro agenta:** tabulka Uem,N v závislosti na A/V níže je od 9/2025
> **historická, nikoli platný normový požadavek**. A/V zůstává použitelné jako
> *geometrický* ukazatel kompaktnosti hmoty (viz [[TypickaPasmaAV]]); požadavek na kvalitu
> obálky se dnes prokazuje podle vyhlášky č. 264/2020 Sb. — viz § *Jak se Uem prokazuje dnes*.

## Jak se Uem prokazuje dnes (vyhl. č. 264/2020 Sb.)

Ověřeno 2026-09-21 **v úplném textu z e-Sbírky** (oficiální registr, znění účinné od
**1. 9. 2024**, citace „264/2020 Sb."; stáhnuto `Get-ESbirka.ps1 -Mode FullText`).

**Žádné „Uem,N" ve vyhlášce není.** V celém textu se vyskytuje jen `Uem` (hodnocená budova),
`Uem,R` (referenční budova) a `ΔUem` (vliv tepelných vazeb). Požadavek je postavený jako srovnání
s referenční budovou, ne jako tabulková mez:

| co | kde v vyhlášce |
|---|---|
| průměrný součinitel prostupu tepla je ukazatel energetické náročnosti | § 3 odst. 1 písm. d) |
| požadavek: hodnoty ukazatelů podle § 3 odst. 1 písm. a), b) a d) hodnocené budovy **nejsou vyšší** než referenční hodnoty pro referenční budovu | § 6 odst. 1 (nové budovy a BTNSE), § 6 odst. 2 (změny dokončených budov) |
| výpočet referenční hodnoty `Uem,R = ∑HT,R,j / ∑Aj + fR · ΔUem,R` | příloha č. 1 odst. 4 |
| `fR` a `ΔUem,R` | příloha č. 1 tabulka 1 |
| `Aj` se stanoví **z vnějších rozměrů** | příloha č. 1 odst. 4 |
| klasifikační třídy A–G i pro Uem (jen pro štítek v průkazu, ne požadavek) | § 10 odst. 1, příloha č. 2 |
| ΔUem nejméně **0,02 W/(m²·K)**, hodnocení dle ČSN 73 0540-2 | příloha č. 5 bod 4 písm. a) |

**A/V se ve vyhlášce nevyskytuje vůbec** — ani v § , ani v žádné příloze (kontrolováno na řetězce
„A/V" a „objemový faktor" v úplném textu). Přísnost požadavku tedy dnes neškáluje s faktorem tvaru
jako v historické tabulce níž: referenční hodnota se skládá po jednotlivých konstrukcích, takže se
geometrie promítne jen přes plochy `Aj`, ne přes mez odvozenou z A/V.

Jedna vazba na normu ve vyhlášce zůstává: referenční `UR,j` se odvozuje z požadovaných hodnot
`UN,20,j` podle **ČSN 73 0540-2** (příloha č. 1 odst. 6). Zrušení požadavku na *Uem* v ČSN
73 0540-2 (8/2025) tedy nesahá na požadavky na *jednotlivé konstrukce*, které vyhláška používá dál.

(source: https://e-sbirka.gov.cz/sb/2020/264 — úplné znění od 1. 9. 2024)

Podle komentáře MPO/EFEKT k ČSN 73 0540 (veřejná sekundární publikace k normě, hodnoty samotné
normy ČSN 73 0540-2 nejsou v komentáři citovány jako placený text, jde o oficiální výklad) se
kvalita obálky budovy předepisuje průměrným součinitelem prostupu tepla **Uem** v závislosti na
**objemovém faktoru tvaru A/V** (dříve nazývaném "geometrická charakteristika"). Vzájemný vztah:
čím vyšší A/V, tím přísnější požadovaná hodnota Uem,N (norma zpřísňuje požadavek pro budovy
s vysokým objemovým faktorem tvaru).

**Systémová hranice** je v tomto kontextu (komentář k ČSN 73 0540, s odkazem na ČSN EN 832 a
ČSN EN ISO 13790) definována jako plocha tvořená vnějším povrchem konstrukcí ohraničujících zónu.
**Obálka budovy** tvoří všechny konstrukce na systémové hranici celé budovy, jež jsou vystaveny
venkovnímu prostředí (čl. 4.9 normy; definice platí i pro jednotlivé zóny budovy).

Průměrný součinitel prostupu tepla Uem se počítá podle vztahu (vzorec 22 v komentáři):

```
Uem = HT / A
```

kde:
- **HT** [W/K] — měrná ztráta prostupem tepla, stanovená ze součinitelů prostupu tepla Uj všech
  teplosměnných konstrukcí tvořících obálku budovy na její systémové hranici (danou vnějšími
  rozměry), jejich ploch Aj (určených z vnějších rozměrů), teplotních redukčních činitelů bj,
  lineárních činitelů prostupu tepla Ψj (a jejich délky) a bodových činitelů prostupu tepla χj
  (a jejich počtu) podle ČSN 73 0540-4;
- **A** [m²] — plocha obálky budovy, součet ploch Aj jednotlivých konstrukcí.

Poznámka k normě: nízký prostup tepla obálkou budovy je základním předpokladem účinného využití
obnovitelných zdrojů energie; energeticky vhodné budovy se navrhují s Uem na doporučené úrovni,
nízkoenergetické a pasivní domy s úrovní ještě nižší.

### A/V vs. plošný faktor tvaru A/Ac

Komentář výslovně rozlišuje dvě různé veličiny, jejichž záměna je časná chyba:

- **objemový faktor tvaru A/V** [m²/m³] — plocha obálky budovy A vztažená k objemu budovy V,
  používaný v ČSN 73 0540-2 pro určení Uem,N (tabulka 9).
- **plošný faktor tvaru A/Ac** — v technických normách k energetické náročnosti budov (např.
  prEN 15217) zkráceně nazývaný "faktor tvaru", vztažený na **celkovou podlahovou plochu Ac**
  (určenou z celkových vnitřních rozměrů podle zvláštního předpisu, tj. plochu všech podlaží
  budovy vymezenou mezi vnějšími stěnami, bez neobyvatelných sklepů a oddělených nevytápěných
  prostor — viz čl. A.5.3 normy).

Vzájemný poměr obou veličin určují konstrukční výšky jednotlivých podlaží hj (resp. průměrná
konstrukční výška podlaží hj,m) a průměrný poměr celkových vnitřních a celkových vnějších rozměrů
(komentář uvádí přibližnou hodnotu **0,8**) podle vztahu (23) komentáře:

```
A/V ≈ 0,8 · (A/Ac) / hj,m
```

Pro tento převod pak v rozmezí 0,7 ≤ A/Ac ≤ 3,5 platí přibližný vztah pro požadovaný součinitel
(vztah 24 komentáře):

```
Uem,rq ≈ 0,30 + 0,525 / (A/Ac)
```

*(needs second source)* — přibližný koeficient 0,8 i vztahy (23) a (24) jsou doloženy pouze
komentářem MPO/EFEKT k ČSN 73 0540 (sekundární publikace k vydání 2011); druhý nezávislý zdroj
nalezen nebyl. Aktuálnost: ve vydání ČSN 73 0540-2:2025 už požadavek na Uem není (viz varování
na začátku sekce), takže vztah (24) je dnes pouze orientační převod mezi faktory tvaru.

### Uem,N podle objemového faktoru tvaru A/V (tabulka 9 komentáře)

Pro obytné budovy (a nebytové budovy s poměrnou plochou průsvitných výplní otvorů obvodového
pláště fw ≤ 0,50 a převažující návrhovou vnitřní teplotou θim = 20 °C) stanovovala ČSN 73 0540-2 ve vydání 2011
požadované (Uem,rq) a doporučené (Uem,rc) hodnoty průměrného součinitele prostupu tepla podle
objemového faktoru tvaru A/V takto:

| A/V [m²/m³] | Uem,rq — požadovaná [W/(m²·K)] | Uem,rc — doporučená [W/(m²·K)] |
|---|---|---|
| ≤ 0,2 | 1,05 | 0,79 |
| 0,3 | 0,80 | 0,60 |
| 0,4 | 0,68 | 0,51 |
| 0,5 | 0,60 | 0,45 |
| 0,6 | 0,55 | 0,41 |
| 0,7 | 0,51 | 0,39 |
| 0,8 | 0,49 | 0,37 |
| 0,9 | 0,47 | 0,35 |
| ≥ 1,0 | 0,45 | 0,34 |
| mezilehlé hodnoty | 0,30 + 0,15/(A/V) | 0,75 · Uem,rq |

Zarovnání řádků ověřeno (REVIEW 2026-09-20). V textu vytaženém z PDF (`pdftotext -layout`) je
řádek hodnot „1,05 / 0,79" vysazen o jeden řádek výš, vedle záhlaví „A / V [m2/m3]"; správné
přiřazení je k prvnímu řádku ≤ 0,2. Potvrzeno dvěma nezávislými cestami:
1. **aritmeticky** — sloupec Uem,rq se na setiny rovná předpisu pro mezilehlé hodnoty
   0,30 + 0,15/(A/V) v každém řádku (0,2 → 1,05; 0,5 → 0,60; 1,0 → 0,45), což při posunu
   o řádek neplatí;
2. **druhým veřejným zdrojem** — MPO, „Výklad ustanovení ČSN 73 0540 Tepelná ochrana budov pro
   obytné dřevostavby" (Ing. Jiří Šála, 11/2005), tabulka 10, uvádí pro A/V 0,2–1,0 shodné
   požadované hodnoty 1,05 / 0,80 / 0,68 / 0,60 / 0,55 / 0,51 / 0,49 / 0,47 / 0,45 a shodný
   vztah 0,30 + 0,15/(A/V) —
   https://mpo.gov.cz/assets/dokumenty/32933/36506/408874/priloha003.pdf

Sloupec doporučených hodnot Uem,rc *(needs second source)* — čísla 0,79 … 0,34 (= 0,75 · Uem,rq)
jsou doložena jen komentářem MPO/EFEKT k vydání 2011. Starší vydání normy mělo doporučené
hodnoty jiné: MPO výklad 11/2005 uvádí 0,75 / 0,58 / 0,50 / 0,45 / 0,42 / 0,39 / 0,38 / 0,36 /
0,35 a vztah 0,25 + 0,10/(A/V). Nejde o rozpor, ale o rozdíl mezi vydáními normy; pro vydání 2011
druhý nezávislý zdroj nalezen nebyl. Žádná hodnota není citována z placeného textu ČSN — vše
z veřejných sekundárních publikací MPO/EFEKT, resp. MPO.

Pro nebytové budovy s fw > 0,50 se hodnoty upravují podle vztahu (25 komentáře):

```
Uem,N,LOP = Uem,N + 0,5 · (fw - 0,50) · Uem,N
```

Pro ostatní budovy (mimo výše uvedené případy) se Uem,N stanoví podle vztahu (26 komentáře):

```
Uem,N = Uem,N,20 · e1 · 35/Δθie
```

(source: efekt.gov.cz — Komentář k ČSN 73 0540 Tepelná ochrana budov, publikace MPO/EFEKT,
https://efekt.gov.cz/upload/7799f3fd595eeee1fa66875530f33e8a/Publikace_Komentar_k_CSN_730540_Tepelna_ochrana_budov_2220047206.pdf)

<!-- nerd:links -->
## See also

- [[ObestavenyProstor]]
- [[TypickaPasmaAV]]
- [[VypocetPlochAObjemu]]
<!-- /nerd:links -->
