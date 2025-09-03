# A Scalability Mod for [Metal Gear Solid Δ: Snake Eater](https://store.steampowered.com/app/2417610/METAL_GEAR_SOLID_D_SNAKE_EATER/)

This mod provides a **graphics tuning overhaul** for Metal Gear Solid Δ: Snake Eater, focusing on **better balancing image quality against performance**.  

In the vanilla game, **Low settings have lazy implementations** — they simply disable features outright instead of offering optimized alternatives. For example, disabling shadows or ambient occlusion entirely rather than using cheaper non-RT methods.  

This mod reworks scalability groups to **preserve visual quality while still reducing GPU load**, ensuring that each setting tier offers meaningful image quality for the performance it provides.

---

## ✨ Features

- **Antialiasing Overhaul**  
  - Implements recommended **TAA/TSR tweaks** from [Hybred's UE Tweaks](https://www.reddit.com/r/MotionClarity/comments/1gghasv/best_unreal_engine_antialiasing_tweaks/).  
  - Adds **tonemapper sharpening** for a clearer image.  
  - Note: The game hardcodes `r.AntialiasingMethod=4` (TSR). Changing AA method requires editing `Engine.ini` or using launch options.

- **Shadow Quality Revamp**  
  - Low now uses **traditional shadow maps**.  
  - Medium–Ultra utilize **Virtual Shadow Maps (VSM)**.  

- **Global Illumination & Ambient Occlusion**  
  - Restores **DFAO (Distance Field AO)** as a fallback when Lumen is disabled.  
  - SSAO properly stacks with Lumen at higher quality levels.

- **Texture Quality Improvements**  
  - Adjusts **MipMapBias** and **Anisotropic Filtering** per quality level.

- **Reflections & SSR Adjustments**  
  - Improved SSR quality.

- **Other Fixes**  
  - Adjusted **Motion Blur** so cutscenes remain cinematic while gameplay is cleaner.

---

## 📊 Quality Level Breakdown

### Shadows
- **Low** → Shadow maps (512px, 1 cascade)  
- **Medium** → Shadow maps (1024px, 3 cascades)  
- **High** → VSM 4x  
- **Ultra** → VSM 8x  

### Global Illumination
- **Low** → DFAO only  
- **Medium** → Lumen, 64x Downsample + ShortRangeAO  
- **High** → Lumen, 32x Downsample + ShortRangeAO  
- **Ultra** → Lumen, 32x Downsample + DiffuseIndirect.SSAO   

### Textures
- **Low** → MipBias +1, Aniso x4  
- **Medium** → MipBias 0, Aniso x8  
- **High** → MipBias -1, Aniso x8  
- **Ultra** → MipBias –2, Aniso x16  


---

## ⚠️ Limitations

- **Antialiasing Method is locked** by the game (`r.AntialiasingMethod=4`).  
  - Can only be overridden via **Engine.ini edits** or CLI commands.  
- **Texture PoolSize is capped at 2000**, likely due to engine-side restrictions.  
