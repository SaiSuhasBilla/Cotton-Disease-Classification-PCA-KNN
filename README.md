# Cotton Disease Diagnosis Using PCA and Cosine-Metric KNN Classifier

This repository provides a step-by-step implementation of the machine vision pipeline described in the 2014 research paper: *"Diagnosis of Diseases on Cotton Leaves Using Principal Component Analysis Classifier"*. 

The system focuses on deterministic statistical texture modeling (Mean and Variance) isolated from the Green (G) channel of RGB digital images, followed by Principal Component Analysis (PCA) dimensionality reduction and K-Nearest Neighbors (KNN) classification.

---

## ⚙️ Methodology & Pipeline

The implementation strictly mirrors the core technical architecture outlined in the paper:

1. **Green (G) Channel Isolation:** Extracts the green channel, as pigmentation changes from plant pathogens are uniquely visible in this spectrum.
2. **Block-Based Grid Partitioning:** Subdivides the image matrix into a uniform grid of $20 \times 20$ blocks.
3. **Statistical Descriptor Assembly:** Calculates local Mean ($\mu$) and Variance ($\sigma^2$) for every block to build a texture feature vector.
4. **Dimensionality Reduction (PCA):** Applies orthogonal principal component decomposition to compress feature dimensions while retaining variance.
5. **Clustering & Classification:** Employs a K-Nearest Neighbors engine using maximum Cosine Distance to classify the disease strains.

---

## 📊 Real-World Performance Considerations

While the paper achieves **95% accuracy** on isolated single-leaf laboratory images with flat backgrounds, deploying this pipeline on noisy, real-world field data containing soil, weeds, shadows, or full plants results in lower performance (~53.8% accuracy). 

### Optimization Notes:
* **Data Isolation:** Isolate data exclusively to clean leaf segments (`fresh cotton leaf` and `diseased cotton leaf`) to match the paper's original laboratory constraints.
* **Feature Upgrades:** To handle complex field imagery without deep learning, replace the simple block-variance step with advanced texture feature descriptors like **Local Binary Patterns (LBP)** or **Histogram of Oriented Gradients (HOG)** before applying the PCA compression step.
