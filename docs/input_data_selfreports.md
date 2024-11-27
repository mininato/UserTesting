### **1. Self-Reports Data**

### **What It Is:**

This dataset contains participants' self-reports about their emotions (e.g., arousal or valence) and the times when they submitted these reports.

### **Required Format:**

- Columns:
    - `participantId`: A unique identifier for the participant.
    - `timeOfNotification`: The timestamp of the self-report (in milliseconds or ISO format).
    - Emotion labels (e.g., `valence`, `arousal`): The emotional states reported by participants.

### **Example Structure:**

| participantId | timeOfNotification | valence | arousal |
| --- | --- | --- | --- |
| 1 | 1672012800000 | Positive | High |
| 1 | 1672013400000 | Neutral | Medium |

### **How to Transform Your Data:**

If your data uses a different timestamp format or column names, here’s how to adjust it:

```python
import pandas as pd

# Load the self-reports data
df_reports = pd.read_csv("path_to_self_reports.csv")

# Rename columns if necessary
df_reports.rename(columns={
    "timestamp_column": "timeOfNotification",
    "emotion_column_1": "valence",
    "emotion_column_2": "arousal"
}, inplace=True)

# Convert timestamp to datetime format if needed
df_reports["timeOfNotification"] = pd.to_datetime(df_reports["timeOfNotification"], unit="ms")

print(df_reports.head())
```