# Tekla Structures — IFC Export

**Summary**: How to export a Tekla Structures model (or part of it) to IFC, what the export types mean, and what to check before/after. IFC is the open BIM exchange format — a clean export is the standard proof of interoperability.

**Sources**:
- https://support.tekla.com/doc/tekla-structures/2026/int_exporting_into_ifc (official, Tekla 2026)
- https://bimcorner.com/export-a-tekla-structures-model-to-an-ifc-file/ (practical walkthrough, 2021)

**Last updated**: 2026-06-05

---

## What it is

IFC (Industry Foundation Classes) is the open BIM exchange format. Tekla Structures can export the whole model or a selection to **IFC2x3**, **IFC4**, or **IFC4.3** (source: support.tekla.com 2026 int_exporting_into_ifc).

## Before you export

1. **Decide the export hierarchy** — from Organizer (recommended), from part UDAs, or from project property UDAs.
2. **Check that parts have known profiles** (source: official).
3. **Define IFC entities** for Tekla model objects if defaults need overriding.
4. **Modify property sets** if needed.
5. **Define a base point** if you'll export by base point (needed for multi-discipline coordination — see *Location by* below).
6. **Decide the purpose** — reference vs coordination vs cost estimation vs fabrication. Drives the export type choice (source: bimcorner).

### Default object → IFC class mapping

Tekla auto-classifies objects (source: bimcorner). Classes in parentheses can be re-assigned via the IFC export tab on the object:

| Tekla object | IFC entity |
| ------------ | ---------- |
| Beam | `IfcBeam` (or `IfcMember`) |
| Column | `IfcColumn` (or `IfcPile`, `IfcMember`) |
| Plybeam / Curved beam | `IfcBeam` (or `IfcMember`) |
| Pad / Strip footing | `IfcFooting` |
| Slab | `IfcSlab` |
| Panel | `IfcWall` or `IfcWallStandardCase` |
| Contour plate | `IfcPlate` (or `IfcDiscreteAccessory`) |
| Bolts / nuts / washers | `IfcMechanicalFastener` |
| Bolt holes | `IfcOpeningElement` |
| Vertical braces | `IfcMember` |
| Railings | `IfcBeam`, `IfcColumn` (or `IfcRailing`) |
| Assemblies, cast units | `IfcElementAssembly` (or `IfcRailing`, `IfcRamp`, `IfcRoof`, `IfcStair`, `IfcWall`) |
| Tekla project | `IfcProject` |
| Reinforcement | `IfcReinforcingBar` |
| Pour object / pour break | `IfcBuildingElementProxy` |
| Surface treatment | `IfcCovering` |
| Weld | `IfcFastener` |

## Export step-by-step (official)

1. Select model objects to export (skip selection to export all).
2. **File → Export → IFC**.
3. Load predefined export settings if any (located in environment folders).
4. **File name** — without extension; extension follows the chosen Format.
5. **Folder** — default is `\IFC` under the model folder. Absolute or relative paths accepted.
6. **Versions** — pick IFC2x3 / IFC4 / IFC4.3. The dialog reshapes based on version.
7. **Format** — `Ifc`, `IfcZip`, or `IfcXml` (IfcXml is IFC2x3 only).
8. **Export type** — see breakdown below.
9. **Selection** — All objects / Selected objects / Selected + their assemblies / Selection filter. *Include assembly information* exports the assembly hierarchy even when only part of an assembly is selected.
10. **Location by** — `Model origin`, `Work plane`, or `Base point: <name>`. For IFC4/IFC4.3 you also pick **Base point export** method: `IfcMapConversion` (schema-compliant IFC4) or `IfcSite coordinate system` (more viewer-compatible, including Trimble Connect).
11. **Object color** / **Layer names** — environment defaults usually fine.
12. **Attribute overrides** + **Property sets** — for Name/Description/Tag and custom data.
13. **Object types** — toggle Bolts, Welds, Grids, Reinforcing bars, Surface treatment & surfaces, Spaces.
14. Save settings to a new file if you'll reuse them (lands in `\attributes` under the model folder).
15. Click **Export**. A message box opens the output folder or the log file.

You can also **Export and upload to Trimble Connect** directly from the same dialog (source: official).

## Export types — pick by purpose

### IFC2x3

| Export type | Use when |
| ----------- | -------- |
| **Coordination View 2.0** | **Default — recommended.** Receiving app may edit/modify geometry. Reinforcing bars as extrusions; cuts/voids via CSG; curved as extrusions; bolts as B-rep. Certified. |
| **Coordination View 1.0** | You need voids and openings as separate `IfcOpeningElement` bodies. |
| **Surface geometry** | Display / reference model only — no re-use or editing. Everything (bars, curves, bolts) exported as B-rep. No CSG. |
| **Steel fabrication view** | Detailed steel for manufacturing. Bolt holes as voids; ships with `IfcPropertySetConfigurations_AISC.xml`. |

bimcorner notes that **Coordination View 2.0** is the recommended default — confirmed by the official 2026 doc.

### IFC4 / IFC4.3

| Export type | Use when |
| ----------- | -------- |
| **Reference view** | Coordination & referencing workflow. For viewer/estimator/builder downstream — not for converting back to native objects. |
| **Design transfer view** | Handover for further editing. Requires conversion of IFC entities to native objects in the receiving app; typically a one-off step. |
| **Precast view** (IFC4 only) | Fabrication data for precast walls/slabs with reinforcement + embeds. Only available in precast roles. Per official: *IFC files exported with Precast view do not contain layer information.* |
| **Bridge view** (IFC4.3 only) | Bridge constructions using the IFC4.3 schema. |

## Limitations to know

Per official 2026 doc:

- **Edge chamfers are omitted** from the exported IFC. Workaround: set IFC export type to B-rep per object via UDAs / IFC export tab.
- **IFC2x3**: rebar assemblies *don't work* — use IFC4 export for rebar assemblies.
- **Pour unit export** is not supported.
- **Export flat wide beams as plates** only works in Coordination View 1.0 / 2.0. In Steel fabrication view / Surface geometry it has no effect; workaround is to set `IfcPlate` as the IFC entity for the beam.

## After export — verify

- **Re-import the IFC as a reference model** back into Tekla. Visual check: is it positioned correctly, is anything missing? Won't catch a single bolt missing but will catch large omissions (source: bimcorner).
- **Read the LogFile** — it lists exported entities and any errors (source: both).

## Useful advanced options

| Option | Purpose |
| ------ | ------- |
| `XS_ENABLE_POUR_MANAGEMENT = TRUE` | Required to have pour objects/pour units (2018+) in the model. |
| `XS_EXPORT_IFC_REBARSET_INDIVIDUAL_BARS` | `FALSE` (default) = groups; `TRUE` = individual bars. |
| `XS_EXPORT_BREP_AS_EXACT_SOLID = TRUE` | Export B-rep objects as exact solids in IFC2x3. Larger files, slower export. |
| `XS_CS_CHAMFER_DIVIDE_ANGLE = 10` | Get smoother edges when exporting B-reps as exact solids. |
| `XS_IFC_EXPORT_OBJECT_LAYER_FROM_UDA` | Use a UDA as the layer name (IFC2x3). |

## File formats (IFC variants)

| Format | What it is |
| ------ | ---------- |
| `.ifc` | Default plain ASCII text exchange. |
| `.ifcXML` | XML structure instead of ASCII. *Usually 300–400% larger than `.ifc`.* (source: bimcorner) *(needs second source)* |
| `.ifcZIP` | Compressed `.ifc` (~60–80% reduction) or `.ifcXML` (~90–95% reduction). (source: bimcorner) *(needs second source)* |

## Beginner takeaway

For a demo model: export **IFC2x3, Coordination View 2.0, Location by Model origin**, then re-import the result as a reference model in a fresh window to verify it looks right. Being able to say "verified by re-import + log file check" is what separates a checked export from a hopeful one (source: bimcorner pattern).

## Related pages

[[Index]] · [[QuickStart]] · [[BeginnerTips]]
