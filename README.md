# A Scalability Mod for [Metal Gear Solid Δ: Snake Eater](https://store.steampowered.com/app/2417610/METAL_GEAR_SOLID_D_SNAKE_EATER/)

This mod provides a **graphics tuning overhaul** for Metal Gear Solid Δ: Snake Eater, focusing on **better balancing image quality against performance**.  

In the vanilla game, **Low settings have lazy implementations** — they simply disable features outright instead of offering optimized alternatives. For example, disabling shadows or ambient occlusion entirely rather than using cheaper non-RT methods.  

This mod reworks scalability groups to **preserve visual quality while still reducing GPU load**, ensuring that each setting tier offers meaningful performance savings without turning the game into a downgraded mess.

---

## ✨ Features

- **Antialiasing Overhaul**  
  - Implements recommended **TAA/TSR tweaks** from [Hybred's UE Tweaks](https://www.reddit.com/r/MotionClarity/comments/1gghasv/best_unreal_engine_antialiasing_tweaks/).  
  - Adds **tonemapper sharpening** for a clearer image.  
  - Note: The game hardcodes `r.AntialiasingMethod=4` (TSR). Changing AA method requires editing `Engine.ini` or using launch options.

- **Shadow Quality Revamp**  
  - Low now uses **traditional shadow maps**.  
  - Medium–Ultra utilize **Virtual Shadow Maps (VSM)**.  
  - Fog scalability tied to Shadow Quality for consistency.

- **Global Illumination & Ambient Occlusion**  
  - Restores **DFAO (Distance Field AO)** as a fallback when Lumen is disabled.  
  - Balances performance with **Software Lumen** and **Hardware Lumen** presets.  
  - SSAO properly stacks with Lumen at higher quality levels.

- **Texture Quality Improvements**  
  - Adjusts **MipMapBias** and **Anisotropic Filtering** per quality level.

- **Reflections & SSR Adjustments**  
  - Low disables SSR; Medium enables Half-Res; High/Ultra use Full-Res.

- **Other Fixes**  
  - Proper **View Distance scaling** that affects foliage/NPCs.  
  - Balanced **Foliage and Shading quality** to match cinematic settings.  
  - Adjusted **Motion Blur** so cutscenes remain cinematic while gameplay is cleaner.

---

## 📊 Quality Level Breakdown

### Shadows
- **Low** → Shadow maps (512px, 1 cascade), Volumetric Fog off  
- **Medium** → Shadow maps (1024px, 4 cascades), Volumetric Fog enabled (16–64)  
- **High** → VSM on, higher fidelity fog (16–128)  
- **Ultra** → VSM on, cinematic fog (8–128)

### Global Illumination
- **Low** → DFAO only  
- **Medium** → Software Lumen, 48x Downsample  
- **High** → Hardware Lumen, 24x Downsample  
- **Ultra** → Hardware Lumen, 12x Downsample   

### Textures
- **Low** → MipBias +2, Aniso x4  
- **Medium** → MipBias +1, Aniso x8  
- **High** → MipBias 0, Aniso x8  
- **Ultra** → MipBias –1, Aniso x16  


---

## ⚠️ Limitations

- **Antialiasing Method is locked** by the game (`r.AntialiasingMethod=4`).  
  - Can only be overridden via **Engine.ini edits** or CLI commands.  
- **Texture PoolSize is capped at 2000**, likely due to engine-side restrictions.  
- Some **NPC/foliage quirks** occur if ViewDistance is pushed too far.
