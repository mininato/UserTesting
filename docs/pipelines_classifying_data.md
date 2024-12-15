## **General Explanation**

The Analyzing Data Pipeline is designed to preprocess, extract features, and classify emotions based on accelerometer data.
This pipeline simplifies the analysis process by automating tasks like filtering noise, normalizing data, extracting meaningful features, and applying machine learning models.

??? info "Click to view diagram"
    ![Overview of pipeline](images/Classify_movement_data.drawio.BG.svg)

## **Use Cases**
**Emotion Recognition:** Classify emotions (e.g., arousal and valence levels) using pre-trained machine learning models on movement data.

## **Input & Configuration**

Raw Accelerometer Data containing xyz data with timestamps and participantid
A pre-trained Model which is trained with the same features which will be extracted in the pipeline in a later step

| **Input**              | **Description**                                                                                     |
|------------------------|-----------------------------------------------------------------------------------------------------|
| Raw Accelerometer Data | Contains `x`, `y`, `z` axis data with `timestamps` and `participantId`.                             |
| Pre-trained Model      | A model trained with the same features that will be extracted in the pipeline during a later step.  |

| **Configuration**     | **Description**                                                                                          |
|------------------------|----------------------------------------------------------------------------------------------------------|
| `cutoff_frequency`     | The cutoff frequency for the low-pass filter.                                                           |
| `data_frequency`       | The sampling rate of the accelerometer data in Hz.                                                      |
| `order`                | The order of the low-pass filter.                                                                       |
| `scaler_type`          | The type of scaler to normalize or standardize the data. Options: `"standard"`, `"minmax"`, or `"none"`.|
| `window_length`        | The length of the sliding window for feature extraction (in seconds).                                   |
| `window_step_size`     | The step size for moving the sliding window (in seconds).                                               |
| `selected_domains`     | List of feature domains to include for extraction (e.g., `['time_domain', 'frequency']`).               |
| `include_magnitude`    | Whether to include magnitude-based features during feature extraction. Options: `True` or `False`.      |
| `model_path`           | Path to the pre-trained model for classification.                                                       |

## **Output**
- A CSV file with all extracted features and predicted emotions as columns.
- Each row represents a time window during which emotions were classified.

| **Time Window** | **Extracted Features**             | **Predicted Emotion** |
|------------------|------------------------------------|------------------------|
| Time Window 1    | Feature values for window 1       | Predicted emotion 1    |
| Time Window 2    | Feature values for window 2       | Predicted emotion 2    |
| Time Window 3    | Feature values for window 3       | Predicted emotion 3    |
