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
[Base_de_donnees_flavia](https://sourceforge.net/projects/flavia/files/Leaf%20Image%20Dataset/)

[`projects flavia Documentation`](https://flavia.sourceforge.net/)


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
```
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
```

* Taille totale : ~150-200 MB (images 224x224)

*La suite va sur  Google Colab avec CNN!*




# ANNEXE Base de données

| Label | Scientific Name | Common Name(s) | Filename | URL |
|------:|-----------------|----------------|----------|-----|
| 1 | *Phyllostachys edulis (Carr.) Houz.* | pubescent bamboo | 1001–1059 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=506646) |
| 2 | *Aesculus chinensis* | Chinese horse chestnut | 1060–1122 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?1625) |
| 3 | *Berberis anhweiensis* Ahrendt | Anhui Barberry | 1552–1616 | [Harvard Herbarium](http://asaweb.huh.harvard.edu:8080/databases/specimens?id=277371) |
| 4 | *Cercis chinensis* | Chinese redbud | 1123–1194 | [Auburn Univ.](http://www.ag.auburn.edu/hort/landscape/dbpages/306.html) |
| 5 | *Indigofera tinctoria* L. | true indigo | 1195–1267 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=26750) |
| 6 | *Acer palmatum* | Japanese maple | 1268–1323 | [Wikipedia](http://en.wikipedia.org/wiki/Acer_palmatum) |
| 7 | *Phoebe nanmu* (Oliv.) Gamble | Nanmu | 1324–1385 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?28039) |
| 8 | *Kalopanax septemlobus* | castor aralia | 1386–1437 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=565257) |
| 9 | *Cinnamomum japonicum* Sieb. | Chinese cinnamon | 1497–1551 | [Wikipedia](http://en.wikipedia.org/wiki/Cinnamomum_japonicum) |
| 10 | *Koelreuteria paniculata* Laxm. | goldenrain tree | 1438–1496 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=503286) |
| 11 | *Ilex macrocarpa* Oliv. | Big-fruited Holly | 2001–2050 | [Harvard Herbarium](http://asaweb.huh.harvard.edu:8080/databases/specimens?id=159529) |
| 12 | *Pittosporum tobira* | Japanese cheesewood | 2051–2113 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=24067) |
| 14 | *Chimonanthus praecox* L. | wintersweet | 2114–2165 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?10204) |
| 15 | *Cinnamomum camphora* (L.) | camphortree | 2166–2230 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=18175) |
| 16 | *Viburnum awabuki* K.Koch | Japan Arrowwood | 2231–2290 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?80375) |
| 17 | *Osmanthus fragrans* Lour. | sweet osmanthus | 2291–2346 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=505977) |
| 18 | *Cedrus deodara* (Roxb.) | deodar | 2347–2423 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=183408) |
| 19 | *Ginkgo biloba* L. | ginkgo, maidenhair tree | 2424–2485 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=183269) |
| 20 | *Lagerstroemia indica* (L.) | Crape myrtle | 2486–2546 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=27110) |
| 21 | *Nerium oleander* L. | oleander | 2547–2612 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=30184) |
| 22 | *Podocarpus macrophyllus* | yew plum pine | 2616–2675 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=183490) |
| 23 | *Prunus serrulata* var. *lannesiana* | Japanese Flowering Cherry | 3001–3055 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?104754) |
| 24 | *Ligustrum lucidum* Ait. f. | Glossy Privet | 3056–3110 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=503450) |
| 25 | *Toona sinensis* M. Roem. | Chinese Toon | 3111–3175 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?36754) |
| 26 | *Prunus persica* (L.) | peach | 3176–3229 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=508766) |
| 27 | *Manglietia fordiana* Oliv. | Ford Woodlotus | 3230–3281 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?23361) |
| 28 | *Acer buergerianum* Miq. | trident maple | 3282–3334 | [GRIN](http://www.ars-grin.gov/cgi-bin/npgs/html/taxon.pl?1088) |
| 29 | *Mahonia bealei* | Beale's barberry | 3335–3389 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=18846) |
| 30 | *Magnolia grandiflora* L. | southern magnolia | 3390–3446 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=18074) |
| 31 | *Populus × canadensis* Moench | Canadian poplar | 3447–3510 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=22457) |
| 32 | *Liriodendron chinense* | Chinese tulip tree | 3511–3563 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=18086) |
| 33 | *Citrus reticulata* Blanco | tangerine | 3566–3621 | [ITIS](http://www.itis.gov/servlet/SingleRpt/SingleRpt?search_topic=TSN&search_value=28888) |
