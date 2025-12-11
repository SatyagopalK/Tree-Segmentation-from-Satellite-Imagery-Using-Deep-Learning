Tree Crown Segmentation from Multispectral Satellite Imagery

ISRO–NRSC | Project Intern | 05 May 2025 – 30 September 2025

📌 Project Overview

This project focuses on pixel-level tree crown mapping from multispectral LISS-4 satellite imagery as part of a wall-to-wall vegetation monitoring workflow. Tree areas are labeled as 1, and non-tree areas as 0, explicitly excluding crops and shrubs. A deep learning–based segmentation pipeline was developed to address fine-scale variability and limited training data.

📸 Dataset Preparation
Source Data

Input imagery: LISS-4 multispectral scenes

Reference masks: Manually prepared using high-resolution KOMSAT imagery

Tree crown masks were derived by overlaying centroid points on LISS-4 chips.

Data Processing Workflow

LISS-4 scenes clipped into 256×256 chips

Chips cropped into 64×64 patches

Dataset prepared for deep learning segmentation

Two-Stage Augmentation Strategy
Stage 1 – Offline Augmentation

Flips

Rotations

Elastic transforms

Distortions

Gaussian blur
➡️ Expanded dataset to 1,476 samples

Stage 2 – On-the-fly Augmentation

Applied via a stratified generator
➡️ Balanced dataset with 1,584 final samples

Dataset was split into train / validation / test for robust evaluation.

🧠 Model Architecture & Training
Model Used

MultiResUNet for high-resolution tree crown segmentation

Loss Functions Tested

Dice + Focal

Tversky + Focal

Tversky

Class-balanced BCE

Asymmetric Loss

Lovasz Hinge

Evaluation Metrics

Accuracy

Dice Coefficient

Intersection over Union (IoU)

F1 Score

📊 Error Analysis & Validation

Evaluation performed on test chips using:

Pixel-wise error maps

Missed-object categorization:

Small: 1–2 px

Medium: 3–5 px

Large: ≥6 px

Vegetation Cover Fraction (VCF) comparison using:

R²

RMSE

Bias

Insights from this analysis guided final model selection.

🏆 Key Results
Loss Function	Accuracy	Dice	IoU	F1	R²
Dice + Focal	0.9643	0.6238	0.4533	0.6238	0.755
Tversky + Focal	0.9648	0.5715	0.4001	0.5715	0.727
Tversky	0.9634	0.6155	0.4445	0.6155	0.741
🗺️ Wall-to-Wall Mapping

Steps used to generate full-scene predictions:

Predicted masks aligned to the input CRS

Mosaicked into a continuous wall-to-wall tree crown map

Pixel resolution aggregated from 5 m → 100 m (≈1 ha)

Final VCF maps generated for regional-scale vegetation assessment

🌱 Impact

This project demonstrates that integrating:

High-resolution reference data

A systematic two-stage augmentation pipeline

A deep learning MultiResUNet architecture

can deliver accurate and scalable tree crown segmentation.
The workflow is applicable to:

Ecological monitoring

Land-cover mapping

Natural resource management

across large geographic regions.
