# Tekla Structures — Beginner Tips & Gotchas

**Summary**: Practical tips, hard-won lessons, and gotchas for new Tekla Structures users. Distilled from independent beginner blogs (SteelExplained tip series). Focus: signals of attention to detail and tidiness — the things an experienced reviewer notices in a model.

**Sources**:
- https://steelexplained.com/7-useful-tips-for-tekla-structures-beginners/
- https://steelexplained.com/10-things-i-wish-i-knew-when-i-first-started-using-tekla-structures/
- https://steelexplained.com/tekla-structures-quick-tips-part-1/

**Last updated**: 2026-06-05

---

## Selection & navigation

- **Enable automatic rotation center.** Without it, rotation behaves erratically — the center can land far off the model when you aim at grey space. Aim at something solid when rotating (source: steelexplained 7-tips bonus tip & quick-tips #1).
- **Select previous objects** — `Alt+P` (or menu) restores the last selection. Saves you when you forget to hold `Ctrl` mid-multi-select and lose the set (source: steelexplained 10-things #10 & quick-tips #2).
- **Select all elements of an assembly** — hold `Alt` and left-click any element of the assembly. Useful to hide, isolate, or inspect a whole assembly fast (source: steelexplained 7-tips #4).
- **Selection modifiers** matter: master *select components*, *select objects in components*, *select assemblies*, *select objects in assemblies* (plus the less-common *select tasks*). Each affects what your clicks actually pick up — wrong modifier is a top beginner frustration (source: steelexplained 10-things #2). See also [[SelectionAndSnapping]].
- **Snap switches first.** When a placement misbehaves, check snaps before anything else. See [[SelectionAndSnapping]].

## Setup & environment

- **Pick the right environment before opening a model.** Each environment ships its own profile catalog, bolt catalog, object classes, and material set — opening a model in the wrong environment causes missing-element / missing-bolt errors. Double-check Model Info before opening someone else's model (source: steelexplained 10-things #1).
- **Tutorials default to metric + Default environment.** Stay on those unless there's a reason not to — keeps you aligned with documentation (source: https://support.tekla.com/learn/first-steps-with-tekla-structures).
- **Position the model near origin (0,0,0)** and use the **base point** to offset the datum level. Tekla loses precision and graphics behave badly when objects are thousands of millimetres from origin. Model close to origin, set base point elevation to reflect real-world height for drawings (source: steelexplained 10-things #9).
- **Never rename a model folder via Windows Right-click → Rename** — Tekla won't open it. If you must rename, use Tekla's *Save as* (also renames the `.db1` file). Even *Save as* changes all GUIDs, so think twice (source: steelexplained 10-things #3).

## Customize & speed up

- **Set up your own keyboard shortcuts** — File → Settings → Keyboard shortcuts. Both modeling and drawing modes have their own. One-time cost, long-term payoff (source: steelexplained 10-things #4). See also [[KeyboardShortcuts]].
- **Customize the ribbon, contextual toolbar, and Applications & Components catalog.** Pin the things you use most; create your own folder for go-to components and save settings per profile (source: steelexplained 10-things #5).
- **Use components — don't model details manually.** Connection components auto-build plates/bolts/welds; manual work for repetitive details is slow and error-prone. Set up component settings per profile family for big wins (source: steelexplained 10-things #6).
- **"Create current connection"** repeats the last component used with its current properties — assign a shortcut for it; saves trips to the Applications & components sidebar (source: steelexplained quick-tips #3).
- **`Ctrl` while moving/cutting offsets the first point.** Click the first point with `Ctrl` held, type a numeric distance, then finish — useful for precise manual cuts and chamfers (source: steelexplained quick-tips #6).

## Drawings polish

- **Three property levels in drawings — drawing, view, object — in that hierarchy.**
  - Drawing-level: affects the whole drawing; set before or change after creation.
  - View-level: only the selected view frame in an open drawing; double-click a view frame to open View Properties.
  - Object-level: only the selected objects. Once set at object level, the object is *no longer affected by higher-level changes* — overrides cascade downward, never upward (source: steelexplained 7-tips #5).
- **Move part marks with their leader line — hold `Shift` while dragging.** Plain left-click drag moves only the frame; the leader stays put and the mark looks detached (source: steelexplained 7-tips #2).
- **Remove revision clouds in bulk** — Tekla auto-stamps revision clouds on changed elements when you modify the model. Open *Applications & components* sidebar, search *Remove change clouds*, double-click. Cleaner drawings = detail polish (source: steelexplained 7-tips #1).
- **Column marks defaulting to 45° on GA drawings?** Some environments set this by default. To force horizontal marks: File → Settings → Advanced Options (`Ctrl+E`) → *Marking: parts* → set `XS_DO_NOT_DRAW_COLUMN_MARKS_AT_45_DEGREES_IN_GA_DRAWING = TRUE`. Reopen the drawing for the change to take effect (source: steelexplained quick-tips #4) *(needs second source)*.
- **Hidden bolts/studs behind objects don't show in drawing views by default.** Toggle them on via advanced options (set to `TRUE` or `AS_PART`) — but you must *re-create* the view; existing views won't update (source: steelexplained quick-tips #8).

## Model-object handling

- **Hide model objects completely — hold `Shift` while clicking hide.** Plain right-click → Hide leaves the reference line behind (source: steelexplained 7-tips #3). See also [[KeyboardShortcuts]] for `Shift+H`.
- **Handles** indicate part direction — start handle is **yellow**, end handle is **magenta**. Part marks reference handles; you also modify part ends via handles. Select multiple handles with `Alt` + window-select. When cloning drawings or copying to another object, ensure handle directions match — use the *swap handles* macro if not (source: steelexplained 7-tips #7).
- **Corner chamfer on plates** — double-click a corner handle of a plate → chamfer properties dialog → choose chamfer type → Modify. Apply to multiple corners at once by multi-selecting handles (source: steelexplained 7-tips #6).
- **"Show with Exact Lines"** (right-click + hold `Shift`) — use to verify clearance e.g. between bolts and a profile radius. Beats eyeballing (source: steelexplained quick-tips #7).
- **Dimensioning curved/radiused members:** picking three random points on the member centerline gives wrong dimension strings. Curved members are auto-segmented internally — use snap override → *end* → click segment ends. Or turn on the part's reference line and click those points (source: steelexplained quick-tips #9).

## Project hygiene (define before you start)

Set these *before* modeling — sets the tone for a "tidy detailer" model (source: steelexplained 10-things #8):

- Fill in project properties
- Prefixes for all element types
- Element classes
- Material types
- Model phases
- Numbering settings
- Hole tolerances
- Dimensioning style
- Drawing templates
- Report layouts
- NC data settings
- Print options + line properties

## Recovery & maintenance

- **"Fatal: Model on disk is corrupted, use the latest backup model."** Solve by closing Tekla, deleting `model.db1` + `model.db2` from the model folder, renaming `model.db1.bak` + `model.db2.bak` to drop the `.bak` extension. Reopen (source: steelexplained 10-things #7).
- **Runaway work area after "Fit work area to entire model"?** Cause is usually a stray distant point/line. File → Diagnose & repair → *Find distant objects* lists them by ID — inquire or delete. Alternative: `Ctrl+A` with all selection switches on → deselect the real model via area-select + `Ctrl` → press `Delete` → run *Fit work area to entire model* again (source: steelexplained quick-tips #5).

## Materials

- **Add a custom material grade** — File → Catalogs → Material Catalog → right-click *Steel* → *Add grade* → rename + fill required fields. If you're not using analysis/design, profile density + plate density are the only fields you must populate (needed for weight calc) (source: steelexplained quick-tips #10).

## Related pages

- [[Index]] — landing page + page map
- [[QuickStart]] — license + UI + core workflow
- [[KeyboardShortcuts]] — full default shortcut reference
- [[SelectionAndSnapping]] — selection/snap switches deep dive
- [[IfcExport]] — IFC export workflow
