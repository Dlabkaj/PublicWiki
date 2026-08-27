# Sweet Home 3D — 3D View, Photos, Videos, Import/Export

**Summary**: 3D view modes and navigation, photo/video rendering, OBJ export, 3D model import, dimensions, texts, print, and plugins.

**Sources**: [Sweet Home 3D User's Guide](https://www.sweethome3d.com/users-guide/)

**Last updated**: 2026-06-22

---

## 3D view modes

### Aerial view (default)

**3D view > Aerial view** — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/), [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Switch to Aerial view mode — 3D view > Aerial view — Ctrl D"), [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/), and [nice photo rendering blog](https://www.sweethome3d.com/blog/nice-photo-rendering-sweet-home-3d/) ("Aerial view, the default option").

Navigate with mouse (left-button drag) or keyboard arrows — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("use the mouse or keyboard arrows to change the current point of view") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) (detailed A/D/W/S/arrow mappings).

### Virtual visit

**3D view > Virtual visit**

A virtual visitor icon appears in the plan, synced to the 3D camera. *(needs second source)*

Visitor indicators:
| Indicator | Function |
|-----------|----------|
| Head angle | Tilt head up/down |
| Field of view | Cone showing current view angle |
| Body angle | Rotate body left/right |
| Eyes elevation | Drag up/down to change observer height |

Navigate with mouse or keyboard arrows — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html).

## 3D view attributes

**3D view > Modify 3D view…** — confirmed by [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/)

- Ground color or texture
- Sky color or texture
- Light brightness
- Wall transparency

## Photo rendering

**Create photo…** toolbar button. Not available in Online or Mobile versions. *(needs second source)*

| Quality level | Output |
|---------------|--------|
| Fast | Looks like real-time 3D view |
| Best (2 levels) | Photorealistic; supports custom light power and time-of-day |

Renderers: **SunFlow** (default) or **YafaRay** (generally faster) — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("YafaRay renderer generally runs faster than SunFlow default renderer") and [nice photo rendering blog](https://www.sweethome3d.com/blog/nice-photo-rendering-sweet-home-3d/) ("Sunflow, the photorealistic rendering engine used in Sweet Home 3D by default ... try the YafaRay rendering engine added to version 7.0").

- Output format: **PNG**. *(needs second source)*
- Computing at best quality can take a very long time — confirmed by [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) ("This will take several minutes (or more)").
- Home can still be edited during render. *(needs second source)*
- Only one Create photo pane can be open at a time. *(needs second source)*

## Video creation

**Create video…** toolbar button. Not available in Online or Mobile versions. *(needs second source)*

Process: *(needs second source)*
1. Position camera in 3D view → click **red button** → adds a path point.
2. Move camera to next position → click red button again.
3. Repeat for full path.
4. Click **Create** → compute frames.
5. Click **Save…** → save as QuickTime file.

- Camera accounts for XY position, vertical elevation, 2 rotation angles, field of view. *(needs second source)*
- Use playback buttons to preview path (fast, no render). *(needs second source)*
- Computing can take minutes to hours depending on home complexity, quality, and hardware. *(needs second source)*
- Play with VLC or transcode to other formats (e.g. MPEG-4). *(needs second source)*

## OBJ export

**3D view > Export to OBJ format…** Not available in Online or Mobile versions. *(needs second source)*

Writes: `.obj` (geometry) + `.mtl` (materials) + texture images — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("create a MTL file describing their color and finally, it will save the images of the textures") and [official forum (Mike53)](https://www.sweethome3d.com/support/forum/viewthread_thread,9623) ("Sweethome3D ONLY exports to .obj, paired with a .mtl file").
Import into Blender / Art of Illusion for advanced rendering — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("reuse your home in 3D software like Blender or Art of Illusion") and [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) (Blender mentioned).

SH3D **only** exports to OBJ natively — for other CAD formats, use an online converter on the OBJ output. *(needs second source)* — [official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,9623)

⚠️ Known issue: OBJ export may fail on **macOS Sonoma** with "Can't create .OBJ file" error (reported Jan 2024; workaround unknown). *(needs second source)*

## HTML 3D export (plugin)

An **HTML plugin** exists that exports the 3D view for browser-based remote viewing. *(needs second source)* — [official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,9623) (separate from OBJ export; see Plugins in official docs)

## 3D model import

**Furniture > Import furniture…** Not available in Online version. Confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/), [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) and [official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,11733).

Supported formats: **OBJ, DAE, 3DS, ZIP** (containing OBJ/DAE/3DS), **KMZ**. Confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) and [Aaron Godfrey blog](https://aarongodfrey.dev/home%20automation/tips_for_creating_a_3d_floorplan_using_sweethome3d/) (OBJ/DAE/KMZ/3DS).

Wizard steps: *(needs second source)*
1. Choose model file.
2. Orient model (arrow buttons) so front face is forward.
3. Set name, size, elevation, color; flag as movable / door / window / staircase.
4. Set icon orientation for catalog thumbnail.
5. Click **Finish** → model appears in catalog and/or plan.

Free model sources:
- `https://www.sweethome3d.com/freeModels.jsp` — 1600+ contributor models *(needs second source)*
- Full version download includes 10,000+ models and 400 textures — confirmed by [Library blog](https://www.sweethome3d.com/blog/exploring-sweet-home-3ds-library-furniture-colors-and-more/) ("over 400 textures available").

**SH3F files** (model library bundles): install by double-click; uninstall by removing file from plugin folder and restarting. *(needs second source)*
**Furniture Library Editor**: separate tool, ~14.4 MB, available at SourceForge. *(needs second source)*

Under Windows/macOS: drag-and-drop a 3D model file directly into SH3D window to launch import wizard — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("Under Windows and macOS, you may also drag and drop a 3D model file in a Sweet Home 3D window to launch this wizard"), [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Drag and drop a OBJ, 3DS, DAE, KMZ or ZIP file onto catalog, furniture list or plan"), and [Keet on official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,11733).

**Quick drag-drop**: drag `.obj`, `.3ds`, or `.dae` from file manager **directly onto the 2D plan** — imports at the drop position (no wizard launch needed) — confirmed by [Keet on official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,11733) ("drag an .obj, .3ds, or .dae file from the file manager in the 2D design pane") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html). Can drag multiple files at once. *(needs second source)*

**Drag textures**: drag an image file into the texture preview/selection window to set a texture without using the file dialog — confirmed by [Keet on official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,11733) ("you can drag an image file in the image preview window where you select/set a texture") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("a BMP, JPEG, GIF or PNG file can be dragged onto wizard").

### OBJ import requirements

A model import needs ALL of (confirmed by Daniels118 + Keet on [official forum](https://www.sweethome3d.com/support/forum/viewthread_thread,11733)):
1. `.obj` file
2. `.mtl` file (materials — same directory, same base name)
3. Texture images (if any — sometimes a separate download; copy to the same directory as OBJ/MTL)

Extract archives without altering the directory structure so SH3D finds related files automatically. *(needs second source)*

### Third-party model tips

| Issue | Workaround |
|-------|-----------|
| Model all grey / no texture | Check you also downloaded the MTL file and textures |
| Parts misaligned | Open in Blender to fix alignment |
| Wrong scale | Move decimal point 1–2 places left |
| FBX format (not supported directly) | Blender: import FBX → export as 3DS → import in SH3D |
| No opening parts | External models never have opening parts unless made for SH3D |
| Monochrome model | Some free models have no materials by design (STL always monochrome) |

⚠️ **Blender 3DS export removed**: Blender 3.0+ dropped built-in 3DS export — use Blender 2.9 or install a custom addon. *(needs second source)*

Format quality ranking for third-party models (community experience): *(needs second source)*
1. **3DS** or **FBX→3DS** — best texture mapping
2. **OBJ + MTL** — good if full package downloaded
3. **DAE** — variable

## Dimensions

Click **Create dimensions** toolbar button. Two methods: *(needs second source)*

1. Click start point → click end point → click third time to set extension line size.
2. Hover over furniture border, wall side, or room side → double-click to accept temporary dimension → click third time to set extension line size.

No extension lines if mouse doesn't move between 2nd and 3rd click. *(needs second source)*

## Texts

Click **Add texts** button → click location in plan → type text in dialog. *(needs second source)*

Change font size and style (e.g. bold) of selected texts via text style toolbar buttons — confirmed by [User's Guide](https://www.sweethome3d.com/users-guide/) ("change the size and the style of the selected texts with the text style buttons") and [Shortcuts blog](https://www.sweethome3d.com/blog/2019/03/29/sweet_home_3d_shortcuts.html) ("Increase the text size ... Toggle bold text style ... Toggle italic text style").

## Print

- **File > Print…** or **File > Print to PDF…** — print furniture list + plan + current 3D view.
- **File > Print preview…** — preview.
- **File > Page setup…** — paper size, margins, orientation, plan scale, header, footer. Not in Online/Mobile. *(needs second source)*

## Plugins

Plugins extend SH3D features; written in Java. Not available in Online or Mobile. *(needs second source)*

Plugin file = **SH3P** file.

Install: *(needs second source)*
- **Windows / macOS**: double-click `.sh3p` file.
- **Linux**: copy to `~/.eteks/sweethome3d/plugins/` (if double-click doesn't work).
- Restart SH3D to activate.

Example: *Home Rotator* plugin adds Plan menu items to rotate all objects CW or CCW. *(needs second source)*

## Related

[[Index]]
[[Interface]]
[[Walls]]
[[FurnitureRooms]]
