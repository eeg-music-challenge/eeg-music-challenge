---
layout: default
---

# Dataset description

Participants will be provided with a dataset consisting of EEG recordings from subjects exposed to various musical pieces that evoke specific emotions. The dataset includes:
EEG recordings with corresponding musical stimuli (Spotify ID) and annotated emotional states.

**Data Collection.** We measure EEG data in a controlled lab, using a 32-channel EPOC Flex EEG recording system with saline sensors. The data is measured at a sampling rate of 128 Hz. All electrodes are placed according to international 10-20 standards. The dataset contains data from 34 young subjects. Each subject listened to 16 trials, each of approximately 90 seconds in length. 8 trials were chosen for each subject from his personal music. Other 8 trials were randomly selected among other participants’ preferences. The emotion felt in each trial is self-assessed after the listening phase, using the Geneva Emotion Wheel. Emotions are then converted in a discrete Valence Dominance space, thus producing 4 different emotional categories. 

**Training Dataset.** More information coming soon...
<!--The training set contains 312 trials, with data coming from 26 subjects. For each subject we have 12 labelled trials, each of approximately 90 seconds.-->

**Test Dataset.** More information coming soon...
<!--The test set consists of two parts: held-out trials and held-out subjects. Data will be released to participants without the label information. The first part will be used in both task 1 and task 2, while the second only in task2:
-	The held-out-trials test set contains 104 trials, with data coming from the 26 subjects seen during training.
-	The held-out-subjects test set contains 128 trials, with data coming from 8 subjects that are not in the training set.-->

**Preprocessing:** More information coming soon...
<!-- We provide two versions of the dataset. The first data version is the raw EEG data. The second version of the dataset has been preprocessed in EEGLab. Particularly, a FIR filter was applied between 0.5 and 40 Hz, while artifacts were removed using Independent Component Analysis (ICA). Challenge participants are free to perform their own preprocessing on both versions of the datasets.-->


<!--{% for entry in site.workshop.program %}
{% if entry.type == "organizer" %}
* {{ entry.time }}: {{ entry.desc }}
{% elsif entry.type == "oral" %}
* {{ entry.time }}: {{ entry.author }}, *{{ entry.title }}*
{% elsif entry.type == "keynote" %}
* {{ entry.time }}: **Keynote**: *{{ entry.title }}* ({{ entry.author }}, {{ entry.affiliation }})
{% endif %}
{% endfor %}-->
