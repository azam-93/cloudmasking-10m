
# Cloud Masking on Sentinel-2 Imagery at 10m Resolutions

This repository contains the implementation of my Master's thesis project on cloud detection using Sentinel-2 satellite data. The goal is to improve cloud masking accuracy at 10m resolution by combining spectral features from multiple resolutions (10m, 20m, and 60m) and applying a machine learning approach (XGBoost).
##  Project Overview
The project is structured into two main stages:
### Stage 1 – Training
- Load Sentinel-2 data from 20m and 60m bands.
- Extract pixel-wise spectral vectors and ground truth labels (SCL masks).
- Train an XGBoost classifier on valid classes.
- Evaluate model performance using classification metrics.

### Stage 2 – Inference:
- Load native 10m bands (B02, B03, B04) and resample 20m bands (B05,B06,B07,B11,B12) to 10m resolution.
- Merge them to create a full-resolution input stack.
- Run inference using the pretrained model from Stage 1.
- Save the predicted masks as `.tif` files for visualization in QGIS.
## Project Structure
```bash
cloudmasking_10m/
├── cloudmasking_10m_final.ipynb       # Main Jupyter Notebook (full training + inference pipeline)
├── README.md                          # Project documentation
├── .gitignore                         
├── /data/                             # Placeholder for raw Sentinel-2 scenes (.SAFE folders)
├── /outputs/                          # Contains output predictions and plots
