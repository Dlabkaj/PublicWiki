# IfcTester (validace IFC proti IDS)

Fakta na této stránce vychází z vlastní oficiální dokumentace projektu (docs.ifcopenshell.org/ifctester.html) — subjekt dokumentuje sám sebe, tagy `*(unverified)*` proto nejsou u faktů z tohoto zdroje použity.

## Co to je

IfcTester umožňuje autorovat a číst soubory Information Delivery Specification (IDS). Umožňuje validovat IFC modely proti IDS a generovat reporty v několika formátech. Funguje z příkazové řádky, jako webová aplikace, nebo jako knihovna. (source: https://docs.ifcopenshell.org/ifctester.html)

## Instalace

```
pip install ifctester
```
(source: https://docs.ifcopenshell.org/ifctester.html)

## Použití z CLI

```
# Validace IFC vůči IDS s výpisem do konzole
python -m ifctester example.ids example.ifc

# Generování HTML reportu
python -m ifctester example.ids example.ifc -r Html -o report.html
```

CLI manuál (`python -m ifctester -h`):
```
usage: __main__.py [-h] [-r REPORTER] [--no-color] [--excel-safe] [-o OUTPUT] ids [ifc]

Uses an IDS to audit an IFC

positional arguments:
  ids                   Path to an IDS
  ifc                   Path to an IFC

options:
  -h, --help            show this help message and exit
  -r REPORTER, --reporter REPORTER
                        The reporting method to view audit results
  --no-color            Disable colour output (supported by Console reporting)
  --excel-safe          Make sure exported ODS is safely exported for Excel
  -o OUTPUT, --output OUTPUT
                        Output file (supported for all types of reporting except Console)
```
(source: https://docs.ifcopenshell.org/ifctester.html)

## Použití z Pythonu

Lze programově vytvořit IDS specifikaci a validovat proti ní IFC model:

```python
import ifcopenshell
from ifctester import ids, reporter

# Vytvoření nové IDS
specs = ids.Ids(title="My IDS")

# Přidání specifikace
spec = ids.Specification(name="My first specification")
spec.applicability.append(ids.Entity(name="IFCWALL"))
requirement = ids.Property(
    baseName="IsExternal",
    value="TRUE",
    propertySet="Pset_WallCommon",
    dataType="IfcBoolean",
    uri="https://identifier.buildingsmart.org/uri/.../prop/LoadBearing",
    instructions="Walls need to be load bearing.",
    cardinality="required")
spec.requirements.append(requirement)
specs.specifications.append(spec)

# Uložení do souboru
specs.to_xml("IDS.xml")

# Otevření IFC souboru
my_ifc = ifcopenshell.open("model.ifc")

# Validace modelu proti IDS požadavkům
specs.validate(my_ifc)

# Výsledky do konzole
reporter.Console(specs).report()
```

Podporované formáty reportů: konzole, JSON, ODS spreadsheet, HTML spreadsheet, BCF (`reporter.Json`, `reporter.Ods`, `reporter.Html`, `reporter.Bcf`).

(source: https://docs.ifcopenshell.org/ifctester.html)

## Relevance pro kontrolu konzistence výkresů

IDS (Information Delivery Specification) je formát pro definici požadavků na entity/vlastnosti v IFC modelu (např. povinné psety, hodnoty atributů). IfcTester tento formát autoruje i validuje — nabízí se jako nástroj pro automatickou kontrolu, že vygenerovaný IFC model splňuje definovaná pravidla (např. přítomnost požadovaných vlastností na stěnách). Zdroj přímo neuvádí příklad kontroly kót nebo tabulky ploch — to je otevřená otázka.

## Odkazy

- Dokumentace: https://docs.ifcopenshell.org/ifctester.html
