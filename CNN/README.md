# README – CNN Image Classification Using Transfer Learning (MobileNetV2)

## 1. Project Overview
This project performs image classification on the Jellyfish Types dataset using Convolutional Neural Networks (CNNs) and Transfer Learning with MobileNetV2. The goal is to train, fine-tune, and evaluate a pre-trained model, then perform systematic hyperparameter tuning and log all experiment results.

This work fulfills the requirements of the Assignment 3 “Image-Based Project” guidelines.

## 2. Requirements Satisfied
- Implemented in Python / Keras / TensorFlow
- Used Transfer Learning (MobileNetV2)
- Performed fine-tuning on the pre-trained model
- No local hard-coded paths (GitHub/Colab directories used)
- Dataset split into train / validation / test folders
- Multiple hyperparameters tuned and logged
- All submission outputs generated:
  - History plots
  - 25 test sample predictions (image + true label + predicted label)
  - Parameter tuning table

## 3. Dataset Structure
The dataset is stored in GitHub and loaded inside Colab using:

```
CNN/data/train
CNN/data/valid
CNN/data/test
```

Each folder contains one subfolder per jellyfish class.

## 4. How the Model Works

### Step 1 — Data Loading & Preprocessing
- Images resized to (224, 224), (192,192), (160,160) depending on experiment
- Data augmentation applied:
  - Random flip
  - Random rotation
  - Random zoom
- Images normalized to [-1, 1] (MobileNetV2 scaling)

### Step 2 — Transfer Learning (Frozen Base)
- Load MobileNetV2 (ImageNet weights, include_top=False)
- Freeze all convolutional layers
- Add classification head:
  - GlobalAveragePooling → Dropout → Dense(softmax)

### Step 3 — Fine-Tuning
- Unfreeze last 20–80 layers depending on experiment
- Reduce learning rate (1e-5 to 5e-6)
- Train until early stopping (patience=3)

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

## 6. How to Run the Notebook
1. Open the provided Colab notebook.
2. Ensure GPU runtime is enabled.
3. Run Step 1 → Step 6 in order.
4. The notebook automatically:
   - Loads the dataset  
   - Builds datasets and model  
   - Trains & fine-tunes the model  
   - Runs all hyperparameter sweeps  
   - Saves experiment logs to:
     ```
     sweeps_mobilenetv2/
     sweeps_mobilenetv2_clean/
     ```
   - Generates prediction plots and tuning table  

No additional setup is required.

## 7. Output Files Generated

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

### 4. Experiment Artifacts
- `experiments.csv`  
- `submission_table.csv`  
- `submission_table.md`  
- Best model checkpoints  
- TensorBoard logs  

## 8. Assumptions
- Dataset is properly organized into `train/valid/test` directories.
- Training accuracy is computed from TensorBoard logs or evaluation on the training dataset.
- All model preprocessing occurs outside the model (no Lambda layers) to allow safe serialization.

## 9. How to Reproduce Results
1. Run the notebook from top to bottom.  
2. Hyperparameter sweep results will appear in:
   ```
   sweeps_mobilenetv2/
   ```
3. Use the generated `submission_table.md` in your final report.

## 10. Contact
If issues arise with dataset loading or fine-tuning, rerun the cell that builds datasets or re-install TensorFlow/Keras dependencies.
