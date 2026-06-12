# 🚁 Drone Vision Forge

### Advanced AI Image Synthesis | SDXL + ControlNet + LoRA Fusion

---

## 📌 Overview

**Drone Vision Forge** is a high-performance AI image generation system specifically designed to produce ultra‑HD, photorealistic drone imagery. Built on **Stable Diffusion XL (Base + Refiner)** and enhanced with **ControlNet Depth**, **LoRA style fusion**, and advanced prompt engineering, it delivers cinematic‑quality results suitable for synthetic data generation, concept art, and visual prototyping.

---

## ✨ Key Features

- **Dual‑Stage Generation**  
  SDXL Base → latent space → SDXL Refiner for enhanced detail and sharpness

- **Multi‑Dimensional Prompt Engineering**  
  Supports **10 drone types**, **10 color palettes**, **10 environments**, and **6 lighting styles**  
  → Over **6,000 unique combinations**

- **Advanced Optimizations**  
  - xFormers memory‑efficient attention  
  - VAE tiling for high‑resolution support (2K+)  
  - CPU offload for low‑VRAM environments  
  - Compel prompt weighting (`++` / `--` syntax)

- **Post‑Processing Pipeline**  
  Sharpness, contrast, color enhancement, and unsharp masking for final polish

- **Batch Generation & Metadata Export**  
  Generate multiple images from configuration lists; each output saved as PNG with full metadata (seed, type, environment, lighting, generation time)

- **Gallery Visualization**  
  Display generated images in a clean grid with embedded metadata labels

---

## 🧠 Supported Attributes

| Category       | Options (10 each)                                                                 |
|----------------|------------------------------------------------------------------------------------|
| **Drone Types** | racing, military, delivery, photography, nano, agri, solar, swarm, underwater, combat |
| **Colors**      | stealth black, arctic white, military olive, neon cyber, fiery orange, forest camo, chrome silver, deep red, gold luxury, desert tan |
| **Environments**| golden field, cyber city, arctic tundra, deep jungle, stormy sky, desert dunes, ocean cliffs, volcano, studio white, space orbit |
| **Lighting**    | golden hour, dramatic rim, overcast soft, neon glow, stormy, blue hour            |

---

## 🛠️ Tech Stack

- **Diffusers** (v0.27+)
- **Transformers** (v4.40+)
- **Accelerate** & **xFormers**
- **ControlNet Aux**
- **Compel** (prompt weighting)
- **Hugging Face Hub**
- **PyTorch** (v2.2+ with CUDA)

---

## 🚀 Quick Start

```python
from drone_vision_forge import DroneImageForge

# Initialize pipeline (auto-detects GPU)
forge = DroneImageForge(pipe, refiner, compel, engineer)

# Generate a single image
result = forge.generate(
    drone_type='racing',
    color='neon_cyber',
    environment='cyber_city',
    lighting='neon_glow',
    width=1024,
    height=1024,
    steps=40,
    seed=42
)

# Save output
result['image'].save('drone_output.png')
```

### Batch Generation

```python
configs = [
    {'drone_type': 'military', 'color': 'stealth_black', 'environment': 'stormy_sky'},
    {'drone_type': 'agri', 'color': 'forest_camo', 'environment': 'golden_field'}
]
results = forge.generate_batch(configs)
```

---

## 📊 Output Example

```
✅ Generated in 30.1s | Seed: 42042
💾 Saved: drone_racing_neon_cyber_42042.png
```

**Metadata included:** drone type, color, environment, lighting, seed, generation time.

---

## 🖼️ Gallery Display

```python
display_drone_gallery(results, cols=3, figsize_per=5.5)
```
Renders a polished grid with metadata labels under each image. Gallery saved as `gallery_overview.png`.

---

## 🧪 System Requirements

- **GPU:** NVIDIA Tesla T4 (15.6 GB VRAM) or equivalent  
- **RAM:** 16 GB+ recommended  
- **Storage:** ~10 GB for model weights  
- **Python:** 3.10+  
- **CUDA:** 12.0+ (optional, CPU fallback available)

---

## 📁 Project Structure

```
drone-vision-forge/
├── notebook.ipynb              # Main Jupyter Notebook
├── drone_output/               # Generated images and galleries
├── requirements.txt            # Dependencies
└── README.md                   # This file
```

---

## 📜 License

MIT License – free for academic and commercial use.

---

## 🙏 Acknowledgments

- [Stability AI](https://stability.ai/) for SDXL models  
- [Hugging Face](https://huggingface.co/) for Diffusers & Transformers  
- [madebyollin](https://huggingface.co/madebyollin) for fp16‑fixed VAE

---

## 📬 Contact

For questions or contributions, feel free to open an issue or pull request.

---

**Drone Vision Forge – Elevate your aerial imagery.** 🚁
