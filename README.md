Fingerprint Biometric Identification System
Project Overview

This project implements a fingerprint biometric identification system using classical image processing and feature-based matching techniques.

The system accepts a single fingerprint image as input, compares it against a database of stored fingerprints, and determines whether access should be granted or denied based on a similarity score and an evaluation-derived threshold.

The objective is to demonstrate a complete biometric pipeline, from preprocessing and feature extraction to evaluation and decision-making.

System Pipeline
1. Image Preprocessing

Fingerprint images are enhanced and normalized to improve ridge visibility and consistency. The preprocessing steps include:

Grayscale conversion

Contrast enhancement using CLAHE

Binarization using Otsu thresholding

Skeletonization to reduce ridges to a single-pixel width

This stage produces clean ridge structures suitable for minutiae extraction.

2. Minutiae Extraction

Distinctive fingerprint features are extracted from the skeletonized image:

Ridge endings

Bifurcations

Minutiae are detected using the crossing number method and stored as feature points defined by their spatial coordinates and type.

3. Minutiae Matching

Fingerprint similarity is computed using a distance-based matching strategy:

Each minutia in the query fingerprint is matched to the nearest unused minutia in the candidate fingerprint

Matches are accepted if the distance is below a predefined threshold

The total number of matches is normalized to produce a similarity score between 0 and 1

Higher scores indicate greater similarity between fingerprints.

4. PCA-Based Alignment

To compensate for rotation and translation differences between fingerprint impressions, a PCA-based alignment step is applied:

Minutiae points are centered using their centroid

Principal Component Analysis is used to estimate the dominant orientation

Minutiae are rotated into a common reference frame before matching

This alignment significantly improves matching performance.

Identification Mode (1:N Matching)

The system operates in identification mode, where a single query fingerprint is compared against all fingerprints in the database. The fingerprint with the highest similarity score is selected as the best match.

An access decision is then made based on a global threshold.

Evaluation and Threshold Selection

System performance is evaluated using labeled genuine and impostor fingerprint pairs. The evaluation includes:

Score distribution analysis

Receiver Operating Characteristic (ROC) curve

Equal Error Rate (EER) computation

The final decision threshold is chosen at the EER point, where the false acceptance rate equals the false rejection rate.

Results:

ROC AUC ≈ 0.85

Overall accuracy ≈ 80%

PCA alignment improved matching performance in approximately 90% of evaluated cases

User Interface

An interactive Gradio-based user interface allows users to:

Upload a fingerprint image

Search the fingerprint database

Visualize minutiae overlays for both the query fingerprint and the best match

Receive a clear access decision

This interface facilitates demonstration and interpretation of the biometric system.
