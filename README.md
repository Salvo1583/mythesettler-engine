<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=180&section=header&text=MyTheSettler&fontSize=40&fontColor=ffffff&fontAlignY=36&desc=Browser%20strategy%20engine%20%26amp%3B%20reverse%20engineering&descSize=18&descAlignY=58" alt="MyTheSettler" width="100%" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/source-private-555555?style=for-the-badge&logo=github" alt="Source private" />
  <img src="https://img.shields.io/badge/project-showcase-36BCF7?style=for-the-badge" alt="Project showcase" />
</p>

> [!NOTE]
> This repository is a **project showcase**: the source code is private. A demo is available on request.

## 🧭 Overview

**MyTheSettler** is a real-time economy strategy game engine for the browser, built to reproduce the exact game logic of a late-90s PC classic with modern 2.5D graphics.

The project combines **reverse engineering** (original binary asset formats, game rules and numbers reconstructed from documentation and community measurements) with a modern, fully tested architecture.

## ✨ Key features

- 🔍 **Reverse engineering of the original formats**: a custom reader for the legacy `.dat` graphics archives, to load sprites from a user-owned copy of the game
- 📚 **Game logic reconstructed from sources**: every rule and number is tracked with its source and reliability, unknown values are explicitly marked as estimates
- 🧵 **Simulation in a Web Worker** at a fixed 17 ticks per second, while rendering stays at 60+ fps with interpolation between snapshots
- 🗺️ **Hex-grid map** with terrain generator and **A\*** pathfinding for thousands of settlers
- 🏗️ **Full economy**: carriers and logistics, construction sites, wood, food, mines and smiths, with economic settings, statistics and alerts
- 🧩 **Data-driven design**: buildings and worker behaviours defined in JSON and validated with Zod
- 🎨 **Procedural graphics** drawn in code, to replace the original assets entirely
- ✅ **~300 automated tests** running in Node, no browser needed

## 🏗️ Architecture

```mermaid
flowchart LR
    subgraph Worker[Web Worker]
        SIM[Simulation<br/>17 ticks/s]
    end
    DATA[(Game data<br/>JSON + Zod)] --> SIM
    SIM -->|typed-array snapshots| R[PixiJS renderer<br/>60+ fps, interpolated]
    ASSETS[.dat reader /<br/>procedural graphics] --> R
    UI[React UI] -->|commands| SIM
```

## 🧰 Tech stack

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![PixiJS](https://img.shields.io/badge/PixiJS_v8-E72264?style=flat)
![WebGL](https://img.shields.io/badge/WebGL_/_WebGPU-990000?style=flat&logo=webgl&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat&logo=vite&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=flat&logo=vitest&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=flat&logo=zod&logoColor=white)

## 📬 Contact

Built by **Salvatore Cutaia**, Computer Engineer specialized in AI agents & automations.

[![GitHub](https://img.shields.io/badge/GitHub-Salvo1583-181717?style=flat&logo=github)](https://github.com/Salvo1583)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Salvatore_Cutaia-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/salvatore-cutaia-6047b0155/)
