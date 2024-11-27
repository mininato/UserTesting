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
