## **General Explanation**
This modular pipeline processes movement data from accelerometers to extract features that can be used for emotion recognition and other analyses. It consists of predefined pipeline components, each represented by a class. These components include data import, filtering, scaling, and feature extraction. The modular structure allows users to set "checkpoints" at various stages, making it easy to reuse intermediate outputs (e.g., scaled data or extracted features) for different configurations or experiments.

??? info "Click to view diagram"
    ![Overview of pipeline](images/Feature_Extraction_Pipeline.drawio.BG.svg)

## **Use Case**

**Extracting meaningful features** from raw accelerometer data for model training.

**Preparing data** for supervised learning.

**Experimenting** with different preprocessing steps (e.g., scaling methods, time windows or cutoff frequencies).

## **Input and Configuration Data**

| **Input/Configuration** | **Description**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| Combined Dataframe      | Pre-combined dataset of accelerometer and self-reports data.                    |
| Raw Accelerometer Data  | CSV file with columns for x, y, z axes, timestamps (timeOfNotification), and participantId. |
| `accel_path`            | Path to the raw accelerometer data file.                                        |
| `reports_path`          | Path to the self-reports data file (optional).                                  |
| `combined_data_path`    | Path to the pre-combined dataset (optional).                                    |
| `features_data_path`    | Path to the pre-extracted features file (optional).                             |
| `cutoff_frequency`      | Cutoff frequency for the low-pass filter (default: 5 Hz).                       |
| `data_frequency`        | Sampling rate of the accelerometer data (default: 25 Hz).                       |
| `order`                 | Filter order (default: 4).                                                      |
| `scaler_type`           | Type of scaling to apply to the accelerometer data:                             |
|                         | - 'standard': StandardScaler (zero mean, unit variance).                        |
|                         | - 'minmax': MinMaxScaler (scales to a [0,1] range).                             |
|                         | - 'none': No scaling applied.                                                   |
| `window_length`         | Length of the sliding window (in seconds, e.g., 60 seconds).                    |
| `window_step_size`      | Step size for the sliding window (in seconds, e.g., 30 seconds).                |
| `selected_domains`      | Domains to extract features from:                                               |
|                         | - Options: 'time_domain', 'spatial', 'frequency', 'statistical', 'wavelet'.     |
|                         | - Default: None (extract all domains).                                          |
| `include_magnitude`     | Whether to include magnitude-based features.                                    |
| `label_columns`         | Emotion label columns to include in the output (e.g., arousal, valence).        |

## **Outputs**
It Outputs a Dataset with these Columns:'time_domain', 'spatial', 'frequency', 'statistical', 'wavelet'

#### **Time Domain Features**
??? note "Click to view Time Domain Features"
    - **Mean (x, y, z, magnitude)**  
    - **Standard Deviation (x, y, z, magnitude)**  
    - **Variance (x, y, z, magnitude)**  
    - **Root Mean Square (RMS) (x, y, z, magnitude)**  
    - **Maximum (x, y, z, magnitude)**  
    - **Minimum (x, y, z, magnitude)**  
    - **Peak-to-Peak Amplitude (x, y, z, magnitude)**  
    - **Skewness (x, y, z, magnitude)**  
    - **Kurtosis (x, y, z, magnitude)**  
    - **Zero-Crossing Rate (x, y, z, magnitude)**  
    - **Signal Magnitude Area (SMA)**  

---

#### **Frequency Domain Features**
??? note "Click to view Frequency Domain Features"
    - **Dominant Frequency (x, y, z, magnitude)**  
    - **Spectral Entropy (x, y, z, magnitude)**  
    - **Power Spectral Density (PSD) Mean (x, y, z, magnitude)**  
    - **Energy (x, y, z, magnitude)**  
    - **Bandwidth (x, y, z, magnitude)**  
    - **Spectral Centroid (x, y, z, magnitude)**  

---

#### **Statistical Features**
??? note "Click to view Statistical Features"
    - **25th Percentile (x, y, z, magnitude)**  
    - **75th Percentile (x, y, z, magnitude)**  

---

#### **Wavelet Domain Features**
??? note "Click to view Wavelet Domain Features"
    - **Wavelet Energy (Approximation) (x, y, z, magnitude)**  

---

#### **Spatial Features**
??? note "Click to view Spatial Features"
    - **Euclidean Norm (Magnitude)**  
    - **Mean Tilt Angle (Pitch, Roll)**  
    - **Correlation between Axes (x-y, x-z, y-z)**  
