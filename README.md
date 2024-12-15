# UserTesting

## 📁 **Use Case 1:** 

Imagine you’re a researcher who wants to analyze movement data. You already conducted a experiment where you collected a dataset of ***accelerometer data*** from participants. The participants had to report their emotions ***every 10 minutes*** throughout the experiment. So you have a second report dataset with ***labeled data***. Now you think it would be nice to ***train a model*** on your recorded data. After a long search in the world wide web you found this pipeline.

💭 **Understanding the Combine Pipeline**

First you want to combine both datasets into one, so it will be easier to work with the data later on. Since the accelerometer data was recorded continuously during the experiment, the data is too large. Therefore you want to filter the accelerometer data ***1 minute before and 1 minute after a report*** which is in total 2 minutes per report. You are a fan of Russell’s 2D emotion model so the emotions were labeled into ***valence and arousal***. 

💭 **Understanding the Feature Extraction Pipeline**

After combining the datasets, you now have one dataset. Obviously you want to extract features for the model training. Since you want to get rid of some noise, you read in several papers that a ***cutoff frequency of 10 Hz*** and an ***order of 4*** is suitable for body movements can reduce noise. You cant decide on a scaler, so you just stick to the ***standard*** for now. A common way to generate more data is using the sliding window technique. You want to have a ***window length of 1 minute and a overlap of 50%***.  You know that your smartwatch was recording the data in ***25Hz***. 

💭 **Understanding the Train Model Pipeline**

Now that you have a dataset with features, you are ready to train the model. You like ***xgboost*** as a model and have read that when using xgboost you don’t need to do a ***PCA***. Lastly you want the model to be able to classify the emotions into ***arousal***.

💭 **Understanding the Results**

You want to now how your model is performing, so you check the ***json file***. Take a short note of the ***accuracy*** and how the label of the emotions were ***mapped***.

## 📁 **Use Case 2:**

💭 **Understanding the Analyze Pipeline**

Imagine you’re still a researcher. But this time you have ***10 minutes of unlabeled accelerometer data***. You want to classify the data using your previously ***trained model***. You want to check the participants arousal every ***2 minutes***. For the rest you choose the ***same settings***.

💭 **Understanding the Results**

A friend told you that the participant’s arousal during the experiment was ***high***. Did the model classify right or wrong? What does one row stand for?

## Thank you for using the pipeline! 😄🫶
