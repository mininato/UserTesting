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
