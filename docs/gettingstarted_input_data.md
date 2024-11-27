## **Summary of Input Requirements**

| Input Type | Purpose | Key Columns |
| --- | --- | --- |
| **Self-Reports Data** | Train models on labeled data | `participantId`, `timeOfNotification`, `emotion_labels`] |
| **Aggregated Data** | Extract features for model training | `participantId`, `timestamp`, `x`, `y`, `z` |
| **Single-Participant** | Predict emotions using a pre-trained model | `timestamp`, `x`, `y`, `z` |

Note

All timestamps must be in milliseconds or ISO datetime format. Columns should match the required names exactly. Use the transformation code provided if your data needs adjustments.