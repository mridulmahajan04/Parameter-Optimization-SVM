# Parameter-Optimization-SVM

# 🧠 Parameter-Optimization-SVM

### 🧬 Breast Cancer Classification using NuSVC with Randomized Hyperparameter Search  
This project applies **Nu-Support Vector Classification (NuSVC)** on the Breast Cancer Wisconsin dataset from `sklearn.datasets`. The objective is to classify tumors as malignant or benign, with a twist: the dataset is made more challenging by reducing its size and adding Gaussian noise.

---

### 📊 Dataset Source  
Built-in `load_breast_cancer()` from `sklearn.datasets`

- **Samples**: Initially 569, reduced to ~60% (~341 samples) using random sampling  
- **Features**: 30 numerical attributes describing cell nuclei (e.g., radius, texture, smoothness)  
- **Target**: Binary classification  
  - `0`: Malignant  
  - `1`: Benign

---

### ⚙️ Preprocessing Steps

- Subsampled the dataset to 60% of original size  
- Added Gaussian noise (`mean=0`, `std=0.8`) to make classification harder  
- Features were standardized using `StandardScaler`

---

### 🤖 Modeling  

Used `NuSVC` from `sklearn.svm` with randomized hyperparameter search:

- **Kernel**: Randomly chosen from `['linear', 'poly', 'rbf', 'sigmoid']`
- **Nu**: Random float between 0.01 and 0.5
- **Gamma**: `"scale"` for linear, else a random float between 0.001 and 1

- Performed 100 random trials for each of 10 random samples  
- Tracked the best accuracy and SVM configuration for each sample

---

### 📈 Visualization  
Plotted convergence graph for the best-performing sample showing accuracy across iterations.  
Saved as `convergence_plot.png`.

---

### 🏁 Results

| Sample | Best Accuracy (%) | Best SVM Parameters |
|--------|-------------------|---------------------|
| S1     | 96.12             | Kernel: linear, Nu: 0.15, Gamma: scale |
| S2     | 95.15             | Kernel: linear, Nu: 0.24, Gamma: scale |
| S3     | 93.20             | Kernel: linear, Nu: 0.10, Gamma: scale |
| S4     | 95.15             | Kernel: linear, Nu: 0.07, Gamma: scale |
| S5     | 94.17             | Kernel: sigmoid, Nu: 0.25, Gamma: 0.072 |
| S6     | 92.23             | Kernel: linear, Nu: 0.11, Gamma: scale |
| S7     | 93.20             | Kernel: linear, Nu: 0.22, Gamma: scale |
| S8     | 94.17             | Kernel: linear, Nu: 0.04, Gamma: scale |
| S9     | 91.26             | Kernel: linear, Nu: 0.07, Gamma: scale |
| S10    | 95.15             | Kernel: linear, Nu: 0.02, Gamma: scale |

- **🏆 Best Sample**: `S1` with **96.12%** accuracy

---
