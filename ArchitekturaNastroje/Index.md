# Nástroje pro kreslení a vizualizaci architektonické studie RD agentem

Posouzení nástrojů, kterými LLM agent reálně vyprodukuje půdorysy, řezy, pohledy, situaci a vizualizace v měřítku. Kritéria: instalovatelnost bez zásahu klienta, skriptovatelnost z agenta, dodržení měřítka a kót, použitelnost výstupu pro navazujícího projektanta, náklad na zprovoznění.

| Stránka | Obsah |
|---|---|
| [IfcOpenShell.md](IfcOpenShell.md) | Python/C++ knihovna nad IFC — autoring, generování 2D výkresů, validace, CLI ekosystém (IfcConvert, IfcCSV, IfcDiff, IfcClash, IfcMCP) |
| [Bonsai.md](Bonsai.md) | Bonsai (dříve BlenderBIM) — nativní IFC autoring a generování výkresů v Blenderu |
| [IfcTester.md](IfcTester.md) | Validace IFC proti IDS, reporty (konzole/JSON/ODS/HTML/BCF) — kandidát na kontrolní krok |
| [FreeCAD-TechDraw.md](FreeCAD-TechDraw.md) | TechDraw Python API — řezy, pohledy, kóty, export DXF/SVG a jeho headless omezení |
| [ezdxf.md](ezdxf.md) | Python knihovna pro čtení/zápis DXF, export do PNG/PDF/SVG, CLI audit |
| [SweetHome3D.md](SweetHome3D.md) | Sweet Home 3D — plug-in API (Java), model vrstva, nasazení pluginu |
| [SweetHome3D-MCP-Server.md](SweetHome3D-MCP-Server.md) | Komunitní MCP plugin — 42 příkazů (stěny, místnosti, kóty, export SVG/PNG/OBJ) přes HTTP |
| [ControlNet-Stable-Diffusion-Rendering.md](ControlNet-Stable-Diffusion-Rendering.md) | ControlNet + Stable Diffusion — renderování ze skic, volba módu, konzistence dávky |
| [ComfyUI-Floorplan-to-3D.md](ComfyUI-Floorplan-to-3D.md) | ComfyUI workflow 2D půdorys → barevný render, modely a hardware |
| [BIM-Formaty-IFC-vs-DWG.md](BIM-Formaty-IFC-vs-DWG.md) | Přehled formátů (IFC, RVT, DWG, COBie, BCF) — pohled třetí strany |
| [StropKvalityLLM.md](StropKvalityLLM.md) | Benchmarky prostorové inteligence LLM/agentů — Blueprint-Bench, RLVR, Sketch2BIM, SVG vs. rastr |

## Doporučený pipeline (jeden)

**IfcOpenShell-Python jako autorská vrstva → IFC jako zdrojový soubor → výkresy generované z modelu → IfcTester/IDS jako kontrola → ControlNet/ComfyUI jen na náladové vizualizace.**

Konkrétně:

1. **Model** — agent staví geometrii skriptem přes `ifcopenshell` (vysokoúrovňové API, čtení/zápis IFC-SPF). Vstupem je strukturované zadání (místnosti, plochy, konektivita), ne volný text.
2. **Výkresy** — 2D výkresy se generují z modelu: IfcOpenShell uvádí generování a anotaci 2D výkresů ze 3D geometrie se zachováním výkresové sémantiky (text, styly čar, šrafy, symboly), Bonsai má generování výkresů mezi funkcemi. Vektorové odvozeniny přes `IfcConvert model.ifc out.svg`.
3. **Předání dál** — `ifccsv -i model.ifc -c plochy.csv -q ".IfcSpace"` pro tabulku ploch, `IfcConvert` pro GLB/OBJ náhled.
4. **Kontrola** — `python -m ifcopenshell.simple_spf`, `python -m ifcopenshell.validate --rules`, `python -m ifctester specs.ids model.ifc -r Html -o report.html`, `ifcdiff` mezi verzemi.
5. **Vizualizace** — až nad hotovým modelem: pohled z modelu (obrys / depth mapa) jde jako control image do ControlNet + Stable Diffusion; fixovaný seed a identický prefix promptu drží konzistenci napříč pohledy.

### Proč tento a ne ostatní

| Kritérium | IfcOpenShell (+Bonsai) | Sweet Home 3D + MCP plugin | FreeCAD TechDraw | ezdxf |
|---|---|---|---|---|
| Instalovatelnost bez zásahu klienta | `pip install ifcopenshell ifctester`; Windows/Mac/Linux/WASM/Docker/AWS Lambda, výslovně i headless serverové nasazení | Nutná instalace desktopové aplikace + ruční kopírování `.sh3p` do plugins složky + restart; nefunguje s Mac App Store buildem ani se starými 32bit instalátory s JRE 1.8 | Instalace FreeCADu; pro export celé stránky navíc potřeba GUI běh | `pip install ezdxf` — nejlevnější, ale sám o sobě nic nemodeluje |
| Skriptovatelnost z agenta | Python API + CLI nástroje (IfcConvert, ifctester, ifccsv, ifcdiff, ifcclash, ifcpatch, ifcedit) + IfcMCP server držící model v paměti mezi voláními | MCP server na `http://127.0.0.1:9877/mcp`, 42 příkazů včetně `add_dimension_line` a `export_svg`; nativní plugin API je ale **Java-only**, vlastní rozšíření = psaní Java pluginu | Python API z maker a konzole; **export celé stránky headless nefunguje** (issue #5710 otevřený, #12144 pro DXF) | Plné Python API + CLI audit |
| Měřítko a kóty | IFC drží metrickou geometrii a sémantiku prvků; kóty a anotace ve výkresové vrstvě | Jednotky v cm, stabilní UUID objektů, kótovací čára s auto-offsetem — pro studii dostačuje | Nejsilnější kótovací sada (délková, úhlová, řetězová, souřadnicová, kóta plochy, šrafy, ISO 286) | Kóty se musí kreslit ručně jako entity |
| Použitelnost pro navazujícího projektanta | IFC otevře libovolný BIM nástroj; otevřený formát pro sdílení napříč platformami | `.sh3d` je formát jedné konzumní aplikace, export jen SVG/PNG/OBJ — projektant z toho model nedostane | DXF/SVG/PDF výkresy, ale bez modelu | DXF = nejběžnější 2D výměna |
| Náklad na zprovoznění | Nízký (pip); největší podíl práce je napsání autorského skriptu | Střední (desktop + plugin + běžící aplikace jako závislost) | Střední až vysoký kvůli GUI/headless komplikacím | Nízký, ale pokrývá jen 2D |

Sweet Home 3D + MCP plugin má smysl jako **rychlý sekundární kanál pro dispoziční skicu a laický 3D náhled klientovi** (agent umí přímo tvořit stěny, místnosti, kóty a exportovat SVG/PNG), ne jako nositel zdrojových dat. FreeCAD TechDraw se hodí, až když bude potřeba klasická výkresová prezentace s plnou kótovací sadou — s vědomím, že export kompletní stránky se musí řešit přes GUI běh nebo skládat z jednotlivých view-exportů. ezdxf je doplněk pro finální DXF, ne autorská vrstva; vlastní dokumentace ho vymezuje jako "ne CAD kernel" a pro CAD skriptování odkazuje na FreeCAD. Generativní obrazové nástroje (ControlNet, ComfyUI workflow) do měřítkové větve nepatří vůbec.

## Realistický strop kvality

Podložený čísly z [StropKvalityLLM.md](StropKvalityLLM.md):

- **Autonomní LLM/agent bez nástrojů a bez zadaných kót je na úrovni náhody.** Blueprint-Bench: většina modelů skóruje na úrovni náhodné baseline nebo pod ní; nad ní statisticky jen GPT-5, Gemini 2.5 Pro, GPT-5-mini a Grok-4; lidský výkon zůstává výrazně nad všemi. Agentní iterativní zpřesňování (Claude Code, Codex CLI) nepřineslo měřitelné zlepšení oproti generování na jeden zátah — Claude Code svůj výstup kontroloval a přesto tvrdil "each room is fully enclosed", i když to nebyla pravda.
- **Obecný model na strukturovaný numerický výstup selhává i s few-shot.** Few-shot baseline na 5-pokojové úloze: Compatibility 2,93, Overlap ~0,55; typické chyby jsou neuzavřené polygony, sebeprůniky a číselný drift ploch.
- **Doménově dotrénovaný model dosáhne řádově lepších čísel, ale pořád ne dokumentace.** SFT+RLVR (best-of-10) na 5–8 místnostech: chyba plochy místnosti 10–12 %, Room ID přesnost 100 %, Overlap 0,03–0,15, Compatibility 0,01–0,15. Autoři sami píší, že výstupy jsou "drafty vyžadující expertní review" — necertifikují předpisy, únikové cesty ani statiku.
- **S člověkem ve smyčce a BIM cílovým formátem lze jít na nulu.** Sketch2BIM: RMSE i MAE u stěn, dveří a oken klesly po dokončení iterací zpětné vazby na 0,00 ft, F1 konvergovalo k ~1,0 do 3–4 iterací; cena je 7 feedback kroků na jeden netriviální půdorys a ve 2 z 10 testů bylo nutné opakovat počáteční extrakci. Pipeline navíc negeneruje schodiště ani MEP.

**Závěr:** počítej se stropem "kvalitní studie jako podklad", ne "stavební dokumentace". Čísla musí do modelu vstoupit jako explicitní zadání (ne být odvozena modelem z obrázků), geometrii musí ověřit nástroj (ne LLM pohledem na výstup) a před předáním projektantovi je nutná lidská kontrola. Odchylka ploch v jednotkách procent je dosažitelná jen proto, že plochy zadáváme a nástroj je počítá zpět — samotný model jich nedosáhne. Pro náladové vizualizace je strop naopak dobrý: uživatelská studie u structure-aware diffusion dala kvalitu obrázků 3,93/5, shodu se vstupní skicou 4,03/5 a přesnost architektonických detailů 3,97/5.

## Zdrojový soubor pro klienta a projektanta

- **Primární: IFC** (IFC4, případně IFC2X3 podle nástroje protistrany). Otevřený formát pro sdílení modelu napříč platformami; IfcOpenShell podporuje IFC2X3/IFC4/IFC4.3 a zapisuje i IFCJSON/IFCXML.
- **Sekundární pro 2D: DXF** (z TechDraw nebo ezdxf) plus **PDF/SVG** pro tisk a náhled — projektant běžně pracuje s DXF, klient chce PDF.
- **Náhledový 3D: GLB nebo OBJ** přes `IfcConvert model.ifc model.glb` — pro klienta bez BIM prohlížeče.
- **Tabulka ploch: CSV/XLSX** přes IfcCSV, generovaná z modelu, ne psaná ručně.
- `.sh3d` jen jako výstup větve Sweet Home 3D, vždy jako doplněk, nikdy jako jediný zdroj.

## Návrh kontroly konzistence výkresů

Kontrola musí být nástrojová a spustitelná ve skriptu po každé generaci. Čtyři vrstvy:

1. **Syntax** — `python -m ifcopenshell.simple_spf model.ifc` (validní SPF, duplicitní ID, hlavička).
2. **Schéma** — `python -m ifcopenshell.validate model.ifc --rules --json` (typy atributů, kardinalita inverzních atributů, express rules). Pozor: dokumentace uvádí, že tato funkce nezachytí některé syntaktické chyby a neimplementuje ověření type/entity/global WHERE rules.
3. **Projektová pravidla přes IDS** — vlastní `specs.ids` (autorovaná programově přes `ifctester.ids`) a `python -m ifctester specs.ids model.ifc -r Html -o report.html`. Sem patří pravidla typu "každý IfcSpace má název a plochu" nebo "každá stěna má Pset_WallCommon.IsExternal". Report jde i jako JSON/ODS/BCF, takže se dá strojově vyhodnotit jako gate.
4. **Regrese mezi verzemi** — `ifcdiff old.ifc new.ifc` po každé změně zadání, `ifcclash` na kolize.

Nad to dvě kontroly nad tabulkou ploch: `ifccsv` vyexportuje plochy z modelu a skript je porovná se zadanými plochami, a stejný CSV je jediným zdrojem čísel do textu studie — číslo se do dokumentu nikdy nepíše ručně.

**Co do kontroly nedávat:** LLM čtoucí vygenerovaný SVG/PNG jako verifikátor topologie. Studie SVG vs. rastr ukazuje, že modely při SVG-only vstupu mylně předpokládaly průchod mezi nesousedícími místnostmi přes zeď — to tvořilo 100 % chybných cest GPT-4o a 92,1 % chybných cest Llamy. Pro inventarizaci místností a popisků je naopak PNG+SVG přínosné (GPT-4o 0,75 → 0,96 u počtu místností na středně složitých plánech).

## Otevřené otázky

- IfcTester ani zdroje k IDS neuvádějí příklad kontroly **kót** nebo tabulky ploch — vrstva 3 výše je návrh, ne doložený postup; je třeba ověřit, co všechno IDS na IfcSpace/quantity dovolí vyjádřit.
- Zdroje nepopisují, jak z IfcOpenShell/Bonsai vygenerovat kompletní výkresový list (rámeček, razítko, měřítko) headless — u FreeCADu je to doložené omezení, u Bonsai neověřeno.
- Není doloženo, zda existuje jiná cesta automatizace Sweet Home 3D než Java plugin / MCP plugin (např. přímá generace `.sh3d` souboru).
- Blueprint-Bench měří rekonstrukci z fotek, ne generování ze zadání — přímé srovnání obou úloh na jednom benchmarku chybí.
