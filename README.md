# Objectif Principal
- Classifier différentes espèces de plantes à partir d'images de feuilles  
- Techniques Suggérées

* Feature extraction (shape, color, texture)
* SVM ou CNN
* OpenCV pour preprocessing

Ma Première Observation : CNN > SVM
Ici on devrait privilégier CNN (Deep Learning) plutôt que SVM traditionnel pour plusieurs raisons :
- OpenCV features + SVM : Simple, rapidePerformance limitée (~70-80%)
- CNN (Transfer Learning) : CNN (Transfer Learning)

## Base de données
[https://sourceforge.net/projects/flavia/files/Leaf%20Image%20Dataset/]

## Structure du Projet 📁
```
plant-species-classification  
├── data  
│   ├── processed/  
│   |   ├── train/(1,525 images)  
│   |   ├── val/(191 images)  
│   |   └── test/(191 images)  
│   └── raw/  
│   └── features/  
├── models  
├── notebooks  
│   ├── 0.1-eda-dataset-exploration.ipynb  
│   ├── 0.2-image-preprocessing.ipynb  
│   ├── 1.0-feature-extraction-opencv.ipynb  
│   ├── 2.0-baseline-svm.ipynb  
│   ├── 2.1-cnn-from-scratch.ipynb  
│   ├── 2.2-transfer-learning.ipynb  
│   ├── 3.0-model-comparison.ipynb  
│   └── DIAGNOSTIC-error-analysis.ipynb  
└── src  
    └── models  
```

## SVM Baseline Results

### Performance
- **Test Accuracy:** 92.15%
- **F1-Score:** 0.9205
- **Training Time:** ~30s (1,525 samples)

### Features Used
- **Shape (6):** area, perimeter, aspect_ratio, extent, solidity, compactness
- **Color (9):** RGB mean, std, skewness
- **Texture (4):** contrast, homogeneity, entropy, energy

### Model Configuration
```python
SVC(kernel='rbf', C=10, gamma='scale')
```

### Confusion Analysis
- **Errors:** 15/191 (7.9%)
- **Perfect Classes:** 12/32 (37.5% with F1=1.0)
- No systematic confusion pattern detected

### Comparison with Literature
| Method | Accuracy | Source |
|--------|----------|--------|
| Original PNN (2007) | 90.3% | Wu et al. |
| SVM + HOG (2018) | 88.7% | Li et al. |
| **Our SVM + OpenCV** | **92.15%** | ✅ **Top tier** |
```

---

## 🚀 Prochaines Étapes : Google Colab (Deep Learning)

Maintenant qu'on a un **excellent baseline SVM (92.15%)**, on va essayer de le **surpasser** avec :

1. **CNN from Scratch** (objectif : 94-96%)
2. **Transfer Learning ResNet50** (objectif : 97-98%)

---

## 📦 Checklist Avant Colab

### **Fichiers à Uploader sur Google Drive**
```
plant-species-classification/
├── data/processed/
│   ├── train/      (1,525 images)
│   ├── val/        (191 images)
│   └── test/       (191 images)
│
└── data/
    └── processed/
        └── dataset_splits.csv

* Taille totale : ~150-200 MB (images 224x224)

*La suite va sur  Google Colab avec CNN!*