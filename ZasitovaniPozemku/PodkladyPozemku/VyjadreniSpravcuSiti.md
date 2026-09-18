# Vyjádření k existenci sítí — postup a role DTM

> Jak stavebník zjišťuje existenci inženýrských sítí na pozemku a získává vyjádření správců sítí, a jaká je role Digitální technické mapy (DTM), Portálu DMVS a Portálu stavebníka v tomto procesu.

Část této stránky (sekce "Postup přes Portál DMVS" níže) vychází z vlastní metodické dokumentace ČÚZK (DTMwiki, provozovatel IS DMVS) k jeho vlastnímu systému — jde o autoritu dokumentující sama sebe, fakta proto nejsou tagována *(unverified)* (source: https://dtmwiki.cuzk.gov.cz/02_sprava/03_informace_pro_su/02_zjisteni_vlastniku_dti, stav "hotovo", projednáno 2025-06-17, poslední úprava 2025-06-19).

## Klíčová fakta

- Součástí žádosti o povolení záměru jsou vyjádření vlastníků veřejné dopravní nebo technické infrastruktury uvedených v digitální technické mapě (§ 184 odst. 2 písm. f) zák. č. 283/2021 Sb.) — stavebník tedy musí sítě v území zjistit a vyjádření jejich vlastníků získat ještě před podáním žádosti (source: https://e-sbirka.gov.cz/sb/2021/283; https://www.dtmcr.cz/clanky/vyjadrovani-k-existenci-siti)
- Oslovují se vlastníci infrastruktury uvedení v DTM; za vlastníka jedná jeho správce nebo provozovatel v rozsahu, v jakém plní editační povinnost podle seznamu editorů DTM krajů (§ 181 odst. 4 zák. č. 283/2021 Sb.) (source: https://e-sbirka.gov.cz/sb/2021/283; https://www.dtmcr.cz/clanky/vyjadrovani-k-existenci-siti)
- Lhůta: vlastník infrastruktury vydá vyjádření do 30 dnů, ve zvlášť složitých případech do 60 dnů ode dne doručení úplné žádosti (§ 181 odst. 1 zák. č. 283/2021 Sb.); součástí žádosti je vždy dokumentace pro povolení záměru (§ 180 odst. 3) (source: https://e-sbirka.gov.cz/sb/2021/283)
- Komerční nástroj pro zjišťování existence sítí a hromadné podání žádostí o vyjádření je podle provozovatele dtmcr.cz systém "Mawis UtilityReport" *(needs second source)* (source: https://www.dtmcr.cz/clanky/vyjadrovani-k-existenci-siti)

## Plánovaný vs. současný stav

Podle tohoto zdroje je záměrem státu **v budoucnu** digitalizovat a automatizovat proces stavebního řízení pod připravovaným Portálem stavebníka, který by měl nahradit/sjednotit služby dnes poskytované systémem Mawis UtilityReport a jednotlivými DTM krajů, měst a obcí do jediného podkladu pro rozhodování ve stavebním řízení (source: https://www.dtmcr.cz/clanky/vyjadrovani-k-existenci-siti). Zdroj (bez uvedeného data) popisuje **plán**. Zákon situaci upřesňuje: Portál stavebníka podávání žádostí vlastníkům infrastruktury umožňuje (§ 268 odst. 1 písm. b) zák. č. 283/2021 Sb.), ale ustanovení o podání žádosti přes portál a o doručování žádosti i vyjádření přes datové rozhraní portálu (§ 180 odst. 2, § 181 odst. 2 a 3) se v přechodném období **do 31. 12. 2027** nepoužijí (§ 334b odst. 1 a 2) (source: https://e-sbirka.gov.cz/sb/2021/283). Vyjádření jednotlivých vlastníků sítí se tedy stále získávají — portál je nenahrazuje, nanejvýš slouží jako kanál pro jejich podání.

DTM krajů (a nad nimi centrální IS DMVS, který má zveřejňovat data DTM krajů) má podle zdroje stavebníkovi zjednodušit orientaci tím, že se může zabývat jen sítěmi uvedenými v DTM kraje.

## Postup přes Portál DMVS (podle metodiky ČÚZK)

Podle metodiky ČÚZK (stav zpracování "hotovo", projednáno 17. 6. 2025) lze žádost o vyjádření vlastníka veřejné dopravní nebo technické infrastruktury podat prostřednictvím Portálu stavebníka a existence sítí se zjišťuje z Portálu DMVS a z DTM kraje — sdělení o existenci sítí už podle nového stavebního zákona není samostatnou součástí vyjádření.

Rozpor s komerčním zdrojem dtmcr.cz ("teprve plán") je vyřešen znění zákona účinným od 11. 6. 2026: podání přes portál umožňuje § 268 odst. 1 písm. b), ale § 180 odst. 2 (podmínky podání přes portál) a § 181 odst. 2 a 3 (doručení žádosti okamžikem odeslání, doručení vyjádření vložením do evidence stavebních postupů) se do 31. 12. 2027 nepoužijí (§ 334b odst. 1 a 2 zák. č. 283/2021 Sb.) (source: https://e-sbirka.gov.cz/sb/2021/283). V přechodném období tedy nelze spoléhat na to, že žádost odeslaná přes portál je vlastníkovi sítě doručena — doručení je třeba ověřit u konkrétního vlastníka.

Právní opora procesu (citace dle ČÚZK metodiky; § 180, § 181 a § 184 ověřeny v e-Sbírce, § 168 SZ a § 4b, § 4d zákona o zeměměřictví jen zprostředkovaně *(needs law verification)*):

- § 168 stavebního zákona (č. 283/2021 Sb.) — vlastník technické infrastruktury má povinnost vést evidenci jí vlastněné infrastruktury a bezplatně na žádost sdělit informace o podmínkách napojení, o ochranných a bezpečnostních pásmech a o základních podmínkách provádění činnosti v těchto pásmech.
- § 4b zákona o zeměměřictví — obsahem DTM jsou i údaje o dopravní a technické infrastruktuře (druhy, umístění, průběh, vlastnosti, ochranná a bezpečnostní pásma, záměry na změny); údaje zapisuje editor, kterým je ze zákona vlastník TI (může tuto povinnost smluvně přenést na správce/provozovatele/jinou osobu).
- § 180–181 stavebního zákona — žádost o vyjádření vlastníka veřejné dopravní nebo technické infrastruktury; lze podat přes Portál stavebníka (s omezením podle § 334b odst. 2 do 31. 12. 2027, viz výše); za vlastníka jedná jeho správce/provozovatel v rozsahu editační povinnosti podle seznamu editorů DTM krajů.
- § 4d odst. 3 písm. c) a d) zákona o zeměměřictví — seznam vlastníků/správců/provozovatelů (editorů) DTI je veden jako součást DMVS a obsahuje i vymezení území jejich působnosti.
- § 184 odst. 2 písm. f) stavebního zákona — vyjádření vlastníků veřejné dopravní nebo technické infrastruktury uvedených v digitální technické mapě je povinnou součástí žádosti o povolení záměru.
- Kompletní "Stanovisko k vyjádření vlastníka veřejné dopravní nebo technické infrastruktury" je dostupné na webu Ministerstva pro místní rozvoj (MMR) — konkrétní URL zdroj neuvádí.

Postup zjištění okruhu vlastníků/vyjadřovatelů DTI ve vybraném území (Portál DMVS):

1. Přihlášení do Portálu DMVS přes JIP/KAAS (nutné mít nastavené přístupové role — návody na webu ČÚZK).
2. V menu vybrat "Dopravní a technická infrastruktura" → "Zjištění území správců dopravní a technické infrastruktury v definovaném území".
3. Zvolit "Žádost o zjištění území správců dopravní a technické infrastruktury".
4. Zadat název záměru a vybrat území — buď zakreslením polygonu v mapě (max. 5 ha na jedno zakreslení, limit vymezeného území 100 ha), nebo přímým výběrem katastrálního území a čísel parcel.
5. Potvrdit vybrané území tlačítkem "POKRAČOVAT".
6. Zvolit způsob zaslání informace o výsledku (např. e-mail).
7. Odeslat žádost tlačítkem "ODESLAT".
8. Výsledkem je výpis vlastníků/vyjadřovatelů DTI v zadaném území včetně kontaktů, stažitelný jako PDF; u každé části DTI je označení "Validní", "Ochranná pásma" nebo "Nevalidní".

Systém nově (poznámka k funkcionalitě) ověřuje nejen průnik zájmového území s vymezenými částmi DTI, ale i to, zda jsou pro danou kombinaci skupina/vlastník/správce/provozovatel v DTM kraje reálně vložena data o objektech a zařízeních DTI či jejich ochranných pásmech. Výsledné skupiny: zelená (vlastník má v území vložená data o objektech/zařízeních DTI), oranžová (vlastník má v území jen ochranné/bezpečnostní pásmo), šedá (vlastník v území nemá žádnou síť).

Konkrétní polohu sítí lze navíc ověřit v mapovém portálu DMVS nebo ve veřejných mapách jednotlivých DTM krajů (odkazy na stránkách ČÚZK); veřejně přístupné prohlížecí služby ale neobsahují neveřejná data.

## Příklad konkrétního správce sítě: CETIN

CETIN provozuje vlastní telekomunikační síť (SEK) a na svém webu nabízí samostatný online formulář "Vyjádření k existenci sítí" pro žádost o polohu svých tras — popis vychází přímo z formuláře CETIN, který je sám sobě zdrojem (source: https://www.cetin.cz/kontakty/vyjadreni-k-existenci-siti).

Formulář rozlišuje tři typy požadavku: nové vyjádření o poloze SEK, informace/stížnosti/připomínky k již vydanému vyjádření, a všeobecné dotazy/stížnosti/připomínky k vyjadřování o poloze SEK (včetně určení DPH dle stáří sítě). Žadatel vyplňuje kontaktní údaje (jméno, telefon, e-mail) a lokalizaci pozemku (kraj, okres, město, ulice, číslo popisné, PSČ), a pro upřesnění existujícího vyjádření navíc katastrální území, název stavby a číslo parcely. Formulář je chráněn CAPTCHou.

Stránka neuvádí lhůtu vydání vyjádření ani cenu/poplatek za jeho vydání. Zákonná lhůta je 30, resp. 60 dnů (§ 181 odst. 1 zák. č. 283/2021 Sb., viz výše); cenu je nutné zjistit jinde (např. v obchodních podmínkách CETIN nebo přímo dotazem).

## Poznámka ke zdroji

dtmcr.cz je marketingová stránka soukromé společnosti (HRDLIČKA spol. s r.o.), která nabízí komerční služby okolo DTM — není to úřední zdroj. Fakta z ní jsou na této stránce ponechána jen tam, kde je potvrzuje zákon nebo metodika ČÚZK; zbytek nese značku *(needs second source)*.

## Otevřené body

- Ověřit v praxi (2026), kteří vlastníci sítí mají zřízen přístup k datovému rozhraní Portálu stavebníka (§ 268 odst. 2) — do 31. 12. 2027 se doručovací pravidla portálu nepoužijí (§ 334b odst. 2), takže u ostatních je nutné žádat přímo.
- Zjistit případný poplatek za vyjádření CETIN (formulář ho neuvádí).
- Dohledat celý text "Stanoviska k vyjádření vlastníka veřejné dopravní nebo technické infrastruktury" na webu MMR (konkrétní URL) a ověřit § 168 SZ a § 4b, § 4d zákona o zeměměřictví v plném znění (zde citovány jen zprostředkovaně přes metodiku ČÚZK).
- Zjistit, kteří konkrétní správci sítí (elektro, plyn, CETIN, vodovody/kanalizace) jsou/nejsou zatím evidováni v DTM ČR — mimo DTM může být nutné žádat přímo.

## Zdroje

- https://e-sbirka.gov.cz/sb/2021/283 — zák. č. 283/2021 Sb., znění účinné od 11. 6. 2026: § 180, § 181, § 184 odst. 2, § 268, § 334b
- https://www.dtmcr.cz/clanky/vyjadrovani-k-existenci-siti — popis procesu vyjadřování k existenci sítí a plánované role Portálu stavebníka a DTM krajů (komerční zdroj, HRDLIČKA spol. s r.o.)
- https://dtmwiki.cuzk.gov.cz/02_sprava/03_informace_pro_su/02_zjisteni_vlastniku_dti — metodika ČÚZK: postup zjištění okruhu vlastníků DTI přes Portál DMVS, právní opora (§ 168, § 180–181, § 184 SZ, § 4b, § 4d zákona o zeměměřictví)
- https://www.cetin.cz/kontakty/vyjadreni-k-existenci-siti — vlastní online formulář CETIN pro žádost o vyjádření k existenci sítí (SEK)

<!-- nerd:links -->
## See also

- [[PortalStavebnika]]
- [[PravniRamec]]
<!-- /nerd:links -->
