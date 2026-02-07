**Handwritten Digital Signature Generation using Vanilla GAN**

This project implements a Vanilla Generative Adversarial Network (GAN) to generate synthetic handwritten digital signatures that resemble real signatures while preserving individual privacy. The generated signatures can be used for data augmentation, research, and signature verification system training without exposing real personal data.

**🔹 Module-Wise Implementation**

**Module 1 — Data Pipeline & Preprocessing**
This module prepares handwritten signature images for GAN training.
Implemented Features:
Load signature images in JPG / PNG format
Resize images (e.g., 64×64 or 128×128)
Convert to grayscale (single-channel images)
Normalize pixel values from [0, 255] → [-1, 1] (Tanh compatible)
Batch processing for efficient training
Purpose:
Ensures clean, standardized signature data for stable GAN training.

**Module 2 — Model Design (Vanilla GAN Architecture)**
Generator (G):
Input: Random noise vector (latent space)
Fully connected layers followed by reshaping
Upsampling using convolutional layers
Activation:
ReLU (hidden layers)
Tanh (output layer)
Discriminator (D):
Input: Real or generated signature image
Convolutional layers for feature extraction
Dense layer with Sigmoid output
Activation: LeakyReLU (0.2)
Loss & Optimizer:
Binary Cross Entropy (BCE)
Adam Optimizer
Learning rate = 0.0002
Beta1 = 0.5

<img width="586" height="619" alt="image" src="https://github.com/user-attachments/assets/61170819-26d1-4010-b33d-bff1a4270f7f" />


**Module 3 — Training & Monitoring**
This module manages the GAN training process.
Training Process:
Train Discriminator on:
Real signature images
Generated (fake) signatures
Train Generator to fool the Discriminator
Repeat for 100–300 epochs
Monitoring:
Track:
Generator loss (G_loss)
Discriminator loss (D_loss)
Save:
Generated signature samples
Model checkpoints (G_final, D_final)
Outcome:
Generated signatures become clearer, smoother, and more realistic over time.

**Module 4 — Evaluation & Visualization**
Evaluates the quality and diversity of generated handwritten signatures.
Quantitative Metrics:
Signature realism score (classifier-based)
Diversity score (variation in signature patterns)
FID proxy score (real vs synthetic comparison)
Qualitative Analysis:
Visual inspection of generated signatures
Detection of mode collapse
Visualizations:
Loss curves (G_loss vs D_loss)
Generated signature image grids
Latent space interpolation
t-SNE plots (real vs synthetic signatures)

**Module 5 — Deployment Layer**
Enables real-world usage of the signature generator.
Implemented Concepts:
Export trained Generator model
Inference script for batch signature generation
Deployment Options:
Streamlit UI
Flask / FastAPI API
Use Cases:
Generate N synthetic signatures on demand
Create large synthetic signature datasets
Control randomness and resolution

**Module 6 — Monitoring & Update Pipeline**
Ensures reliability, ethics, and long-term performance.
Monitoring:
Track inference latency
Monitor generation frequency
Log failures
Model Updates:
Periodic retraining with new signature samples
Version control:
G_v1, G_v2, G_v3
Privacy Assurance:
Prevent memorization of real signatures
Compare generated signatures with nearest real samples

**🖊️ Real-Life Applications**
Signature verification system training
Banking and financial document authentication
Academic research on handwriting analysis
Biometric security system development
Data augmentation for deep learning models

**🛠️ Technologies Used**
Python
TensorFlow / Keras
NumPy, Matplotlib
Google Colab
Streamlit / Flask (deployment)

**▶️ How to Run**
Open the notebook in Google Colab
Run all cells sequentially
View generated signature images and loss curves
Use inference or deployment scripts for generation

**📌 Conclusion**
This project demonstrates that a Vanilla GAN can effectively generate synthetic handwritten digital signatures while preserving user privacy. The approach is suitable for secure data augmentation and biometric research, and it also highlights the need for advanced GAN variants when working with highly complex signature patterns.
