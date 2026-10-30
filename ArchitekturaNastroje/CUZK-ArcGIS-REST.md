# ČÚZK — polohopis a výškopis přes ArcGIS REST

Jak agent stáhne hranici parcely, budovy v okolí a výškopis (DMR, DMP) přímo ze služeb, na kterých stojí Geoprohlížeč a Aplikace výškopisu ČÚZK — bez klikání v GUI.

Ověřeno: 2026-10-11

Nástroj: AIArchitect `tools/cuzk/cuzk.py` (vše níže jedním příkazem), `tools/cuzk/vyber_terenu.py` (mapa pro zóny bodů terénu podle účelu), `tools/terrain/tin.py` (interpolace po trojúhelnících).

## Co a kde

| Data | Služba | Poznámka |
|---|---|---|
| Parcela (hranice, výměra, druh pozemku) | `https://ags.cuzk.gov.cz/arcgis/rest/services/RUIAN/MapServer/5/query` | filtr `katastralniuzemi=<kód k.ú.> AND kmenovecislo=<kmen> AND poddelenicisla=<pododdělení>` |
| Katastrální území (kód) | `…/RUIAN/MapServer/7/query` | `where=nazev LIKE '…'` — pozor na stejnojmenná k.ú. |
| Stavební objekty (půdorys, NP, rok, č. p.) | `…/RUIAN/MapServer/3/query` | polygony; dotaz obálkou (`esriGeometryEnvelope`) |
| DMR 5G (holý terén) | `https://ags.cuzk.gov.cz/arcgis2/rest/services/dmr5g/ImageServer` | `identify` po bodu, `exportImage` jako rastr |
| DMP 1G (povrch s budovami, 2009–2013) | `…/arcgis2/rest/services/dmp1g/ImageServer` | stavby po roce 2013 v něm chybí |
| DMP OK (povrch z obrazové korelace) | `…/arcgis2/rest/services/dmp_obrazova_korelace/ImageServer` | novější; zachytí i stavby dokončené v roce 2019; datum snímkování služba neuvádí *(1 zdroj)* |
| Katastrální mapa jako obrázek (kontrola) | `https://services.cuzk.gov.cz/wms/wms.asp?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&LAYERS=KN&CRS=EPSG:5514&BBOX=<xmin,ymin,xmax,ymax>&WIDTH=…&HEIGHT=…&FORMAT=image/png` | lomové body RÚIAN na ní sedí na pixel — ověřeno 2026-10-11 |
| Převod S-JTSK → WGS84 | `https://ags.cuzk.gov.cz/arcgis/rest/services/Utilities/Geometry/GeometryServer/project` | `inSR=5514&outSR=4326&transformation=5239`; bez transformace se výsledek liší o ~2,5 m |

Souřadnice jsou v EPSG:5514 v Esri podání — **záporné**, x roste na východ, y na sever. Výšky jsou v Bpv.

## Omezení, na která agent narazí

- **`getSamples` vrací 403** („Request forbidden by administrative rules") na obou endpointech DMR 5G. Hromadné vzorkování je zakázané. `identify` po jednom bodu funguje.
- **`exportImage` funguje**: `format=tiff&pixelType=F32&compression=None&size=<šířka>,<výška>` nad obálkou v metrech dá rastr 1 m. GeoTIFF je **dlaždicový** (128×128), nekomprimovaný float32. Georeference je v tagu 33922 (tiepoint) a pixel je 1 m (tag 33550). Bez numpy se přečte přes `struct`.
- Kontrola: hodnota z rastru se v testu shodovala s `identify` na 0,08 m.
- `MapServer` RÚIAN vrací kódy (`druhpozemkukod`, `zpusobyvyuzitipozemku`). Číselník je v `domain.codedValues` v popisu vrstvy (`…/MapServer/5?f=json`).

## Body terénu do modelu — interpolace rozhoduje víc než hustota

Ověřeno 2026-10-11 na svahu 6–14 %, porovnáním s rastrem DMR 5G 1 m (842 buněk):

| Body | Interpolace | Průměrná / max. chyba |
|---|---|---|
| mřížka 1 m (1905 bodů) | IDW (váha 1/d²) přes všechny body | 0,14 / 0,40 m |
| mřížka 5 m | lineárně po trojúhelnících (Delaunay) | 0,05 / 0,23 m |
| adaptivně, zhuštěno kde TIN > 0,05 m | lineárně po trojúhelnících | 0,01 / 0,05 m |

- IDW přes všechny body táhne výšku k průměru — chyba roste se sklonem a hustší mřížka ji nespraví.
- Lineární interpolace je na rovnoměrném svahu přesná při libovolné rozteči. Body jsou potřeba tam, kde se **mění sklon** (zlom svahu, náspy, příkopy), ne tam, kde je strmo.
- Pod ~0,05 m nemá smysl zpřesňovat: DMR 5G sám má střední chybu 0,18 m.

## Přesnost — co z toho smí do studie

- **DMR 5G**: úplná střední chyba výšky 0,18 m v odkrytém terénu, 0,3 m v zalesněném. Nezná navážky a výkopy po datu skenování.
- **DMP 1G**: střední chyba 0,4 m u budov, 0,7 m u vegetace [1].
- **Hranice z RÚIAN/KN** je obraz katastrální mapy, ne vytyčení. Přesnost záleží na kódu kvality lomových bodů; ten služba RÚIAN nevrací. Výměra v KN se může lišit od plochy geometrie — u parcely ve výměře „z dřívější evidence" i o jednotky procent.
- Na studii (osazení, sklon, varianty) to stačí. **Geodetické zaměření nenahrazuje** — pro dokumentaci k povolení stavby je potřeba polohopis a výškopis od geodeta.

## Zdroje

1. Popis služby DMP 1G — `https://ags.cuzk.gov.cz/arcgis2/rest/services/dmp1g/ImageServer?f=json` (pole `description`), staženo 2026-10-11.
2. Seznam služeb — `https://ags.cuzk.gov.cz/arcgis2/rest/services?f=json`, `https://ags.cuzk.gov.cz/arcgis/rest/services?f=json`, staženo 2026-10-11.
3. Vrstva Parcela RÚIAN, popis a číselníky — `https://ags.cuzk.gov.cz/arcgis/rest/services/RUIAN/MapServer/5?f=json`, staženo 2026-10-11.
