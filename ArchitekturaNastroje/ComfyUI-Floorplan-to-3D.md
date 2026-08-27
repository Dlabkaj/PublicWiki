# ComfyUI workflow — 2D půdorys → 3D barevný render

Zdroj: workflow stránka ComfyUI.org (katalog komunitních workflow šablon, ne oficiální ComfyUI dokumentace) — publikováno 2025-06-13. Třetí strana, fakta níže jsou tagovaná jako u běžného zdroje.

## Co workflow dělá

Konvertuje architektonický 2D půdorys (line-art) na 3D-barevný render: auto-coloring stěn/oken/nábytku přes ControlNet, generování materiálových textur (dřevo/sklo/dlažba), simulace osvětlení (přírodní i umělé stínování) a 4K upscaling přes UltimateSDUpscale. (source: https://comfyui.org/en/architectural-floor-plan-3d-rendering-workflow)

## Požadované modely a nody

- **Flux** — základní generativní model
- **ControlNet** (ControlNet-lineart, weight 0.8) — zachování původní struktury
- **LoRA** — "lwpm-Coloring LoRA", optimalizace distribuce barev, weight 0.6
- **AD-Laozhuang 1.5** — architektonicky specializovaný base model, vyžaduje komerční licenci *(needs second source)*
- Klíčové nody: `ConstrainImage|pysssss` (resize vstupu na 1024×1024 s gray padding), `CannyEdgePreprocessor` (prahy 100/200), `ControlNetApplyAdvanced` (end step 0.8), `CLIPTextEncodeFlux` (duální text encoder T5-XXL+CLIP-L), `UltimateSDUpscale` (R-ESRGAN_4x+, tile 512×512)

(source: https://comfyui.org/en/architectural-floor-plan-3d-rendering-workflow)

## Hardware

Doporučeno: nízké VRAM (≤8 GB). Podrobněji: base generování 8 GB, 4K upscale 16 GB+ — při nedostatku VRAM lze UltimateSDUpscale krok vypnout. (source: https://comfyui.org/en/architectural-floor-plan-3d-rendering-workflow)

## Vstup/výstup

- Vstup: PNG/JPG, čistý line-art bez textových popisků, uzavřené stěny, jasné pozice dveří/oken (příklad vstupu 1024×768)
- Výstup standard: 1024×768 barevný render; HD varianta: 2048×1536

(source: https://comfyui.org/en/architectural-floor-plan-3d-rendering-workflow)

## Troubleshooting (dle zdroje)

- Color bleed → snížit váhu LoRA (default 0.6 → 0.4)
- Structure drift (ztráta struktury) → zvýšit ControlNet end step (default 0.8 → 1.0)

(source: https://comfyui.org/en/architectural-floor-plan-3d-rendering-workflow)

## Poznámka k důvěryhodnosti

Stránka je z katalogu komunitních ComfyUI workflow šablon (marketing/blog formát s odkazy na desítky dalších workflow), ne z primární dokumentace nástroje ani od autora modelu AD-Laozhuang. Konkrétní čísla vah/prahů brát jako orientační výchozí hodnoty z jednoho zdroje, ne jako obecně ověřený standard.
