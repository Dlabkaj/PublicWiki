# Tekla Structures — Concrete Rebar (Footings)

**Summary**: How to reinforce concrete footings in Tekla Structures — the three rebar systems (rebar sets, legacy bar groups, auto-components), and a practical recipe for vertical bars in pad footings plus lapping perimeter bars in strip footings. Aimed at a symbolic demo model, not code-compliant design.

**Sources**: interactive modeling session 2026-06-06 (REBAR ribbon observed in Tekla Structures 2026 Educational version); general Tekla rebar workflow knowledge. Exact component names *(verify in your environment's catalog)*. Fills the concrete-rebar gap left out of the initial Tekla research pass.

**Last updated**: 2026-06-06

---

## Three ways to place rebar

The **REBAR** ribbon tab exposes two systems; a third lives in the component catalog:

| System | Tools | When to use |
| ------ | ----- | ----------- |
| **Rebar sets** (modern) | Crossing, Longitudinal, By face, By guidelines | Shape-adaptive bars that update when the concrete changes. Easiest to edit. Best default for a demo. |
| **Legacy reinforcement** | Bar group, Single bar, Mesh, Strand | You draw the bar shape and distribution by hand. Full manual control. |
| **Components** (auto) | Concrete tab → Applications & components (**Ctrl+F**) → search `footing` | One drop auto-reinforces a whole footing (bottom mat + edge/vertical bars). Least effort, tidy result. |

For a task judged on care/detail/3D-orientation (not engineering), the pragmatic combo is: **components for bulk, hand-placed bars for the parts you want to show off.**

## Fastest: footing reinforcement component

1. **Concrete** tab → **Applications & components** catalog (**Ctrl+F**).
2. Search `footing` → e.g. **Pad footing reinforcement** / **Strip footing reinforcement** *(names vary by environment)*.
3. Click the component, then click the footing part. It generates bottom mat + vertical/edge bars.
4. Double-click the component symbol to edit bar size, spacing, cover.

## Manual recipe

### Vertical bars in corner pad footings (dowels / starters)
- Work in a **side / elevation view** (or section) so the pad height is visible — placement is far easier than in 3D.
- REBAR → **Single bar**: draw one vertical bar inside the pad, snapping to top/bottom faces and respecting cover.
- REBAR → **Bar group** (or select the bar and array it): spread it into a grid across the pad plan area. Set diameter + spacing in Properties.
- Model one pad fully, then **copy** the rebar to the other corner pads (efficient + consistent — a deliberate-looking detail).

### Lapping horizontal bars around the foundation (strip footings)
- These are longitudinal bars running along the strips, looping the perimeter.
- Best tool: rebar set **Longitudinal** or **By guidelines** — pick the strip, draw bars along its length; they adapt if the part changes.
- **Lap splices** at corners: with rebar sets, use the splice option (Edit → splice) so Tekla generates laps automatically. With legacy bar groups, overlap two groups manually by the lap length.

## Gotchas

- **Rebar belongs to a part.** One rebar set spans a single concrete part (or the faces you select). If pads and strips are **separate parts**, create bars per part and **lap them at the joints** — don't expect one bar to run through everything. (Modelling the foundation as one cast-in-place part avoids this, but don't re-model just for this.)
- **Cover** — set concrete cover in rebar properties so bars sit *inside* the concrete. Bars poking out / floating in air is the #1 beginner tell.
- **Use a section/elevation view** for placement precision; use 3D only to sanity-check.
- **Numbering** — run numbering afterward so bars get marks. Clean rebar marks in a drawing read as attention to detail.

## Related pages

[[Index]] · [[QuickStart]] · [[BeginnerTips]]
