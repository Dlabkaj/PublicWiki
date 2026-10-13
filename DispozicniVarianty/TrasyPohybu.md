# Trasy pohybu (cesty chůze)

Jak ověřit, že se dispozicí dá pohodlně chodit: nakreslit pravděpodobné cesty lidí a projít je s otevřenými dveřmi. Plochy místností ani volné místo před každým kusem nábytku zvlášť neodhalí uličku, kterou mezi sebou nechají.

Ověřeno: 2026-10-12

## Metoda

1. **Nakresli trasy, kudy se bude chodit každý den.** Vstup → kuchyň (nákup), vstup → schodiště, ložnice → koupelna a WC, obývák → terasa nebo zahrada. Uvnitř místnosti vede trasa od dveří ke každému kusu nábytku, který se používá: k posteli, ke skříni, k lince, ke stolu [1].
2. **Trasa je nejkratší rozumná cesta** (*desire line*). Když je navržená cesta delší, lidé zkracují rohy a protahují se kolem nábytku [1]. Trasa, která obchází nevhodně postavený nábytek („kličkování"), je chyba [2].
3. **Projdi trasy s otevřenými dveřmi.** Dveřmi se prochází s křídlem otevřeným. Křídlo, které se otevírá doprostřed místnosti nebo do směru chůze, zúží cestu každému, kdo jde kolem [1].
4. **Najdi nejužší místo každé trasy** a porovnej ho s šířkou níže.
5. **Zkontroluj křížení.** Trasa nesmí vést středem sezení (mezi gaučem a televizí) ani pracovním trojúhelníkem kuchyně [1], [2].

## Šířky

| trasa | šířka | zdroj |
|---|---|---|
| hlavní trasa: chodba, zádveří, obývák, kuchyň | **≥ 90 cm**, pohodlně 120 cm | [1], [3]; viz [[ZariditelnostAVolnaMista]] |
| vedlejší trasa: kolem postele, v ložnici, pracovně, koupelně | **≥ 60 cm** | [1], [3] |
| posledních ~1 m k nábytku | 60 cm, ke gauči z boku kolem konferenčního stolku 45 cm | [3] |
| protažení (ne pro každodenní cestu) | 45 cm | [3] |
| průchod dveřmi | světlá šířka dveří; vnitřní 80 cm, vstupní doporučeně 90 cm | [4]; § 39 odst. 1 vyhl. č. 146/2024 Sb. |

Žádné z čísel kromě šířky dveří není předpis. Pro chodbu v rodinném domě šířku nepředepisuje nic, viz [[KomunikacniPlochyAZadveri]].

## Dveře

- **Křídlo se otevírá ke stěně vedle zárubně, ne do provozní části místnosti** [1]. Prakticky: závěs na té straně, kam se po vstupu *nejde*. Křídlo pak leží podél stěny a cesta dál je volná.
- **Dveře nedávej do rohu.** Mezi zárubní a rohem nech **45 cm, lépe 60 cm**: vejde se tam skříň nebo knihovna a klika neodírá zeď [4]. Technické minimum je asi 10 cm na obložku zárubně [5].
- **Dvoje dveře blízko sebe se nesmějí otvírat proti sobě.** Když jinak nejde, zavěs je tak, aby se otvíraly od sebe [1], [5].
- **Otevřené dveře nesmějí zablokovat chodbu ani vytvořit úzké hrdlo** [1].
- **Koupelna a WC — zdroje se rozcházejí.** ESTAV doporučuje otevírat ven, aby šlo pomoci člověku, který uvnitř upadne za dveře [4]. Zahraniční zdroj vede dveře do místnosti, aby se nezužovala chodba, a dovnitř otevírané dveře nesmějí narážet na WC ani umyvadlo [1]. Rozhoduje provoz: v úzké chodbě dovnitř, u bezbariérové koupelny nebo u starších lidí ven nebo posuvné.
- **Kde se křídlo nevejde**, zvaž posuvné nebo zásuvné dveře. Zmenšují průchod asi o 5 cm [4].

## Jak to kontroluje nástroj

`tools/check/check.py`, skupina `use` (modul `tools/check/paths.py`):

- Rozdělí každou místnost na buňky 5 × 5 cm. Překážkou jsou stěny, nábytek a **všechna křídla otevřená o 90°**.
- Hledá trasy dveře ↔ dveře, dveře ↔ schodiště a od dveří ke každému používanému kusu nábytku. U každé trasy změří nejužší místo.
- Hlídá také trasu mezi gaučem a TV a kličkování (trasa delší než 2× přímá vzdálenost).
- `python tools/plan2d/from_design.py <model> --variant X --routes --out …html` trasy nakreslí. Zelené tečkované projdou, červené ne a jejich nejužší místo je zakroužkované.

Nástroj neví, které trasy jsou nejčastější. Nerozliší ani, že vstupní dveře se za sebou zavřou. Červenou trasu u dveří, které se po průchodu zavírají, je proto potřeba posoudit očima.

## Zdroje

1. Arcadium 3D: Floor Plan Design Mistakes That Ruin Home Flow. https://arcadium3d.com/articles/floor-plan-design-mistakes-that-ruin-home-flow
2. ESTAV: Zónování domu a bytu je důležité pro pohodlné bydlení. https://www.estav.cz/cz/5421.zonovani-domu-a-bytu-je-dulezite-pro-pohodlne-bydleni
3. interior-design-expert, `references/space-planning.md` (MIT, curiositech/some_claude_skills). https://github.com/curiositech/some_claude_skills
4. ESTAV: Doporučené rozměry dveří a směr jejich otevírání. https://www.estav.cz/cz/2844.doporucene-rozmery-dveri-a-smer-jejich-otevirani
5. České stavby: Interiérové dveře. https://www.ceskestavby.cz/jak-se-stavi-dum/interierove-dvere-5803.html
