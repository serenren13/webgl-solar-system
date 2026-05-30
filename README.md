# 🪐 Mini Solar System

An interactive 3D solar system simulation built with vanilla WebGL, featuring real-time lighting, texture mapping, and live camera/orbit controls.

---

## Table of Contents

- [Project Description](#project-description)
- [Installation](#installation)
- [How to Use](#how-to-use)
- [Major Components and Features](#major-components-and-features)
- [Feature Status](#feature-status)
- [Credits](#credits)

---

## Project Description

Mini Solar System is a browser-based 3D simulation of the Earth–Moon–Sun system, rendered using raw WebGL (no Three.js or game engine). It features Phong shading with diffuse, ambient, and specular components applied to the Earth and Moon, while the Sun renders as a self-illuminated textured sphere. Users can interactively adjust the Earth's orbit and the camera position in real time using sliders in the control panel.

---

## Installation

### Prerequisites

- [Node.js](https://nodejs.org/) (for `npx serve`)
- [Git LFS](https://git-lfs.com/) — required to pull the texture image files (`.jpg`), which exceed GitHub's standard file size limits

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/serenren13/webgl-solar-system.git
   cd webgl-solar-system
   ```

2. **Pull LFS assets** (texture images):
   ```bash
   git lfs pull
   ```
   > If Git LFS is not installed, run `git lfs install` first, then retry.

3. **Serve the project locally:**
   ```bash
   npx serve .
   ```

4. **Open in browser:**
   ```
   http://localhost:3000
   ```

---

## How to Use

Once the app is running, you'll see a canvas with the solar system alongside two control panels:

**Earth Settings** — adjust how Earth orbits the Sun:
- **Orbit Speed** — how fast Earth revolves
- **Orbit Distance** — how far Earth is from the Sun
- **Orbit Angle** — the tilt of Earth's orbital plane
- **Reset** — restores Earth settings to default

**Camera Settings** — adjust the viewer's perspective:
- **X / Y / Z** — translate the camera along each axis
- **FoV** — field of view (zoom in/out effect)
- **Reset** — restores camera to default position

---

## Major Components and Features

| File | Description |
|---|---|
| `fp.js` | Core WebGL logic — shader setup, texture loading, render loop, orbit + rotation math |
| `fp.html` | HTML structure, UI controls (sliders/buttons), and inline GLSL shader source |
| `fp.css` | Styling for the layout, control panel, and canvas |
| `helpers.js` | Helper utilities for WebGL setup and matrix operations |
| `listeners.js` | Event listeners for all slider and button inputs |
| `earth.jpg` | Earth surface texture (tracked via Git LFS) |
| `moon.jpg` | Moon surface texture (tracked via Git LFS) |
| `sun.jpg` | Sun surface texture (tracked via Git LFS) |

### Shading

The fragment shader applies **Phong lighting** to Earth and Moon (diffuse + ambient + specular), while the Sun uses direct texture color with no shading, simulating self-illumination.

### Transformations

The vertex shader handles per-object scaling, Y-axis rotation (spin), and translation — all driven by uniforms updated each frame.

---

## Feature Status

| Feature | Status |
|---|---|
| Sun, Earth, Moon rendering | ✅ Complete |
| Texture mapping | ✅ Complete |
| Phong shading (Earth & Moon) | ✅ Complete |
| Earth orbit controls (speed, distance, angle) | ✅ Complete |
| Camera controls (X, Y, Z, FoV) | ✅ Complete |
| Reset buttons | ✅ Complete |
| Moon orbit around Earth | ✅ Complete |

---

## Credits

- **Developer:** Serenity Phillips ([@serenren13](https://github.com/serenren13))
- **WebGL Utilities:** [Angel & Shreiner WebGL Common Library](https://www.cs.unm.edu/~angel/WebGL/7E/Common/)
- **Sphere Model:** [brent-munsell/graphics msphere.js](https://cdn.jsdelivr.net/gh/brent-munsell/graphics/models/msphere.js)
- Built as a final project for COMP 590 at UNC Chapel Hill
