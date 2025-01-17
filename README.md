# Vocal Tract Segmentation using IMU-Net

Project for the Neuroengineering course held at @Politecnico di Milano.

## Context and Clinical Relevance

This neuroengineering project focuses on **segmenting the vocal tract** using a **architecture IMU-Net**, a variation of U-Net. This model could be applied in clinical environments to aid in diagnosing disorders related to the vocal tract, such as **Apraxia of Speech** and **Dysarthria**. 
The goal is to divide the vocal tract into seven distinct segments, leveraging **Magnetic Resonance Imaging (MRI)**:

1. Background and vocal tract
2. Upper lip
3. Hard palate
4. Soft palate
5. Tongue
6. Lower lip
7. Head

<br> <!-- Spazio extra tra figura e testo -->

<div align="center">
   <img width="480" alt="MRI Image" src="IMAGES/Screenshot 2025-01-17 alle 01.39.54.png">
   <br>
   <strong><em>Figure 1– Vocal tract segment</em></strong>
</div>

<br> <!-- Spazio extra tra figura e testo -->
This segmentation can be valuable in clinical settings, supporting the diagnosis of speech-related disorders like **Apraxia of Speech** and **Dysarthria**, as well as assessing **velopharyngeal closure**.
<br> <!-- Spazio extra tra figura e testo -->

<div align="center">
   <img width="240" alt="MRI Image" src="IMAGES/iniziale.jpg">
   <br>
   <strong><em>Figure 2– MRI image before preprocessing </em></strong>
</div>
<br> <!-- Spazio extra tra figura e testo -->




- **Data augmentation** involved rotating, translating, and zooming images to enhance model generalization.


  
## Data Preparation

- The dataset was divided into **training**, **validation**, and **test** sets, stratified by patient, with a 70%/20%/10% split.
- **Preprocessing** included removing Gaussian noise using gamma transformations, Gaussian filtering, and pixel thresholding to eliminate noise.
  

## Neural Network Architecture

The **IMU-Net** architecture was implemented, built on a U-Net backbone with residual blocks in both the encoding and decoding paths to improve performance. 

### Key Components:
- **Encoding blocks**: Extract global features from the images.
- **Bottleneck**: Includes dilated convolutions to increase the receptive field.
- **Decoding blocks**: Reconstruct spatial details using skip connections to combine global and local information.


## Training Methodology

- **Metrics Monitored**: DICE coefficient, accuracy, precision, recall, and mean IoU (Intersection over Union).
- The loss function used was **weighted cross-entropy** to give more importance to underrepresented classes.
- The **Adam optimizer** was used with a learning rate scheduler and early stopping.
<br> <!-- Spazio extra tra figura e testo -->

<div align="center">
   <img width="480" alt="GIF Image" src="IMAGES/video.gif">
   <br>
   <strong><em>Figure 3– Predicted mask over training epochs</em></strong>
</div>
<br> <!-- Spazio extra tra figura e testo -->

## Results

- Multiple trials were conducted with varying hyperparameters such as learning rate, batch size, and number of epochs.
- The best model was obtained with **filtered and augmented data**, yielding promising results in segmenting the seven vocal tract classes.
- **Cross-validation** was conducted with different patient combinations to assess model generalization.

## Conclusions

- The IMU-Net architecture successfully segments the vocal tract into the desired classes.
- The model shows potential for clinical application in diagnosing speech disorders.


