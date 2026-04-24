# Multi-Scale Structural Similarity (MS-SSIM) Analysis 👁️📊

This repository contains a Python implementation and analysis of the **Multi-Scale Structural Similarity (MS-SSIM)** index, based on the landmark paper by Z. Wang et al. 

It demonstrates why evaluating image quality across multiple resolutions better aligns with the Human Visual System (HVS) compared to traditional single-scale methods.

## 🚀 Key Experiment: Noise vs. Blur

We applied two different types of distortion to a reference image (Rocket) to analyze how MS-SSIM evaluates structural degradation.

### 📊 Results Summary
| Distortion Type | Scale 1 (Original) | Scale 5 (Coarsest) | **Final MS-SSIM** | Human Perception Equivalent |
| :--- | :---: | :---: | :---: | :--- |
| **Gaussian Noise** | 0.0779 | 0.9691 | **0.0731** | Structurally destroyed; heavily degraded. |
| **Gaussian Blur** | 0.7913 | 0.9992 | **0.7987** | Details lost, but global structure intact. |

*(Note: MS-SSIM scores range from 0 to 1, where 1 indicates perfect structural similarity.)*

## 🧠 Core Findings

1. **Scale-Dependent Visibility:** At the highest resolution (Scale 1), noise severely penalizes the score. However, as the image is downsampled (Scale 2 to 5), the noise is smoothed out, and the structural similarity rapidly recovers. This mimics human vision—noise is less noticeable from a distance.
2. **Structural Integrity:**
   Unlike random noise, Gaussian blur preserves the macroscopic outlines and global patterns of the image. Consequently, MS-SSIM correctly assigns a much higher overall score to the blurred image, reflecting that it is still "recognizable" to a human observer.
3. **The Advantage over Single-Scale SSIM:**
   By aggregating scores across multiple scales using calibrated weights, MS-SSIM avoids over-penalizing or under-penalizing specific frequency domains. It provides a robust, human-aligned metric.

## 💼 Practical Applications
This implementation is highly relevant for **Image Quality Assessment (IQA)** tasks in the industry, such as:
* Evaluating the performance of lossy compression algorithms (JPEG, WebP).
* Benchmarking AI-driven image denoising and super-resolution models.
* Automated quality control in media streaming pipelines.

## 🛠️ How to Run
*(여기에 라이브러리 설치 방법이나 노트북 실행 방법 추가: 예: `pip install scikit-image matplotlib`)*
