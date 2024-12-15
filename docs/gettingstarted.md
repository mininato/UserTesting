# Getting Started with the Emotion Recognition Pipeline

Welcome to the **Emotion Recognition Pipeline**! This guide will help you install, configure, and use the pipeline to analyze movement data and recognize emotions efficiently.

---

## **1. Installation**

### Prerequisites

- **Python**: Version 3.8 or higher.
- **Environment**: It is recommended to create a virtual environment for managing dependencies.

```bash
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate
```

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/emotion-recognition-pipeline.git
   cd emotion-recognition-pipeline
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## **2. How Data Processing Works**

Data analysis typically follows a structured workflow, consisting of four major stages: **Data Acquisition**, **Data Preprocessing**, **Feature Extraction**, and **Model Training & Evaluation**. Here's a brief overview of these stages and how the pipeline fits into this process.

![Data Processing Workflow](images/Data_Process_BG.drawio.svg)

### 2.1. **Data Acquisition**

In this stage, raw data is collected from various sources. For this pipeline:

- **Data Sources**: Accelerometer measurements and self-reports.

- **Format**: CSV files containing timestamped accelerometer readings (`x`, `y`, `z`) and self-report labels (e.g., `arousal`, `valence`).

The pipeline begins with the **ImportData** class to load raw data into a structured format.

---

### 2.2. **Data Preprocessing**

Raw data often contains noise, inconsistencies, or irrelevant information. This stage involves:

1. **Synchronization**: Combining accelerometer and self-report data using timestamps and a defined time window.

2. **Filtering**: Removing high-frequency noise using a low-pass filter.

3. **Scaling**: Normalizing accelerometer data for consistent feature computation.

The pipeline includes:

- `01_combining_dataframes_pipeline.py`: Synchronizes raw data into a combined dataset.

- **LowPassFilter** and **ScaleXYZData** classes for filtering and scaling.

---

### 2.3. **Feature Extraction**

This stage converts raw accelerometer data into meaningful features representing movement patterns. Features are grouped into domains such as:
- **Time Domain**: Mean, variance, RMS, skewness, etc.

- **Frequency Domain**: Spectral entropy, dominant frequency, etc.

- **Spatial Features**: Euclidean norm, tilt angles, etc.

The pipeline uses:

- `02_feature_extraction_pipeline.py`: Extracts features based on your configuration in `_config.py`.

- **ExtractFeatures** class: Handles computation across multiple feature domains.

---

### 2.4. **Model Training & Evaluation**

With extracted features, this stage trains a machine learning model to classify emotions:

1. **Model Training**: Uses classifiers like RandomForest, SVM, or XGBoost.

2. **Hyperparameter Optimization**: Employs Bayesian search for tuning.

3. **Evaluation**: Generates performance metrics and feature importance.

The pipeline uses:
- `03_training_model_pipeline.py`: Trains a model using extracted features.
- **TrainModel** class: Handles training, hyperparameter tuning, and evaluation.

---

## **3. How to combine Dataframes**

---

## **4. How to extract Features?**

---

## 5. **How to train a Model**

---

## 6. **How to classify Movement Data**

---

## 7. Support

For detailed instructions or issues, refer to the repository documentation or contact us at `<support-email>`.

---

This additional section provides clarity about the general data analysis process and highlights how the pipeline fits into this workflow. Let me know if you need further refinements!