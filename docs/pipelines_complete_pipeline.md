## **General Explanation**
This pipeline is designed for users who want to train a machine learning model for emotion recognition in one complete process. It takes raw accelerometer data (x, y, z, and timestamps) and self-reports as input, processes the data through several steps, and outputs a trained model along with a detailed report on its performance.

The pipeline automates all necessary preprocessing steps, including combining data, filtering noise, scaling, extracting features, and training the model. It is ideal for users looking for a straightforward, end-to-end solution without intermediate checkpoints. By the end of the pipeline, users receive:

1. A fully trained and optimized model ready for use.

2. A report containing model performance metrics, hyperparameter details, and feature importances.

This setup is especially useful for researchers or analysts who need a training pipeline for emotion classification based on accelerometer data combined with self-reports.

??? info "Click to view diagram"
    ![Overview of pipeline](images/Complete_pipeline.drawio.BG.svg)

## **Inputs & Configuration**

| **Input Type**          | **Description**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| Raw Accelerometer Data  | CSV file with columns for x, y, z axes, timestamps (timeOfNotification), and participantId. |
| Self-Reports Data       | CSV file with columns for timeOfNotification, participantId, and emotion labels (e.g., arousal, valence). |

**Configuration**

For the configuration please see:
[configuration file](config.md)

## **Outputs**

| **Output**             | **Description**                                                                                   |
|-------------------------|---------------------------------------------------------------------------------------------------|
| **Trained Model**       | A serialized model file (e.g., `xgboost_best_model_target.pkl`) saved with the target name for easy identification. |
| **Classification Report** | A JSON file containing detailed metrics like precision, recall, and F1-score.                   |

