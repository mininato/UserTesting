# Getting Started with the Emotion Recognition Pipeline

Welcome to the **Emotion Recognition Pipeline**! This guide will help you install, configure, and use the pipeline to analyze movement data and recognize emotions efficiently.

---

## **1. Installation**

### Prerequisites

- **Python**: Version 3.10 or higher.
- **Environment**: It is recommended to create a virtual environment for managing dependencies.

```bash
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate
```

### Steps

1. Clone the repository:
   ```bash
   git clone https://huggingface.co/spaces/mininato/EmotionClassificationPipeline
   cd EmotionClassificationPipeline
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
---
## **2. Understanding Movement Data**

Movement data refers to the information captured about how a body moves through space. It is typically recorded using sensors like **accelerometers** and **gyroscopes**, which measure changes in velocity and angular rotation. For example, smartwatches and fitness trackers collect movement data in three axes with a sampling rate:

- X-axis: Forward and backward movement

- Y-axis: Side-to-side movement

- Z-axis: Up and down movement

- Sampling Rate: Devices record data at a specific frequency, like 25Hz (25 data points per second), to ensure smooth and continuous tracking.

The recorded data is stored in raw formats, often as time-series data with timestamps and helps us **understand physical activity patterns, postures, and even subtle gestures.**

![AccelData](images/AccelData.png)

---
## **3. Understanding Emotions**

Emotions are **psychological and physiological responses** that can be categorized using different models. A widespread model is the **2D Valence-Arousal Model by Russell** with these axes:

- Arousal: Refers to the intensity of the emotion, ranging from calm (low arousal) to excited (high arousal).
- Valence: Refers to the positivity or negativity of the emotion, ranging from unpleasant (negative valence) to pleasant (positive valence).

![Emotion Model](images/Valence_Arousal.drawio.svg)

There are also other emotion models:

- Ekman's six fundamental types of emotions

- The Positive and Negative Affect Schedule (PANAS) Model

The Emotions can be reported in a csv like this:
![Selfreports](images/Selfreports.png)

---
## **4. Movement Data Processing**
Movement Data can be processed in these 4 steps: 

**Data Acquisition**, **Data Preprocessing**, **Feature Extraction**, and **Model Training & Evaluation**.

![Data Processing Workflow](images/Data_Process_BG.drawio.svg)

---
## **5. The User-Friendly Pipeline to Recognize Emotions with Movement Data**

A pipeline was developed to make this process more **efficient, reusable, consistent and automated.**

---

### **5.1 What is a Pipeline in general?**
In data processing and machine learning, a pipeline is a **structured sequence of steps** to transform **raw input data** into **meaningful outputs**, for example classifications. Each step in a pipeline performs a specific function, and the output of one step serves as the input for the next.

![Simple Pipeline](images/Pipeline_Simple.drawio.svg)

---

### **5.2 Structure of the Emotion Recognition Pipeline**

This Pipeline consists out of **multiple smaller pipelines** which can be used seperately for **different purposes** and work as **checkpoints** in your experimental workflow.

![Complete Pipeline](images/Complete_PipelineDiagram_End.drawio.svg)

---
## **6.General Workflow using the Gradio User Interface**

### **6.1 How to use Gradio Interface**

![Gradio Showcase](images/gradiotut.gif){ style="max-width: 100%; height: auto; display: block; margin: 0 auto;" }

---

> **Note:** If you want to read more on each setting then click [here](other.md).

### **6.2. How to combine Dataframes**

1. Import Accelerometer Data & SelfReports Data
2. Set the time window that you want to filter (in minutes before and after a report)
3. Set the emotion labels that exist in your data (e.g. valence, arousal)
4. Execute Pipeline
5. Download combined dataset

---

### **6.3. How to extract Features**
1. Import the combined dataset
2. Add cutoff frequency and order for low pass filter
3. Set desired scaler
4. Set window length and overlapping step size (in seconds) for sliding window technique
5. Set frequency in which data was recorded
6. Set magnitude
7. Set the emotion labels that exist in your data (e.g. valence, arousal)
8. Execute Pipeline
9. Download features dataset

---

### **6.4 How to train a Model**
1. Import the features dataset
2. Select if PCA is being applied and the PCA variance
3. Select classifier
4. Set the emotion labels that exist in your data (e.g. valence, arousal)
5. Select which label should be the target for the model to classify
6. Execute Pipeline
7. Download model.pkl file and report.json file

---

### **6.5 How to classify Movement Data**
1. Import accelerometer data and model
2. Add cutoff frequency and order for lowpassfilter
3. Set desired scaling type
4. Set period for classifying movement data
5. Set frequency in which data was recorded
6. Set magnitude (measure of the overall strength or intensity of a signal, calculated by combining the contributions of all three accelerometer axes (x, y, z))
7. Set the emotion labels that exist in your data (e.g. valence, arousal)

---
