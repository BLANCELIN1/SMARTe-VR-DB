# SMARTe-VR-DB

   In recent years, with the advancement of artificial intelligence (AI) technology, adaptive learning, which supports learning according to the characteristics of individual learners, has been attracting attention in the field of education. In particular, a system that optimizes learning content by analyzing learners' eye gaze, facial expressions, and behavioral data in real time has the potential to respond to individual optimization, which has been difficult to achieve with conventional standardized education. However, adaptive learning has the "cold start problem," in which an optimal learning plan cannot be provided with insufficient initial learner data, and the issue that information based on individual learner characteristics is not sufficiently collected and analyzed.
  
   To solve these issues, we propose a new lecture system to realize adaptive learning by constructing a learning comprehension evaluation model using face-tracking data. This will make it possible to realize individually optimized learning support by quantitatively analyzing the learner's state and evaluating comprehension in real time.
 Nowadays, there are various methods for collecting facial feature data. However, considering future development potential and the accuracy of real-time facial data collection, we have chosen VR as our primary method for collecting facial data.
   
   For this study, we used the XR ELITE VR device(see Figure 1(a)). One of its most notable features is its ability to track facial movements and eye gaze in real-time. The device is equipped with an infrared sensor and an illuminator, which enable highly precise measurement of gaze direction and pupil position, as well as detailed capturing of facial expression data. This allows for a deeper understanding of the user's emotions and intentions, which can then be utilized for enhancing interactions in VR applications.
   
   Additionally, the XR ELITE can be transformed into a lightweight, glasses-like form by detaching the rear battery pack (see Figure 1(b)), making it suitable for long-duration use. This feature aligns well with the objective of our experiment, which aims to reduce the burden on students during extended sessions. Reducing physical weight strain is considered crucial for maintaining long-term concentration. On the other hand, considering the stability of data collection and battery life, we adopted PC VR mode instead of standalone mode. By drawing power directly from a PC, we were able to ensure a stable, high-frequency, and long-duration data collection environment.

| ![Figure 1(a) XR ELITE](https://github.com/user-attachments/assets/62984e0d-aa1f-4699-abf1-d584d6d699a6) | ![Figure 1(b) XR ELITE (Without Battery)](https://github.com/user-attachments/assets/a370a77f-096c-48f2-abf1-c4d4e3140dc3) |
|:---:|:---:|
| **Figure 1(a) XR ELITE** | **Figure 1(b) XR ELITE (Without Battery)** |





In facial tracking data collection, the system captures comprehensive facial movements, including eye movements, pupil position, eye openness, and movements of the lips, teeth, tongue, cheeks, and jaw. Specifically, the infrared sensor and illuminator enable highly precise measurement of gaze direction, pupil size, and eye openness. Additionally, 53 types of blendshapes (facial movement combinations used for detailed expression tracking) are utilized to track facial movements at a frequency of 60Hz. This technology allows real-time capturing of facial expressions and movements, which are then reflected onto an avatar, enabling more natural and realistic communication between the user and the system.
 Unlike other VR devices, which use different approaches for face-tracking data collection, the XR ELITE separately captures the upper and lower parts of the face (as shown in Figure 2). These are categorized into Eye Expression (upper face) and Lip Expression (lower face), combining data from both for more accurate tracking.


![image](https://github.com/user-attachments/assets/8055830e-f634-4d17-a033-d036ed34eb8e)

Figure 2     Structure of Face-Tracking Data

 
There are several major advantages to collecting eye expressions and lip expressions separately. The eyes and mouth are the most dynamic parts of the face, each with distinct movement characteristics. For instance, eye movements reflect gaze direction and emotional changes, while mouth movements are closely related to speech, emotional expression, and eating-related actions. By handling these data separately, we can capture each with greater accuracy and enhance the precision of overall facial movement reproduction. Separating eye expressions and lip expressions also allows for independent data analysis. For example, analyzing eye gaze movement and mouth movement during speech separately enables a more detailed understanding of the user’s emotions and intentions. This analysis allows the system to provide appropriate feedback based on the user's responses and intentions.

For this study, we utilized the VIVE OpenXR Face Tracking Library. The Eye Expression and Lip Expression data are represented as enumerations (enum). For instance, the enumeration XR_EYE_EXPRESSION_LEFT_BLINK_HTC indicates how much the user's left eye is closed—a value closer to 1 means the eye is fully closed, while a value closer to 0 means it is fully open (see Figure 3(a) and 3(b)). Similarly, for lip expressions, the enumeration XR_LIP_EXPRESSION_JAW_OPEN_HTC represents how much the user’s mouth is open—a value closer to 1 means the mouth is fully open, whereas a value closer to 0 means it is closed (see Figure 4(a) and 3(b)).


| ![image](https://github.com/user-attachments/assets/7d839ca6-30fb-42b0-984a-7455d95aeb5f) | ![image](https://github.com/user-attachments/assets/5dc84f94-95db-4f38-8b94-fea1b13ac045) |
|:---:|:---:|
| **Figure 3** XR_EYE_EXPRESSION_LEFT_BLINK_HTC （0）| **Figure 3** XR_EYE_EXPRESSION_LEFT_BLINK_HTC （1）|


| ![image](https://github.com/user-attachments/assets/aad596cd-9f13-4f3e-ad51-ff79aed45e40) | ![image](https://github.com/user-attachments/assets/70ebf529-67ce-4974-93a9-5f2ca8452893) |
|:---:|:---:|
| **Figure 4** XR_LIP_EXPRESSION_JAW_OPEN_HTC（0） | **Figure 4** XR_LIP_EXPRESSION_JAW_OPEN_HTC（1） |


The specific facial regions and data collected in our study are summarized in Table 1.
