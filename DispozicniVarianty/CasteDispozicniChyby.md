# Časté dispoziční chyby

Ne seznam vkusových rad, ale to, co majitelé hotových domů říkají, že by udělali jinak. Hlavní zdroj
je anketa [Dřevostavitel.cz](https://www.drevostavitel.cz/clanek/spatny-navrh-dispozice) mezi
**více než 1000 majiteli** zděných domů i dřevostaveb, uspořádaná do 12 bodů. To je empirický zdroj,
ne normativní — ale právě proto je pro fázi B4 cennější než obecné zásady.

## Co se vrací nejčastěji

| chyba | co s tím v B4 |
|---|---|
| **jedna koupelna je málo**, a WC společné s koupelnou označili majitelé za největší chybu | druhé WC je otázka na klienta už v A4, ne dodatečné přání; MT projekt doporučuje pro čtyřčlennou rodinu dvě koupelny |
| **jen jeden záchod** | totéž — a stojí to metry, které musí být v programu |
| **podceněná technická místnost** | citace z ankety: „dnes bych navrhnul aspoň **2,5 × 2,5 m**"; viz [Hygienická jádra a TZB](HygienickaJadraATZB.md) |
| **chybějící pokoje** (bod 4 ankety) | program z A4 se v B4 nerozšiřuje sám — ale varianta, která jednu místnost navíc umožní, to má mít napsané jako svůj přínos |
| **málo zásuvek** | není dispozice, je to TZB; do studie patří jen tam, kde to určuje polohu nábytku |
| **malá předsíň, zvlášť s dětmi a kočárkem** | viz [Komunikační plochy a zádveří](KomunikacniPlochyAZadveri.md) |
| **francouzské okno vedle televize** | kolize okna a nábytku — tohle najde až rozkreslený nábytek, ne hmota |
| **kombinace podlahového vytápění a radiátorů** | rozhodnutí TZB, které ale mění, kde smí být nábytek |

Koupelna je podle ankety statisticky místnost, ve které se tráví nejméně času — a přesto bývá
nadměrná. Metry z ní jdou lépe do úložných prostor.

## Úložné prostory — chyba, kterou dispozice udělá, i když všechno ostatní vyjde

Sbíhají se tu dva nezávislé zdroje: anketa Dřevostavitele (technická místnost, komora, půdní prostor
se „rozhodně vyplatí") a [HomeInCube](https://www.homeincube.cz/nejcastejsi-chyby-v-dispozici-interieru-a-co-s-nimi-bez-rekonstrukce/),
který skladovací nábytek a předsíň jmenuje mezi hlavními problémy hotových interiérů. HomeInCube je
ale text o úpravách interiéru bez stavebních zásahů, tedy slabý zdroj pro fázi návrhu — bere se jako
potvrzení směru, ne jako číslo.

Pro B4 z toho plyne **kontrolní otázka, ne norma**: kde je v každé variantě místo pro úklidové věci,
sezónní textil, kola, kočárek a zahradní nářadí? Pokud odpověď zní „v technické místnosti", je třeba
ověřit, že se tam vejde i k technologiím — viz [Hygienická jádra a TZB](HygienickaJadraATZB.md).

## Provozní kolize, které se dají odhalit na půdorysu

Z [ESTAV](https://www.estav.cz/cz/5421.zonovani-domu-a-bytu-je-dulezite-pro-pohodlne-bydleni)
a [MD architekti](https://www.master-design.cz/blog/dokonaly-dum/logika-vnitrniho-prostoru):

1. **Průchozí kuchyně** a komunikační trasa mezi pohovkou a televizí.
2. **Provozně blízké místnosti daleko od sebe** — typicky ložnice a koupelna.
3. **Kličkování** — trasa, která obchází nevhodně umístěný nábytek.
4. **Dveře, které narážejí** do nábytku nebo odřezávají výhled do zahrady.
5. **Pohled z obývacího pokoje přímo na dveře WC.**
6. **Hlučná kuchyně vedle ložnice** (MT projekt) — akustika mezi zónami.

Body 1–3 a 6 jsou strojově kontrolovatelné, jakmile jsou v modelu místnosti a jejich funkce; body 4–5
potřebují dveřní křídla a nábytek, tedy fázi B5 a výš. Co z toho dělá `tools/dispozice/dispozice.py`,
je popsáno v [Indexu](Index.md).

## Related pages

- [Zónování a orientace](ZonovaniAOrientace.md)
- [Komunikační plochy a zádveří](KomunikacniPlochyAZadveri.md)
- [Hygienická jádra a TZB](HygienickaJadraATZB.md)
