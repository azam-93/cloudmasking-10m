
# Cloud Masking on Sentinel-2 Imagery at 10m Resolutions

This repository contains the implementation of my Master's thesis on cloud detection, focused on improving cloud masking accuracy at 10m resolution using Sentinel-2 imagery. While Sen2Cor provides cloud masks at 20m and 60m resolutions, they often lack the spatial detail required for high-resolution applications such as land monitoring and agriculture.

To overcome this limitation, the project combines multispectral data from 10m, 20m, and 60m bands and applies an XGBoost-based machine learning pipeline to generate refined cloud masks at 10m resolution. Validation was conducted using a manually corrected Scene Classification Layer (SCL), created in QGIS to ensure higher accuracy during the inference phase.

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
