# Nahlížení do katastru a data o parcele

> Jak dálkově zjistit údaje o parcele, stavbě a řízeních vedených v katastru nemovitostí, a jak k nim přistupovat automatizovaně (WFS/API).

Tato stránka vychází z vlastní dokumentace ČÚZK (provozovatele aplikace Nahlížení do KN a katastru nemovitostí) o jeho vlastních službách — jde o autoritu dokumentující sama sebe, fakta o fungování aplikace proto nejsou tagována jako neověřená.

## Klíčová fakta

- Aplikace "Nahlížení do katastru nemovitostí" (nahlizenidokn.cuzk.gov.cz) umožňuje získávat vybrané údaje o parcelách, stavbách, jednotkách a právech stavby evidovaných v katastru nemovitostí, dále informace o stavu řízení pro zápis vlastnických a jiných práv, nebo pro potvrzování geometrických plánů (source: https://nahlizenidokn.cuzk.gov.cz/)
- Nahlížení do KN nevyžaduje registraci a je bezplatné (source: https://nahlizenidokn.cuzk.gov.cz/)
- Aplikace je určena výhradně pro interaktivní práci uživatele — automatizované získávání/vytěžování dat přes ni není dovoleno (source: https://nahlizenidokn.cuzk.gov.cz/)
- Pro automatizovaný přístup k datům KN je k dispozici bezplatné REST API na adrese https://api-kn.cuzk.gov.cz/ (source: https://nahlizenidokn.cuzk.gov.cz/)

## Právní rámec poskytování dat KN

Rozsah a podmínky poskytování údajů z katastru nemovitostí se řídí vyhláškou č. 358/2013 Sb., o poskytování údajů z katastru nemovitostí, v platném znění (source: https://cuzk.gov.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Poskytovani-udaju-z-KN.aspx). Vyhláška je platná, aktuální znění je účinné od 1. 7. 2024; formám dálkového přístupu odpovídají její paragrafy: § 5 "Nahlížení do katastru a poskytování ústních informací", § 11 "Dálkový přístup k údajům katastru za úplatu", § 13 "Bezúplatný dálkový přístup k údajům katastru", § 14a "Bezúplatná webová služba dálkového přístupu", § 15 "Údaje katastru v elektronické podobě" (source: https://e-sbirka.gov.cz/sb/2013/358 — osnova; znění paragrafů zde nebylo čteno).

## Přehled aplikací a webových služeb ČÚZK

Mimo obvyklé formy vydávání informací, výpisů, opisů a kopií na katastrálních pracovištích poskytuje ČÚZK výstupy i přes internet (source: https://cuzk.gov.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Poskytovani-udaju-z-KN.aspx):

- **Nahlížení do KN** — bezplatná aplikace, omezený rozsah informací (viz výše).
- **Dálkový přístup k datům KN (DP)** — placená aplikace s širším rozsahem dat.
- **Webové služby Dálkového přístupu (WSDP)** — placené webové služby.
- **Bezúplatné webové služby Dálkového přístupu (REST API)** — volně dostupné webové služby.
- **Webová služba pro vyhotovitele a ověřovatele geometrických plánů (WSGP)**.
- **WMS služby pro katastrální mapy** a **Webové mapové dlaždicové služby pro katastrální mapu (WMTS KN)**.
- **INSPIRE téma Parcely (CP)** — zahrnuje prohlížecí služby (WMS 1.3.0 a WMS 1.1.1) a stahovací služby (WFS 2.0.0, nebo předpřipravené soubory po katastrálních územích ve formátu GML). Toto je zdroj geometrie parcely dálkovým přístupem.
- **INSPIRE téma Budovy (BU)** — stejná struktura služeb (WMS prohlížecí, WFS 2.0.0/GML stahovací) pro geometrii budov.

Data v elektronické podobě (SPI — soubor popisných informací, DKM — digitální katastrální mapa, rastrová data skenovaných katastrálních map) poskytují v rámci své působnosti jednotlivá katastrální pracoviště; výstupy přesahující rámec jednoho pracoviště zajišťuje ČÚZK, odbor správy dat — vždy jen za legislativně stanovených podmínek.

Datum poslední aktualizace zdrojové stránky: 15. 9. 2026 (source: https://cuzk.gov.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Poskytovani-udaju-z-KN.aspx).

## WFS/INSPIRE služby pro geometrii parcely (Mapový server ČÚZK)

Tato sekce vychází z vlastního rozcestníku ČÚZK (services.cuzk.gov.cz) k jeho mapovému serveru — subjekt dokumentuje sám sebe, fakta proto nejsou tagována jako neověřená (source: http://services.cuzk.gov.cz/).

Všechny služby mapového serveru ČÚZK jsou poskytovány bezúplatně a řídí se Podmínkami poskytování prostorových dat a síťových služeb ČÚZK.

**Neharmonizované služby (specifické pro ČR):**
- Katastrální mapa — prohlížecí služba WMS (`https://services.cuzk.gov.cz/wms/local-km-wms.asp`) a WMTS (JTSK i Google projekce); data ve formátu VFK-ISKN (stavová i změnová, aktualizace měsíčně, dostupnost 4 měsíce zpět), VKM, SHP, DGN, DXF.
- Záznamy podrobného měření změn (ZPMZ) — stahovací služba WFS (`https://services.cuzk.gov.cz/wfs/local-zpmz-wfs.asp`); poskytuje polygony a definiční body zájmových oblastí ZPMZ, stejná data jako v aplikaci Nahlížení do KN.
- Správní jednotky (správní a územní členění státu, obvody katastrálních pracovišť) — WMS (`local-ux-wms.asp`).

**Harmonizované (INSPIRE) služby — relevantní pro geometrii parcely:**
- **Katastrální parcely (téma Cadastral Parcels, CP)** — hranice parcel a hranice katastrálních území. Prohlížecí služba WMS (`https://services.cuzk.gov.cz/wms/inspire-cp-wms.asp`) a stahovací služba WFS (`https://services.cuzk.gov.cz/wfs/inspire-cp-wfs.asp`), případně předpřipravené GML soubory po katastrálních územích.
- **Katastrální parcely — národní rozšíření (Cadastral Parcels Extended, CPX)** — kompletní kresba katastrální mapy; pouze stahovací služba WFS (`https://services.cuzk.gov.cz/wfs/inspire-cpx-wfs.asp`), bez WMS.
- **Budovy (téma Buildings, BU)** — WMS (`inspire-bu-wms.asp`) a WFS (`inspire-bu-wfs.asp`).
- **Adresy (téma Addresses, AD)** — WMS (`inspire-ad-wms.asp`) a WFS (`inspire-ad-wfs.asp`).
- **Správní jednotky (téma Administrative Units, AU)** — WMS (`inspire-au-wms.asp`) a WFS (`inspire-au-wfs.asp`).

INSPIRE harmonizované WFS služby (AD, AU, BU, CP, CPX) podporují dotazy ve formě KVP (key-value pair) i SOAP (od 19. 4. 2022, dle standardu OGC WFS 2.0); přístupové URL pro SOAP jsou odlišné a uvedeny v capabilities dané služby.

Podrobnější informace a metadata k INSPIRE službám jsou na Geoportálu ČÚZK.

## Otevřené body

- Ověřit rozsah a licenční podmínky REST API (https://api-kn.cuzk.gov.cz/) a "Bezúplatných webových služeb Dálkového přístupu (REST API)" — zda se jedná o stejnou službu a zda pokrývá i geometrii parcely, nebo jen atributová data.
- Ověřit znění § 13 a § 14a vyhlášky č. 358/2013 Sb. — přesný rozsah bezplatně poskytovaných dat (zatím ověřeny jen názvy paragrafů).

## Zdroje

- https://e-sbirka.gov.cz/sb/2013/358 — osnova vyhl. č. 358/2013 Sb., o poskytování údajů z katastru nemovitostí (znění účinné od 1. 7. 2024)

- https://nahlizenidokn.cuzk.gov.cz/ — úvodní stránka aplikace Nahlížení do katastru nemovitostí (ČÚZK), popis funkcí a podmínek přístupu
- https://cuzk.gov.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Poskytovani-udaju-z-KN.aspx — přehled ČÚZK: právní rámec (vyhl. č. 358/2013 Sb.) a všechny aplikace/webové služby pro poskytování dat KN, včetně INSPIRE/WFS služeb pro parcely a budovy
- http://services.cuzk.gov.cz/ — rozcestník mapového serveru ČÚZK: konkrétní WMS/WFS/WMTS endpointy pro katastrální mapu, ZPMZ a INSPIRE témata (Parcely, Parcely-rozšíření, Budovy, Adresy, Správní jednotky)
