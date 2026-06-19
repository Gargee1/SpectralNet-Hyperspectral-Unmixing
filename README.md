# SpectralNet: Modified DUENet for Hyperspectral Image Unmixing

## Overview

SpectralNet is a modified version of the Denoising Unmixing Encoder Network (DUENet) developed for hyperspectral image unmixing and mineral classification. The architecture combines spectral-spatial feature extraction, Dynamic Time Warping (DTW)-based spectral similarity learning, variational latent representations, Gaussian interpolation smoothing, and capsule-based abundance estimation.

The proposed modifications improve training stability, reduce routing complexity, and enable efficient transfer from synthetic to real hyperspectral datasets.

## Features

* 3D convolutional spectral-spatial encoder
* DTW-based spectral similarity gating
* Variational Autoencoder (VAE) bottleneck
* Gaussian latent interpolation smoothing
* Linear capsule abundance estimation
* Synthetic-to-real transfer learning
* Mineral classification and abundance prediction

## Repository Structure

```text
SpectralNet-Hyperspectral-Unmixing/

├── datasets/
│   ├── synthetic_cuprite/
│   └── real_cuprite/
│
├── code/
│   ├── SpectralNet.py
│   ├── zero_shot_real.py
│   └── finetune_real.py
│
├── models/
│   ├── duenet_best.pth
│   └── spectralnet_finetuned_real.pth
│
├── results/
├── figures/
├── report/
└── README.md
```

## Datasets

### Synthetic Cuprite

Synthetic hyperspectral dataset generated using mineral endmember spectra from the USGS spectral library.

**Materials**

* Alunite
* Andradite
* Buddingtonite
* Dumortierite
* Kaolinite_1
* Kaolinite_2
* Muscovite
* Montmorillonite
* Nontronite
* Pyrope
* Sphene
* Chalcedony

### Real Cuprite

AVIRIS Cuprite hyperspectral dataset containing 188 spectral bands after removal of water absorption bands.

Dataset download links are provided in the corresponding dataset folders.

## Requirements

Python 3.10+

### Main Dependencies

* numpy
* torch
* torchvision
* matplotlib
* scikit-learn
* scipy

## Training on Synthetic Data

Run:

```bash
python code/SpectralNet.py
```

This trains SpectralNet using the synthetic Cuprite dataset and saves model checkpoints.

### Output

```text
models/
└── duenet_best.pth
```

---

## Zero-Shot Evaluation on Real Data

Run:

```bash
python code/zero_shot_real.py
```

The synthetic model is directly evaluated on the real Cuprite dataset without additional training.

### Outputs

* Classification Accuracy
* Kappa Coefficient
* Predicted Mineral Abundances

## Fine-Tuning on Real Data

Place the pretrained model in:

```text
models/duenet_best.pth
```

Run:

```bash
python code/finetune_real.py
```

The model weights are initialized from the synthetic training stage and adapted to the real dataset.

### Output

```text
models/
└── spectralnet_finetuned_real.pth
```

## Model Architecture

SpectralNet consists of:

1. 3D Convolutional Encoder
2. DTW Similarity Gating Layer
3. Variational Autoencoder Bottleneck
4. Gaussian Interpolation Module
5. Linear Capsule Abundance Estimator

## Evaluation Metrics

The following metrics are reported:

* Overall Accuracy (OA)
* Per-Class Accuracy
* Kappa Coefficient
* Normalized Root Mean Squared Error (NRMSE)
* Spectral Reconstruction Error

## Project Status

This repository currently contains the implementation of SpectralNet and supporting scripts.
