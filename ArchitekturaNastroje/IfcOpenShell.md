# IfcOpenShell

Fakta na této stránce vychází z vlastní oficiální dokumentace projektu IfcOpenShell (docs.ifcopenshell.org) a webu projektu (ifcopenshell.org) — subjekt dokumentuje sám sebe, tagy `*(unverified)*` proto nejsou u faktů z těchto zdrojů použity.

## Co to je

IfcOpenShell je open-source softwarová knihovna pro vývojáře a pokročilé uživatele BIM pracující s formátem IFC (Industry Foundation Classes). Kromě C++ a Python API zahrnuje ekosystém nástrojů, zejména IfcConvert (konverze IFC modelů do jiných formátů) a Bonsai (add-on pro Blender poskytující grafickou platformu pro autoring IFC). Podporuje i doplňkové standardy BCF, bSDD a IDS. (source: https://docs.ifcopenshell.org/introduction.html)

## Možnosti

- Prohlížení modelů (prostory, vlastnosti, vztahy), editace a extrakce atributů, přesun objektů a změna geometrie.
- Tvorba nových objektů z knihovních prvků, správa klasifikačních systémů, dokumentů a knihovních referencí.
- Generování 2D výkresů, harmonogramů a tvorba výkresových listů.
- Investigace a editace strukturálních analytických modelů, správa distribučních systémů a portů.
- Tvorba stavebních harmonogramů, kritické cesty a animací sekvencí.
- Tvorba nákladových rozpočtů pomocí vzorců a odvození množství z prvků modelu.
- Detekce kolizí (clash detection) a správa problémů pro koordinaci modelu.

(source: https://docs.ifcopenshell.org/introduction.html)

## Vlastnosti a specifika

- Vyvíjen od roku 2011 komunitou stovek vývojářů; vyučován na řadě univerzit a citován ve stovkách akademických publikací — popisováno jako nejstarší a nejzralejší open-source IFC knihovna.
- Podporované platformy: Windows, Mac Intel, Mac Silicon (M1, M2), Linux, WebAssembly (WASM), Docker, AWS Lambda, Google Colab.
- Vývoj v C++, Pythonu, nebo JavaScriptu (přes Pyodide).
- Všechny nástroje lze používat jako vývojářskou knihovnu, přes CLI, nebo přes grafické rozhraní — vhodné i pro headless serverové nasazení.
- Podporuje schémata IFC2X3, IFC4 a IFC4.3; lze načíst i vlastní (experimentální/draft) schémata za běhu bez rekompilace.
- Vestavěná IFC validace od základní syntaktické validace po detailní kontroly "Where Rule" — jde o stejnou validaci, která pohání oficiální buildingSMART validation engine.
- Čtení a zápis formátů IFC-SPF, IFCJSON, IFCXML, IFCHDF5, MySQL, SQLite.
- Vysokoúrovňové API pro stovky úkolů — např. kopírování objektů, kalkulace nákladů, 4D simulace jedním řádkem kódu.
- Konverze parametrické geometrie na explicitní geometrii pro libovolný CAD systém (booleovské operace, komplexní sweepy).
- Geometrie lze převést na voxely a analyzovat (výška stropu, formwork analýza, únikové vzdálenosti).
- Generování a anotace 2D výkresů ze 3D geometrie se zachováním výkresové sémantiky a propojením modelových dat s výkresovými symboly. Výkresy lze bohatě anotovat textem, styly čar, šrafami a symboly — používá se pro dodání komerčních výkresů projektů.
- Detekce kolizí, porovnání modelů, konverze do více než 10 dalších formátů (DAE, GLB, OBJ, SVG a další). Integrace s IDS, BCF, bSDD.
- Licence: IfcOpenShell a jeho knihovny pod LGPL-3.0-or-later, s výjimkou Bonsai a IfcSverchok, které jsou pod GPL-3.0-or-later.

(source: https://docs.ifcopenshell.org/introduction.html)

## Ekosystém nástrojů (relevantní k výkresům/vizualizaci)

| Nástroj | Popis |
|---|---|
| IfcOpenShell | Jádro knihovny pro C++ vývojáře — parsování schémat, tesselace a zpracování implicitní geometrie. |
| IfcOpenShell-Python | Python bindings k jádru + vysokoúrovňové analytické a autoring funkce. |
| IfcConvert | CLI aplikace pro konverzi IFC geometrie do formátů OBJ, DAE, GLB, STP, IGS, XML, SVG, H5 a IFC. |
| Bonsai | Grafický add-on pro Blender — analýza, autoring a editace IFC, tvorba BIM modelů od začátku. |
| IfcMCP | MCP (Model Context Protocol) server, který zpřístupňuje IfcOpenShell query/edit nástroje AI coding assistentům. Model se načte do paměti a zůstává tam napříč voláními nástrojů, takže mezi operacemi není potřeba I/O souborů. |
| IfcTester | Autorování a čtení Information Delivery Specification (IDS) souborů; validace IFC modelů proti IDS a generování reportů; funguje z CLI, jako webová appka i jako knihovna. |
| IfcQuery | CLI nástroj pro dotazování a inspekci IFC modelů — prostorová hierarchie, inspekce prvků, traversování vztahů, clash detection, dokumentace schématu, harmonogramy prací a nákladů. |
| IfcClash | CLI nástroj a knihovna pro clash detection na jednom nebo více IFC modelech, definice clash setů s filtry přes IFC query syntax. |
| IfcCSV | Zobrazení a editace IFC dat přes tabulky/tabulková data (CSV, ODS, XLSX, Pandas DataFrames, Python listy). |
| IfcDiff | CLI nástroj a knihovna pro porovnání změn mezi dvěma IFC modely. |
| IfcPatch | CLI nástroj a knihovna pro spouštění předdefinovaných úprav IFC souboru ("patch recipe") — vhodné pro datové pipeline nebo hromadné opravy. |
| IfcEdit | CLI wrapper pro všechny mutační funkce ifcopenshell.api — procházení dostupných API modulů, dokumentace ke každé funkci, spouštění libovolné API funkce nad IFC souborem z příkazové řádky. |

(source: https://docs.ifcopenshell.org/introduction.html)

## Ukázky CLI/Python použití (z webu projektu)

Web projektu (ifcopenshell.org) uvádí tyto konkrétní příklady příkazů relevantní pro pipeline výkresů/kontrol:

```
# Konverze modelu do jiných formátů
IfcConvert model.ifc model.glb
IfcConvert model.ifc model.dae
IfcConvert --model-offset "10000;10000;0" model.ifc model.dae

# Kontrola BIM požadavků (IDS) a report
ifctester specs.ids model.ifc
ifctester -r Html -o out.html test.ids bldg.ifc

# Porovnání modelů
ifcdiff old.ifc new.ifc

# Rozpis objektů do tabulky
ifccsv -i input.ifc -c out.csv -q ".IfcWall"

# Detekce kolizí
ifcclash -o results.json clashsets.json
```

Python příklad načtení a úpravy modelu:
```python
import ifcopenshell
model = ifcopenshell.open('model.ifc')
walls = model.by_type('IfcWall')
walls[0].Name = 'My wall'
model.write('updated-model.ifc')
```

(source: https://ifcopenshell.org/)

## Vestavěná validace modelu (`ifcopenshell.validate`)

Modul `ifcopenshell.validate` slouží k validaci datového modelu IFC. Lze jej spustit z příkazové řádky:

```
python -m ifcopenshell.validate /path/to/model.ifc --rules
```

CLI manuál (`python -m ifcopenshell.validate -h`):
```
usage: validate.py [-h] [--rules] [--json] [--fields] [--spf] files [files ...]

positional arguments:
  files          The IFC file to validate.

options:
  -h, --help     show this help message and exit
  --rules        Run express rules.
  --json         Output in JSON format.
  --fields       Output more detailed information about failed entities (only with --json).
  --spf          Output entities in SPF format (only with --json).
```

Funkce `validate(f, logger, express_rules=False)` pro daný IFC model (soubor nebo cestu k němu) ověří, zda jsou hodnoty atributů entit správně dodány — u každé instance entity kontroluje, že entita není abstraktní, že každá hodnota atributu má správný typ a že inverzní atributy mají správnou kardinalitu. Kontrolují se i simple types, select types, enumerace a agregace. Doporučeno je předat cestu k souboru, aby byly zachyceny i interní C++ chyby z fáze parsování. Poznámka zdroje: některé chyby syntaxe, duplicitní numerické identifikátory nebo neplatné názvy entit tato funkce nezachytává (ty mohou být zalogovány a lze je získat přes `ifcopenshell.get_log()`); ověření type/entity/global WHERE rules touto funkcí také není implementováno.

Python příklad:
```python
logger = ifcopenshell.validate.json_logger()
ifcopenshell.validate.validate("/path/to/model.ifc", logger, express_rules=True)
from pprint import pprint
pprint(logger.statements)
```

(source: https://docs.ifcopenshell.org/autoapi/ifcopenshell/validate/index.html)

## SPF syntax validace

Kromě schema validace (`ifcopenshell.validate`, viz výše) umí IfcOpenShell zkontrolovat, zda IFC-SPF soubor obsahuje korektní SPF syntaxi:

```
python -m ifcopenshell.simple_spf path/to/model.ifc
Valid
```

Při chybě vypíše řádek/sloupec a typ problému (např. neočekávaná čárka, duplicitní instance ID, chybějící hlavička). Volitelný argument `--json` vrátí výsledek ve formátu JSON. Schema validace (`ifcopenshell.validate`) navíc kontroluje atributy, názvy entit, datové typy, kardinalitu a where rules.

(source: https://docs.ifcopenshell.org/ifcopenshell-python/validation.html)

## Odkazy

- Dokumentace: https://docs.ifcopenshell.org/introduction.html
- Web projektu: https://ifcopenshell.org/
