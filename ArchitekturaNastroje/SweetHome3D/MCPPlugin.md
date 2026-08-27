# Sweet Home 3D MCP Plugin — Agent Control Interface

**Summary**: Complete reference for the MCP plugin that lets an AI agent control Sweet Home 3D over HTTP — 42 commands, installation, config, coordinate system.

**Sources**: [grimashevich/sweethome3d-mcp-server README](https://github.com/grimashevich/sweethome3d-mcp-server)

**Last updated**: 2026-06-22

---

> ⚠️ CONFLICT: [[../Index]] states ~4 GitHub stars; as of 2026-06-22 the repo shows **13 stars**. Repo has matured since the parent page was written. *(unverified — star count is live data)*

## What it does

Plugin embeds a JSON-RPC 2.0 MCP server **inside** Sweet Home 3D — no external proxy, no separate process. *(unverified)*

```
Claude Desktop / Claude Code
        │ HTTP (JSON-RPC 2.0)
        ▼
┌─────────────────────────────────────┐
│  Sweet Home 3D + MCP Plugin         │
│  Built-in HTTP server on port 9877  │
│  http://127.0.0.1:9877/mcp          │
└─────────────────────────────────────┘
```

**Repo**: https://github.com/grimashevich/sweethome3d-mcp-server *(unverified)*
**License**: GPL v2 *(unverified)*
**Latest release**: v1.1.0 (March 13, 2026) *(unverified)*

---

## Requirements

| Requirement | Minimum |
|-------------|---------|
| Sweet Home 3D | 6.0+ |
| Java | 11+ |

⚠️ Old 32-bit Windows SH3D installer ships with JRE 1.8 → plugin silently fails to load (`UnsupportedClassVersionError`). *(unverified)*

---

## Installation

1. Download latest `.sh3p` from [Releases](https://github.com/grimashevich/sweethome3d-mcp-server/releases). *(unverified)*
2. Copy to plugins folder: *(unverified)*

| OS | Plugins folder |
|----|----------------|
| Windows | `%APPDATA%\eTeks\Sweet Home 3D\plugins\` |
| macOS | `~/Library/Application Support/eTeks/Sweet Home 3D/plugins/` |
| Linux | `~/.sweethome3d/plugins/` |

3. (Re)start Sweet Home 3D — MCP server starts automatically. *(unverified)*
4. Verify: **Tools → MCP Server…** shows server status. *(unverified)*

---

## Claude configuration

### Claude Desktop (`claude_desktop_config.json`)

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

### Claude Code (`.mcp.json` in project directory)

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

Shortcut: plugin's **Tools → MCP Server… → "Auto-configure Claude Desktop"** button writes the config automatically. *(unverified)*

---

## Coordinate system

- Units: **centimetres** (e.g. 500 = 5 m) *(unverified)*
- X axis: right; Y axis: down (screen coordinates) *(unverified)*
- Object IDs: stable UUIDs — safe to reuse across calls *(unverified)*

---

## All 42 Commands

*(unverified — all entries from README)*

### Scene (2)

| Command | Description |
|---------|-------------|
| `get_state` | Full scene state: walls, furniture, rooms, camera, labels, levels |
| `clear_scene` | Remove all objects from the scene |

### Walls (5)

| Command | Description |
|---------|-------------|
| `create_wall` | Single wall between two points |
| `create_walls` | Rectangular room (4 connected walls) |
| `modify_wall` | Change height, thickness, color, arc, coordinates |
| `delete_wall` | Delete wall by ID |
| `connect_walls` | Connect two walls for correct corner rendering |

### Rooms (3)

| Command | Description |
|---------|-------------|
| `create_room_polygon` | Room from an array of polygon points |
| `modify_room` | Change name, floor/ceiling color, visibility |
| `delete_room` | Delete room by ID |

### Furniture (8)

| Command | Description |
|---------|-------------|
| `list_categories` | All furniture catalog categories with item counts |
| `list_furniture_catalog` | Browse catalog; filter by name, category, or type |
| `place_furniture` | Place a catalog item in the scene |
| `modify_furniture` | Move, rotate, resize, recolor furniture by ID |
| `delete_furniture` | Delete furniture by ID |
| `duplicate_objects` | Duplicate one or more objects by ID |
| `group_furniture` | Group multiple pieces into one object |
| `ungroup_furniture` | Split a group back into individual pieces |

### Doors & Windows (1)

| Command | Description |
|---------|-------------|
| `place_door_or_window` | Place from catalog into a wall (auto-computes position and angle) |

### Textures & Appearance (3)

| Command | Description |
|---------|-------------|
| `list_textures_catalog` | Browse texture catalog; filter by name or category |
| `apply_texture` | Apply catalog texture to wall side or room surface |
| `set_environment` | Ground/sky colors, lighting, wall transparency, drawing mode |

### 3D Shapes (1)

| Command | Description |
|---------|-------------|
| `generate_shape` | Create custom 3D geometry: primitives (box, sphere, cylinder, cone, wedge, arch, stairs, torus, hemisphere, pipe), extrude, mesh, CSG boolean ops (union, subtract, intersect) |

### Annotations (2)

| Command | Description |
|---------|-------------|
| `add_label` | Text annotation on the 2D floor plan |
| `add_dimension_line` | Measurement line with auto-offset |

### Camera (3)

| Command | Description |
|---------|-------------|
| `set_camera` | Switch to top/observer mode; set position, lookAt point, or target object |
| `store_camera` | Save the current viewpoint as a named bookmark |
| `get_cameras` | List all saved camera viewpoints |

### Multi-level (4)

| Command | Description |
|---------|-------------|
| `add_level` | Add a new level (floor/storey) |
| `list_levels` | List all levels; shows which is currently selected |
| `set_selected_level` | Switch the active level |
| `delete_level` | Delete a level and all its objects |

### Rendering & Export (4)

| Command | Description |
|---------|-------------|
| `render_photo` | Ray-traced 3D render (Sunflow); standard or overhead bird's-eye view; inline JPEG or saved PNG |
| `export_plan_image` | 2D floor plan as PNG |
| `export_svg` | 2D floor plan as SVG |
| `export_to_obj` | 3D scene as Wavefront OBJ (ZIP: OBJ + MTL + textures) |

### Save / Load (2)

| Command | Description |
|---------|-------------|
| `save_home` | Save the scene to a .sh3d file |
| `load_home` | Load a .sh3d file, replacing the current scene |

### Checkpoints — undo timeline (3)

| Command | Description |
|---------|-------------|
| `checkpoint` | Save an in-memory snapshot (optional description) |
| `restore_checkpoint` | Restore from a snapshot (supports force mode) |
| `list_checkpoints` | List all snapshots with current undo cursor position |

### Batch (1)

| Command | Description |
|---------|-------------|
| `batch_commands` | Execute multiple commands in one request |

---

## What an agent can drive

Based on the command list, an agent can autonomously: *(unverified)*

- **Read** the full scene state at any time (`get_state`)
- **Draw** walls and rectangular outlines (`create_wall`, `create_walls`, `connect_walls`)
- **Define** rooms with arbitrary polygons (`create_room_polygon`)
- **Place** any catalog furniture/door/window by name (`list_furniture_catalog`, `place_furniture`, `place_door_or_window`)
- **Edit** geometry, colors, textures of any object by UUID (`modify_wall`, `modify_furniture`, `apply_texture`)
- **Delete** any object by UUID
- **Group/ungroup** furniture
- **Manage** levels (add, switch, delete)
- **Annotate** the plan with labels and dimension lines
- **Control** camera / viewpoints
- **Render** photos and export plan as PNG/SVG/OBJ
- **Save/load** `.sh3d` project files
- **Checkpoint** and roll back changes
- **Generate** custom 3D shapes (primitives + CSG ops) — beyond standard catalog
- **Set** environment (sky, ground, lighting, wall transparency)
- **Batch** multiple commands in a single call

---

## Related

[[Index]]
[[../Index]]
