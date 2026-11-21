# Referenční budova a zdroj energie — hlavní páka ke třídě B

Jak se třída PENB počítá proti referenční budově a proč ji nejvíc ovlivňuje zdroj energie (faktor primární energie z neobnovitelných zdrojů). Vychází z komentářů TZB-info (autor Ing. Michal Čejka, člen pracovní skupiny MPO) psaných k **návrhu** novely z ledna 2020 a z reportu o konferenci k novele 222/2024 Sb. Hodnoty z návrhu 2020 nejsou automaticky platné znění; závazné jsou přílohy vyhlášky popsané na stránce [[Vyhlaska-264-2020-vypocet-a-tridy]].

## Jak to funguje, jednoduše
1. Výpočtem se vytvoří **referenční budova**: stejný tvar, velikost, prosklení, orientace, vnitřní uspořádání a klima jako váš dům, ale se **standardní výbavou** předepsanou vyhláškou (zdroj: https://www.tzb-info.cz/energeticka-narocnost-budov/20685-novela-vyhlasky-c-78-2013-sb-cast-2-uprava-parametru-referencni-budovy). Referenční budova má pro každý účel (vytápění, teplá voda, chlazení) vždy stejný typ zdroje, ať váš dům používá cokoli; potvrzuje to tabulka 4 přílohy č. 1 s pevnými faktory primární energie referenční budovy pro každý typ spotřeby (https://e-sbirka.gov.cz/sb/2020/264).
2. Spočítá se energie referenční budovy a energie vašeho domu. Třída se určuje poměrem vašeho domu k referenční hodnotě (násobky hranic viz [[Vyhlaska-264-2020-vypocet-a-tridy]]).
3. Hodnotí se tři věci: **obálka** (průměrný součinitel prostupu tepla U<sub>em</sub> proti referenčnímu), **celková dodaná energie** a **primární energie z neobnovitelných zdrojů**. Třída B se tedy nedá dosáhnout samotným zateplením, rozhoduje i to, čím se topí a ohřívá voda.

## Co má referenční budova (a váš dům to může překonat)
Hodnoty ze zdroje 20685 (návrh 2020) porovnané s platnou tabulkou 1 přílohy č. 1 (https://e-sbirka.gov.cz/sb/2020/264, viz [[Vyhlaska-264-2020-vypocet-a-tridy]]); níže uvedené parametry kromě konkrétních čísel U se v platném znění shodují:
- **Obálka:** U referenčních konstrukcí = redukční činitel f<sub>R</sub> × požadovaná hodnota U<sub>N,20</sub> z ČSN 73 0540-2. Pro budovu s téměř nulovou spotřebou (novostavba) f<sub>R</sub> = 0,7, což odpovídá zhruba doporučeným hodnotám U<sub>rec,20</sub>; pro dokončenou budovu a její změnu f<sub>R</sub> = 1,0 (zdroj 20685; f<sub>R</sub> potvrzuje tab. 1 přílohy č. 1). Vyhláška konkrétní referenční U jednotlivých konstrukcí neuvádí, jen vzorec U<sub>R,j</sub> = f<sub>R</sub> · e<sub>1</sub> · U<sub>N,20,j</sub> (e<sub>1</sub> = 1 pro 18–22 °C), shora omezený vzorcem (6) přílohy č. 1, který se u oken uplatní při velkém podílu prosklení svislých konstrukcí. Čísla z tabulky zdroje 20685 pro novostavbu: stěna 0,21, střecha 0,17, podlaha a stěna k zemině 0,32, strop k nevytápěnému prostoru 0,42, okno 1,05 W/(m²·K); aritmeticky jde přesně o 0,7 × U<sub>N,20</sub> (0,30; 0,24; 0,45; 0,60; 1,5), přičemž hodnoty U<sub>N,20</sub> pocházejí z ČSN 73 0540-2 a zde je uvádí jen zdroj 20685 *(needs second source)*.
- **Přirážka na tepelné vazby** 0,02 W/(m²·K).
- **Vytápění:** referenční účinnost zdroje 92 %, distribuce 90 %, sdílení 88 % (zdroj 20685). Podle zdroje 20685 tyto účinnosti odpovídají vysokoteplotní soustavě s radiátory s termostatickými hlavicemi a izolovanými rozvody převážně uvnitř obálky (souhrnná účinnost cca 73 %); vyhláška sama typ soustavy nepopisuje.
- **Teplá voda:** účinnost zdroje 88 %.
- **Větrání:** u obytných zón je referenční zpětné získávání tepla **0 %**, tj. referenční dům větrá přirozeně; instalace rekuperace tedy dům oproti referenci zlepšuje. Referenční měrný příkon ventilátoru 1 500 W·s/m³ (zdroj uvádí snížení z 1 750).
- **Obnovitelné zdroje:** vyrobená elektřina Q<sub>el,R</sub> = 0 a využitá energie slunce, větru, vody a geotermální energie Q<sub>env,R</sub> = 0. Referenční dům nemá fotovoltaiku ani tepelné čerpadlo, takže každý takový prvek ve vašem domu se počítá jako plus.
- **Osvětlení:** referenční příkon 0,032 W/(m²·lx) × korekční činitel 1,7 (kompaktní zářivky) pro obytné zóny; LED osvětlení je tedy lepší než reference.
- Okenice se v referenční budově nepředpokládají (tepelný odpor 0), vliv okenic lze v hodnocené budově zohlednit.

Důležitá poznámka zdroje: změny referenčních parametrů se nedají hodnotit po jednom, u většiny nových budov podle autora nevedou k nutnosti víc úsporných opatření než dříve (zdroj 20685) *(needs second source)*. Jde o názor autora k návrhu 2020 vůči vyhlášce 78/2013.

## Proč rozhoduje zdroj energie — faktory primární energie
**Primární energie z neobnovitelných zdrojů** = dodaná energie na patě domu × faktor daného energonositele. Faktor vyjadřuje, kolik neobnovitelné primární energie je potřeba na získání jedné kWh u vás doma (účinnost těžby, přeměny a distribuce; u elektřiny také energetický mix), není to environmentální hodnocení a nezohledňuje emise ani vliv na zdraví (zdroj: https://www.tzb-info.cz/energeticka-narocnost-budov/20716-novela-vyhlasky-c-78-2013-sb-cast-3-nastaveni-faktoru-primarni-energie-z-neobnovitelnych-zdroju). Výpočet jako součet součinů dodané energie a faktorů stanoví § 5 odst. 1 vyhlášky. Směrnice (EU) 2018/844 z tohoto ukazatele dělá hlavní ukazatel energetické náročnosti (zdroj 20716).

Platné faktory (po novele 222/2024 Sb.) jsou v tabulce na stránce [[Vyhlaska-264-2020-vypocet-a-tridy]]: zemní plyn 1,0; elektřina 2,1; pelety, kusové dřevo, štěpka 0,1; energie okolního prostředí 0; elektřina dodaná mimo budovu −2,1.

### Co z toho plyne pro jednotlivé zdroje
Odvozeno z uvedených faktorů a z toho, že referenční budova počítá vytápění a teplou vodu s faktorem 1,0 (plyn) a ostatní spotřeby s 2,1 (tab. 4 přílohy č. 1, viz [[Vyhlaska-264-2020-vypocet-a-tridy]]). U novostavby (budova s téměř nulovou spotřebou od 1. 1. 2022) se referenční primární energie navíc snižuje o ΔE<sub>p,R</sub> podle **tabulky 6** přílohy č. 1 (tab. 5 pro tento sloupec odkazuje na tab. 6): u obytné zóny 20–50 % (energeticky vztažná plocha ≤ 120 m²) nebo 20–60 % (> 120 m²) podle měrné potřeby tepla na vytápění referenční budovy, lineárně interpolováno. Hodnota 25 % z tab. 5 platí jen pro dokončenou budovu a její změnu. Požadavek na primární energii nové stavby je tedy přísnější, než by odpovídalo samotným referenčním účinnostem a faktorům:
- **Plynový kondenzační kotel** má faktor 1,0, tedy stejný jako referenční vytápění; samotný plyn třídu B nezaručí a kvůli snížení ΔE<sub>p,R</sub> musí dům s plynem referenci překonat účinností soustavy, obálkou a doplňky. Podle Ing. Miroslava Urbana, Ph.D. z FSv ČVUT (zdroj 27911) po novele 2024 lépe vychází i plynový kotel kombinovaný s větráním se zpětným získáváním tepla.
- **Přímé elektrické vytápění** je nejhorší: faktor 2,1 oproti referenčnímu 1,0 pro vytápění.
- **Tepelné čerpadlo:** do dodané energie se počítá i energie okolního prostředí (§ 4 odst. 9 písm. d), ale její faktor je 0, takže primární energii tvoří jen elektřina na pohon × 2,1. Podle Ing. Urbana (zdroj 27911) díky snížení faktoru elektřiny nyní **lépe vycházejí tepelná čerpadla s přirozeným větráním**.
- **Biomasa** (pelety, kusové dřevo, štěpka) má faktor 0,1, tedy téměř nulový příspěvek k neobnovitelné primární energii; je to nejsilnější páka na tento ukazatel, ale ne na celkovou dodanou energii.
- **FVE** snižuje množství energie odebrané ze sítě a přebytek dodaný mimo budovu se odečítá faktorem −2,1, v rozsahu podle § 5 odst. 2 písm. b) a přílohy č. 6 (do primární energie budovy nejvýše do výše její celkové roční dodané energie, bod 8 přílohy č. 6; ověřeno v e-Sbírce, viz [[Vyhlaska-264-2020-vypocet-a-tridy]]). Referenční budova FVE nemá, takže jde o čistý přínos. Autor 20716 uvádí, že kvůli stabilitě faktoru elektřiny bude i nadále nutné snižovat primární energii pomocí **lokálních OZE na budově**.
- **Dálkové teplo:** faktor 0,1 / 0,7 / 1,3 podle účinnosti a podílu OZE soustavy; v praxi je problém zjistit konkrétní soustavu (zdroj 27911: neexistuje jednotná databáze, plánuje se faktor pro každou teplárnu zvlášť).

### Orientační ilustrace (vlastní výpočet z faktorů, ne údaj ze zdroje)
Na 1 kWh tepla na vytápění: referenční budova ≈ 1,0 / 0,92 (zdroj) / 0,9 / 0,88 ≈ 1,37 kWh primární energie (zjednodušeně, bez dalších ztrát). Tepelné čerpadlo se sezónním topným faktorem 3 a stejnými ztrátami distribuce a sdílení ≈ 2,1 / 3 / 0,9 / 0,88 ≈ 0,88. Ilustrace nezahrnuje snížení referenční hodnoty o ΔE<sub>p,R</sub> (tab. 6), takže výsledný požadavek pro novostavbu je nižší než 1,37. Hodnota topného faktoru je zde jen příklad; skutečný dům počítá energetický specialista podle ČSN EN 15316 a hodinového kroku.

## Faktory v návrhu 2020 a v platném znění (rozpor vyřešen)
Zdroj 20716 (návrh z ledna 2020, před schválením) uvádí **elektřinu 2,6**, **dřevěné peletky 0,2**, zemní plyn 1,0, elektřina dodaná mimo budovu −2,6, teplo dodané mimo budovu −1,3 a soustavy zásobování teplem 0,2 / 0,9 / 1,3 (účinná >80 % OZE / ≤80 % OZE / ostatní). Platná tabulka po novele 222/2024 Sb. (stránka [[Vyhlaska-264-2020-vypocet-a-tridy]]) má elektřinu **2,1**, pelety **0,1**, elektřinu mimo budovu −2,1 a soustavy 0,1 / 0,7 / 1,3. Zdroj 27911 potvrzuje, že novela 222/2024 faktory výrazně změnila a snížený faktor elektřiny zvýhodnil tepelná čerpadla. Rozpor se vysvětluje časem (návrh 2020 vs. znění 2024), ne chybou; pro výpočet použít 2,1 a hodnoty z 2020 neuvádět jako platné. Platné hodnoty potvrzuje text přílohy č. 3 v e-Sbírce (https://e-sbirka.gov.cz/sb/2024/222). Zdroj 20716 dále uvádí původní hodnotu elektřiny 3,0 (neobnovitelná primární energie ve vyhlášce 78/2013), ze které návrh 2020 snižoval na 2,6.

## Hranice tříd A–G: ověření sloupců přílohy č. 2
Přiřazení sloupců tabulky tříd je ověřeno podle záhlaví přílohy č. 2 v e-Sbírce (https://e-sbirka.gov.cz/sb/2020/264); tabulka a hranice třídy B (1,2 × E<sub>R</sub> pro primární energii) jsou na stránce [[Vyhlaska-264-2020-vypocet-a-tridy]]. Zdroje 20685, 20716 ani 27911 tabulku tříd nerozebírají.

## Plánované zpřísnění (EPBD IV)
Podle zprávy z konference TZB-info o PENB 2024 (zdroj: https://www.tzb-info.cz/energeticka-narocnost-budov/27911-hodnoceni-energeticke-narocnosti-budov-v-kontextu-revidovane-epbd-iv-a-zmen-vyhlasky-264-2020-sb, datum 3. 1. 2025). Jde o směrnici (EU) 2024/1275 (EPBD IV); česká transpozice není v účinnosti, data níže jsou převzata z reportu, ne z textu směrnice *(needs law verification)*:
- **od roku 2028** mají nové veřejné budovy vznikat ve standardu ZEB (budova s nulovými emisemi), **od roku 2030** se povinnost týká všech budov; definice ZEB se má metodicky upřesnit, nepůjde o „absolutní nulu“ (Ing. Čejka: „evoluci, ne revoluci“), důraz na snížení potřeby primární energie a OZE;
- **uhlíková stopa budovy (GWP)** má být podle reportu od roku 2030 součástí PENB „pro všechny budovy“ (zda jde jen o nové budovy, ověřit v čl. 7 směrnice); chybí národní data o materiálech, připravuje se strategie a národní databáze LCA;
- **ukazatel připravenosti na chytrá řešení (SRI)**, výsledek v procentech;
- **renovační pasy** (zpracovávané autorizovanými osobami), SFŽP plánoval web pro první vlnu v 1.–2. čtvrtletí 2025.
Pro dům stavěný dnes z toho plyne: standard dnešní novostavby (NZEB od 1. 1. 2022) nemusí k roku 2030 stačit; konkrétní národní provedení zdroj neuvádí.

## Open questions
- Přesné hodnoty E<sub>R</sub> v kWh/(m²·rok) pro typický rodinný dům (vyhláška je neuvádí, počítají se pro konkrétní dům).
- Jaká třída vychází pro dům s TČ, rekuperací a FVE proti plynovému domu se stejnou obálkou (potřebuje výpočet, ne odhad).
- Zda a jak se národně provede zpřísnění po EPBD IV pro rodinné domy (transpozice a termín); data ZEB 2028/2030 a GWP 2030 ověřit v čl. 7 směrnice (EU) 2024/1275 na EUR-Lex (při této revizi se text nepodařilo načíst).

<!-- nerd:links -->
## See also

- [[PENB-povinnost-a-cena-prakticky]]
- [[Vyhlaska-264-2020-vypocet-a-tridy]]
- [[Zatepleni-a-cesty-ke-tride-B-naklady]]
<!-- /nerd:links -->
