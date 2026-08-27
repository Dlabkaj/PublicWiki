# Sweet Home 3D — Blueprint Import & Wall Drawing

**Summary**: How to import a floor plan blueprint as background, draw walls precisely, and edit wall attributes.

**Sources**: [Sweet Home 3D User's Guide](https://www.sweethome3d.com/users-guide/)

**Last updated**: 2026-06-22

---

## Import blueprint as background image

Menu: **Plan > Import background image…** *(needs second source)*

Wizard steps:
1. **Choose image** — supports BMP, JPEG, GIF, PNG. *(needs second source)* Keep file small (helper image, not art).
2. **Scale** — drag endpoints of colored line to match a known length; type real length in field.
3. **Origin** — set point in the image that maps to (0, 0) in the plan.
4. Click **Finish** — image appears behind grid at chosen scale.

Edit later: **Plan > Modify background image…** *(needs second source)*

Tip (iOS): *Tape Measure* app can generate a scaled floor plan from photos; export as image → import into SH3D. *(needs second source — app mentioned in official guide only)*

## Drawing walls

1. Click **Create walls** button in toolbar.
2. Click plan → **start point** of wall.
3. Click → each **waypoint** / end point.
4. **Double-click** the final point OR press **Escape** to end the chain.
5. Each new click = end of current wall + start of next wall.

**During drawing**: a small yellow tooltip shows current **length, angle, and wall thickness** to help stay precise. — [Creating 3D Floor Plans guide](https://www.sweethome3d.com/blog/creating-3d-floor-plans-with-sweet-home-3d/) + [User's Guide](https://www.sweethome3d.com/users-guide/)

**Do not draw walls around door/window openings** — SH3D auto-computes holes when openings are placed.

Walls appear simultaneously in plan and 3D view in real time.

### Rounded / curved walls

Walls can be curved. In wall-drawing mode, use `Ctrl`+Click (Win/Linux) or `Alt`+Click (Mac) to curve the segment — confirmed by [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Curve currently drawn wall ... Ctrl + Click ... alt + Click") and [sbcode.net Drawing Walls](https://sbcode.net/sh3d/drawing-walls/) ("You also have the option to create rounded walls").

### Entering exact length / angle

After pressing **Enter** during wall drawing, type exact length and angle — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("enter the length and the angle of the wall being created after pressing the enter key") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Enter wall dimensions with the keyboard ... Enter").
Not available in Online or Mobile versions. *(needs second source)*

### Angle magnetism (15° snapping)

Default: wall angle snaps to multiples of 15°. *(needs second source)*

| OS | Key to disable magnetism |
|----|--------------------------|
| Windows | **Alt** |
| macOS | **Cmd** |
| Linux | **Shift + Alt** |

Also disable globally via Preferences. *(needs second source)*

Use **alignment lines** and **walls tooltip** for precise placement. *(needs second source)*
Change plan scale with **Zoom** buttons. *(needs second source)*

## Selecting objects

Click **Select** button in toolbar to exit drawing mode and enable selection.

- Click object → select it.
- Draw selection rectangle → select all enclosed objects.
- **Shift + click** → add to / remove from selection.
- Drag or **arrow keys** → move selected walls (and other objects) — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("drag and drop them, or use keyboard arrow keys") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Move selected items pixel by pixel — Arrows").
- Selected wall: drag start/end points with mouse to reshape.
- **Plan > Split wall** — split selected wall into two.

## Editing wall attributes

Double-click a wall OR **Plan > Modify walls…** → wall dialog box.

Double-click OR right-click → **Modify Wall** opens the same dialog. *(needs second source)* — [sbcode.net Drawing Walls tutorial](https://sbcode.net/sh3d/drawing-walls/)

| Attribute | Options |
|-----------|---------|
| Left side color/texture | Color picker or texture |
| Right side color/texture | Color picker or texture |
| Thickness | Numeric |
| Start height | Numeric (height at wall start point) |
| End height | Numeric (height at wall end point) |

Walls can have **different start and end heights** — useful for sloped walls under a roof. *(needs second source)* — [sbcode.net Drawing Walls](https://sbcode.net/sh3d/drawing-walls/)

To use a custom image as texture: click **Import** in the texture picker → texture import wizard. *(needs second source)*

## Related

[[Index]]
[[Interface]]
[[FurnitureRooms]]
