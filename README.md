# Disaster Relief Blue Tarp Detection 🏠

Machine learning classification system for identifying emergency shelters in post-disaster aerial imagery of Haiti.

## 🎯 Project Overview

After natural disasters, humanitarian organizations need to rapidly assess shelter needs across affected areas. This project uses machine learning to automatically detect blue tarps (emergency shelters) in aerial RGB imagery, enabling faster and more comprehensive disaster response mapping.

**Impact:** Automated detection of emergency shelters across 2+ million pixels of aerial imagery, potentially accelerating humanitarian resource allocation.

## 📊 Dataset

- **Training Set:** ~63,000 labeled pixels from aerial imagery
  - Classes: Blue Tarp, Rooftop, Soil, Vegetation, Various Non-Tarp
  - Binary classification: Tarp vs. Not Tarp
  
- **Holdout Set:** 2+ million unlabeled pixels across multiple aerial image tiles
  - Real-world test data with geocoordinates
  - RGB values from Rochester Institute of Technology aerial surveys

## 🔬 Methodology

### Feature Engineering
- RGB color space analysis and visualization
- Principal Component Analysis (PCA) for dimensionality reduction
- Class balancing using SMOTE (Synthetic Minority Over-sampling Technique)

### Models Evaluated
Comprehensive comparison of 11 classification algorithms:
- **Traditional ML:** Logistic Regression, LDA, QDA, KNN
- **Ensemble Methods:** Random Forest, XGBoost
- **Support Vector Machines:** Linear, Polynomial, and RBF kernels
- **Neural Networks:** Multi-Layer Perceptron (MLP)

### Optimization Strategy
- Hyperparameter tuning via cross-validation
- Custom threshold optimization for F1-score
- Parallel processing with 20 workers for computational efficiency

### Evaluation Metrics
- F1-Score (primary metric for imbalanced classes)
- ROC-AUC
- Precision/Recall
- True/False Positive Rates

## 🏆 Key Results

**Best Performing Model:** K-Nearest Neighbors (KNN)
- Optimal classification of blue tarps in holdout imagery
- Balanced precision and recall for disaster assessment

**Visualization Outputs:**
- Original aerial imagery
- Tarp probability heatmaps overlaying original images
- Side-by-side comparison for rapid visual assessment

## 🛠️ Technical Stack

**Languages & Core Libraries:**
- R (tidyverse ecosystem)
- tidymodels (modeling framework)

**ML/Statistical Libraries:**
- discrim, brulee, bonsai, xgboost
- themis (class imbalancing)

**Visualization:**
- ggplot2, plotly (3D RGB scatter plots)
- patchwork (multi-panel layouts)
- ggmap (geospatial context)

**Performance:**
- future (parallel processing)
- Custom threshold optimization functions

## 📁 Repository Structure

```
├── data/
│   ├── HaitiPixels.csv          # Labeled training data
│   ├── holdouts/                # Unlabeled test imagery
│   └── village*.jpg             # Aerial photos
├── Project-2_Foster_Patrick_Epperson_John.Rmd
├── plotly_training.png          # 3D RGB visualization
└── figs/                        # Model performance exports
```

## 🚀 Running the Analysis

### Prerequisites
```r
install.packages(c("tidymodels", "tidyverse", "xgboost", 
                   "discrim", "themis", "future", "plotly"))
```

### Environment Setup
Create a `.env` file with Google Maps API key (for geocoordinate visualization):
```
gmapskey=YOUR_API_KEY_HERE
```

### Execution
```r
# Open in RStudio and knit, or:
rmarkdown::render("Project-2_Foster_Patrick_Epperson_John.Rmd")
```

**Note:** Processing 2M+ pixels requires significant compute. Parallel processing is configured for 20 cores.

## 💡 Key Insights

1. **RGB Color Space Effectiveness:** Blue tarps show distinct spectral signatures in RGB space, making them separable from natural terrain and structures.

2. **Model Selection Trade-offs:** While complex models like Random Forest showed strong training performance, simpler models like KNN generalized better to unseen aerial imagery.

3. **Threshold Optimization:** Custom threshold tuning for F1-score was critical given the imbalanced nature of tarp vs. non-tarp pixels.

4. **Real-World Application:** The heatmap visualization approach provides actionable intelligence for humanitarian organizations by highlighting high-probability shelter locations.

## 🔮 Future Enhancements

- **Multi-spectral data:** Incorporate NIR bands for improved tarp detection
- **Deep learning:** CNN architectures for spatial context awareness
- **Real-time processing:** Optimize for rapid analysis of incoming drone imagery
- **Change detection:** Track shelter deployment/removal over time
- **Integration:** API for GIS/disaster management systems

## 📝 Project Context

Group project for machine learning course (April 2025). Demonstrates end-to-end ML pipeline from exploratory data analysis through model deployment on real humanitarian data.

## 👥 Contributors

- Patrick Foster
- John Michael Epperson

---

*This project demonstrates practical machine learning for social good, combining statistical rigor with real-world humanitarian applications.*
