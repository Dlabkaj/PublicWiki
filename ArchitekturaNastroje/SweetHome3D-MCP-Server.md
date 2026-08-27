# Sweet Home 3D MCP Plugin (grimashevich/sweethome3d-mcp-server)

Fakta na této stránce vychází z vlastního README/dokumentace repozitáře na GitHubu (grimashevich/sweethome3d-mcp-server) — subjekt dokumentuje sám sebe, tagy `*(unverified)*` proto nejsou u faktů z tohoto zdroje použity. Jde o software třetí strany (community plugin, ne oficiální produkt eTeks/Space Mushrooms).

## Co to je

Plugin pro Sweet Home 3D, který vestavuje MCP (Model Context Protocol) server přímo do aplikace. Umožňuje Claude a dalším AI asistentům ovládat Sweet Home 3D přes HTTP — vytvářet stěny, umisťovat nábytek, renderovat fotky a další — bez externího proxy nebo samostatného serverového procesu. Server běží na `http://127.0.0.1:9877/mcp`. (source: https://github.com/grimashevich/sweethome3d-mcp-server)

## Požadavky a instalace

- Sweet Home 3D 6.0 nebo novější, Java 11 nebo novější (bundled s SH3D nebo systémová).
- Staré 32bitové Windows instalátory SH3D s JRE 1.8 plugin nenačtou (`UnsupportedClassVersionError`).
- Instalace: stažení `.sh3p` souboru z Releases, zkopírování do plugins složky (Windows: `%APPDATA%\eTeks\Sweet Home 3D\plugins\`; macOS: `~/Library/Application Support/eTeks/Sweet Home 3D/plugins/`; Linux: `~/.sweethome3d/plugins/`), restart aplikace. MCP server startuje automaticky na portu 9877, stav lze ověřit v Tools → MCP Server...
- Na macOS nefunguje s Mac App Store buildem SH3D (sandboxováno, chybí `com.apple.security.network.server` entitlement) — nutné použít standalone/installer verzi z sweethome3d.com.

(source: https://github.com/grimashevich/sweethome3d-mcp-server)

## Konfigurace pro Claude

Claude Desktop (`claude_desktop_config.json`) i Claude Code (`.mcp.json`):
```json
{
  "mcpServers": {
    "sweethome3d": {
      "type": "http",
      "url": "http://localhost:9877/mcp"
    }
  }
}
```
Plugin má tlačítko "Auto-configure Claude Desktop" v Tools → MCP Server..., které tento config zapíše automaticky. (source: https://github.com/grimashevich/sweethome3d-mcp-server)

## Dostupné příkazy

42 příkazů napříč 12 kategoriemi. Výběr relevantní pro tvorbu výkresů a export:

| Kategorie | Příkaz | Popis |
|---|---|---|
| Scene | `get_state` | Plný stav scény: stěny, nábytek, místnosti, kamera, popisky, úrovně |
| Walls | `create_wall`, `create_walls`, `modify_wall`, `delete_wall`, `connect_walls` | Tvorba/úprava/mazání stěn, spojení stěn pro správné vykreslení rohů |
| Rooms | `create_room_polygon`, `modify_room`, `delete_room` | Místnost z polygonu bodů, úprava jména/barev, mazání |
| Furniture | `list_categories`, `list_furniture_catalog`, `place_furniture`, `modify_furniture`, `delete_furniture`, `duplicate_objects`, `group_furniture`, `ungroup_furniture` | Práce s katalogem a umístěným nábytkem |
| Doors & Windows | `place_door_or_window` | Umístění z katalogu do stěny (automatický výpočet pozice/úhlu) |
| Textures & Appearance | `list_textures_catalog`, `apply_texture`, `set_environment` | Textury, barvy oblohy/země, osvětlení, průhlednost stěn |
| 3D Shapes | `generate_shape` | Vlastní 3D geometrie: primitiva (box, koule, válec, kužel, klín, oblouk, schody, torus, polokoule, trubka), extrude, mesh, CSG booleovské operace |
| Annotations | `add_label`, `add_dimension_line` | Textová anotace na 2D půdorysu, kótovací čára s auto-offsetem |
| Camera | `set_camera`, `store_camera`, `get_cameras` | Přepínání top/observer režimu, ukládání pohledů |
| Multi-level | `add_level`, `list_levels`, `set_selected_level`, `delete_level` | Práce s podlažími |
| Rendering & Export | `render_photo` (ray-traced přes Sunflow, standardní i bird's-eye), `export_plan_image` (2D PNG), `export_svg` (2D SVG), `export_to_obj` (3D OBJ+MTL+textury v ZIP) | Export výkresů a renderů |
| Save/Load | `save_home`, `load_home` | Práce se soubory `.sh3d` |
| Checkpoints | `checkpoint`, `restore_checkpoint`, `list_checkpoints` | In-memory snapshoty s undo timeline |
| Batch | `batch_commands` | Více příkazů v jednom requestu |

(source: https://github.com/grimashevich/sweethome3d-mcp-server)

## Souřadnicový systém

Jednotky: centimetry (500 = 5 metrů). Osa X doprava, osa Y dolů (souřadnice obrazovky). Všechna ID objektů jsou stabilní UUID, bezpečná pro použití napříč více voláními. (source: https://github.com/grimashevich/sweethome3d-mcp-server)

## Architektura a build ze zdroje

Plugin je jedna samostatná komponenta bez externích runtime závislostí: `plugin` (entry point `SH3DMcpPlugin`), `http` (streamable HTTP MCP server, JSON-RPC 2.0, port 9877), `command` (42 handlerů příkazů, auto-registrace přes `CommandRegistry`), `bridge` (thread-safe wrapper Sweet Home 3D API — `HomeAccessor` běžící přes EDT, `CheckpointManager`, `ObjectResolver`), `protocol` (ručně psaný JSON parser bez závislostí), `config` (nastavení, auto-konfigurátor Claude Desktop).

Build vyžaduje Java 11+, Maven 3.6+ (nebo `mvnw`). `SweetHome3D.jar` (46 MB) není v gitu — skript `scripts/setup-dev.sh`/`.bat` jej získá z lokální instalace SH3D nebo stáhne ze SourceForge. Výstupní artefakt: `target/sh3d-mcp-plugin-1.0.0.sh3p`.

Přidání nového příkazu vyžaduje jednu třídu implementující `CommandHandler` a `CommandDescriptor`, zaregistrovanou v `SH3DMcpPlugin.createCommandRegistry()`.

Licence: GNU General Public License v2.0. Plugin využívá Sweet Home 3D Plugin API (GPL v2) a Java3D (BSD/JOGL licence).

(source: https://github.com/grimashevich/sweethome3d-mcp-server)

## Vydání

Dle stránky Releases existují dvě verze: v1.0.0 (vydáno 27. února) a v1.1.0 (vydáno 13. března, aktuálně nejnovější). Rok u dat stránka neuvádí — GitHub rok vypouští u data ve stávajícím roce, jde tedy pravděpodobně o rok 2026 *(needs second source)*. (source: https://github.com/grimashevich/sweethome3d-mcp-server/releases)

## Odkazy

- Repozitář: https://github.com/grimashevich/sweethome3d-mcp-server
- Releases: https://github.com/grimashevich/sweethome3d-mcp-server/releases
