## **General Explanation**

The **Combining DataFrames Pipeline** is designed to preprocess and merge raw accelerometer data and self-reports into a unified dataset. It simplifies the process of aligning timestamps, aggregating movement data within a specified time window, and dynamically adding contextual labels from self-reports. This pipeline is modular, making it reusable and adaptable for different stages of analysis, from preprocessing to model training.

??? info "Click to view diagram"
    ![Overview of pipeline](images/Combine_dataframes.drawio.BG.svg)

## **Use Case**

**Combine raw accelerometer and self-reports data:** Create a structured dataset ready for feature extraction or model training.
**Preprocess data consistently:** Ensure uniform handling of timestamps, labels, and accelerometer data across different datasets.
**Prepare data for exploratory or predictive analysis:** Use the resulting combined dataset as the foundation for understanding relationships between movement patterns and self-reported labels.

## **Inputs**

| **Input Type**          | **Description**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| Raw Accelerometer Data  | CSV file with columns for x, y, z axes, timestamps (timeOfNotification), and participantId. |
| Self-Reports Data       | CSV file with columns for timeOfNotification, participantId, and emotion labels (e.g., arousal, valence). |
| Configuration Settings  | - `time_window`: Specifies the size (in minutes) of the time window for aggregating accelerometer data around each self-report. |
|                         | - `label_columns`: A list of columns from the self-reports dataset to use as labels (e.g., ["arousal", "valence"]). |

## **Outputs**
It Outputs a Dataset with these Columns:

| **Column Name**      | **Description**                                                                 |
|----------------------|---------------------------------------------------------------------------------|
| participantId        | Participant identifier.                                                         |
| selfreport_time      | Timestamp of the self-report.                                                   |
| accel_time           | Timestamp of the accelerometer reading.                                         |
| x                    | Accelerometer reading for the x axis.                                           |
| y                    | Accelerometer reading for the y axis.                                           |
| z                    | Accelerometer reading for the z axis.                                           |
| Emotion labels       | Emotion labels from `label_columns`.                                            |
| groupid              | A unique identifier for each group of self-report and its corresponding accelerometer data. |