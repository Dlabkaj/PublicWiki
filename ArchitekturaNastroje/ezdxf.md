# ezdxf — Python knihovna pro DXF

Fakta na této stránce vychází z vlastní dokumentace projektu ezdxf (oficiální web ezdxf.mozman.at a ReadTheDocs dokumentace verze 1.4.4) — subjekt dokumentuje sám sebe, tagy `*(unverified)*` proto nejsou u faktů z tohoto zdroje použity.

## Co to je

ezdxf je Python balíček pro čtení, úpravu a zápis DXF (Drawing Interchange File) dokumentů — formátu vyvinutého Autodeskem. Nejde o CAD kernel ani o konvertor formátů: ezdxf neumí konvertovat mezi verzemi DXF ani mezi DXF a DWG. Pro konverzi DXF verzí/DWG doporučuje vlastní dokumentace bezplatný ODAFileConverter od Open Design Alliance. Pro CAD kernel s Python skriptováním odkazuje na FreeCAD. (source: https://ezdxf.readthedocs.io/en/stable/introduction.html)

- Licence: MIT
- Vyžaduje Python 3.10+, běží nezávisle na OS (Windows, Linux, macOS)
- Závislosti: pyparsing, numpy, fontTools, typing_extensions
- Podporované DXF verze: R12 (AC1009) až R2018 (AC1032); starší verze umí načíst, ale ukládá je jako R12
(source: https://ezdxf.readthedocs.io/en/stable/introduction.html)

## Instalace

```
pip install ezdxf
```

Volitelně s podporou vykreslování (matplotlib + PySide6, export do PNG/PDF/SVG a interaktivní zobrazení):

```
pip install ezdxf[draw]
```
(source: https://ezdxf.mozman.at/)

## Základní použití

```python
import ezdxf
from ezdxf import colors
from ezdxf.enums import TextEntityAlignment

doc = ezdxf.new(dxfversion="R2010")
doc.layers.add("TEXTLAYER", color=colors.RED)
msp = doc.modelspace()
msp.add_line((0, 0), (10, 0), dxfattribs={"color": colors.YELLOW})
msp.add_text(
    "Test",
    dxfattribs={"layer": "TEXTLAYER"}
).set_placement((0, 0.2), align=TextEntityAlignment.CENTER)
doc.saveas("test.dxf")
```
(source: https://ezdxf.mozman.at/)

Nové entity se vždy přidávají do layoutu (modelspace, paperspace layout nebo block layout). Funkce `ezdxf.new()` může s argumentem `setup=True` vytvořit i standardní zdroje (linetypy, textové styly). Pro zobrazení textových stylů v DXF prohlížeči/CAD aplikaci musí aplikace znát cestu k TTF fontům — tuto konfiguraci ezdxf neřeší. (source: https://ezdxf.readthedocs.io/en/stable/tutorials/simple_drawings.html)

## Add-on r12writer

Add-on `r12writer` vytváří jednoduché DXF R12 výkresy s omezenou sadou typů: LINE, CIRCLE, ARC, TEXT, POINT, SOLID, 3DFACE a POLYLINE. Výhodou je rychlost a malá paměťová náročnost — entity se zapisují přímo do souboru/streamu bez vytváření dokumentové struktury v paměti. (source: https://ezdxf.readthedocs.io/en/stable/tutorials/simple_drawings.html)

## Ostatní funkce (z přehledu na oficiálním webu)

- Zachovává obsah při načtení/úpravě DXF — neznámé tagy třetích stran zůstávají zachovány pro budoucí úpravy
- Plně typově anotovaný kód (prochází `mypy --ignore-missing-imports`)
- Volitelné C-extensions v binárních wheel balíčcích pro Windows, Linux, macOS (rychlost)
- Drawing add-on: export DXF do PNG, PDF nebo SVG přes matplotlib, nebo interaktivní zobrazení přes Qt
- CLI nástroj `ezdxf` pro zobrazení, kreslení, inspekci, procházení a audit DXF souborů ze shellu
- Další add-ony: r12writer, dxf2code, pycsg, MTextExplode, text2path, geo interface, mesh exchange, můstky na OpenSCAD a ODA File Converter
- Podpora ASCII i binárního DXF formátu
(source: https://ezdxf.mozman.at/)
