# Project Title
Spoken Digit Recognition System

**Prepared for:** UMBC Data Science Master Degree Capstone by Dr. Chaojie (Jay) Wang  

**Author:** Harshith Nalgonda

**Github:** https://github.com/Harshithnalgonda

**LinkedIn:** https://www.linkedin.com/in/nalgonda-harshith-8bb198218/ 
## Background
**Objective:** The main objective of this study is to build a spoken digit recognition system which takes audio recordings (.WAV file format) of the words as an input and predicts the word.

### What can be achieved
- Developing accurate and reliable spoken digit recognition systems can greatly benefit individuals with visual impairments or disabilities. These systems can be integrated into assistive technologies such as screen readers or voice-controlled devices, providing users with improved accessibility to digital content and services.
- Spoken digit recognition can serve as a biometric authentication method, offering a secure and convenient way for users to verify their identity.
- With the growing popularity of voice-controlled devices and virtual assistants, there is a need for accurate spoken digit recognition to facilitate hands-free interactions. LSTM-based models can enable these systems to accurately understand and respond to spoken commands, enhancing user convenience and productivity.
- In telecommunications, spoken digit recognition plays a crucial role in automated customer service systems, such as interactive voice response (IVR) systems.

## Data
- **Dataset:** The dataset is in the form of audio clips (.WAV format). It has 65000 long utterances of 30 short words, by thousands of different people. The audio clips were originally collected by Google. There are 20 core command words which were recorded with most speakers saying each of them five times. The core words are: yes, no, up, down, left, right, on, off, stop, go, zero, one, two, three, four, five, six, seven, eight, nine. There are 10 auxiliary words which most speakers said only once: bed, bird, cat, dog, happy, house, marvin, sheila, tree, wow.
- **Size:** 1.4 GB
- **Input datatype:** Audio files in .WAV format
- **Source:** [IBM Developer Exchange - Speech Commands](https://developer.ibm.com/exchanges/data/all/speech-commands/)

## Expected Outcome
The spoken digit recognition system should be able to recognize one of the 30 short words stated above correctly when an audio file is given as input in .WAV format.
