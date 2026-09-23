# Podlažnost a tepelné ztráty

> Vliv počtu nadzemních podlaží a tvaru půdorysu na měrnou potřebu tepla na vytápění, podle parametrické studie ČVUT (Monte Carlo model RD).
>
> **Celá stránka stojí na jedné studii** — Ing. Jan Antonín, Pavel Kopecký, ČVUT, Fakulta stavební, katedra Konstrukcí pozemních staveb, publikováno na TZB-info **18. 1. 2010**. Je to primární zdroj pro svůj vlastní model a jeho výsledky, ale druhý nezávislý model to nenahrazuje.
>
> ⚠️ **Studie je z roku 2010** a její seznam literatury odkazuje na ČSN EN ISO 13790 (2009), TNI 730329 (2009) a ČSN 730540-2 (2007). Fyzika geometrie obálky se od té doby nezměnila, takže směr výsledku platí; požadavkové hodnoty a klasifikační hranice citované v článku jsou ale 16 let staré a nesmí se z této stránky přebírat jako aktuální požadavek.
>
> Směr výsledku je zásadní pro rozhodnutí o podlažnosti a vysvětluje zdánlivý rozpor mezi marketingovými zdroji — viz
> [Bungalov vs. patrový dům, § Tepelné ztráty](BungalovVsPatrovyDum.md).

## Key facts

- Ve studii (parametrický model o 18 vstupních parametrech, simulace Monte Carlo se vzorkováním metodou latinských čtverců, měsíční výpočet dle EN ISO 13790 v souladu s TNI 730329) patří počet nadzemních podlaží mezi tři nejvýznamnější parametry ovlivňující měrnou potřebu tepla na vytápění — spolu se součinitelem prostupu tepla konstrukcí (U_kon) a oken (U_w) (source: https://stavba.tzb-info.cz/nizkoenergeticke-stavby/6182-tepelna-bilance-pasivnich-a-nizkoenergetickych-rodinnych-domu-parametricka-studie)
- **Jak bylo to pořadí významnosti získáno a proč se na něj nelze plně spolehnout**: ze střední hodnoty Pearsonova korelačního koeficientu mezi vstupem a sledovanou veličinou. Studie k tomu sama dodává, že jakmile se z modelovaného souboru vybere jen určitá skupina objektů (tj. zúží se rozsah některého vstupu), *„stane se určitý vstupní parametr nedůležitým, jiný naopak nabude na významu“*. Pořadí tedy platí pro celý rozsah tab. 1, ne pro konkrétní zadání jednoho klienta (source: tamtéž)
- **Při stejném objemu budovy** má vyšší počet nadzemních podlaží **nepříznivý** vliv na průměrný součinitel prostupu tepla U_em — opačně než objem, kde vyšší objem je příznivý; vliv počtu podlaží je výraznější. Citace ze zdroje: *"Objekty o více nadzemních podlažích jsou potom z tohoto pohledu oproti jednopatrovým budovám znevýhodněny."* Platí pro čtvercový půdorys a konstantní objem — **ne** pro srovnání při stejné užitné ploše, kde vychází patrový dům lépe (menší celková obálka). Grafy, ze kterých závěr vychází, jsou navíc spočteny pro **izolační standard nízkoenergetického RD (NERD)** a model připouští jen **1 až 3 nadzemní podlaží** (tab. 1), takže výsledek je ověřen právě na rozsahu, který volba bungalov/patro potřebuje *(needs second source — jediná studie a jedna autorská skupina)* (source: tamtéž)
- Důvod: s rostoucím počtem podlaží při daném objemu roste podíl prosklených fasád vůči ploše střechy a podlahy, které mají příznivější součinitel prostupu tepla (source: tamtéž)
- Členitost povrchu (faktor f_A) má na měrnou potřebu tepla výrazně menší vliv než počet podlaží (source: tamtéž)

## Faktory geometrie použité v modelu

Model popisuje geometrii budovy dvěma bezrozměrnými faktory (při zachování objemu):

- **f_AP — faktor půdorysného tvaru**: vyjadřuje zvýšení obalové plochy objektu způsobené odklonem půdorysu od referenčního čtverce. Rozsah v modelu 0–1, se zavedeným omezením minimální šířky budovy 5,0 m (tab. 1 zdroje).
- **f_A — faktor členitosti povrchu**: vyjadřuje poměrné zvýšení plochy obálky budovy při zachování podlahové plochy i objemu. Rozsah v modelu 1–1,3; pro velmi členitý objekt se hodnota pohybuje okolo 1,30 (source: tamtéž).

## Příklad z citlivostní analýzy

Při kombinaci U_w = 1,20 W/(m²K) a U_kon = 0,20 W/(m²K) není podle modelu prakticky možné splnit požadavek na U_em pro pasivní rodinný dům (source: tamtéž). **Pozor na to, co je to za bod**: U_w = 1,20 je horní (nejhorší) mez vlastního rozsahu modelu pro okna (0,70–1,20) a U_kon = 0,20 je střed rozsahu 0,10–0,30. Je to tedy pesimistická kombinace na kraji rozsahu, ne typický případ — nelze z něj dělat obecné „na pasivní standard okna nestačí“. Tyto dvě hodnoty jsou vstupy modelu, **ne citace normy**; článek k nim pouze poznamenává, že "odpovídá přibližně hodnotám doporučeným normou", a v seznamu literatury odkazuje na **ČSN 730540-2 ve vydání z roku 2007** *(needs second source — zastaralé vydání normy; doporučené hodnoty je nutno před použitím zkontrolovat proti aktuálnímu vydání)*. Žádná hodnota na této stránce není citována z placeného textu ČSN.

V případové studii, kdy je předem znám pouze součinitel prostupu tepla konstrukcí (U_kon = 0,150–0,175 W/(m²K)) a ostatní parametry (vč. počtu podlaží, tvaru, počtu osob, rekuperace) se pohybují v obecných mezích modelu, lze s pravděpodobností cca 98 % tvrdit, že měrná potřeba tepla na vytápění bude pod 50 kWh/(m².a) (source: tamtéž).

## Open questions

- Charakteristika "U_w = 1,20 / U_kon = 0,20 odpovídá přibližně doporučeným hodnotám normy" je tvrzení článku, který odkazuje na ČSN 730540-2 ve vydání 2007. Před použitím v B2 je nutno zkontrolovat aktuální vydání — z placeného textu normy se na tuto stránku žádná hodnota přebírat nesmí.
- Celá stránka má jediný zdroj. **Studie sama uvádí, že model byl verifikován proti jinému parametrickému modelu, který nezávisle vyvinul Pavel Kopecký, a že se pro srovnatelné vstupy oba modely dobře překrývají** — to je věcně cenné, ale jako druhý zdroj to neplatí: Kopecký je spoluautorem téhož článku a téže katedry, takže jde o vnitřní verifikaci, ne o nezávislé potvrzení. Chybí tedy stále druhý výpočet vlivu počtu podlaží na U_em od jiné skupiny; na tomto výsledku stojí i rozhodnutí sporu na stránce Bungalov vs. patrový dům.
- Studie je z roku 2010 a pracuje s ČSN 730540-2 (2007). Pro fázi B2 je třeba dohledat, zda se od té doby změnily požadavkové hodnoty U_em pro NERD a pasivní RD — směr vlivu podlažnosti tím zůstane nedotčen, ale poloha šedé („nesplní požadavek“) oblasti v grafech se mohla posunout.

## Sources

- https://stavba.tzb-info.cz/nizkoenergeticke-stavby/6182-tepelna-bilance-pasivnich-a-nizkoenergetickych-rodinnych-domu-parametricka-studie (18. 1. 2010) — Ing. Jan Antonín, Pavel Kopecký, ČVUT, Fakulta stavební, katedra Konstrukcí pozemních staveb; parametrická studie (Monte Carlo model RD, 18 vstupů), vliv počtu podlaží a tvaru na tepelnou bilanci. Jediný zdroj této stránky s výpočtovým modelem.
