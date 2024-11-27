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
