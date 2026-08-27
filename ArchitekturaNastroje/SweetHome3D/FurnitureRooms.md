# Sweet Home 3D — Furniture, Doors/Windows, Rooms & Levels

**Summary**: Adding and editing furniture and openings; drawing rooms with correct doorsteps; managing multi-storey levels.

**Sources**: [Sweet Home 3D User's Guide](https://www.sweethome3d.com/users-guide/)

**Last updated**: 2026-06-22

---

## Catalog search

Enable **Searchable list** option in Preferences → type letters to search furniture catalog by name or keyword. *(needs second source)* — [Furniture libraries 1.8 blog](https://www.sweethome3d.com/blog/furniture-libraries-1-8/)

Special catalog keywords: *(needs second source)*
- `Adjustable` — item has a **Modify openings / Modify posture** button in its dialog (shape is configurable, e.g., doors that can be opened/closed, furniture with poseable joints).
- `Default` — one of the 100 default catalog items.

## Adding furniture (including doors & windows)

Two methods:
- **Drag-and-drop** from catalog to plan (or to furniture list).
- Select in catalog → click **Add furniture** toolbar button.

Added piece is simultaneously selected in catalog, furniture list, plan, and 3D view. *(needs second source)*

**Recommended order**: add doors/windows first → then furniture. *(needs second source)*

### Magnetism behavior

- **Door/window** dropped on a wall → auto-oriented and auto-resized to wall orientation and thickness.
- **Furniture** dropped near a wall → auto-rotated so back face lies against wall. *(needs second source)*
- Piece dropped on a larger piece → auto-elevated to sit on top (if default elevation = floor level). *(needs second source)*
- **Alt** toggles 15° rotation magnetism during drag. *(needs second source)*

## Furniture corner indicators (when selected)

| Indicator location | Action |
|-------------------|--------|
| Rotation corner | Drag → rotate; **Alt** = toggle 15° snap |
| Elevation corner | Drag → change height from floor |
| Height corner | Drag → change piece height |
| Size corner | Drag → change width and depth |

## Furniture dialog

Double-click piece OR **Furniture > Modify…** — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("double-click on a piece of furniture or choose Furniture > Modify…") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Furniture > Modify… Ctrl E ... Double-click on a piece").

Editable attributes:
- Name
- Rotation angle
- Location (X, Y)
- Elevation from floor
- Size (width / depth / height)
- Color or texture
- Visibility (invisible = hidden in plan/3D but stays in furniture list) *(needs second source)*
- Mirror 3D model shape
- Light power (affects photo render at best 2 quality levels) — confirmed by [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) ("Light power (%)")

## Drawing rooms

Click **Create rooms** toolbar button. Two methods:

1. **Manual**: click each corner → double-click at last point OR press **Escape** after last point.
2. **Auto (faster)**: double-click anywhere inside an existing closed surface (surrounded by walls) → room fills the surface automatically.

**Draw walls and place doors first**, then use the double-click-inside method to create rooms quickly. *(needs second source)*

Auto-created rooms include **half doorstep** of each door on their walls — ensures adjacent rooms join correctly in 3D when doors are open. *(needs second source)*

### Room editing

- In **Select** mode: drag room corner points to reshape.
- **Plan > Modify rooms…** → room dialog — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Plan > Modify rooms… Ctrl Alt E ... Double-click on a room").

Room dialog attributes:
- Name
- Floor color or texture
- Ceiling color or texture

## Levels (multi-storey)

Add a level: **Plan > Levels > Add level** OR click the **+** tab at the top of the plan view — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("Plan > Levels > Add level ... clicking on the + tab") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Add a level — Plan > Add level — Ctrl Alt N"; note: shortcuts blog flattens the path).

- Each level = a tab at the top of the plan. Active tab = where new objects are placed — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Select a level in plan ... Click on level tab").
- Lower level shown in **light color** in plan view for reference while drawing on upper level. *(needs second source)*
- Objects can be copy-pasted between levels. *(needs second source)*
- **Underground**: enter negative elevation — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) and [Tips and Tricks index](https://www.sweethome3d.com/tips/) ("How to add a basement to a design ... with a level at a negative elevation").

Edit level: double-click its tab OR **Plan > Levels > Modify level…** — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Plan > Modify level… Ctrl Alt B ... Double-click on level tab").

| Attribute | Notes |
|-----------|-------|
| Elevation | Bottom of this level from ground (negative = underground) |
| Height | Ceiling height of this level |
| Floor thickness | Structural floor slab thickness |

The level dialog shows a table of all levels for cross-reference. *(needs second source)*

## Importing custom furniture

**Furniture > Import furniture…** wizard — tick **"Add to Catalog"** and set a category so the piece is findable later. *(needs second source)* Rename it if the default name is not human-readable. *(needs second source)* — [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/)

Import textures: **Furniture > Import texture…** — set Name and Category — confirmed by [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) ("Furniture menu item and clicking on Import texture...") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Furniture > Import texture…"). Best practices for custom textures: *(needs second source)*
- Use **seamless** (tileable) textures — abrupt edges look bad when repeated.
- Photo lighting must be **even** across the image.
- Recommended size: **square, ≤ 256 × 256 pixels**.

## Furniture sub-parts

Every furniture item is composed of **separate parts**, each independently customizable — confirmed by [Library blog](https://www.sweethome3d.com/blog/exploring-sweet-home-3ds-library-furniture-colors-and-more/) and [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/):

- Each part can have its own color/texture (e.g., chair legs vs. back, sofa feet vs. cushions).
- Individual parts can be made **invisible**.

**Trick**: like bed A's frame but bed B's blanket? Place both at the same location, then make everything except the blanket of bed B invisible.

### Editing per-material (part-level)

Right-click furniture in plan → **Modify furniture…** → Color and texture section → select **Materials** radio button → click **Modify…** — [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) + [Library blog](https://www.sweethome3d.com/blog/exploring-sweet-home-3ds-library-furniture-colors-and-more/)

In the materials dialog:
- Parts listed by name; clicking a part makes it **flash in the Preview** for identification. *(needs second source)*
- Per-part: make invisible, change color, or apply texture.

## Related

[[Index]]
[[Walls]]
[[ThreeDView]]
