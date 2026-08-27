# Sweet Home 3D — Photo Rendering Workflow

**Summary**: Detailed guide for getting realistic photo renders — camera setup, quality levels, lens options, lighting, and sun simulation.

**Sources**: [How to get a nice photo rendering (official blog, Dec 2016)](https://www.sweethome3d.com/blog/nice-photo-rendering-sweet-home-3d/)

**Last updated**: 2026-06-22

---

## Camera / point of view

Two view modes (also used for photos — see [[ThreeDView]]): *(unverified)*

- **Aerial view** — perspective around the home; preference "Aerial view centered on selection" makes it orbit the selected object. *(unverified)*
- **Virtual visit** — human-level camera; placed in plan, oriented with mouse/keyboard. *(unverified)*

### Field of view

Default horizontal field of view: **63°** (≈ 29 mm lens on 24×36 full-frame camera). *(unverified)*

Change it via **3D view > Modify virtual visitor…** dialog. *(unverified)*

Wider FOV (e.g. 70°) shows more of the scene from the same position. *(unverified)*

### Store / restore point of view

- **Store**: 3D view > Store point of view (`Ctrl Alt R` / `Cmd Alt R`) OR right-click in 3D view → Store point of view… → give it a name *(unverified)*
- **Restore**: right-click in 3D view → **Go to point of view** → select saved name *(unverified)* — [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/)

---

## Creating a photo

Menu: **3D view > Create photo** *(unverified)*

### Quality levels (4 levels)

| Level | Speed | Notes |
|-------|-------|-------|
| 1 — Fastest | Fast | Same quality as real-time 3D view |
| 2 | Medium | |
| 3 — Second-best | Slow | Lighting simulation active; extra options unlocked |
| 4 — Best | Slowest | Full photorealistic; lighting simulation active; extra options unlocked |

At the **two best quality levels**, extra options appear: *(unverified)*

### Lens options (best 2 levels only)

| Lens | Notes |
|------|-------|
| Pinhole (default) | Infinite depth of field |
| Depth of field | Focus distance 250 cm; limited DoF |
| Fisheye | Special use cases |
| Spherical | Special use cases |

### Image size

- More pixels = more detail + longer compute + larger file. *(unverified)*
- Create large images only once lighting is confirmed correct. *(unverified)*
- Proportions: apply 3D view ratio, choose standard ratio, or set custom width/height. *(unverified)*

⚠️ **"3D view" proportions gotcha**: if "Apply proportions = 3D view" is selected, the render shows ONLY what is currently visible in the 3D viewport — not the full plan. Use a standard ratio for full-plan renders. *(unverified)* — [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/)

### Rendering engines

| Engine | Notes |
|--------|-------|
| SunFlow (default) | Open-source photorealistic renderer |
| YafaRay | Added in v7.0; generally faster than SunFlow |

---

## Lighting

### Ceiling lights (auto-added)

SH3D adds **ceiling lights in the centre of each room by default**. *(unverified)*

⚠️ **Ceiling lights only added to areas defined as rooms** using the Create rooms tool. Having 4 walls is NOT enough — if a space has no Room object, it gets no auto ceiling light. *(unverified)* — [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/)

Disable with the **"Add ceiling lights"** option in the Create photo pane (best 2 quality levels). *(unverified)*

Recommendation: if the home already has many lamps, disable ceiling lights to avoid overexposure. Default brightness often too high. *(unverified)*

### Light sources from catalog

- Found in **Lights category** of the furniture catalog. *(unverified)*
- Types: White, Incandescent (warmer), Fireglow, and others with different colors/temperatures. *(unverified)*
- Default light power: **50% of maximum**. *(unverified)*
- More lights = longer render time. *(unverified)*
- **Warning**: when resizing a light source, do not let it touch the ceiling — ceiling turns black at the intersection. *(unverified)*

### Adjust light power

Methods: *(unverified)*
1. Drag the **power indicator** on the light in the plan.
2. Select lights → **Furniture > Modify…** → edit **Light power** field.
3. **Batch**: hold `Shift` + left-click each fixture → right-click → **Modify furniture…** → change Light power % for all at once. *(unverified)* — [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/)

### Sunlight

Controlled by **Date and Time** in the Create photo dialog. *(unverified)*

Sun direction also depends on: *(unverified)*
- Geographical location (set in compass dialog)
- Home orientation (compass North direction)

Set North: **Plan > Modify compass** — rotate compass object in plan. *(unverified)*

Note: when camera is placed inside the house, sunlight alone often doesn't produce enough illumination in SH3D — add extra light sources. *(unverified)*

### Shininess

Objects can be set to **Matt** (less shiny) in the furniture dialog. *(unverified)*
Reduces over-specular highlights on furniture like doors, windows, frames, tulips, etc. *(unverified)*

---

## Rendering workflow (recommended)

1. Choose point of view; store it.
2. Set Date/Time and compass/North for desired sunlight.
3. Disable "Add ceiling lights" if home is already well-lit.
4. Set light source powers; keep to 10–30% range for realism.
5. Render at lower quality first to check lighting balance.
6. Set Matt shininess on overspecular objects.
7. Add extra White/Incandescent light sources as fill; keep them off the ceiling.
8. Final render at best quality with desired pixel size.

*(workflow inferred from blog tip, not an official numbered list)*

---

## Related

[[ThreeDView]]
[[FurnitureRooms]]
[[Index]]
