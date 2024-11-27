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
