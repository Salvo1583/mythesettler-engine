<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=180&section=header&text=MyTheSettler&fontSize=40&fontColor=ffffff&fontAlignY=36&desc=Motore%20di%20strategia%20nel%20browser%20e%20reverse%20engineering&descSize=18&descAlignY=58" alt="MyTheSettler" width="100%" />
</p>

<p align="center"><a href="README.md">🇬🇧 English</a> · <b>🇮🇹 Italiano</b></p>

<p align="center">
  <img src="https://img.shields.io/badge/codice-privato-555555?style=for-the-badge&logo=github" alt="Codice privato" />
  <img src="https://img.shields.io/badge/vetrina-progetto-36BCF7?style=for-the-badge" alt="Vetrina del progetto" />
</p>

> [!NOTE]
> Questo repository è una **vetrina del progetto**: il codice sorgente è privato. Una demo è disponibile su richiesta.

## 🧭 Panoramica

**MyTheSettler** è un motore di gioco strategico in tempo reale, basato sull'economia, che gira nel browser. Riproduce la logica di gioco esatta di un classico per PC di fine anni '90, con una grafica 2.5D moderna.

Il progetto unisce il **reverse engineering** (formati binari originali degli asset, regole e numeri di gioco ricostruiti da documentazione e misurazioni della community) a un'architettura moderna e completamente testata.

## ✨ Funzionalità principali

- 🔍 **Reverse engineering dei formati originali**: un lettore scritto da zero per gli archivi grafici `.dat`, per caricare gli sprite da una copia del gioco posseduta dall'utente
- 📚 **Logica di gioco ricostruita dalle fonti**: ogni regola e ogni numero ha la sua fonte e il suo grado di affidabilità, i valori ignoti sono marcati esplicitamente come stime
- 🧵 **Simulazione in un Web Worker** a 17 tick al secondo fissi, mentre il rendering resta a 60+ fps interpolando tra gli snapshot
- 🗺️ **Mappa esagonale** con generatore di terreno e pathfinding **A\*** per migliaia di coloni
- 🏗️ **Economia completa**: portatori e logistica, cantieri, legno, cibo, miniere e fabbri, con impostazioni economiche, statistiche e avvisi
- 🧩 **Progettazione guidata dai dati**: edifici e comportamenti dei lavoratori definiti in JSON e validati con Zod
- 🎨 **Grafica procedurale** disegnata via codice, per sostituire del tutto gli asset originali
- ✅ **Circa 300 test automatici** che girano in Node, senza browser

## 🏗️ Architettura

```mermaid
flowchart LR
    subgraph Worker[Web Worker]
        SIM[Simulazione<br/>17 tick/s]
    end
    DATA[(Dati di gioco<br/>JSON + Zod)] --> SIM
    SIM -->|snapshot in array tipizzati| R[Renderer PixiJS<br/>60+ fps, interpolato]
    ASSETS[Lettore .dat /<br/>grafica procedurale] --> R
    UI[Interfaccia React] -->|comandi| SIM
```

## 🧰 Tecnologie

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![PixiJS](https://img.shields.io/badge/PixiJS_v8-E72264?style=flat)
![WebGL](https://img.shields.io/badge/WebGL_/_WebGPU-990000?style=flat&logo=webgl&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat&logo=vite&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=flat&logo=vitest&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=flat&logo=zod&logoColor=white)

## 📬 Contatti

Realizzato da **Salvatore Cutaia**, ingegnere informatico specializzato in agenti AI e automazioni.

[![GitHub](https://img.shields.io/badge/GitHub-Salvo1583-181717?style=flat&logo=github)](https://github.com/Salvo1583)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Salvatore_Cutaia-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/salvatore-cutaia-6047b0155/)
[![Website](https://img.shields.io/badge/Website-neuralform.it-111111?style=flat&logo=googlechrome&logoColor=white)](https://neuralform.it/)
