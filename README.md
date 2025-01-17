# Vocal Tract Segmentation using IMU-Net

## Context and Clinical Relevance

This neuroengineering project focuses on **segmenting the vocal tract** using a **deep learning architecture (IMU-Net)**, a variation of U-Net. The goal is to divide the vocal tract into seven distinct segments, leveraging **Magnetic Resonance Imaging (MRI)**:

1. Background and vocal tract
2. Upper lip
3. Hard palate
4. Soft palate
5. Tongue
6. Lower lip
7. Head

![Example MRI Image](path_to_mri_image.jpg)

This segmentation can be valuable in clinical settings, supporting the diagnosis of speech-related disorders like **Apraxia of Speech** and **Dysarthria**, as well as assessing **velopharyngeal closure**.

## Data Preparation

- The dataset was divided into **training**, **validation**, and **test** sets, stratified by patient, with a 70%/20%/10% split.
- **Preprocessing** included removing Gaussian noise using gamma transformations, Gaussian filtering, and pixel thresholding to eliminate noise.
  
![Preprocessing Example](path_to_preprocessing_example.jpg)

- **Data augmentation** involved rotating, translating, and zooming images to enhance model generalization.

## Neural Network Architecture

The **IMU-Net** architecture was implemented, built on a U-Net backbone with residual blocks in both the encoding and decoding paths to improve performance. 

### Key Components:
- **Encoding blocks**: Extract global features from the images.
- **Bottleneck**: Includes dilated convolutions to increase the receptive field.
- **Decoding blocks**: Reconstruct spatial details using skip connections to combine global and local information.

![IMU-Net Architecture](path_to_imunet_architecture_diagram.jpg)

## Training Methodology

- **Metrics Monitored**: DICE coefficient, accuracy, precision, recall, and mean IoU (Intersection over Union).
- The loss function used was **weighted cross-entropy** to give more importance to underrepresented classes.
- The **Adam optimizer** was used with a learning rate scheduler and early stopping.

## Results

- Multiple trials were conducted with varying hyperparameters such as learning rate, batch size, and number of epochs.
- The best model was obtained with **filtered and augmented data**, yielding promising results in segmenting the seven vocal tract classes.
- **Cross-validation** was conducted with different patient combinations to assess model generalization.

![Model Performance](path_to_model_performance_chart.jpg)

## Conclusions

- The IMU-Net architecture successfully segments the vocal tract into the desired classes.
- The model shows potential for clinical application in diagnosing speech disorders.

### Future Work:
- Test the model on larger, multi-center datasets.
- Evaluate the model's robustness to noise at various levels.
- Explore additional augmentations, such as mirroring images and testing different neural network architectures.

## Clinical Context

This model could be applied in clinical environments to aid in diagnosing disorders related to the vocal tract, such as **Apraxia of Speech** and **Dysarthria**. High recall is especially important to avoid false negatives, ensuring that patients with speech-related conditions are correctly identified.

![Clinical Application](path_to_clinical_application_image.jpg)
