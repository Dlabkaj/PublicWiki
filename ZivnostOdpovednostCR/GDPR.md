# GDPR — nakládání s osobními údaji klienta a sousedů (katastr nemovitostí)

> Stránka stojí na dvou úředních zdrojích (ÚOÚ a ČÚZK), které popisují **vlastní agendu** — v tomto rozsahu jde o primární pramen. Neobsahuje však text GDPR ani katastrálního zákona; právní tituly viz [[Index]].
> **Toto není právní stanovisko.** Viz [[Index]].

## Katastr nemovitostí — Q&A (Úřad pro ochranu osobních údajů, uoou.gov.cz)

- **Rodné číslo jako identifikátor vlastníka nemovitosti** v katastrálním operátu stanovuje katastrální zákon; rodná čísla mohou obsahovat i dokumenty, na jejichž základě jsou do katastru zapisována práva/povinnosti k nemovité věci — tyto dokumenty jsou evidovány ve **sbírce listin**, která je součástí katastru.
- **Katastr je veřejným seznamem** — v zásadě kdokoliv je oprávněn do něj nahlížet, pořizovat si opisy, výpisy nebo náčrty a získávat údaje ze sbírky listin, není-li stanoveno jinak; přístup k některým informacím je podmíněn identifikací zájemce a formálně upraven (vyhláška k poskytování údajů z katastru nemovitostí).
- **Zpřístupňování informací z katastru (vč. rodných čísel) je výkonem veřejné moci prováděným na právním základě dle GDPR — tj. bez souhlasu nositele rodného čísla.**
- Informace z katastru jsou obecně veřejně přístupné z titulu **zásady publicity** (veřejné kontroly obsahové a věcné správnosti evidovaných informací) — princip veřejnosti katastru je v ČR tradiční, byl součástí obecného knihovního zákona od roku 1871.
- ⚠️ **Klíčové omezení: s informacemi získanými z katastru nelze nakládat jinak než k naplnění účelů uvedených v katastrálním zákoně**, a to bez ohledu na to, zda mají charakter osobních údajů či nikoliv. — přímo relevantní pro zkoumaný případ: zpracování čísel parcel, LV a jmen vlastníků z katastru v `userInput/` musí sledovat účel dle katastrálního zákona, nikoli libovolné použití agentem.
- Užití a šíření informací z katastru **v rozporu s katastrálním zákonem** může být posouzeno jako **správní delikt** — v prvním stupni jej projednává katastrální úřad.
- Pokud použití rodného čísla nestanoví zákon, osoba, která rodné číslo z katastru získala, s ním **bez souhlasu jeho nositele nakládat nemůže**; nakládání s cizím rodným číslem v rozporu se zákonem o evidenci obyvatel fyzickou osobou projednává obec s rozšířenou působností, právnickou osobou **Úřad pro ochranu osobních údajů**.
- **Použití listiny, která rodné číslo obsahuje, není samo o sobě nakládání přímo s rodným číslem** — je-li listina získaná z katastru použita za legitimním účelem, nejde o neoprávněné nakládání s rodným číslem.

(source: https://uoou.gov.cz/profesional/qa-otazky-a-odpovedi/katastr-nemovitosti)

## Katastr nemovitostí a ochrana osobních údajů (ČÚZK, cuzk.gov.cz, poslední aktualizace 31. 5. 2019)

- **ČÚZK je v postavení správce osobních údajů evidovaných v katastru, katastrální úřady jsou zpracovateli** těchto osobních údajů.
- Vedení osobních údajů v katastru se řídí katastrálním zákonem, který stanoví, že **katastr nemovitostí je veřejný seznam** — správce ani zpracovatel proto **nemusí žádat o souhlas** s vedením osobních údajů, neboť jde o jejich zákonnou povinnost tyto údaje zpracovávat a zveřejňovat.
- **Osobní údaje se z katastru nikdy nevymazávají**, neboť katastrální úřady jsou povinny vést historii právních vztahů k nemovitostem v celé kontinuitě (od založení evidence nemovitostí).
- V katastru se o fyzické osobě zapisuje: **jméno, příjmení, rodné číslo** (nemá-li je, datum narození), **adresa trvalého pobytu** (nemá-li ji, adresa bydliště).
- Vedení rodného čísla je nezbytné pro jednoznačnou identifikaci vlastníka, protože v katastru je zapsána řada osob se stejným jménem, příjmením a datem narození jako jiná zapsaná osoba (**cca 6 000 duplicit a cca 150 triplicit** dle zdroje) *(needs second source — číslo pochází z jediného zdroje ČÚZK a je datováno k roku 2019)* a adresa není spolehlivým identifikačním údajem. Rozsah osobních údajů v KN je dle zdroje **přiměřený účelům, pro které je katastr veden**, a účinností GDPR se nezměnil.
- Od 1. 1. 2019 (novela vyhlášky č. 358/2013 Sb.) došlo ke změně jen při poskytování údajů katastru v **souborové formě (VFK)** obsahující osobní údaje — soubor popisných informací ve výměnném formátu nyní obsahuje pouze **šifrovaný interní identifikátor fyzické osoby (pseudonymizace)**; údaje o konkrétním vlastníkovi lze na základě identifikátoru získat novou webovou službou dálkového přístupu, přičemž **posouzení zákonnosti a přiměřenosti rozsahu takto získaných osobních údajů je povinností koncových uživatelů** a užití funkce je auditováno (např. dozorovým úřadem).
- Změna se **netýká** poskytování jednotlivých údajů (např. výpisů z katastru) ani uživatelů aplikací Dálkový přístup nebo Nahlížení do katastru nemovitostí — ⚠️ relevantní pro zkoumaný případ: jednotlivé výpisy (čísla parcel, LV, jména vlastníků) získané standardním nahlížením/výpisem nejsou dotčeny pseudonymizací uvedenou výše.

(source: https://cuzk.gov.cz/Je-dobre-vedet/Ochrana-osobnich-udaju/Katastr-nemovitosti-a-ochrana-osobnich-udaju.aspx)

## Open questions

- Zdroj řeší primárně rodné číslo jako osobní údaj v katastru; explicitně neřeší postavení jiných osobních údajů z katastru relevantních pro zkoumaný případ — čísla parcel, LV (listy vlastnictví), jména vlastníků sousedních pozemků — v kontextu zpracování AI agentem mimo samotné nahlížení do katastru (např. uložení v `userInput/`).
- Zdroj neuvádí právní titul a dobu uchování pro *soukromoprávní* subjekt (provozovatele AI agenta), který si údaje z katastru stáhne a uloží pro účely zpracování studie — řeší jen samotné zpřístupnění údajů katastrálním úřadem jako výkon veřejné moci.
- Nejasný je vztah mezi "legitimním účelem" použití listiny s rodným číslem (zmíněno v poslední odpovědi) a konkrétním účelem zpracování v rámci architektonické studie pro klienta — vyžaduje ověření/doplnění dalším zdrojem (ČÚZK).
