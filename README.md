# ⚡ GeoAccel-AI: GPU-Optimized Geospatial Annotation

**Accelerating Geospatial Intelligence through distillation, segmentation, and proprietary embeddings.**  
Developed under the **SvarAikyam AI / AI Fusion** initiative, this project integrates deep visual distillation models, segmentation refinement, and GPU-accelerated feature search to automate large-scale annotation and object discovery in high-resolution (3m) satellite imagery.

---

## 🌍 Overview

**GeoAccel-AI** enables *automated detection, labeling, and visual search* across multi-band satellite datasets — empowering geospatial workflows through AI-driven similarity and segmentation refinement.  
The visual search can identify and classify diverse infrastructure and terrain categories with minimal human supervision.

Supported object classes:
> Brick Kiln | STP | Solar Panel | Sheds | Metro Shed | Play Ground | Pond-1 | Pond-2


### 🔹 Core Pipelines

| Stage | Description |
| ------ | ------------ |
| **Prototype Creation** |  Extracts proprietary feature embeddings from annotated `.json` polygons (ground truth). |
| **Batch Prototype Builder** |  Builds class prototypes across all TIF + JSON pairs. |
| **Auto-Annotation (GPU Optimized)** |  Performs multi-scale window detection using embedding similarity search and segmentation-based refinement for detected regions. |
| **Batch Detection** |  Executes large-scale annotation runs across hundreds of satellite tiles, generating object-level metadata. |
| **Model Training** | YOLOv8-based detection fine-tuned on discovered regions; used as a region proposal network (RPN) for refinement. |
| **Final Visual Search** | Embedding-based similarity retrieval to identify query objects in unseen images. |
| **Interactive Review UI** | Provides OpenCV-based annotation validation, class editing, and YOLO export tools. |
                                         |

---
## Yolo Model Training 
Below are the metrics for a representative YOLOv8 model trained for 200 epochs.  
Since the extracted embeddings contain a degree of variability, moderate precision is expected — yet sufficient for rapid bootstrapping of geospatial datasets.
![Metrics](results/yolo_model_trainig_losses.png)
*Figure 1: YOLOv8 training loss curves over 200 epochs.*

## ⚙️ GPU Profiling & Agentic Optimization
Integrated with **Nsight Systems**, **Nsight Compute**, and **Torch Profiler** for kernel-level insights, enabling precise GPU workload tuning.
Includes experimental support for **Agentic GPU Optimization**, orchestrating autotuning of CUDA kernels and Triton ops for real-time efficiency gains on **RTX 3060** .

![Initial Profiling Report](profiling/report.png)
*Figure 2: Initial Profiling Report on RTX3060 (12GB).*

![Optimized Profiling Report](profiling/report_optimized.png)
*Figure 3: Optimized Profiling Report on RTX3060 (12GB).*
---

## 🖼️ Results

<p align="center">
  <img src="results/sat_det.png" alt="Initial Annotation" width="720"><br>
  <em>Figure 4: Initial Annotation for Training.</em>
</p>

<p align="center">
  <img src="results/final_seen_result.png" alt="Final Known Objects" width="720"><br>
  <em>Figure 5: Final Result — Detected Known Objects in Unseen Image.</em>
</p>

<p align="center">
  <img src="results/building_chip_search.png" alt="Unseen Objects" width="720"><br>
  <em>Figure 6: Final Result — Detected Unseen Objects in Unseen Image.</em>
</p>

---



## 🧠 Research Context

**GeoAccel-AI** represents a unified, GPU-optimized geospatial AI framework that fuses:
- **Visual distillation** for semantic and texture representation
- **Segmentation refinement** for pixel-level precision
- **Agentic profiling & kernel discovery** for dynamic GPU efficiency

It serves as a bridge between **remote sensing**, **AI-driven automation**, and **edge-to-cloud scalability**, enabling faster Earth observation analytics and infrastructure monitoring.

---

## 📄 Citation

```
@misc{geoaccel_ai_2025,
  title  = {GeoAccel-AI: GPU-Optimized Auto-Annotation for Satellite Imagery},
  author = {Atul Vaish},
  year   = {2025},
  url    = {https://github.com/intelav/GeoAccel-AI}
}
```

---

© 2025 SvarAikyam AI | AI Fusion — Applied Research in GPU Optimization & Geospatial Intelligence


