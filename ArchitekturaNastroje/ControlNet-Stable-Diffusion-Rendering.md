# ControlNet + Stable Diffusion — architektonické renderování ze skic

Zdroj: tutoriálový blog agentbus.sh (obecný AI-guides web, autor Qasim, publikováno 15. února 2026, čtení 7 min) — třetí strana, ne autorita nástroje. Fakta níže jsou tagovaná jako u běžného zdroje.

## Princip

ControlNet se Stable Diffusion umí ze skici, Canny edge mapy nebo depth-extrahovaného půdorysu vygenerovat vyrenderovanou scénu "za méně než minutu" *(needs second source)* — zdroj neuvádí hardware ani rozlišení, ke kterým se čas váže. Zdroj uvádí, že kvalita zatím nenahradí finální klientské výstupy, ale hodí se pro rané concept-exploration a mood boardy. (source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

## Instalace

```
pip install diffusers transformers accelerate torch controlnet-aux pillow
```
(source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

## Minimální pipeline (Canny edge conditioning)

```python
import torch
from diffusers import StableDiffusionControlNetPipeline, ControlNetModel
from diffusers.utils import load_image
from controlnet_aux import CannyDetector

controlnet = ControlNetModel.from_pretrained(
    "lllyasviel/sd-controlnet-canny",
    torch_dtype=torch.float16,
)
pipe = StableDiffusionControlNetPipeline.from_pretrained(
    "stable-diffusion-v1-5/stable-diffusion-v1-5",
    controlnet=controlnet,
    torch_dtype=torch.float16,
)
pipe.enable_model_cpu_offload()

sketch = load_image("sketch_facade.png")
canny = CannyDetector()
edges = canny(sketch, low_threshold=50, high_threshold=150)

result = pipe(
    prompt="photorealistic modern house exterior, concrete and glass facade, "
           "warm sunset lighting, landscaped garden, architectural photography, "
           "8k, sharp detail",
    negative_prompt="blurry, cartoon, sketch, low quality, deformed, watermark",
    image=edges,
    num_inference_steps=30,
    controlnet_conditioning_scale=0.85,
).images[0]

result.save("rendered_facade.png")
```
(source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

Nižší `controlnet_conditioning_scale` = víc kreativní volnosti; vyšší = větší věrnost skice. (source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

## Volba ControlNet módu podle vstupu

- **Canny edges** — čisté liniové kresby (fasády, pohledy, wireframy s ostrými obrysy). Doporučené prahy: low 50-100, high 150-250
- **Depth maps** — 3D modely / prostorové vztahy, vstup z MiDaS nebo Z-buffer render
- **Lineart** (model `lllyasviel/control_v11p_sd15_lineart`) — ručně kreslené skici, natrénováno na uměleckých liniích na rozdíl od Canny (fotografické hrany)

(source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

## Prompt engineering pro architekturu

Doporučená struktura promptu: subjekt (typ budovy + styl, např. brutalist/mid-century/parametric/biophilic) → materiály (konkrétní texturové názvy, model je zná a renderuje s odpovídajícími odrazy) → fotografický styl (např. "golden hour lighting, architectural photography, Dezeen magazine style, 8k"). Odkaz na konkrétní publikace (Dezeen, ArchDaily, Architectural Digest) v promptu tlačí model k editorial-kvalitním kompozicím. (source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

## Konzistence napříč dávkou renderů (více pohledů stejného projektu)

Doporučený přístup: fixovaný seed + identický prefix promptu napříč renderů, měnit jen suffix pro konkrétní pohled (např. "front facade view" vs. "interior"). Zdroj upozorňuje, že stejný seed nezaručí identické obrázky (control images se liší), ale drží konzistentní paletu barev, materiály a náladu osvětlení. Pro těsnější konzistenci doporučuje kombinaci s IP-Adapter (referenční render jako style image + skica jako structural control). (source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)

## Časté chyby a řešení (dle zdroje)

- **Tensor device mismatch** → použít `enable_model_cpu_offload()` místo ručního `.to("cuda")`
- **Výstup ignoruje skicu** → zvýšit `controlnet_conditioning_scale` (start 0.85, až 1.0); zkontrolovat, zda Canny práh není příliš agresivní
- **Rozmazané/vymyté renderery** → zvýšit `num_inference_steps` z 30 na 50; přidat "blurry, soft focus, haze" do negative promptu
- **CUDA out of memory** → `enable_model_cpu_offload()` + `enable_vae_slicing()` + `enable_vae_tiling()` pro chunk-wise VAE decode
- **Špatná velikost control image** → resize skici na cílové rozlišení před preprocessingem (`Image.LANCZOS`)
- **Nekonzistentní styl napříč dávkou** → držet 80 % promptu identických, měnit jen view-specific suffix

(source: https://agentbus.sh/posts/how-to-build-ai-architectural-rendering-with-controlnet-and-stable-diffusion/)
