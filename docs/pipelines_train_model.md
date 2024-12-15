## **General Explanation**

This pipeline is designed for analyzing and classifying movement data efficiently and modularly. It allows users to preprocess raw accelerometer data, apply dimensionality reduction with PCA, and train machine learning models with hyperparameter optimization. The modular design ensures flexibility, enabling users to set "checkpoints" to reuse preprocessed or feature-engineered data across different experiments.

??? info "Click to view diagram"
    ![Overview of pipeline](images/Train_Model.drawio.BG.svg)

## **Use Cases**
**Training a Machine Learning Model:** Train a classification model using pre-extracted features and save the best-performing model.

**Experimenting with Different Models:** Reuse the same preprocessed feature set to train multiple models with different configurations.

## **Input & Configuration**

| **Input**               | **Description**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| Features Dataset (CSV)  | A CSV file with pre-calculated features, including columns for the features themselves, any relevant metadata, and a target label. |

| **Configuration**       | **Description**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| `use_accel`             | Whether to load raw accelerometer data (used only for preprocessing outside this pipeline). |
| `use_reports`           | Whether to include self-reports data. (Not required for feature-based pipelines). |
| `use_combined`          | Whether to use combined data (raw accelerometer + self-reports).                 |
| `use_features`          | Whether to load a pre-extracted feature dataset. Must be set to True for this pipeline. |
| `apply_pca`             | Whether to apply PCA for dimensionality reduction.                               |
| `pca_variance`          | Variance threshold for PCA, specifying how much of the total variance should be retained. |
| `classifier`            | The type of model to train: xgboost, svm, or randomforest.                       |
| `target_label`          | The column name in the dataset to use as the target variable.                    |
| `selected_domains`      | Domains of features to include in the training (e.g., time, frequency). All domains by default. |
| `n_splits`              | Number of cross-validation splits for Bayesian hyperparameter tuning.            |
| `n_iter`                | Number of iterations for the hyperparameter search.                              |
| `n_jobs`                | Number of parallel jobs for Bayesian optimization.                               |
| `n_points`              | Number of parameter settings sampled in parallel during optimization.            |

## **Outputs**

| **Output**             | **Description**                                                                                   |
|-------------------------|---------------------------------------------------------------------------------------------------|
| **Trained Model**       | A serialized model file (e.g., `xgboost_best_model_target.pkl`) saved with the target name for easy identification. |
| **Classification Report** | A JSON file containing detailed metrics like precision, recall, and F1-score.                   |
