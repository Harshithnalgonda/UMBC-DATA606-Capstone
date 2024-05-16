# Spoken Word Recognition System

**Prepared for:** UMBC Data Science Master Degree Capstone by Dr. Chaojie (Jay) Wang  

**Author:** Harshith Nalgonda

**Github:** https://github.com/Harshithnalgonda

**LinkedIn:** https://www.linkedin.com/in/nalgonda-harshith-8bb198218/ 
## Background

### What is the project about? ### 
The main objective of this study is to build a spoken word recognition system which takes audio recordings of the words as an input and predicts the word accurately. Here, all the audio files are in WAV format. This study involves implementing deep learning algorithms trained on dataset of labelled audio samples to classify and decode spoken words.

### What can be achieved?
Though this study is performed with limited set of spoken words, it can have variety of applications as below when it is further studied with more number of words. 
- Spoken word recognition technology enables accessibility for individuals with disabilities, such as those who are visually impaired or have mobility limitations. Voice-controlled interfaces allow users to interact with devices, applications, and services using spoken commands, thereby removing barriers to access and enhancing inclusivity.
- Spoken word recognition enables hands-free operation of devices and systems, which is particularly useful in situations where manual interaction is impractical or unsafe, such as while driving, cooking, or operating machinery. Voice-controlled assistants like Siri, Alexa, and Google Assistant allow users to perform tasks without needing to physically touch a device.
- Spoken word recognition can be used in automated customer service systems, such as interactive voice response (IVR) systems, virtual agents, and chatbots, to handle customer inquiries, provide information, and route calls to the appropriate departments. Speech recognition enhances the efficiency and scalability of customer support operations.
  
### What are your research questions?
- Which featurization technique is highly effective in predicting the word?
- How deep learning (LSTMs) can be utilized for effective prediction of the word?
## Data
- **Dataset -** The data is in the form of audio clips (.WAV format). It has 65000 long utterances of 30 short words, by thousands of different people. The audio clips were originally collected by Google. There are 20 core command words which were recorded with most speakers saying each of them five times. The core words are: yes, no, up, down, left, right, on, off, stop, go, zero, one, two, three, four, five, six, seven, eight, nine. There are 10 auxiliary words which most speakers said only once: bed, bird, cat, dog, happy, house, marvin, sheila, tree, wow.
- **Size -** 1.4 GB
- **Shape -** When the data is presented in the row columnar format, there would be 65000 rows and 2 columns (Audio, Command word) where in each row would represent an audio file and the corresponding command word respectively. 
- **Input datatype -** Audio files in .WAV format
- **Source -** [IBM Developer Exchange - Speech Commands](https://developer.ibm.com/exchanges/data/all/speech-commands/)
- **Target variable -** Here target variable "command word" contains all the command words which are classified into 30 categories. ( yes, no, up, down, left, right, on, off, stop, go, zero, one, two, three, four, five, six, seven, eight, nine, bed, bird, cat, dog, happy, house, marvin, sheila, tree, wow.)

## Expected Outcome
The spoken word recognition system should be able to recognize one of the 30 short words stated above correctly when an audio file is given as input in .WAV format.

## Data Preparation

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/c1d7300d-7102-4f5b-81d8-1f7b3c60cad7)

The dowloaded file is of size 1.4 GB and is of file type .tar.gz. The download process has been performed using 'wget' which is used to download files from the web.
Now to extract all the files in the tar.gz file, tarfile library has been used as below.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/4f494f3a-2d8b-4fa9-832c-d0b68ccadbd9)

We need to show all the audio paths and their corresponding labels in the form of a dataframe. For this we extracted all the audio paths and labels using os.walk and stored them in 2 separate lists. Then, using the lists created for audio paths and labels, a dataframe has been created. 

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/bb2ca37b-10ac-43e7-8683-e3e2fd4d8da1)

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/33fdb315-f95a-4b73-974b-e4d5c7335d9a)

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/7226900a-1f36-47ef-8c28-32476cec5852)

There are 64727 files in the dataset

## Exploratory Data Analysis

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/58c7a0e8-3208-40a4-9dda-40f78063a71f)

It can be observed that the number of audio files for the 'background noise' is as low as 6 files whereas the core word 'stop' has 2380 audio files which is the highest among the dataset. Therefore, dropping records with label "_background_noise_" since it has low counts and its a noise as below.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/bb4635cf-4ac9-41e7-94bf-f1bf433d3fe1)

Since the dataset is huge for the computational resources to handle, I have sampled 70% of the data from the original dataset. The data is sampled in such a way that 70% data is extracted for each class label ensuring that the data from any class label is not missed which is shown as below.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/0e5b3c87-5884-435d-80e3-18b34c539f5c)

So, the effective size of the data that has been used for this study is 0.7*1.4 GB = 0.98 GB.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/7943bfc2-f4eb-4f8f-a06e-0a1ea611d043)

It can be observed that the distribution of class labels has not been changed after sampling the data from the original dataset.

Now , let us view spectrum of few sample audio files. These spectrum plots helps in understanding the frequency compositions of the audio signal.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/87045531-9946-47a1-b73b-9c89eeb95722)

Following are the specturm of sample audio files belonging to Happy core words group.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/8ed724c3-e1d8-4e2e-a5bc-fb047f50068d)

Following are the specturm of sample audio files belonging to Seven core words group.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/23b2f591-1af1-4fd6-8d65-f4e73d9a93bb)

Then, splitting the data into train and test in the ratio of 80:20 respectively using stratification for maintaining same distribution of class labels in train and test data. The target class labels are encoded using label encoder. 

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/f3ef8044-48f2-4c63-a61a-d5e84595a7c8)

## Data Featurization

Dipti Joshi et. al [2023] [1] did a comparative study of MFCC and Mel Spectrogram for Raga Classification using CNN and it has been observed that CNN with Mel Spectrogram outperformed CNN with MFCC. Therefore, for my study Mel Spectrogram featurization has been considered.

Using Librosa, audio file is featurized into array. This array represents the amplitude of the audio signal at a specific point in time. The essentially represents the digital representation of the audio waveform in the raw format.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/66ddedfd-24b7-4d6d-94d8-55c72c68859c)

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/0169c891-75b4-44c2-8547-dee734199ccb)

While loading the audio files, we are using sampling rate of 22050 so one sec will give array of length 22050. Since all the files in train and test does not have exact duration of 1 sec, array lengths will not be same for all these files. Therefore we have to make all these arrays of same length of 22050 by padding.

These are further processed to compute the mel-scaled spectrogram of the input audio data where the above raw format is used as an input. Mel-Spectrogram is a type of spectrogram where the frequencies are converted to mel scale, which more closely aligns with human perception of sound. The resulting spectrogram is then converted to a logarithmic scale. This enhances the contrast and makes it easier to analyze the spectrogram. In a linear scale spectrogram, small variations in amplitude may be overshadowed by larger values, making it challenging to discern fine details, especially in regions with low energy. By using a logarithmic scale, the differences in amplitude are more evenly distributed across the range, enhancing the visibility of both low and high-energy components.

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/b8596a17-2e6d-4d8b-8deb-5ad67ee67043)

![image](https://github.com/Harshithnalgonda/UMBC-DATA606-Capstone/assets/125507937/5616f496-4c6f-4da7-9e6d-32b2edc6e742)

## Modelling




















