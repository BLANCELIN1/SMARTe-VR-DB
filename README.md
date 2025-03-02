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

Table 1
| Name | Description |
|------|------------|
| **XR_EYE_EXPRESSION_LEFT_BLINK_HTC** | This blend shape influences blinking of the left eye. When this value goes higher, the left eye approaches closed. |
| **XR_EYE_EXPRESSION_LEFT_DOWN_HTC** | This blend shape influences the muscles around the left eye, moving these muscles further downward with a higher value. |
| **XR_EYE_EXPRESSION_LEFT_IN_HTC** | This blend shape influences the muscles around the left eye, moving these muscles further rightward with a higher value. |
| **XR_EYE_EXPRESSION_LEFT_OUT_HTC** | This blend shape influences the muscles around the left eye, moving these muscles further leftward with a higher value. |
| **XR_EYE_EXPRESSION_LEFT_SQUEEZE_HTC** | The blend shape closes the eye tightly, and at that time, XR_EYE_EXPRESSION_LEFT_BLINK_HTC value is 1. |
| **XR_EYE_EXPRESSION_LEFT_UP_HTC** | This blend shape influences the muscles around the left eye, moving these muscles further upward with a higher value. |
| **XR_EYE_EXPRESSION_LEFT_WIDE_HTC** | This blend shape keeps the left eye wide, and at that time, XR_EYE_EXPRESSION_LEFT_BLINK_HTC value is 0. |
| **XR_EYE_EXPRESSION_RIGHT_BLINK_HTC** | This blend shape influences blinking of the right eye. When this value goes higher, the right eye approaches closed. |
| **XR_EYE_EXPRESSION_RIGHT_DOWN_HTC** | This blend shape influences the muscles around the right eye, moving these muscles further downward with a higher value. |
| **XR_EYE_EXPRESSION_RIGHT_IN_HTC** | This blend shape influences the muscles around the right eye, moving these muscles further leftward with a higher value. |
| **XR_EYE_EXPRESSION_RIGHT_OUT_HTC** | This blend shape influences the muscles around the right eye, moving these muscles further rightward with a higher value. |
| **XR_EYE_EXPRESSION_RIGHT_SQUEEZE_HTC** | The blend shape closes the eye tightly, and at that time, XR_EYE_EXPRESSION_RIGHT_BLINK_HTC value is 1. |
| **XR_EYE_EXPRESSION_RIGHT_UP_HTC** | This blend shape influences the muscles around the right eye, moving these muscles further upward with a higher value. |
| **XR_EYE_EXPRESSION_RIGHT_WIDE_HTC** | This blend shape keeps the right eye wide, and at that time, XR_EYE_EXPRESSION_RIGHT_BLINK_HTC value is 0. |
| **XR_LIP_EXPRESSION_CHEEK_PUFF_LEFT_HTC** | This blend shape puffs up the left side of the cheek further with a higher value. |
| **XR_LIP_EXPRESSION_CHEEK_PUFF_RIGHT_HTC** | This blend shape puffs up the right side of the cheek further with a higher value. |
| **XR_LIP_EXPRESSION_CHEEK_SUCK_HTC** | This blend shape sucks in the cheeks on both sides further with a higher value. |
| **XR_LIP_EXPRESSION_JAW_FORWARD_HTC** | This blend shape moves the jaw forward with a higher value. |
| **XR_LIP_EXPRESSION_JAW_LEFT_HTC** | This blend shape moves the jaw further leftward with a higher value. |
| **XR_LIP_EXPRESSION_JAW_OPEN_HTC** | This blend shape opens the mouth further with a higher value. |
| **XR_LIP_EXPRESSION_JAW_RIGHT_HTC** | This blend shape moves the jaw further rightward with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_APE_SHAPE_HTC** | This blend shape stretches the jaw further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_DOWNLEFT_HTC** | This blend shape lowers the left lower lip further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_DOWNRIGHT_HTC** | This blend shape lowers the right lower lip further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_INSIDE_HTC** | This blend shape rolls in the lower lip further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_LEFT_HTC** | This blend shape moves your lower lip leftward. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_OVERLAY_HTC** | This blend shape stretches the lower lip further and lays it on the upper lip further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_OVERTURN_HTC** | This blend shape pouts your lower lip. Can be used with XR_LIP_EXPRESSION_MOUTH_UPPER_UPRIGHT_HTC and XR_LIP_EXPRESSION_MOUTH_LOWER_DOWNRIGHT_HTC to complete the upper O mouth shape. |
| **XR_LIP_EXPRESSION_MOUTH_LOWER_RIGHT_HTC** | This blend shape moves your lower lip rightward. |
| **XR_LIP_EXPRESSION_MOUTH_POUT_HTC** | This blend shape allows the lips to pout more with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_RAISER_LEFT_HTC** | This blend shape raises the left side of the mouth further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_RAISER_RIGHT_HTC** | This blend shape raises the right side of the mouth further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_STRETCHER_LEFT_HTC** | This blend shape lowers the left side of the mouth further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_STRETCHER_RIGHT_HTC** | This blend shape lowers the right side of the mouth further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_UPPER_INSIDE_HTC** | This blend shape rolls in the upper lip further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_UPPER_LEFT_HTC** | This blend shape moves your upper lip leftward. |
| **XR_LIP_EXPRESSION_MOUTH_UPPER_OVERTURN_HTC** | This blend shape pouts your upper lip. Can be used with XR_LIP_EXPRESSION_MOUTH_UPPER_UPRIGHT_HTC and XR_LIP_EXPRESSION_MOUTH_UPPER_UPLEFT_HTC to complete the upper O mouth shape. |
| **XR_LIP_EXPRESSION_MOUTH_UPPER_RIGHT_HTC** | This blend shape moves your upper lip rightward. |
| **XR_LIP_EXPRESSION_MOUTH_UPPER_UPLEFT_HTC** | This blend shape raises the left upper lip further with a higher value. |
| **XR_LIP_EXPRESSION_MOUTH_UPPER_UPRIGHT_HTC** | This blend shape raises the right upper lip further with a higher value. |
| **XR_LIP_EXPRESSION_TONGUE_DOWNLEFT_MORPH_HTC** | This blend shape doesn’t make sense. When both the left and down blend shapes appear at the same time, the tongue will be deformed. |
| **XR_LIP_EXPRESSION_TONGUE_DOWNRIGHT_MORPH_HTC** | This blend shape doesn’t make sense. When both the right and down blend shapes appear at the same time, the tongue will be deformed. |
| **XR_LIP_EXPRESSION_TONGUE_DOWN_HTC** | This blend shape sticks the tongue out and down extremely. |
| **XR_LIP_EXPRESSION_TONGUE_LEFT_HTC** | This blend shape sticks the tongue out and left extremely. |
| **XR_LIP_EXPRESSION_TONGUE_LONGSTEP1_HTC** | This blend shape sticks the tongue out slightly. In step 1 of extending the tongue, the main action of the tongue is to lift up, and the elongated length only extends to a little bit beyond the teeth. |
| **XR_LIP_EXPRESSION_TONGUE_LONGSTEP2_HTC** | This blend shape sticks the tongue out extremely. Continuing from step 1, it extends the tongue to the longest. |
| **XR_LIP_EXPRESSION_TONGUE_RIGHT_HTC** | This blend shape sticks the tongue out and right extremely. |
| **XR_LIP_EXPRESSION_TONGUE_ROLL_HTC** | This blend shape sticks the tongue out with a rolling motion. |
| **XR_LIP_EXPRESSION_TONGUE_UPLEFT_MORPH_HTC** | This blend shape doesn’t make sense. When both the left and up blend shapes appear at the same time, the tongue will be deformed. |
| **XR_LIP_EXPRESSION_TONGUE_UPRIGHT_MORPH_HTC** | This blend shape doesn’t make sense. When both the right and up blend shapes appear at the same time, the tongue will be deformed. |
| **XR_LIP_EXPRESSION_TONGUE_UP_HTC** | This blend shape sticks the tongue out and up extremely. |

This system provides a foundation for predicting learners' comprehension levels by tracking students' learning behaviors in detail and collecting related data. The learning behavior data in this system refers to actions such as how students take notes while watching lectures or how they annotate lecture materials. These behaviors reflect learners' learning styles and comprehension levels and serve as a reference for providing appropriate learning support tailored to each student.

The collected data includes detailed log information about various actions students perform in each section, with multiple recorded items, as shown in Table 2. The following sections describe how these data items are utilized and how they are analyzed in relation to learners' comprehension levels.

First, the collected data is structured into 10 columns, starting with the student ID, followed by details such as the start and end times of each session, action types, and interaction details. The data is recorded based on attributes such as "User ID," "Session," "Start Time (Unix Time)," and "End Time (Unix Time)," allowing tracking of when each action occurs.

Particularly, the use of Unix time ensures temporal consistency and enables consistent recording of detailed behavior logs. For example, in a provided sample case, a user with User ID "Lin" highlighted the text "He is a boy" on Page 1 of the lecture slides in yellow during Session 1 at the Unix timestamp 1725459023.

Table 2: Example of Learning Log Data Storage

| User ID | Session  | Start-Time (Unix Time) | End-Time (Unix Time) | Start-Time (Lecture Time) | End-Time (Lecture Time) |
|---------|---------|----------------------|----------------------|--------------------------|--------------------------|
| Lin     | Session1 | 1725459023           | 1725459045           | 00:01:23:30               | 00:01:23:45              |

| Action Type | Interaction Mode | Interaction Target | Interaction Outcome |
|------------|----------------|------------------|-------------------|
| TextBook   | Yellow Mark    | Page1            | He is a boy       |



Detailed Explanation of Data Fields
User ID: Records a unique name or number for each student.

Session: Records the current session. A complete session spans from the start of a lecture video playback to the end of the AUTO QA multiple-choice question section.

Start-Time (Unix Time): Records the Unix timestamp when the action begins. Unix time refers to the number of seconds elapsed since UTC January 1, 1970, 00:00:00, without considering leap seconds. The smallest recording unit is milliseconds (ms).

End-Time (Unix Time): Records the Unix timestamp when the action ends.

Start-Time (Lecture Time): Records the lecture video timestamp when the action starts. The AutoQA section defaults to 0.

End-Time (Lecture Time): Records the lecture video timestamp when the action ends. The AutoQA section defaults to 0.

Action Type: Describes the major category of the user's activity or operation platform. There are three main categories:
TextBook
Question
FaceTrack

Interaction Mode: Describes the specific method of interaction between the user and the system.
For example, under the TextBook category, possible interactions include:
Yellow Mark
Red Mark
Page Turn, etc.

Interaction Target: Describes the object or goal of the interaction.
For example, the current page or a specific question.

Interaction Outcome: Describes the result or output of the interaction.
For example, the highlighted target or the selected answer.



