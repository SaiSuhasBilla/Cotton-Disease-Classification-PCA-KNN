# Cotton Disease Diagnosis Using PCA and Cosine-Metric KNN Classifier

[cite_start]This repository provides a step-by-step implementation of the machine vision pipeline described in the 2014 research paper: *"Diagnosis of Diseases on Cotton Leaves Using Principal Component Analysis Classifier"*[cite: 1, 2, 3]. 

[cite_start]The system focuses on deterministic statistical texture modeling (Mean and Variance) isolated from the Green (G) channel of RGB digital images, followed by Principal Component Analysis (PCA) dimensionality reduction and K-Nearest Neighbors (KNN) classification[cite: 9, 14, 112].

---

## ⚙️ Methodology & Pipeline

The implementation strictly mirrors the core technical architecture outlined in the paper:

1. [cite_start]**Green (G) Channel Isolation:** Extracts the green channel, as pigmentation changes from plant pathogens are uniquely visible in this spectrum[cite: 14, 15].
2. [cite_start]**Block-Based Grid Partitioning:** Subdivides the image matrix into a uniform grid of $20 \times 20$ blocks[cite: 112].
3. [cite_start]**Statistical Descriptor Assembly:** Calculates local Mean ($\mu$) and Variance ($\sigma^2$) for every block to build a texture feature vector[cite: 108, 112, 113].
4. [cite_start]**Dimensionality Reduction (PCA):** Applies orthogonal principal component decomposition to compress feature dimensions while retaining variance[cite: 40, 41, 42].
5. [cite_start]**Clustering & Classification:** Employs a K-Nearest Neighbors engine using maximum Cosine Distance to classify the disease strains[cite: 143].

---

## 🚀 Getting Started on Google Colab

### 1. Uploading the Dataset
1. Zip your local dataset folder into `Cotton Disease.zip`.
2. Open your Google Colab notebook environment.
3. Drag-and-drop the zip file directly into the Colab **Files** session storage workspace.

### 2. Execution Order
Execute the Colab notebook blocks sequentially to:
* Extract the zipped dataset structures into the active runtime workspace path.
* Load processing packages (`OpenCV`, `scikit-learn`) and configure directory target maps.
* Run the uniform block texturing math routines and partition datasets into split arrays.
* Evaluate the aggregate samples loaded into active memory.
* Fit the PCA transformation model matrix, map vectors into low-dimensional space, and yield classification metrics.
* [cite_start]Generate figures matching the research layout (Visual Grid Overlays, Eigenvalue Descending Scatter Plots, and Real-Time Evaluation Tables)[cite: 116, 137, 179].

---

## 📊 Real-World Performance Considerations

[cite_start]While the paper achieves **95% accuracy** on isolated single-leaf laboratory images with flat backgrounds[cite: 17, 193], deploying this pipeline on noisy, real-world field data containing soil, weeds, shadows, or full plants results in lower performance (~53.8% accuracy). 

### Optimization Notes:
* [cite_start]**Data Isolation:** Isolate data exclusively to clean leaf segments (`fresh cotton leaf` and `diseased cotton leaf`) to match the paper's original laboratory constraints[cite: 9, 12, 190].
* [cite_start]**Feature Upgrades:** To handle complex field imagery without deep learning, replace the simple block-variance step with advanced texture feature descriptors like **Local Binary Patterns (LBP)** or **Histogram of Oriented Gradients (HOG)** before applying the PCA compression step[cite: 107, 195].
