# Tekla Structures — Quick Start

**Summary**: Bare-basics quick start for a new Tekla Structures user: get a free student license, learn the UI, and build a first simple 3D model (footings, columns, beams, connections) through drawings, reports, and IFC export.

**Sources**: support.tekla.com "First steps with Tekla Structures", support.tekla.com modeling videos, download.trimble.com student pages, tekla.com Campus, bimcorner.com — all accessed 2026-06-05. Links inline below.

**Last updated**: 2026-06-05

---

## 0. Get the software (free, for students)

Installation itself is skipped here (already installed). For license activation:

1. Create a free **Trimble Identity**.
2. Sign in to your **Tekla Online Profile** with that identity → **Activate licenses** tab → activate the **student subscription** (no cost).
3. Download installer + needed **environment** installers/extensions (the environment sets defaults like profiles, materials, drawing standards).

Free learning path: **[Tekla Campus](https://www.tekla.com/solutions/campus/students)** gives step-by-step video tutorials plus the full **Tekla Structures Learning Edition for four months**. The official **[First steps with Tekla Structures](https://support.tekla.com/learn/first-steps-with-tekla-structures)** eLearning course (introduction + 6 modules + final test, **digital badge** on completion) is the canonical beginner track and covers exactly what's needed for a small demo: create project → navigate → footings/columns/beams → selection switches/filters → copy & multi-edit → connections → GA drawing → basic report → IFC export (source: https://support.tekla.com/learn/first-steps-with-tekla-structures).

> Note: tutorials default to the **metric system** and the **default environment**. Keep those for the demo unless there's a reason not to.

## 1. The interface (orientation)

Main UI pieces a beginner must know:

- **Ribbon** — top toolbar, command tabs grouped by task (model parts, drawings, etc.).
- **File menu** — new/open/save, import/export, settings.
- **Side pane** — panels like the component catalog, properties, etc.
- **Views** — you work in model views; a **3D view** plus **plan/elevation** views. Learn to orbit, zoom, pan, and switch between views.
- **Selection switches** — control **what** you can pick (parts, points, components, assemblies…). If you can't select something, check these.
- **Snap switches** — control **where** your clicks land (endpoints, midpoints, intersections, grid points, free points). This is how you place things precisely. Most beginner placement frustration = wrong snap settings.
- **Filters** — narrow selections in big models.

Three workspaces conceptually: **Modeling** (build the 3D model), **Drawing** (generate construction drawings), **Report** (lists/quantities).

## 2. Core modeling workflow (first model)

Order the official "First steps" course follows:

1. **Create a new project** — set basic project properties.
2. **Create grids** — the grid defines your column/beam locations (X/Y lines + levels). Everything snaps to the grid. Set spacing to match your intended building.
3. **Add footings / pad foundations** — at grid intersections.
4. **Add columns** — place at grid intersections; pick a profile (e.g. an HEA/HEB or hollow section for steel). See [Modeling steel columns and beams](https://support.tekla.com/video/modeling-steel-columns-and-beams).
5. **Add beams** — span between columns along grid lines; floor beams as needed. See [Modeling columns, beams, and slabs](https://support.tekla.com/video/modeling_columns_beams_and_slabs).
6. **Copy & modify** — use copy tools to repeat parts across the grid; multi-edit properties to change many parts at once. (Big time-saver and a "care/detail" signal.)
7. **Add connections** — drop **connection components** between beams and columns (e.g. end-plate, base plate). Tekla auto-builds the plates/bolts/welds. See [Modeling beam to column connections](https://support.tekla.com/video/modeling-beam-to-column-connections).

## 3. Output

8. **General arrangement (GA) drawing** — create from the model, modify it, preview, print. This is the simplest drawing type and enough for a demo.
9. **Basic report** — generate a parts/quantities list from the model.
10. **Export IFC** — the open BIM exchange format; the usual hand-off to other disciplines.

## 4. Beginner tips

- **Snap switches first.** When placement misbehaves, check snaps before anything else.
- **Grid is the skeleton.** Get grid spacing/levels right early — re-doing it later is painful.
- **Use the default/metric environment** for consistency with tutorials.
- **Numbering** — Tekla assigns part/assembly marks; running numbering before drawings/reports keeps everything consistent (detail polish).
- Keep the first model **small and finished**: a single bay or small frame fully detailed beats a half-built tower.

## Related pages

[[Index]]
