# CNN Image Classification Using Transfer Learning (MobileNetV2)

## 1. Project Overview
This project performs image classification on the Jellyfish Types dataset using Convolutional Neural Networks (CNNs) and Transfer Learning with MobileNetV2. 

## 2. Dataset Structure
The dataset is stored in GitHub and loaded inside Colab using:

```
CNN/data/train
CNN/data/valid
CNN/data/test
```

Each folder contains one subfolder per jellyfish class.

## 5. Hyperparameter Tuning
A sweep of 8 experiments was conducted, varying:

- Image size  
- Batch size  
- Optimizer (Adam / RMSprop)  
- Learning rates (frozen & fine-tune)  
- Dropout probability  
- L2 regularization  
- Data augmentation strength  
- Depth of fine-tuning (unfreeze N layers)  
- Number of epochs  

A CSV log (`experiments.csv`) and final submission table were generated automatically.

## 7. Submission Output Generated

### 1. Training History Plots
- Accuracy vs Epoch  
- Loss vs Epoch  

### 2. 25 Test Sample Predictions
Each sample includes:
- Image  
- True Label  
- Predicted Label + Confidence  

### 3. Hyperparameter Tuning Table
Includes:
- Iteration number  
- Parameter settings  
- Training accuracy  
- Validation accuracy  
- Test accuracy  

## 8. Assumptions
- Dataset is properly organized into `train/valid/test` directories.
- All model preprocessing occurs outside the model (no Lambda layers) to allow safe serialization.

## How to Run Code
Use Google Colab
1. Open the notebook Linear_Regression.ipynb in Colab
2. Go to Runtime -> Run all

## 10. Contact
If issues arise with dataset loading or fine-tuning, rerun the cell that builds datasets or re-install TensorFlow/Keras dependencies.
