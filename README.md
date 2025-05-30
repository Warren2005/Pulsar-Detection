# 🌌 Pulsar Detection Project

> **"Can we build a reliably accurate model that can predict whether an astronomical observation is a pulsar based on the characteristics of the signal received?"**

## 🚀 Introduction

Pulsars are highly magnetized, rotating neutron stars that emit beams of electromagnetic radiation out of their magnetic poles. These celestial lighthouses help us uncover secrets about the universe, including gravitational waves, exoplanets, and the interstellar medium.

This project aims to identify pulsars using radio signal data from the **High Time Resolution Universe (HTRU) Southern Low Latitude Pulsar Survey**, collected via the Parkes 64-meter radio telescope.

We build a classification model in **R** using statistical features from integrated radio pulse profiles to detect whether an astronomical signal is from a pulsar or not.

---

## 📂 Dataset

- **Source:** HTRU_2 dataset (Cameron et al., 2020)
- **Observations:** 17,898
- **Features:** 8 numerical attributes + 1 binary target (`Class`)
- **Format:** CSV
- **Target Values:**
  - `1`: Pulsar
  - `0`: Non-Pulsar

### 📊 Features Explained

Each feature is derived from signal characteristics:
| Feature Name | Description |
|--------------|-------------|
| `mean_integrated_profile` | Average intensity of the integrated profile |
| `std_integrated_profile` | Signal spread — relates to how much of the rotational phase is covered |
| `skewness_integrated_profile` | Signal symmetry — pulsars tend to have low skewness |
| `exc_kurtois_integrated_profile` | Kurtosis — helps detect secondary pulses (interpulses) |
| `mean_dmsnr`, `std_dmsnr`, `skewness_dmsnr`, `exc_kurtois_dmsnr` | DM-SNR curve metrics (not used in the final model) |

📌 These features were selected based on their astrophysical significance, especially as described by Lyne & Graham-Smith (2012) and Lommen (2015).

---

## 🔍 Methodology

We used **K-Nearest Neighbours (KNN)** as our classification algorithm, implemented with the `tidymodels` framework in R.

### 🧰 Tools and Libraries
```r
library(tidyverse)
library(tidymodels)
library(GGally)
library(MLmetrics)
library(yardstick)
library(themis)
library(RColorBrewer)
library(repr)
```

### 🧪 Preprocessing Steps
- Renamed columns for clarity
- Converted to tibble format
- Split dataset into training and testing sets
- Resampled using SMOTE (Synthetic Minority Oversampling Technique)

### ⚙️ Model Development
- Trained using KNN with cross-validation
- Tuned hyperparameters (`k`) for optimal performance
- Evaluated using metrics like Accuracy, Recall, and Precision

---

## 📈 Results

- **Model Accuracy:** High precision and recall achieved for pulsar classification
- **Key Insights:**
  - Integrated profile statistics are significantly more predictive than DM-SNR values.
  - KNN showed effective performance with the selected features.

---

## 🧠 Why It Matters

Pulsar detection has several scientific and practical benefits:

- 🕰️ Natural cosmic clocks for timekeeping and relativistic experiments
- 🪐 Exoplanet detection via pulse period variation
- 💥 Insight into particle physics under extreme conditions
- 🌠 Understanding stellar evolution post-supernova

_Cited from Lommen (2015) and Lyne & Graham-Smith (2012)_

---

## 📚 References

- Lommen, A. N. (2015). _Using Pulsars to Detect Gravitational Waves_. Physics Today.  
- Lyne, A., & Graham-Smith, F. (2012). _Pulsar Astronomy_. Cambridge University Press.  
- Cameron, A., et al. (2020). _High Time Resolution Universe Survey Data_. Parkes Observatory, CSIRO.

---

## 💡 Future Work

- Incorporate more sophisticated models like Random Forests or SVMs
- Perform feature importance analysis
- Visualize decision boundaries in feature space
- Extend the model to detect binary pulsars or millisecond pulsars

---

## 📁 Project Structure
```
📦 Pulsar-Detection/
├── 📜 README.md
├── 📊 HTRU_2.csv
├── 📁 Notebooks/
│   └── pulsar_model.Rmd
└── 📁 Results/
    └── performance_metrics.csv
```

---

## 🤝 Contributing

Contributions, feedback, or collaborations are welcome! Feel free to fork this repo, submit issues, or suggest improvements.
