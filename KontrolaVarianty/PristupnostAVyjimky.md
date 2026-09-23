# Přístupnost a výjimky

Dvě otázky, které rozhodují o tom, jak verdikt fáze B5 zní: **musí být rodinný dům bezbariérový?**
a **který nález je ještě prominutelný a který je konec varianty?** Obě jsou odpovězené doslovným
textem z e-Sbírky (vyhl. č. 146/2024 Sb. ve znění od 1. 7. 2026, zák. č. 283/2021 Sb.).

## Přístupnost: běžný rodinný dům ji nemusí splnit

**§ 29 odst. 1:** „Stavba **podle druhu a účelu** musí být navržena a provedena tak, aby splnila
požadavky na přístupnost podle normy uvedené v **příloze č. 14** k této vyhlášce, pokud tato vyhláška
nestanoví jinak."

**§ 29 odst. 3** pak jmenuje, u kterých staveb musí být příchod z veřejného prostranství bez schodů
a vytyčený vodicími liniemi: stavba **občanského vybavení** v částech pro veřejnost, stavba
**bytového domu** a stavba pro výkon práce více než 25 osobami. **Rodinný dům v tom výčtu není.**

Kdy se přístupnost u RD přesto řeší:

- **Je-li to MUST z fáze A6** — přání klienta (bydlení pro stárnoucí rodiče, člen domácnosti na
  vozíku). Pak platí norma z přílohy č. 14, tedy ČSN 73 4001. Hodnoty z ní se do studie necitují,
  odkazuje se na ni.
- **Byt s univerzálním standardem** (§ 49 odst. 5): manipulační prostor kruhu o průměru minimálně
  **1,2 m** ve všech místnostech.
- **Byt zvláštního určení v bezbariérovém standardu** (§ 49 odst. 6): kruh **1,5 m** ve všech
  místnostech. § 49 odst. 3 dělí byty zvláštního určení na bezbariérový, specifický a pro osoby se
  zrakovým postižením.
- **§ 49 odst. 4:** příchod k bytu zvláštního určení nebo k bytu s univerzálním standardem musí být
  bez schodů a vyrovnávacích stupňů; výškový rozdíl se řeší rampou nebo výtahem.

> Praktický důsledek pro B5: u běžného RD se do verdiktu píše „**přístupnost se nevyžaduje** (§ 29
> odst. 1 a 3 — RD není v výčtu), klient ji v A6 nežádal". Kruh 1,2 m se testuje jen tehdy, když si
> klient univerzální standard vyžádal — a pak je to tvrdý geometrický požadavek ve **všech**
> místnostech, který obvykle rozhodne o šířce chodby i o rozměru koupelny.

## Výjimky: seznam je uzavřený

**§ 95 odst. 1** vyhlášky (doslova): „Za podmínek stanovených v § 138 odst. 1 stavebního zákona lze
povolit výjimku z **§ 7 odst. 1 a 3, § 8, § 9 odst. 1 a 3, § 10 odst. 3, § 11 odst. 1, 2 a 4,
§ 12 odst. 1, § 38 odst. 3, § 53 odst. 1, § 79 odst. 2**, přílohy č. 8 části 10, přílohy č. 9 části 1
bodu 1.3. a 1.10. a přílohy č. 9 části 2 bodu 2.4."

**Odst. 2:** ve velkých sídlech podle § 91 odst. 1 lze dále povolit výjimku z **§ 11 odst. 5**
a **§ 15**.

**§ 138 odst. 1 zák. č. 283/2021 Sb.** dává podmínky: výjimku lze povolit **pouze z těch ustanovení,
ze kterých to prováděcí předpis výslovně umožňuje**, a jen pokud se tím **neohrozí bezpečnost,
ochrana zdraví nebo života osob nebo zvířat, životní prostředí, sousední pozemky nebo stavby** —
a řešením podle výjimky musí být **dosaženo účelu** sledovaného požadavky na výstavbu.

### Co to znamená pro verdikt

| nález | prominutelný? |
|---|---|
| počet parkovacích stání (§ 7 odst. 1 a 3) | **ano** |
| odstup 2 m od hranice a stavební čára (§ 11 odst. 1, 2 a 4) | **ano** |
| podjezdná výška garáže (§ 38 odst. 3) | **ano** |
| **světlá výška obytné místnosti 2,5 m (§ 38 odst. 1)** | **ne** — v seznamu není |
| **denní osvětlení a zastínění souseda (§ 20)** | **ne** |
| **šířky dveří a vnitřních komunikací (§ 39)** | **ne** |
| **schodiště (§ 31)** | **ne** |
| **1 záchod a 1 koupelna (příloha č. 3 bod 1)** | **ne** |
| předsazené části nad veřejným prostranstvím (§ 11 odst. 5) | jen ve velkých sídlech |

> **Tohle je ta nejužitečnější věta celé fáze B5:** dvoumetrový odstup je vyjednatelný, světlá výška
> **není**. Varianta, která má FAIL na § 38 odst. 1 nebo na § 20, se nesmí posílat do B6 s poznámkou
> „vyřešíme výjimkou" — žádná výjimka neexistuje. Varianta s FAIL na § 11 odst. 2 se posílat může,
> ale s napsaným rizikem a s tím, že rozhodnutí není naše.

Formulace verdiktu má proto tři stupně a **prostředním se nesmí zametat**:

1. **projde** — žádný FAIL, WARNy vypsané.
2. **projde s pojmenovanou výjimkou** — FAIL jen v ustanovení z § 95, s uvedením paragrafu, důvodu
   a toho, že výjimku povoluje stavební úřad za podmínek § 138 odst. 1 SZ.
3. **zamítnuta** — FAIL v ustanovení mimo § 95, nebo neodstranitelná kolize. Zapsat důvod do
   `output/rozhodnuti.md` a variantu archivovat.

## Related pages

- [Požární bezpečnost RD](PozarniBezpecnostRD.md)
- [Konstrukční proveditelnost](KonstrukcniProveditelnost.md)
- [Poloha a stavební čára (B3)](../OsazeniNaPozemku/PolohaAStavebniCara.md)
- [Světlé a podchodné výšky (B4)](../DispozicniVarianty/SvetleVyskyAPodchodneVysky.md)
