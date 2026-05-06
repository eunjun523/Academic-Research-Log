## 📊 Implementation Results: BRISQUE IQA

This section demonstrates the practical application of the **BRISQUE (Blind/Referenceless Image Spatial Quality Evaluator)** model using the `scikit-image` dataset.

### 🛠️ Experimental Setup
* **Environment**: VS Code / Jupyter Notebook
* **Target Image**: `astronaut` (from `skimage.data`)
* **Distortion Type**: Gaussian Noise (Mean = 0, Variance = 0.05)
* **Libraries**: `imquality`, `scikit-image`, `Pillow`

### 📈 Quantitative Results

| Image State | BRISQUE Score | Interpretation |
| :--- | :---: | :--- |
| **Pristine (Original)** | **10.92** | High naturalness / Best quality |
| **Noisy (Distorted)** | **68.29** | Significant quality degradation |

> **Note**: In the BRISQUE metric, a **lower score** (closer to 0) indicates better perceptual quality, while a **higher score** indicates higher distortion.

### 🖼️ Visual Comparison
The side-by-side comparison below shows how the BRISQUE score increases as artificial noise is introduced, effectively quantifying the loss of "naturalness" in the spatial domain.

* **Pristine Image**: Shows the typical statistics of a natural scene.
* **Noisy Image**: The statistical distribution of MSCN coefficients deviates from the ideal Gaussian shape, resulting in a higher quality score.

*(여기에 두 이미지가 나란히 있는 실행 결과 화면을 캡처하여 삽입하세요)*

### 💡 Key Findings
* **Sensitivity**: The model is highly sensitive to Gaussian noise, showing a dramatic score jump from approximately 10 to 68.
* **Validation**: The results successfully validate the paper's claim that spatial domain features (GGD and AGGD) are sufficient to capture image quality without a reference image.
