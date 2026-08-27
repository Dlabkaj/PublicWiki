# Tekla Structures — Selection & Snapping

**Summary**: What the selection switches, snap switches, and snap override toolbars do, how to customize them, and why most beginner placement problems trace back to wrong switch state.

**Sources**:
- https://support.tekla.com/doc/tekla-structures/2023/mod_customize_toolbars
- https://support.tekla.com/doc/tekla-structures/2026/gen_keyboard_shortcuts
- https://steelexplained.com/10-things-i-wish-i-knew-when-i-first-started-using-tekla-structures/
- https://steelexplained.com/7-useful-tips-for-tekla-structures-beginners/

**Last updated**: 2026-06-05

---

## The three toolbars

Tekla Structures has three switch-based toolbars that control picking behaviour:

1. **Selecting** — *what* you pick (parts, components, assemblies, points, …)
2. **Snapping** — *where* clicks land (endpoints, midpoints, intersections, grid, free)
3. **Snap override** — temporarily restrict snapping to a single type for the next pick

All three are available both in modeling and drawing modes (source: support.tekla.com 2023 mod_customize_toolbars).

## Customizing a toolbar (hide/show switches)

- Click the **eye button** on the toolbar to open the list of all switches, **or** right-click on the toolbar.
- Click a switch name in the list to hide it — eye icon turns to "hidden".
- Click again to bring it back — eye icon returns to "visible".
- Company administrators can distribute the customized toolbars across the organization (source: support.tekla.com 2023 mod_customize_toolbars).

## Selection switches (modifiers)

The five modifiers — master these to control what your clicks actually grab (source: steelexplained 10-things #2):

- **Select components**
- **Select objects in components**
- **Select assemblies**
- **Select objects in assemblies**
- **Select tasks** (less commonly used)

Beginner trap: if you can't pick what you want, the wrong selection switch is almost always the cause — check switches before assuming Tekla is broken.

### Selection shortcuts (recap)

| Action | Shortcut |
| ------ | -------- |
| Rollover highlight on/off | `H` |
| *Select all* selection switch | `F2` |
| *Select parts* selection switch | `F3` |
| Select all in model | `Ctrl+A` |
| **Select previous objects** | `Alt+P` |
| Select assembly (click any element) | `Alt`+click |
| Add to selection | hold `Shift` |
| Toggle selection | hold `Ctrl` |
| Selection filters | `Ctrl+G` |
| Hide object | `Shift+H` |

Full list: [[KeyboardShortcuts]] (source: https://support.tekla.com/doc/tekla-structures/2026/gen_keyboard_shortcuts).

## Snap switches

Control which point types your cursor will snap to.

| Switch | Shortcut |
| ------ | -------- |
| Snap to reference lines/points | `F4` |
| Snap to geometry lines/points | `F5` |
| Snap to nearest points | `F6` |
| Snap to any position | `F7` |
| Ortho on/off | `O` |
| Cycle snap points forward / back | `Tab` / `Shift+Tab` |

When placement misbehaves, *check snaps first.* Most beginner frustration with placing parts in the wrong spot is snap state, not user error (source: steelexplained / QuickStart guidance).

## Coordinate input

While placing or moving, you can switch coordinate modes mid-operation:

- `R` — relative coordinate input
- `A` — absolute coordinate input
- `G` — global coordinate input
- `X` / `Y` / `Z` — lock that axis on/off
- `Ctrl` held while clicking the first point — **offset the first point** (lets you type a numeric offset or pick an offset distance, then click final position — useful for manual cuts/chamfers) (source: steelexplained quick-tips #6).

## Filters (Ctrl+G)

Filters narrow what selection switches actually act on — e.g. only beams of a certain profile, or only parts of phase 2. In a big model, switching is too coarse; filters get you to the exact subset.

## Related pages

[[Index]] · [[QuickStart]] · [[BeginnerTips]] · [[KeyboardShortcuts]]
