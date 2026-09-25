# SatQuery AI: An Interactive Vision-Language Assistant for Multimodal Remote Sensing Image Analysis

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Theme](https://img.shields.io/badge/Theme-Space_Technology-orange.svg)](#)
[![Domain](https://img.shields.io/badge/Organization-SAC%20%2F%20ISRO-brightgreen.svg)](#)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](#)

> **Smart India Hackathon (SIH)**  
> **Problem Statement:** SatQuery AI — An Interactive Vision-Language Assistant for Multimodal Remote Sensing Image Analysis through Text Queries  
> **Organization:** Space Applications Centre (SAC), ISRO, Department of Space  
> **Mentors / Domain Experts:** Md Aminur Hossain, Sanjay K Singh, S Devakanth Naidu

---

## 📌 Overview

**SatQuery AI** is an agentic vision-language platform designed to analyze complex remote-sensing imagery using simple natural-language queries. Unlike standard single-task GIS pipelines or generic vision-language models (VLMs), SatQuery AI employs an intelligent, agent-driven orchestration layer that automatically selects, sequences, and executes domain-adapted specialist models across optical, Synthetic Aperture Radar (SAR), multitemporal, and cross-modal satellite datasets.

---

## 🎯 Key Features & Capabilities

- **Natural Language Remote Sensing Analysis:** Query single or paired remote-sensing images using conversational prompts.
- **Agentic Model & Tool Orchestrator:** Dynamic intent classification, format validation, model selection from a specialist registry, and auditable parameter execution.
- **Cross-Modal Reasoning (Optical + SAR):** Jointly process co-registered optical/multispectral (e.g., Sentinel-2, Cartosat-2S) and SAR (e.g., Sentinel-1, RISAT) imagery for structural and contextual feature fusion.
- **Bi-Temporal Change Analysis:** Detect, localize, and query changes between historical and recent passes using Change VQA and spatial change heatmaps.
- **Domain-Specific Fine-Tuning:** Vision-language models adapted for multispectral bands, geospatial resolutions, and remote-sensing terminology via datasets like **BigEarthNet.txt**.
- **Evidence-Grounded Visualization & Reporting:** Spatial bounding boxes, segmentation masks, confidence intervals, auditable execution traces, and downloadable analysis reports.

---

## 📥 Supported Input Modalities & Formats

| Input Type | Supported Data | Primary Tasks |
| :--- | :--- | :--- |
| **Single Image** | Optical, Multispectral, or SAR | Visual Question Answering (RSVQA), Scene Description, Visual Grounding |
| **Cross-Modal Pair** | Co-registered Optical/Multispectral + SAR | Complementary feature extraction, cloud-penetrating water/built-up mapping |
| **Bi-Temporal Pair** | Multi-date image pairs ($T_1$ & $T_2$) | Change detection, change description, Change-VQA (CDVQA), difference mapping |

- **Geospatial Formats:** GeoTIFF / TIFF (native metadata & coordinate reference systems preserved).
- **Benchmark Formats:** PNG / JPEG (supported for standard evaluation subsets).

---

## 🧠 System Architecture & Workflow

```text
[User Query + Image Input(s)]
           │
           ▼
┌──────────────────────────────────────────────┐
│       Agentic Orchestration Controller       │
│  - Task Classification & Intent Parsing      │
│  - Metadata, Format & Compatibility Checks   │
│  - Tool Registry & Execution Planner         │
└──────┬──────────────┬──────────────┬─────────┘
       │              │              │
       ▼              ▼              ▼
┌──────────────┐┌──────────────┐┌──────────────┐
│ Single-Image ││  Cross-Modal ││ Bi-Temporal  │
│  RS-VLM /    ││ Fusion Engine││ Change VQA / │
│  Grounding   ││(Optical+SAR) ││ Change Maps  │
└──────┬───────┘└──────┬───────┘└──────┬───────┘
       │               │               │
       └───────────────┼───────────────┘
                       ▼
┌──────────────────────────────────────────────┐
│           Response & Evidence Aggregator     │
│  - Spatial Visual Grounding & Mask Overlays   │
│  - Confidence Scoring & Auditable Trace      │
│  - Interactive UI & Downloadable PDF Reports │
└──────────────────────────────────────────────┘
```

---

## 📊 Datasets & Benchmarks

### 1. Training & Fine-Tuning
- **[BigEarthNet.txt](https://arxiv.org/abs/2603.29630):** Primary multimodal remote-sensing dataset utilizing Sentinel-1 (SAR) and Sentinel-2 (Multispectral) image-text pairs for domain adaptation.

### 2. Public Evaluation Benchmarks
- **[VRSBench](https://arxiv.org/abs/2406.12384):** Evaluation for remote-sensing image captioning, visual grounding, and single-image VQA.
- **[RSVQA](https://arxiv.org/abs/2003.07333):** High-resolution and low-resolution satellite visual question answering.
- **[CDVQA](https://arxiv.org/abs/2112.06343):** Multitemporal change-detection visual question answering.

### 3. ISRO / SAC Evaluation Set (Hidden Benchmark)
- Co-registered **Cartosat-2S** (Optical) and **RISAT** (SAR) pairs for validation of cross-modal reasoning and change assessment.

---

## 📈 Evaluation Criteria

| Evaluation Component | Metrics & Evidence | Weight |
| :--- | :--- | :---: |
| **Agentic Task Routing & Orchestration** | Task selection accuracy, valid execution paths, input verification, parameter configuration, invalid call rate | **20%** |
| **Single-Image Remote-Sensing VLM** | VRSBench & RSVQA accuracy; captioning/grounding metrics | **20%** |
| **Multitemporal Change Understanding** | CDVQA answer accuracy, change map F1-score & IoU | **25%** |
| **ISRO Cross-Modal Paired Analysis** | Cartosat-2S & RISAT QA accuracy, extraction F1/IoU, visual evidence localization | **25%** |
| **Robustness, Usability & Reporting** | GeoTIFF handling, latency, confidence reporting, UI/UX, downloadable reports | **10%** |

---

## 🚀 Quickstart

### Prerequisites
- Python 3.10+
- CUDA-enabled GPU (recommended $\ge$ 16GB VRAM)
- GDAL & Rasterio native dependencies

### 1. Installation
```bash
# Clone the repository
git clone https://github.com/your-username/SatQuery-AI.git
cd SatQuery-AI

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Configure Environment
```bash
cp .env.example .env
# Set your model weights paths, cache directories, and server port in .env
```

### 3. Run the Application
```bash
# Start backend and web GUI
python app.py
```
Open your browser at `http://localhost:7860` to access the interface.

---

## 💬 Example Queries

- **Single Image Analysis:**  
  > *"Describe the predominant land-cover classes and list visible transport infrastructure in this scene."*
- **Visual Grounding:**  
  > *"Highlight the reservoir boundary and locate water bodies referred to in the image."*
- **Multitemporal Change Detection:**  
  > *"What structural developments occurred between Date 1 and Date 2, and where did urbanization happen?"*
- **Cross-Modal SAR + Optical:**  
  > *"Use the optical and SAR images together to isolate flood boundaries beneath cloud cover."*

---

## 👥 Contributors & Mentorship

- **Mentors (SAC / ISRO):**
  - **Md Aminur Hossain** ([aminur@sac.isro.gov.in](mailto:aminur@sac.isro.gov.in))
  - **Sanjay K Singh**
  - **S Devakanth Naidu**
- **Developed by:** [Your Team Name / GitHub Handles]

---

## 📜 License
This project is licensed under the Apache 2.0 License. See the [LICENSE](LICENSE) file for details.
