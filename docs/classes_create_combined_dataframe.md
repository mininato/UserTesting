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