### **Paths for Import Data**

1. **`accel_path`:**
    - Path to the accelerometer data file.
    - Contains raw movement data (x, y, z axes) recorded by a device (e.g., smartwatch).
    - Example: `single_participant_positive_high.csv` contains accelerometer data for a specific participant.
2. **`reports_path`:**
    - Path to the self-reports data file.
    - Includes participant-reported labels, such as emotional states (e.g., valence, arousal).
3. **`combined_data_path`:**
    - Path to the combined data file.
    - This file matches accelerometer data with self-reports, linking movements with emotions over a specific time window.
4. **`features_data_path`:**
    - Path to the features data file.
    - Contains pre-calculated features extracted from accelerometer data for analysis, so feature extraction can be skipped.
5. **`model_path`:**
    - Path to a pre-trained machine learning model.
    - Used for predicting emotional states based on accelerometer data (e.g., an XGBoost model trained to predict arousal).

---

### **Label Configuration**

1. **`label_columns`:**
    - List of labels (columns) in the dataset that represent emotional states.
    - Example: `["valence", "arousal"]` specifies these two emotions as labels.
2. **`target_label`:**
    - The label the model will predict.
    - Only one label can be selected at a time (e.g., `"arousal"` for predicting arousal levels).

---

### **Configuration for Combined Data**

1. **`time_window`:**
    - Defines the time range (in minutes) before and after a self-report to extract accelerometer data.
    - Example: `2` means extract 2 minutes of data before and after each self-report.

---

### **Configuration for Feature Extraction**

1. **`window_length`:**
    - Length of the time window (in seconds) used to segment accelerometer data for feature extraction.
    - Example: `60` means divide the data into 1-minute windows.
2. **`window_step_size`:**
    - Step size (in seconds) for moving the window forward.
    - Smaller values overlap windows more, providing more data segments.
3. **`data_frequency`:**
    - Sampling rate of the accelerometer data, in Hz.
    - Example: `25` means the device records 25 data points per second.
4. **`selected_domains`:**
    - Specifies which feature domains to extract.
    - Options: `"time_domain"`, `"spatial"`, `"frequency"`, `"statistical"`, `"wavelet"`.
    - Example: `["time_domain", "frequency"]` means only extract features from these two domains. `None` extracts all domains.
5. **`include_magnitude`:**
    - Whether to include magnitude-based features (combining x, y, z axes into one measurement).
    - Example: `True` includes magnitude features.

---

### **Configuration for Low-Pass Filter**

1. **`cutoff_frequency`:**
    - Frequency limit for the low-pass filter (in Hz).
    - Removes high-frequency noise while keeping important movement data below this frequency.
2. **`order`:**
    - Order of the low-pass filter, determining how sharply it removes unwanted frequencies.
    - Example: `4` creates a smooth filter with a moderate cutoff.

---

### **Configuration for Scaling**

1. **`scaler_type`:**
    - Type of scaler used to standardize or normalize data.
    - Options:
        - `"standard"`: Centers the data to have a mean of 0 and a standard deviation of 1.
        - `"minmax"`: Scales the data to a range of 0 to 1.
        - `"none"`: No scaling applied.

---

### **Configuration for PCA**

1. **`apply_pca`:**
    - Whether to apply Principal Component Analysis (PCA) to reduce the number of features.
    - Example: `False` skips PCA.
2. **`pca_variance`:**
    - The amount of variance to retain when applying PCA.
    - Example: `0.95` keeps 95% of the information in the data.

---

### **Configuration for Model Training**

1. **`classifier`:**
    - The machine learning model to use for training.
    - Options: `"xgboost"`, `"svm"`, `"randomforest"`.
    - Example: `"xgboost"` uses XGBoost for training.

---

### **Configuration for Hyperparameter Tuning**

1. **`n_splits`:**
    - Number of folds for cross-validation.
    - Example: `5` means split the data into 5 groups for evaluation.
2. **`n_iter`:**
    - Number of iterations for hyperparameter tuning.
    - Example: `30` tests 30 combinations of settings.
3. **`n_jobs`:**
    - Number of CPU cores to use for parallel processing.
    - Example: `1` uses all available cores.
4. **`n_points`:**
    - Number of hyperparameter combinations to test in parallel.
    - Example: `1` tests one combination at a time.
5. **`param_space`:**
    - Custom hyperparameter space for the selected model.
    - Example:
        - `"learning_rate": (0.05, 0.2)` specifies the range of learning rates to test for the XGBoost model.
        - Set to `None` to use default hyperparameters defined in the `TrainModel` class.

---