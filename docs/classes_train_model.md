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