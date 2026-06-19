# SpectralNet: Modified DUENet for Hyperspectral Image Unmixing

# Overview
SpectralNet is a modified version of the Denoising Unmixing Encoder Network (DUENet) developed for hyperspectral image unmixing and mineral classification. The architecture combines spectral-spatial feature extraction, Dynamic Time Warping (DTW)-based spectral similarity learning, variational latent representations, Gaussian interpolation smoothing, and capsule-based abundance estimation.

The proposed modifications improve training stability, reduce routing complexity, and enable efficient transfer from synthetic to real hyperspectral datasets.

# Features
3D convolutional spectral-spatial encoder
DTW-based spectral similarity gating
Variational Autoencoder (VAE) bottleneck
Gaussian latent interpolation smoothing
Linear capsule abundance estimation
Synthetic-to-real transfer learning
Mineral classification and abundance prediction

# Repository Structure
SpectralNet-Hyperspectral-Unmixing/ 

datasets/ 
synthetic_cuprite/ 
real_cuprite/ 

code/ 
SpectralNet.py 
zero_shot_real.py 
finetune_real.py 

models/ 
duenet_best.pth
spectralnet_finetuned_real.pth

results/  

figures/ 

README.md

# Datasets
Synthetic Cuprite

Synthetic hyperspectral dataset generated using mineral endmember spectra from the USGS spectral library.

Materials:

Alunite
Andradite
Buddingtonite
Dumortierite
Kaolinite_1
Kaolinite_2
Muscovite
Montmorillonite
Nontronite
Pyrope
Sphene
Chalcedony
Real Cuprite

AVIRIS Cuprite hyperspectral dataset containing 188 spectral bands after removal of water absorption bands.

Dataset download links are provided in the corresponding dataset folders.

# Requirements
Python 3.10+

Main dependencies:

numpy
torch
torchvision
matplotlib
scikit-learn
scipy

# Training on Synthetic Data
Run:
python src/SpectralNet.py
This trains SpectralNet using the synthetic Cuprite dataset and saves model checkpoints.

Output:
models/
    duenet_best.pth

# Zero-Shot Evaluation on Real Data
Run:
python src/zero_shot_real.py
The synthetic model is directly evaluated on the real Cuprite dataset without additional training.

Outputs:
Classification accuracy
Kappa coefficient

# Fine-Tuning on Real Data

Place the pretrained model in:
models/duenet_best.pth

Run:
python src/finetune_real.py
The model weights are initialized from the synthetic training stage and adapted to the real dataset.

Output:
models/
    spectralnet_finetuned_real.pth

# Model Architecture
SpectralNet consists of:

3D Convolutional Encoder
DTW Similarity Gating Layer
Variational Autoencoder Bottleneck
Gaussian Interpolation Module
Linear Capsule Abundance Estimator

# Evaluation Metrics
The following metrics are reported:

Overall Accuracy (OA)
Per-Class Accuracy
Kappa Coefficient
NRMSE
Spectral Reconstruction Error
