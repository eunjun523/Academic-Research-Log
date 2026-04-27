# Feature Similarity Index (FSIM) Analysis 👁️🧬

This repository provides a Python implementation and comparative analysis of the **Feature Similarity (FSIM)** index, based on the paper *"FSIM: A Feature Similarity Index for Image Quality Assessment"* by Lin Zhang et al. 

The project explores how FSIM utilizes **Phase Congruency (PC)** and **Gradient Magnitude (GM)** to provide a more human-centric evaluation of image quality compared to traditional metrics like SSIM and VIF.

## 🚀 Key Experiment: Synthetic Distortion Benchmarking

We simulated five representative types of image degradation on a high-quality reference image (`Astronaut`) to observe how FSIMc (color version) maintains structural consistency.

## 📊 Results Summary

| Distortion Type | SSIM | **FSIMc** | VIF | Human Perception Equivalent |
| :--- | :---: | :---: | :---: | :--- |
| **Gaussian Noise** | 0.637 | **0.903** | 0.340 | Heavily grainy but features remain recognizable. |
| **Correlated Noise** | 0.974 | **0.988** | 0.816 | "Clumpy" noise; easily masked by human vision. |
| **Denoising Artifacts**| 0.751 | **0.902** | 0.342 | Waxy texture; fine details lost, structure intact. |
| **JPEG Compression** | 0.884 | **0.948** | 0.443 | Blocky artifacts present in high-frequency areas. |
| **Transmission Error**| 0.823 | **0.903** | 0.402 | Random color blocks creating "False Edges." |

*(Note: Scores range from 0 to 1, where 1 indicates perfect similarity to the reference image.)*

## 🧠 Core Findings

1.  **Structural Robustness (Contrast Invariance):** FSIMc consistently scored above **0.90** even when the image was visibly degraded. This is because **Phase Congruency (PC)** extracts the "invariant backbone" of the image, which aligns with how humans recognize objects regardless of noise or brightness shifts.
2.  **VIF's Informational Rigidity:** While FSIMc focuses on "shapes," **VIF** measures the loss of statistical information. VIF showed a dramatic drop (approx. 0.34) in noisy scenarios, reflecting a high sensitivity to the loss of natural image statistics (NSS).
3.  **The "False Edge" Sensitivity:** In the Transmission Error test, the appearance of artificial color blocks introduced sharp contrast boundaries. FSIMc correctly penalized these as structural anomalies (0.903), demonstrating its sensitivity to **locally inconsistent feature maps.**
4.  **Frequency Masking:** All metrics correctly assigned higher scores to **Correlated Noise** than **Gaussian Noise**, validating the HVS property where low-frequency distortions are less distracting than high-frequency "salt" noise.

## 🛠️ How to Run

### 1. Prerequisites
* **Python 3.8+** is required.
* **VS Code Extensions:** Ensure the **Python** and **Jupyter** extensions are installed in your VS Code.

### 2. Environment Setup
Install the necessary IQA and image processing libraries using the terminal in VS Code:
```bash
pip install torch torchvision piq scikit-image opencv-python
```

### 3. Execution via Jupyter Notebook
1. Open the provided `FSIM.ipynb` file in VS Code.
2. Select your Python kernel (top right corner of the editor).
3. Run each cell sequentially (or click **"Run All"**) to execute the benchmarking analysis.

### 4. Expected Output
* **Inline Results:** The notebook will display real-time similarity scores (SSIM, FSIM, VIF) directly below the code cells.
* **Integrated Visualization:** A **2x3 Matplotlib plot** will be rendered within the notebook, showing the reference image (`Astronaut`) and its 5 distorted variants, each labeled with its respective quality scores for immediate comparison.

---

### 💡 Tip for GitHub README
깃허브에 올리실 때, `FSIM.ipynb` 파일 자체를 레포지토리에 포함하면 깃허브가 자동으로 노트북의 실행 결과(그래프와 점수)를 웹 브라우저에서 보여줍니다. 따라서 이 `How to Run` 섹션과 함께 **"You can view the pre-rendered results directly in the FSIM.ipynb file."** 같은 문구를 추가하면 보는 사람이 훨씬 편하겠죠?
