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
Flips, rotations, elastic transforms, distortions, Gaussian blur
→ Expanded dataset to 1,476 samples

Stage 2 – On-the-fly Augmentation
Used in a stratified generator during training
→ Balanced dataset with 1,584 final samples

Dataset split into train / validation / test for robust evaluation.

🧠 Model Architecture & Training
Model Used

MultiResUNet for high-resolution segmentation

Loss Functions Tested

Dice + Focal

Tversky + Focal

Tversky

Class-balanced BCE

Asymmetric Loss

Lovasz Hinge

Evaluation Metrics

Accuracy

Dice coefficient

Intersection over Union (IoU)

F1 Score

📊 Error Analysis & Validation

Performed detailed evaluation on test chips, including:

Pixel-wise error maps

Missed-object categorization:

small (1–2 px)

medium (3–5 px)

large (≥6 px)

Vegetation Cover Fraction (VCF) comparison

R²

RMSE

Bias

This analysis guided selection of the best models.

🏆 Key Results

Top-performing model configurations:

Loss Function	Accuracy	Dice	IoU	F1	R²
Dice + Focal	0.9643	0.6238	0.4533	0.6238	0.755
Tversky + Focal	0.9648	0.5715	0.4001	0.5715	0.727
Tversky	0.9634	0.6155	0.4445	0.6155	0.741
###🗺️ Wall-to-Wall Mapping

After model selection, predictions were generated for the entire LISS-4 scene:

Predicted masks aligned to the input CRS

All predictions mosaicked into a continuous wall-to-wall map

Pixel resolution aggregated from 5 m → 100 m (~1 ha)

Final VCF maps produced for large-scale vegetation assessment

🌱 Impact

The project demonstrates that combining:

high-resolution reference data,

two-stage augmentation, and

deep learning segmentation

can deliver accurate and scalable tree crown mapping.
This framework is applicable to ecological monitoring, land-cover mapping, and natural resource management across large geographic regions.
