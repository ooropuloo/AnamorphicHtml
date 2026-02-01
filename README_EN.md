# AnamorphicHtml — Glasses-Free 3D on L-Shaped Screens (WIP)

[![Status](https://img.shields.io/badge/Status-Experimental-orange)](https://github.com/ooropuloo/AnamorphicHtml)
[![Help Wanted](https://img.shields.io/badge/Help%20Wanted-Feedback%20Needed-red)](https://github.com/ooropuloo/AnamorphicHtml/issues)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

English | [中文](README.md)

An experimental project exploring whether pure frontend technology (HTML5 Canvas + JavaScript) can achieve mall-grade **glasses-free 3D effects** on **L-shaped flexible AMOLED screens**.

![Preview](images/preview.jpg)

> **⚠️ Current Status: Not Yet Achieving Desired Effect**
>
> The current algorithm can perform geometric deformation, but fails to produce the correct depth illusion that makes objects appear to "pop out" of the screen.
>
> **I desperately need community suggestions and help!**

---

## Table of Contents

- [Hardware Specs](#️-hardware-specs)
- [The Problem](#-the-problem)
- [Current Implementation](#️-current-implementation)
- [File Structure](#file-structure)
- [How to Run](#-how-to-run)
- [Help Wanted](#-help-wanted)
- [Related Technical Fields](#-related-technical-fields)
- [Contributing](#-contributing)

---

## 🖥️ Hardware Specs

Instead of using spliced screens, I'm using a single **Flexible AMOLED** panel bent into an L-shape, eliminating the bezel gap in the middle. This should theoretically provide a more seamless illusion.

| Specification | Value |
|---------------|-------|
| Size | 6.67 inch |
| Resolution | 1080(W) × 2400(H) (aspect ratio ~1:2.2) |
| Active Area | 154.56mm × 69.552mm |
| Bend Configuration | Screen bent 90° at midpoint, forming floor and back display surfaces |

With smartphone-grade pixel density, close-range viewing should be far more detailed than mall LED walls.

---

## ❓ The Problem

The L-shaped glasses-free 3D displays in shopping malls (like spaceships or whales appearing to fly out) are stunning. My current approach is to apply keystone/mesh distortion to regular 2D videos and project them onto the L-shaped screen.

**Result:** ❌ The geometry looks correct, but it appears as "flat wallpaper pasted on a corner" — no depth perception.

### My Current Hypothesis

After research, I believe simple 2D Canvas warping is insufficient because:

1. **Lack of Off-axis Projection**: Mall content is rendered from 3D software with asymmetric view frustums targeting a specific sweet spot — not post-processed warping of 2D footage.

2. **No Depth Information**: Regular 2D video has no Z-axis data, making it impossible to correctly remap pixels to their proper positions in L-shaped 3D space.

---

## 🛠️ Current Implementation

A pure frontend experimental tool — no backend required, just open in a browser.

**Tech Stack**: HTML5 Canvas 2D (no WebGL), Vanilla JS

**Features**:
- Bilinear Interpolation Mesh Deformation
- Real-time L-shaped screen 3D preview
- Adjustable parameters: panel angle, perspective intensity, shadow simulation
- **Baking**: Export warped video as WebM (VP9)

---

## File Structure

```
AnamorphicHtml/
├── images/
│   └── preview.jpg               # Tool preview screenshot
├── anamorphic-3d-converter.html  # Main tool (3D preview + adjustment + baking)
├── index.html                    # Legacy 6-point calibration tool
├── LICENSE
├── README.md                     # Chinese README
└── README_EN.md                  # English README
```

---

## 🚀 How to Run

```bash
git clone https://github.com/ooropuloo/AnamorphicHtml.git
cd AnamorphicHtml
# Open directly in browser
open anamorphic-3d-converter.html   # macOS
start anamorphic-3d-converter.html  # Windows
```

Or simply download the HTML files and open with any modern browser.

---

## 🆘 Help Wanted

I'm seeking advice from experts in the following areas:

### Key Questions

1. **How to implement Off-axis Projection in pure frontend?**
   - Do I need to switch to WebGL/Three.js?
   - Are there Canvas 2D approximations?

2. **How to infer or simulate depth from 2D video?**
   - Is browser-based ML depth estimation (MiDaS, DPT) feasible?
   - Are there lighter alternatives?

3. **What's the production pipeline for mall-grade glasses-free 3D content?**
   - Must it be rendered from scratch in 3D software (Blender, Unity, Unreal)?
   - Can existing 2D footage be converted?

### If You Have Relevant Experience, Please Help!

- Share suggestions in [Issues](https://github.com/ooropuloo/AnamorphicHtml/issues)
- Submit [Pull Requests](https://github.com/ooropuloo/AnamorphicHtml/pulls) to improve the code
- Share relevant papers or resource links

---

## 🔬 Related Technical Fields

If you're familiar with any of these areas, your insights would be invaluable:

- **Anamorphic Projection**
- **Off-axis Projection** / Asymmetric View Frustum
- **Autostereoscopy** / Glasses-free 3D Display
- **Forced Perspective**
- **Spatial Computing**
- **WebGL / Three.js**
- **Monocular Depth Estimation**
- **Computational Photography**
- **Volumetric Display**

---

## 🤝 Contributing

All forms of contribution are welcome!

1. **Questions or Suggestions** → [Open an Issue](https://github.com/ooropuloo/AnamorphicHtml/issues/new)
2. **Share Knowledge** → Discuss technical details in Issues
3. **Improve Code** → Fork & Pull Request
4. **Spread the Word** → Star this project to increase visibility

---

## 📄 License

MIT License - See [LICENSE](LICENSE)
