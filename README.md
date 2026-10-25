# 🏎️ Desk Racer

[![Three.js](https://img.shields.io/badge/Three.js-r183-black?style=flat&logo=three.js)](https://threejs.org/)
[![Rapier 3D](https://img.shields.io/badge/Rapier_3D-v0.19-orange?style=flat)](https://rapier.rs/)
[![Vite](https://img.shields.io/badge/Vite-6.2-646CFF?style=flat&logo=vite)](https://vitejs.dev/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat&logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=flat&logo=typescript)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Miniature 1:87 HO-scale coaster time-trial racing game running in Three.js and Rapier3D physics directly in the browser.**

[🇹🇷 Türkçe Dokümantasyon için tıklayın (README.tr.md)](README.tr.md)

---

## 📸 Overview

**Desk Racer** places you in the cockpit of a 1:87 micro-kart navigating an elaborate roller-coaster circuit constructed across a cozy golden-hour workstation. Drift past keyboards, zoom under laptop stands, bank through spiral drops around coffee mugs, and chase your fastest lap times.

### ✨ Highlights

- **1:87 Micro Scale Physics**: Authentic kart handling with suspension damping, drift momentum, downforce, and banked corner adherence powered by `@dimforge/rapier3d-compat`.
- **Cinematic Macro Photography Visuals**: Tilt-shift macro depth-of-field simulation using a custom single-pass hardware-depth Bokeh pass with a 25-tap Golden-Angle Vogel spiral disc kernel, paired with ACES Filmic Tone Mapping and Unreal Bloom.
- **Dynamic Procedural Audio**: Dual-layer procedural Web Audio synthesizer blending synthesized engine RPM oscillations, throttle sputters, curb rumbles, and tire drift friction loops.
- **4 Distinct Camera Systems**:
  1. **Chase View (1)**: Smooth spring-damped third-person racing camera.
  2. **Cockpit / Visor POV (2)**: Immersive driver helmet view with subtle edge vignette.
  3. **Full Desk View (3)**: High isometric overview of the entire desk diorama.
  4. **Drone View (4)**: Cinematic spectator tracking camera.
- **Live Vector HUD**:
  - Angled segmented SVG speedometer with dynamic cyan illumination.
  - Real-time 3D tilted track minimap showing live kart position.
  - Lap tracker, live timer with millisecond precision, split differences, and F1 countdown lights.
- **Auto-Pilot Mode**: Sit back and observe the micro-kart execute optimal racing lines automatically.
- **Mobile Touch Interface**: Full on-screen steer and pedal controls designed for mobile browsers.

---

## 🎮 Controls

### Desktop Keyboard

| Key | Action |
|:---:|:---|
| <kbd>W</kbd> or <kbd>↑</kbd> | Accelerate (Throttle) |
| <kbd>A</kbd> or <kbd>←</kbd> | Steer Left |
| <kbd>D</kbd> or <kbd>→</kbd> | Steer Right |
| <kbd>S</kbd> or <kbd>↓</kbd> | Brake / Reverse |
| <kbd>1</kbd> | Chase Camera |
| <kbd>2</kbd> | Cockpit / Visor POV |
| <kbd>3</kbd> | Full Desk View |
| <kbd>4</kbd> | Drone Spectator View |
| <kbd>P</kbd> | Toggle Auto-Pilot Mode |
| <kbd>M</kbd> | Toggle Sound (Mute / Unmute) |
| <kbd>Enter</kbd> | Start Time Trial / Race Again |

### Mobile & Touch Screens
On touch-capable devices, virtual steering buttons (**Left** / **Right**) appear on the bottom-left corner and pedal controls (**Accel** / **Brake**) appear on the bottom-right corner automatically.

---

## 🛠️ Tech Stack & Architecture

- **Rendering Engine**: [Three.js](https://threejs.org/) (WebGL with PCF Soft Shadows, PMREM studio environment, and custom post-processing pipeline).
- **Physics**: [Rapier3D](https://rapier.rs/) (`@dimforge/rapier3d-compat`) WebAssembly physics engine.
- **Post-Processing**: `EffectComposer`, `RenderPass`, `UnrealBloomPass`, `OutputPass`, and custom Vogel Spiral `BokehPass`.
- **Audio**: Web Audio API oscillator synthesis combined with stereo buffer audio samples (`/public/assets/audio/`).
- **Build Tool**: [Vite 6](https://vitejs.dev/) with automated gstatic 3D model streaming proxy.
- **Languages**: JavaScript (ESNext modules) & TypeScript.

---

## 📂 Project Structure

```
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   ├── workflows/
│   │   └── ci.yml
│   └── PULL_REQUEST_TEMPLATE.md
├── public/
│   └── assets/
│       ├── audio/              # Sound effects & engine audio loops
│       └── data/               # Track spline data & desk manifests
├── src/
│   ├── audio/
│   │   └── WebAudioSynth.js    # Procedural sound synthesis engine
│   ├── physics/
│   │   └── KartPhysicsController.js # Rapier3D vehicle physics logic
│   ├── scene/
│   │   ├── CoasterTrackBuilder.js   # Procedural track spline & rail geometry
│   │   ├── DeskDioramaBuilder.js   # Workstation desk props & materials
│   │   ├── GoldenHourAtmosphere.js # Lighting, sun angles & volumetric fog
│   │   ├── MicroKartBuilder.js     # 1:87 HO-scale kart mesh assembly
│   │   ├── ProceduralTextures.js   # Procedural canvas textures
│   │   └── RoomEnvironmentBuilder.js# Surrounding room walls and lighting
│   ├── App.tsx
│   ├── main.js                 # Three.js render loop, HUD and camera controller
│   ├── main.tsx
│   └── style.css               # HUD styling & responsiveness
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── package.json
├── README.md
├── README.tr.md
├── tsconfig.json
└── vite.config.ts
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18.0.0 or later recommended)
- `npm`, `pnpm`, or `bun`

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/desk-racer.git
   cd desk-racer
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm run dev
   ```
   Open your browser and navigate to `http://localhost:3000`.

### Production Build

To create an optimized production build:
```bash
npm run build
```

To preview the production build locally:
```bash
npm run preview
```

### Type Checking & Linting

```bash
npm run lint
```

---

## 🌐 3D Model Assets Note

The 3D GLTF/GLB models (`room_environment.glb`, `desk_props.glb`, `track_coaster.glb`, `kart_1to87.glb`) are configured in `vite.config.ts` to be fetched and cached transparently via Vite's proxy and build hooks from Google's static model repository during development and build, ensuring low repository size and fast cloning.

---

## 🤝 Contributing

Contributions, bug reports, and suggestions are welcome!
Please check out [CONTRIBUTING.md](CONTRIBUTING.md) to get started.

---

## 📄 License

This project is open-source and licensed under the [MIT License](LICENSE).
Feel free to use, modify, and build upon this code for your personal and commercial projects.
