## Classify Movement Data Class

This class is designed to **analyze movement data** using a pre-trained model. It takes movement data as input, predicts emotional states (like mood or stress level) based on the data, and then saves the results to a file. It works automatically, so you don't need to know how the model itself works.

Step-by-Step Explanation:

1. **Loading the Pre-Trained Model:**
    - The class uses a pre-trained machine learning model (a program that has already learned how to make predictions based on past data).
    - When you run this class for the first time, it finds and loads this model from a file.
2. **Processing Movement Data:**
    - The input data (like movement from a smartwatch) must already be prepared and organized into a table of numbers (called "features").
    - This class uses the loaded model to analyze the movement data and predict emotions or states based on it.
3. **Adding Predictions:**
    - Once predictions are made, the class adds a new column to your table. This column contains the predicted emotions for each row of data.
4. **Saving the Results:**
    - The updated table (with the predictions added) is saved as a file. This file is easy to open in programs like Excel or similar tools.
    - The file's name includes the "window length" (a setting for how the data is divided into chunks), making it easy to identify later.
5. **Messages:**
    - The class shows messages like "Model loaded" and "Data classified successfully" to confirm that everything is working as expected.

## Create Combined Dataframe Class

This class combines two datasets: **self-reported emotion data** (like arousal and valence ratings) and **movement data** (from a smartwatch's accelerometer). It matches these two types of data based on the time they were recorded and saves the combined result in a new file. This is helpful for analyzing how emotions relate to movement patterns.

---

### Step-by-Step Explanation:

1. **Input Data:**
    - The class works with two datasets:
        - **Self-Reports:** A table where participants record their emotions (like arousal or valence) at specific times.
        - **Movement Data:** A table of movement information (accelerometer data), recorded at different times.
    - These datasets must be provided as inputs when using this class.
2. **Label Selection:**
    - You can choose which emotions (labels) to include, like arousal and valence. If you don’t specify, it defaults to using these two labels.
3. **Filtering the Data:**
    - It removes any rows in the self-report data where the labels are missing or invalid.
    - Ensures that the labels you want to analyze exist in the dataset.
4. **Matching Movement and Emotion Data:**
    - For each self-reported emotion entry, the class looks for movement data recorded in a specific time range around that entry (called a "time window"). This links movement patterns with the emotions reported at a similar time.
5. **Combining the Data:**
    - It creates a new table (or DataFrame) where each row includes:
        - **Participant Information:** Like their ID.
        - **Emotion Labels:** For example, arousal and valence ratings.
        - **Movement Data:** Accelerometer values (x, y, z) recorded at specific times.
    - Each row connects a participant's emotion and movement data based on the matching time window.
6. **Group Identifier:**
    - A unique "group ID" is added to each combined entry to indicate which participant and self-report it belongs to.
7. **Saving the Results:**
    - The combined data is saved as a file. The file name includes details like the size of the time window and which labels were used. This makes it easy to identify later.
8. **Friendly Messages:**
    - The class shows messages at different stages (e.g., “Processing label: arousal” or “Combined dataframe exported successfully”), so you know what’s happening.

## Extract Features Class

This class analyzes **movement data** (like accelerometer readings from a smartwatch) by dividing it into time chunks ("windows") and calculating **features** (mathematical summaries) for each chunk. These features help in understanding patterns in movement, such as average speed, variability, or frequency of movement. The results are saved in a file for further analysis or use in machine learning.

---

### Step-by-Step Explanation:

1. **Input Data:**
    - The input is a table containing accelerometer data, which measures movement along three axes: x, y, and z.
    - The data is recorded continuously, so this class divides it into manageable time chunks, called "windows."
2. **Window Creation:**
    - Each window represents a specific time span of movement (e.g., 1 minute).
    - A "step size" determines how much the window moves forward for the next chunk (e.g., every 30 seconds).
    - This ensures all the data is analyzed efficiently.
3. **Feature Extraction:**
    - The class calculates a variety of features for each window. These features summarize the movement data and make it easier to analyze or use in machine learning.
    - Features are grouped into **domains**, including:
        - **Time Domain Features:** Basic statistics like average movement, variability, and extremes.
        - **Spatial Features:** Measures like angles (tilt) and correlations between axes.
        - **Frequency Domain Features:** Patterns in how often movement occurs (e.g., fast vibrations vs. slow sways).
        - **Statistical Features:** Percentiles to capture movement range.
        - **Wavelet Features:** A way to break movement into simple patterns for analysis.
    - Users can choose which domains to include or calculate all features if no preference is set.
4. **Magnitude Calculation:**
    - The class can also calculate features for the "magnitude," which combines x, y, and z movements into one overall measure of intensity.
5. **Combining Features with Labels:**
    - If emotion labels (like arousal and valence) are available, they are added to the features for each window. This makes it possible to link movement patterns with emotions.
6. **Saving the Results:**
    - The calculated features for all windows are saved in a file. The file name includes details like the window size, step size, and selected domains for easy identification.
7. **Friendly Messages:**
    - Messages like "All features extracted successfully" are displayed to let the user know the process is complete.

## Import Data Class

This class is responsible for **importing data** that will be analyzed. Depending on what you want to analyze, it can load different types of data:

- **Raw accelerometer data:** Movement data from a smartwatch.
- **Self-report data:** Information provided by participants, like emotions or experiences.
- **Combined data:** A dataset where accelerometer and self-report data are already matched.
- **Pre-extracted features:** If features (summaries of movement data) have already been calculated, it can load those instead.

This flexibility allows you to start your analysis from different stages, depending on your needs.

---

### Step-by-Step Explanation:

1. **Customizable Data Loading:**
    - You decide which type of data you want to work with by setting the appropriate options (e.g., `use_accel`, `use_reports`, `use_combined`, `use_features`).
    - The class automatically chooses the correct file paths for the selected data, based on settings in the configuration file.
2. **Importing Features:**
    - If you’ve already extracted features (summaries of movement data), the class loads that data from a file.
    - This is useful if you want to skip the feature extraction step and jump straight into analysis.
3. **Importing Combined Data:**
    - If you’ve already matched accelerometer and self-report data, the class loads this pre-combined dataset.
    - This saves time by skipping the data-matching step.
4. **Importing Raw Data:**
    - If no combined data or features are available, the class loads:
        - **Raw accelerometer data**: Measurements of movement (x, y, z axes).
        - **Self-report data** (if available): Participant-provided information, such as emotions or labels.
5. **Error Handling:**
    - If you try to load raw accelerometer data without specifying its file path, the class raises an error to let you know that a path is required.
6. **Output:**
    - Depending on what you’re working with, the class outputs:
        - A single dataset (features, combined data, or accelerometer data alone).
        - Two datasets (accelerometer data and self-report data), if both are available.
7. **Friendly Messages:**
    - The class prints messages to let you know which data has been successfully loaded, such as:
        - “Features dataframe imported successfully.”
        - “Raw accelerometer data imported successfully.”

## Low Pass Filter Class

This class is designed to **smooth out accelerometer data** by removing high-frequency noise (quick and insignificant changes in movement). It uses a mathematical technique called a **low-pass filter** to focus on slower, meaningful movement patterns. This is useful when analyzing movement data because it makes trends and significant motions clearer.

---

### Step-by-Step Explanation:

1. **Input Data:**
    - The input is a table (DataFrame) with three columns: **x, y, z**. These represent movement measurements along three axes.
2. **Low-Pass Filter:**
    - The filter removes fast, noisy signals from the data. For example:
        - If you’re walking, the filter keeps the steady up-and-down motion of your steps but removes tiny vibrations caused by your device or environment.
3. **How It Works:**
    - A mathematical function (called a **Butterworth filter**) is applied to the data.
    - It keeps movement data below a certain speed (frequency), determined by the **cutoff frequency**. Movements faster than this speed are considered noise and are removed.
4. **Filter Settings:**
    - **Cutoff Frequency:** The speed at which the filter decides whether to keep or remove a signal (e.g., 5 Hz means it keeps motions slower than 5 cycles per second).
    - **Sampling Rate:** The rate at which the device records movement data (e.g., 25 Hz means 25 data points per second).
    - **Filter Order:** Determines the sharpness of the filtering. A higher order makes the cutoff more precise.
5. **Smoothing the Data:**
    - The class applies the low-pass filter to the **x, y, and z** columns of the data, smoothing them to remove noise.
6. **Output:**
    - The filtered data is returned as a table (DataFrame) with the same structure as the input.
    - The smoothed columns (**x, y, z**) are ready for further analysis.
7. **Error Handling:**
    - If the input data doesn’t include the required columns (**x, y, z**), the class raises an error to ensure proper usage.
8. **Friendly Messages:**
    - After the filter is applied, the class prints a message: “Low-pass filter applied successfully,” so the user knows the process is complete.

## PCAHandler Class

This class handles **Principal Component Analysis (PCA)**, a mathematical method used to simplify large datasets. PCA reduces the number of variables (columns) in the data while keeping as much important information as possible. It’s especially helpful when working with complex data, like features extracted from accelerometer readings.

---

### Step-by-Step Explanation:

1. **What is PCA?**
    - PCA transforms the data into a smaller set of "principal components." These are new variables that summarize the original data.
    - For example, if you have 100 columns, PCA can reduce it to just a few components that still capture most of the data's variation.
2. **Input Data:**
    - The input is a table (DataFrame) with many columns (features).
3. **When PCA is Applied:**
    - The class applies PCA only if `apply_pca` is set to `True`. If not, the data remains unchanged.
    - **Variance:** You can specify how much of the original data’s information (variance) you want to keep. For example:
        - `variance=0.95` means PCA will retain 95% of the data's important information.
4. **How It Works:**
    - During **fitting** (`fit` method):
        - The class calculates the PCA transformation based on the input data.
        - This identifies which components (combinations of columns) best summarize the data.
    - During **transformation** (`transform` method):
        - The data is transformed into its principal components, reducing the number of columns.
5. **Output:**
    - If PCA is applied, the output is a simplified table (DataFrame) with fewer columns (principal components).
    - If PCA is not applied, the data remains the same.
6. **Key Features:**
    - **Automatic Adjustment:** PCA automatically determines how many components to use based on the `variance` value.
    - **Flexibility:** You can turn PCA on or off using `apply_pca`.
7. **Error Handling:**
    - If PCA is enabled but hasn't been "fitted" to the data, the class ensures that an error doesn’t occur by skipping PCA.

## Scale XYZ Data Class

This class **scales accelerometer data** to make the measurements more consistent and easier to analyze. Scaling adjusts the values of the data without changing its overall patterns, which is especially important when working with machine learning models.

---

### Step-by-Step Explanation:

1. **Input Data:**
    - The input is a table (DataFrame) with three columns: **x, y, z**. These represent movement measurements along three axes.
2. **Why Scaling Is Important:**
    - Accelerometer values can have different ranges (e.g., x might range from -10 to 10, while z might range from -1 to 1).
    - Scaling ensures that all axes are on the same scale, which helps:
        - Prevent certain axes from dominating the analysis.
        - Improve the performance of machine learning algorithms.
3. **Scaling Methods:**
    - The class offers three scaling options:
        1. **Standard Scaling (`standard`):**
            - Adjusts the data so it has a **mean of 0** and a **standard deviation of 1**. This centers the data and normalizes its spread.
        2. **Min-Max Scaling (`minmax`):**
            - Adjusts the data to fit within a **range of 0 to 1**. This is useful when you want all values to be non-negative and comparable.
        3. **No Scaling (`none`):**
            - Leaves the data unchanged. This is useful if scaling is not necessary for your analysis.
4. **How It Works:**
    - During **transformation** (`transform` method):
        - The class identifies the **x, y, z** columns in the input data.
        - Depending on the scaling method:
            - It applies the chosen scaling method to these columns.
            - If `none` is selected, it skips scaling and returns the data as it is.
5. **Output:**
    - The output is the same table (DataFrame) but with the **x, y, z** columns scaled according to the selected method.
6. **Error Handling:**
    - If an invalid scaling method is provided, the class raises an error, ensuring only valid options (`standard`, `minmax`, or `none`) are accepted.
7. **Friendly Messages:**
    - After scaling is applied, the class prints: “Data scaled successfully,” confirming the operation is complete.

## Train Model Class

This class is responsible for **training a machine learning model** to classify emotions or behaviors based on movement data. It automates the entire training process, including preparing the data, finding the best model settings, evaluating performance, and saving the results.

---

### Step-by-Step Explanation:

1. **Input Data:**
    - The input is a dataset with:
        - **Features:** Data that describes movements (e.g., accelerometer readings).
        - **Target Label:** The emotion or state you want the model to predict (e.g., arousal or valence).
2. **Target Label Encoding:**
    - The target label (e.g., "high," "medium," "low") is converted into numbers (e.g., 0, 1, 2) so the model can understand it.
    - A **mapping** is created to show how the original labels correspond to these numbers.
3. **Model Selection:**
    - You can choose from three machine learning models:
        - **XGBoost:** Great for handling complex datasets.
        - **Support Vector Machine (SVM):** Works well for smaller datasets.
        - **Random Forest:** Easy to use and interpretable.
    - This choice is specified in the configuration file.
4. **Hyperparameter Tuning:**
    - Models have settings (called hyperparameters) that affect how they learn.
    - The class automatically tries different combinations of these settings to find the best one using **Bayesian optimization**. This saves time compared to manual tuning.
5. **Cross-Validation:**
    - The class uses **Stratified Group K-Fold Cross-Validation** to test the model’s performance during training.
    - This ensures the model is evaluated fairly and works well across different groups of data (e.g., participants).
6. **Model Training:**
    - The best settings from hyperparameter tuning are used to train the model.
    - The class outputs the model’s **accuracy** and a detailed **classification report** (e.g., how well it predicts each label).
7. **Saving Results:**
    - The class saves:
        - The trained model (for future use).
        - Metadata, such as:
            - The best settings.
            - The model's accuracy.
            - Label mappings and feature importances (if available).
        - A detailed classification report as a JSON file.
8. **Output Files:**
    - The saved files include:
        - **Model File:** Contains the trained model.
        - **Metadata File:** Includes information about the model’s performance and settings.
        - **Classification Report:** Shows how well the model predicts each label.