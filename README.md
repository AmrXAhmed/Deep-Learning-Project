### Deep Learning-Based Prediction of CDK5 Inhibitory Activity
#A deep learning pipeline to predict the inhibitory potency (pKi) of small molecules targeting Cyclin-dependent kinase 5 (Cdk5) using molecular fingerprints and regression models.

#📌 Overview
Cdk5 is a promising drug target implicated in neurodegenerative diseases (e.g., Alzheimer's, Parkinson's) and various cancers. This project leverages neural networks to predict inhibitory activity (pKi values) of small molecules based on structural data from the ChEMBL database.

#🧬 Dataset
Source: ChEMBL 25

Target: pKi values against Cdk5 (UniProt ID: Q00535)

Size: 1038 curated compounds

Preprocessing: Performed with RDKit (neutralization, salt removal, deduplication)

#🧪 Molecular Fingerprints
Used multiple feature encodings to represent molecules:

MACCS Keys (166-bit substructure)

Morgan Fingerprints (Radius 2 & 3, 2048-bit ECFP)

RDKit Topological Fingerprints (path-based, 2048-bit)

#🧠 Models
1. Multilayer Perceptron (MLP)
Framework: TensorFlow/Keras

Optimizer: Adam (lr=0.001)

Loss: Mean Squared Error (MSE)

Regularization: Dropout (0.3–0.5), EarlyStopping

2. 1D Convolutional Neural Network (CNN)
Input: 3D reshaped fingerprint tensor

Layers: Conv1D → GlobalMaxPooling → Dense → Output

Notes: CNN underperformed compared to MLP for sparse fingerprints

#🧪 Evaluation Metrics
MSE (Mean Squared Error)

MAE (Mean Absolute Error)

R² Score

Best performance achieved with MACCS and Morgan (r=2) fingerprints:

Fingerprint	MSE	MAE	R²
MACCS	0.75	0.63	0.11
Morgan (r=2)	0.74	0.65	0.13

#🔍 Virtual Screening
Used best-performing model to screen ~70,000 compounds from the Enamine kinase library

Identified top candidates with predicted pKi > 8.3

Visualized high-affinity structures and key substructures influencing predictions

#📊 Visualization & Analysis
Learning curves, pKi distribution histograms

Atom-level contribution heatmaps

Jaccard similarity of fingerprint types

Confusion between radius-2 and radius-3 fingerprints



