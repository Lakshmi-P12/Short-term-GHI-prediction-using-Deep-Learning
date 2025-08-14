# Spatiotemporal Autoencoder-Based Framework for GHI Prediction Using Visible Satellite Imagery

## Project Description

This project focuses on short-term Global Horizontal Irradiance (GHI) forecasting using visible-band satellite imagery from the INSAT-3D series. The model uses a spatiotemporal autoencoder integrated with ConvLSTM layers to capture cloud movement and predict GHI for the next 2 hours at 30-minute intervals.
It combines:

* Physics-based clear-sky irradiance modeling (PVLib Solis model)
* Cloud mask generation and cloud index computation
* Deep learning for temporal pattern recognition

The system is designed for operational nowcasting in renewable energy systems where real-time solar forecasting is required.

## Features & Methodology Summary

* Area of Interest (AOI) based processing: Focuses only on the specified geographic region to reduce computation time.
* Cloud detection: Uses autoencoder reconstruction error to identify cloud coverage in visible satellite imagery.
* Cloud index calculation: Quantifies cloud attenuation effect on GHI.
* Clear-sky GHI estimation: Uses PVLibâ€™s Solis model.
* Spatiotemporal deep learning model:

  * Encoder for extracting spatial features
  * ConvLSTM layers for capturing temporal patterns
  * Decoder for reconstructing future frames
* GHI prediction: Predicts 4 future steps (2 hours) from 6 past observations (3 hours).

## How to Run the Code

1. Clone the Repository

2. Install Dependencies
   pip install -r requirements.txt

3. Prepare Input Data

   * Satellite Data: INSAT-3D visible-band imagery in `.h5` format.
   * Cloud Mask Files: `. npy` binary mask files for each timestamp.
   * Place your input files in a `data/` folder inside the project directory.

4. Running the Notebook

   * Open the Jupyter Notebook:
     jupyter notebook GHI_Forecasting_final_code.ipynb

   * Run all cells in order.

5. AOI and File Creation During Execution

   * At the start, you define your Area of Interest (AOI) with latitude, longitude, and altitude in the code.
   * The script:

     * Clips satellite imagery to your AOI.
     * Creates cloud mask arrays (`. npy` files).
     * Computes Cloud Index (CI) for each timestamp.
     * Generates clear-sky GHI values using PVLib.
     * Prepares time series sequences for training and validation.
   * After training, the model creates:

     * Saved Model Weights in `.h5` format.
     * Prediction Results in `.csv` format.
     * Visualization Plots (actual vs predicted GHI).

## Dependencies & Requirements

Python 3.8+ and the following packages:

* `numpy`
* `pandas`
* `matplotlib`
* `h5py`
* `tensorflow`
* `scikit-learn`
* `pvlib`
* `jupyter`
* `opencv-python`
* `seaborn`

## Authors & Credits

* Lakshmi P “Vellore Institute of Technology, Chennai"
* Kalpalathika N “Vellore Institute of Technology, Chennai"
* Jumin Salih “Vellore Institute of Technology, Chennai"
* Nihal Siddiqi “Vellore Institute of Technology, Chennai"
* Bhuvaneswari A “Assistant Professor, Vellore Institute of Technology, Chennai"

Research Paper: *Enhanced Short-Term GHI Prediction Using Cloud-Aware Deep Autoencoder Network* “IEEE, ICSCSA 2025.
