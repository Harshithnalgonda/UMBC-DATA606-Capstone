# Project Title
Spoken Word Recognition System

**Prepared for:** UMBC Data Science Master Degree Capstone by Dr. Chaojie (Jay) Wang  

**Author:** Harshith Nalgonda

**Github:** https://github.com/Harshithnalgonda

**LinkedIn:** https://www.linkedin.com/in/nalgonda-harshith-8bb198218/ 
## Background
**Objective:** The main objective of this study is to build a spoken word recognition system which takes audio recordings (.WAV file format) of the words as an input and predicts the word.

### What can be achieved
- Spoken word recognition technology enables accessibility for individuals with disabilities, such as those who are visually impaired or have mobility limitations. Voice-controlled interfaces allow users to interact with devices, applications, and services using spoken commands, thereby removing barriers to access and enhancing inclusivity.
- Spoken word recognition enables hands-free operation of devices and systems, which is particularly useful in situations where manual interaction is impractical or unsafe, such as while driving, cooking, or operating machinery. Voice-controlled assistants like Siri, Alexa, and Google Assistant allow users to perform tasks without needing to physically touch a device.
- Spoken word recognition is used in automated customer service systems, such as interactive voice response (IVR) systems, virtual agents, and chatbots, to handle customer inquiries, provide information, and route calls to the appropriate departments. Speech recognition enhances the efficiency and scalability of customer support operations.

## Data
- **Dataset:** The dataset is in the form of audio clips (.WAV format). It has 65000 long utterances of 30 short words, by thousands of different people. The audio clips were originally collected by Google. There are 20 core command words which were recorded with most speakers saying each of them five times. The core words are: yes, no, up, down, left, right, on, off, stop, go, zero, one, two, three, four, five, six, seven, eight, nine. There are 10 auxiliary words which most speakers said only once: bed, bird, cat, dog, happy, house, marvin, sheila, tree, wow.
- **Size:** 1.4 GB
- **Input datatype:** Audio files in .WAV format
- **Source:** [IBM Developer Exchange - Speech Commands](https://developer.ibm.com/exchanges/data/all/speech-commands/)

## Expected Outcome
The spoken word recognition system should be able to recognize one of the 30 short words stated above correctly when an audio file is given as input in .WAV format.
