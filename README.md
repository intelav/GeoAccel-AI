# ⚡ DINO-SAM-Accel: GPU-Optimized Geospatial Annotation

**Accelerating Geospatial Intelligence through distillation,segmentation and GPU Optimization.**
This project unites self-supervised embeddings from  **DINOv2** (distillation model)  and **Segment Anything 2 (SAM2)** (segmentation model) polygon refinement for the detected bounding box of those embeddings — all optimized for GPU-accelerated annotation and enables visual search in high-resolution (3m) satellite imagery.

---

## 🌍 Overview

**DINO-SAM-Accel** enables *automated detection, labeling, and visual search* across multi-band satellite datasets — empowering geospatial workflows through AI-driven similarity and segmentation refinement.The visual search could include any objects including below 8 classes. 

Supported object classes:

> Brick Kiln | STP | Solar Panel | Sheds | Metro Shed | Play Ground | Pond-1 | Pond-2

### 🔹 Core Pipelines

| Stage | Description |
| ------ | ------------ |
| **Prototype Creation** | `create_features_dino.py` extracts DINOv2 feature vectors from annotated `.json` polygons (ground truth). |
| **Batch Prototype Builder** | `batch_create_dino_prototypes.sh` creates prototypes for all TIF + JSON pairs (101 in total across 8 classes). |
| **Auto-Annotation (GPU Optimized)** | `auto_annotate_dino_nvtx_optimized.py` performs window-based detection using DINOv2 embeddings, cosine similarity search, and SAM2 refinement for detected bounding boxes. |
| **Batch Detection** | `batch_auto_annotate_dino.sh` runs the optimized annotator across 150 images, detects all 8 object types, and saves bounding boxes in CSV format. |
| **Model Training** | YOLOv8 model trained on detected bounding boxes; used as a region proposal network (RPN) for refinement. |
| **Final Visual Search** | DINOv2 embeddings + cosine similarity label the new search regions to find query objects. |
| **Interactive Review UI** | `ui_review.py` enables OpenCV-based visual verification, class editing, and YOLO export. |                                            |

---
## Yolo Model Training 
Below is the model metrics trained for 200 epochs.
As extracted embeddings has some amount of noise , hence its expected to have very less precision . 
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

**DINO-SAM-Accel** represents a unified GPU-accelerated geospatial AI workflow that fuses:

* **DINOv2 embeddings** for invariant patch-level representation
* **SAM2 segmentation refinement** for precision polygonization
* **Agentic profiling & kernel discovery** for adaptive GPU efficiency

Designed for **researchers and developers in remote sensing, computer vision, and HPC-AI convergence**, it bridges edge inference and cloud-scale analytics for Earth observation intelligence.

---

## 📄 Citation

```
@misc{dino_sam_accel_2025,
  title  = {DINO-SAM-Accel: GPU-Optimized Auto-Annotation for Satellite Imagery},
  author = {Atul Vaish},
  year   = {2025},
  url    = {https://github.com/intelav/DINO-SAM-Accel}
}
```

---

© 2025 SvarAikyam AI | AI Fusion — Applied Research in GPU Optimization & Geospatial Intelligence

