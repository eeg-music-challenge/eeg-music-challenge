---
layout: default
---

# Dataset description

Participants are provided with a dataset consisting of EEG recordings from subjects exposed to various musical pieces that evoke specific emotions. The dataset includes EEG recordings with corresponding musical stimuli (Spotify ID) and annotated emotional states.

**Data Collection.** 

We measure EEG data in a controlled lab, using a 32-channel EPOC Flex EEG recording system with saline sensors. The data is measured at a sampling rate of 128 Hz. All electrodes are placed according to international 10-20 standards. The dataset contains data from 34 young subjects. Each subject listened to 16 trials, each of approximately 90 seconds in length. 8 trials were chosen for each subject from his personal music. Other 8 trials were randomly selected among other participants’ preferences. The emotion felt in each trial is self-assessed after the listening phase, using the Geneva Emotion Wheel (https://www.unige.ch/cisa/gew). 
The wheel is divided into 20 emotion families and are placed in a circle according to a valence-power reference system:
- emotions at the *right* have positive valence
- emotions at the *left* have negative valence
- emotions at the *top* have high power (dominance)
- emotions at the *bottom* low power (dominance)

**Training Dataset.** 

The training set contains 294 trials, with data coming from 26 subjects. For each subject we have about 12 labelled trials, each of approximately 90 seconds.

Each trial comes with the following information:

- **session type** specifes if the given trial belongs to *personal* or *other* session. If *personal* the song was selected among the subject's personal playlists. If *other* the song was selected among the other participants' playlists.
- **subject_id** it is the identifier of the subject.
- **spotify_track_id** is the identifier of the song on Spotify.
- **song_title** is the title of the song. Each song was played from the beginning and stopped at the end of the trial.
- **song_author** is the list of the authors of a song.
- **emotion** is the self-assessed emotion using the Geneva Emotion Wheel
- **label** is the emotion label in a Valence-Dominance space.
- **id** is the identifier of the trial.

For labels we divided the above-mentioned circle into 4 groups that correspond to our emotional states:
- 0 indicates an emotion with high valence and high power (e.g. Joy)
- 1 indicates an emotion with high valence and low power (e.g. Relief)
- 2 indicates an emotion with low valence and low power (e.g. Sadness)
- 3 indicates an emotion with low valence and high power (e.g. Anger) 

**Test Dataset.** 

The test set consists of two parts: held-out trials and held-out subjects. Data will be released to participants without the label (i.e. emotion) and subject information. 

The first part will be used in both task 1 and task 2, while the second only in task2:
-	The **held-out-trials test** set contains 104 trials, with data coming from the 26 subjects seen during training. 
-	The **held-out-subjects** test set contains 122 trials, with data coming from 8 subjects that are not in the training set.

For task 1 the held-out trials test set also contains 44 additional trials either with or without stimulation information.

**Preprocessing**

We provide two versions of the dataset. 

The first data version is the **raw EEG data**. The second version of the dataset has been **preprocessed in EEGLab**.

Particularly, a FIR filter was applied between 0.5 and 40 Hz, while artifacts were removed using Independent Component Analysis (ICA). This version of the dataset is refered as **pruned** in the dataset release.

Challenge participants are free to perform their own preprocessing on both versions of the datasets.

**Files structure**

Each EEG file is placed in the tree structure according to the data type - raw or pruned - and the split to which it belongs - train or held-out trials or held-out subjects test set.

Each file is named using the convention ID_eeg.EXT where ID is the identifier of the trial and EXT is *fif* for both raw and pruned data.

Supposing the root name is *dataset* we have the following structure

<pre>
dataset
├── splits_subject_identification.json
├── splits_emotion_recognition.json
├── raw
│   ├── train
│   │   ├── 1135903657_eeg.fif
│   │   └── ...
│   ├── test_trial 
│   └── test_subject       
└── pruned
    ├── train
    │   ├── 1135903657_eeg.fif
    │   └── ...
    ├── test_trial 
    └── test_subject
</pre>

Although the dataset structure is consistent across both tasks, not all files within the test sets folder will be utilized for each task at inference time. 

The list of IDs that will serve as the test set is specified in two separate JSON files: 
- *splits_subject_identification.json* for Task 1 
- *splits_emotion_recognition.json* for Task 2

Predictions made for IDs not included in these JSON files will be disregarded during evaluation.