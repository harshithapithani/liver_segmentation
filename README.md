# 🧠 3D Liver Segmentation Using Deep Learning

## 📌 Overview

This project implements a **3D U-Net-based deep learning pipeline** to segment liver regions from volumetric CT scans. It uses PyTorch and MONAI to process 3D medical images, train a segmentation model, and evaluate its performance.

The project uses the **Medical Segmentation Decathlon (Task03_Liver)** dataset.

## 🎯 Objectives

- Segment liver regions from 3D CT scans.
- Preprocess volumetric medical images in NIfTI format.
- Apply intensity normalization and foreground cropping.
- Perform data augmentation to improve model generalization.
- Train a 3D U-Net model using PyTorch and MONAI.
- Evaluate segmentation performance using the Dice similarity coefficient.
- Visualize predicted segmentation masks.

## 🛠️ Technologies Used

- **Python**
- **PyTorch**
- **MONAI**
- **NumPy**
- **NiBabel**
- **Matplotlib**
- **Scikit-learn**

## 📂 Project Structure

```text
liver_segmentation/
│
├── liver_segmentation.py   # Main segmentation pipeline
├── requirements.txt        # Required Python libraries
├── README.md               # Project documentation
└── .gitignore              # Files excluded from Git
```

## 📊 Dataset

This project is designed for the Medical Segmentation Decathlon Liver dataset.

The dataset contains volumetric CT images and their corresponding segmentation masks in NIfTI (`.nii.gz`) format.

Expected dataset structure:

```text
Task03_Liver/
├── imagesTr/
│   ├── volume-1.nii.gz
│   └── ...
│
└── labelsTr/
    ├── volume-1.nii.gz
    └── ...
```

The image and label filenames must match.

**Note:** The dataset is not included in this repository. Download it separately and configure the dataset path in the Python script.

## ⚙️ Methodology

### 1. Data Preprocessing
- Load 3D CT scans and segmentation labels using MONAI.
- Normalize CT intensity values.
- Convert segmentation masks into binary labels.
- Crop irrelevant background regions.
- Extract 3D patches for training.

### 2. Data Augmentation
- Random flipping.
- Random 90-degree rotations.
- Random sampling of foreground and background patches.

### 3. Model Architecture

A **3D U-Net** is used for volumetric image segmentation.

The model processes 3D CT patches and predicts two classes:
- Background
- Foreground, representing the combined liver and tumor regions in the current implementation.

### 4. Model Training
- Loss function: Dice Loss.
- Optimizer: Adam.
- Learning rate: `0.0001`.
- Training epochs: `50`.
- Training and validation split: `80:20`.

These are the default configuration settings in the provided implementation.

### 5. Evaluation

The model is evaluated using the **Dice similarity coefficient**, which measures the overlap between the predicted segmentation and the ground-truth mask.

A higher Dice score indicates better overlap.

Actual performance results should be added after training and evaluating the model.

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/harshithapithani/liver_segmentation.git
cd liver_segmentation
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

## ▶️ How to Run

1. Download the Medical Segmentation Decathlon Task03_Liver dataset.
2. Extract the dataset into the appropriate directory.
3. Update the dataset path in `liver_segmentation.py`.
4. Enable GPU acceleration if available.
5. Run the training pipeline:

```bash
python liver_segmentation.py
```

The script trains the model, evaluates validation performance, visualizes a segmentation result, and saves the trained model.

**Environment note:** The current implementation uses Google Colab and Google Drive. For local execution, update the dataset paths and replace Colab-specific Drive mounting with your local directory path.

## 📈 Results

The pipeline reports:
- Training loss for each epoch.
- Validation Dice score.
- Best validation Dice score.
- Visualization of the original CT scan, ground-truth mask, and predicted segmentation.

Add screenshots and actual evaluation metrics here after running the model.

## 🔮 Future Improvements

- Implement separate liver and tumor segmentation.
- Experiment with alternative 3D segmentation architectures.
- Optimize hyperparameters to improve segmentation performance.
- Develop an interactive interface for visualizing segmentation predictions.
- Evaluate the model on independent test data.

## ⚠️ Disclaimer

This project is intended for educational and research purposes. The model has not been established as suitable for clinical diagnosis or medical decision-making.

## 👩‍💻 Author

**Harshitha Pithani**

GitHub: [harshithapithani](https://github.com/harshithapithani)
