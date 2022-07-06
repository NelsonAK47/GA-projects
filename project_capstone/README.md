
# Office Working/Home Sitting Posture Recognition


## Executive Summary
Working in front of computer or laptop is a very common task that people do nowadays especially with the rise of information technology (IT). This situation is more prevalent when COVID-19 happened in which almost all activities shifted to home and companies started to digitalize their working approach. As such, there may be a lot of different workstation styles at home. Thus, there is an increase necessity to recognize home sitting posture for long term ergonomic benefits.

This type of problem is a suitable implementation for Computer Vision machine learning to judge real-time sitting posture to ensure good ergonomics.

This project is divided to 2 separate camera points, first POV is based on webcam and second POV is based on side cam (trained based on left, right, diagonal left back view and diagonal right back view). Both POVs produced a high accuracy model of 99% accuracy and 99% F1-score and are able to predict straight, slouch, slouch + roundshoulder, uneven shoulder and lieback postures) with the help of Computer Vision and Pose Estimation tools. 

While there is still work to be done to realise its full potential, this shows that there is room for use of Computer Vision and Machine Learning in our daily lives. With the right camera angles, better pose estimation technology and support from local support from Workplace Safety and Health Council (WSH), the future can definitely see less people complaining about their pain as well as more people mitigating long term health effects due to their desk job.  

## Background
The term "ergonomics" has been playing a huge part in people daily lives due to the rapid growth of information technology. Many people especially office workers sit in front of their computers or laptops for their work. According to a study led by [Lin Yang](https://jamanetwork.com/journals/jama/fullarticle/2731178), an epidemiologist in Cancer Epidemiology and Prevention Research, on top of the usual 9am to 5pm sitting hours and school hours, **30% to 43%** of the US population used a computer for **2 hours per day or more** and **13% to 25%** used a computer for **3 or more hours** each day. This amounted to **a minimum of 10 hours per day**.

This situation is more prevalent when COVID-19 arises, shifting offices to homes in which chairs, tables and work kits are less standardized. Some people sit on normal kitchen chairs or even work at dining tables. The "new normal" has changed our business casual to home casual, our in-person meetings into web conferences and our in-person school rooms into online assignments and virtual lessons. As such, people engage in more screen time than ever before and they spend longer durations at workstations that are poorly-designed for long-term use. A survey led by [Davis](https://journals.sagepub.com/doi/full/10.1177/1064804620937907) studied 8,500 participants at the University of Cincinnati and was later evaluated by an experienced ergonomist. Many **chairs** were at wrong height **(41% too low and 2% too high)**, which resulted in elevated arms, slouching and resulted in poor head position. In addition, many **monitors** were setup at bad height **(52% too low and 4% too high)** resulted in slouching and roundshoulders as well.

A study by Workplace Safety and Health [(WSH)](https://www.straitstimes.com/singapore/ergonomics-problems-cost-singapore-35-billion-a-year) Council cited stiff necks from bad posture at work costs Singapore **$3.5 billions a year**. Common effects of poor sitting posture include spine curvature, back pain, neck pain & headaches, poor sleep, disrupted digestion, lack of motivation and a decrease in productivity. On average, workers took an average of three days of medical leave due to pain while those who worked through their pain had a reduced productivity of 15% percent [(source)](https://www.straitstimes.com/singapore/health/head-body-pain-costs-economy-84b-yearly).

## Problem Statement
Driven by the myriad cost above, the aim of this project is to build a sitting body posture detection through webcam and sidecam. This can be applied to everyone who spend their time in front of computers or laptops. It is also applicable for home and office environment. 

## Proposed Approach
Human naturally learns to recognize postures based on face and body or pose landmarks. As they learn through videos, pictures or experiences, they will understand postures based on those learned features over their life experiences. However, it is not sustainable for human to monitor a large scale of postures consistently and over a long period.

Thus, this opens up an opportunity to create a machine learning model to monitor body posture while humans do their work. The model will 'learn' the pattern of those body postures through coordinates and some added features based on a collection of labelled body postures. Once the model has been trained, it will be deployed to webcam or sidecam for testing.

Since, there is limited online sitting photos or videos dataset, below are the proposed flows of work:
    
    1. Select existing model(s) to detect key joints detections and coordinates 
    
    2. Collect own dataset by own recording
    
    3. Explore the dataset and add additional features
    
    4. Build machine learning models and tune
    
    5. Compare and evaluate models to obtain the best model
    
    6. Implement the best model againts live video cam for pose prediction

## Summary of Model Training

**Summary of models are as follows (for webcam):**

|Models|Validation Accuracy|Mean F1 Score of 5 Postures|
|---|:--:|:--:|
|Logistic Regression|99.8%|99.8%|
|Ridge Classification|97.2%|97.2%|
|Random Forest Classifier|99.6%|99.6%|
|Gradient Boosting Classifier|99.6%|99.8%|
|Adaptive Boosting (ADA) Classifier|53.2%|45.1%|
|Decision Tree Classifier|98.6%|98.6%|

**PyCaret generated models (for webcam):**

![](https://github.com/NelsonAK47/GA-projects/blob/main/project_capstone/Pictures/webcam_pycaret.PNG)

Models used were Random Forest Classifier for manual learning and Extra Trees Classifier for PyCaret generated model. Dataset was train/test split by 0.7/0.3 and achieved an accuracy of ~99.6% and ~100% respectively.

This shows that model is capable of classifying postures (straight, slouched, slouched + roundshoulder, uneven shoulder, lieback) correctly.

**Webcam Confusion Matrix**

![](https://github.com/NelsonAK47/GA-projects/blob/main/project_capstone/Pictures/webcam_cm_rf.PNG)

**Summary of models are as follows (for sidecam):**

|Models|Validation Accuracy|Mean F1 Score of 4 Postures|
|---|:--:|:--:|
|Logistic Regression|98.8%|98.8%|
|Ridge Classification|95.2%|94.5%|
|Random Forest Classifier|99.6%|99.1%|
|Gradient Boosting Classifier|99.5%|99%|
|Adaptive Boosting (ADA) Classifier|59.4%|57.7%|
|Decision Tree Classifier|97.4%|97%|

**PyCaret generated models (for sidecam):**

![](https://github.com/NelsonAK47/GA-projects/blob/main/project_capstone/Pictures/sidecam_pycaret.PNG)

Similar to webcam, Random Forest Classifier and Extra Trees Classifier have good model performance of ~99.6% and ~99.9% accuracy with similar 0.7/0.3 train test split. Therefore, models are capable for posture prediction.

**Sidecam Confusion Matrix**

![](https://github.com/NelsonAK47/GA-projects/blob/main/project_capstone/Pictures/sidecam_cm_rf.PNG)

The best models were then tested to identify in real live camera. The models are able to detect sitting postures based on the same camera angles and remind users to sit straight when bad postures are more than 15 secs.

## Limitations & Future Work

Although current model has performed well under real live camera, it has some limitations:
    
    1.  Model is currently limited to identifying straight, slouched/hunched, slouched/hunched + roundshoulders, uneven shoulder(webcam) and lieback. However, there are many combined postures such as cross legs, butterfly sit posture, knee angle detection, etc. In addition, there are many more complex postures and alignments such as monitor alignment, table/chair height optimisation, etc
    2.  Current models are trained based on limited own dataset with certain angles and camera placements. In the future, more cameras can be used to train to create more robust models to cater for all environments.
    3.  Model is only capable of reminding bad postures after 15 secs through audio. However, in real life scenario, it is better to give live angle recommendations for the users to adjust to straight posture.


 All in all, future improvements can include :
 - More complex postures specifically legs joints as these body parts also affect sitting ergonomics.
 - Utilise more cameras to cover all camera angles/placements for model training. Thus, it will be able to create a much robust model at different placements when deployed to offices/homes.
 - Train more models to cater for 2 or more people in a frame.
 - Explore deep learning models (CNN or RNN) for dataset training.
 - It is also possible to use object detection models such as Mask R-CNN or YOLO to detect monitors, chairs and tables to ultimately give recommendations for best alignments/placements and heights for each workstation.
 - Use Tkinter to develop GUI app for posture record and recommendations to correct postures.
