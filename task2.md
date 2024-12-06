---
layout: default
---

# Task 2 - Emotion Recognition

In this task participants are asked to infer the emotional category of EEG recordings.

We have 4 emotional labels:
- 0 indicates an emotion with high valence and high power (e.g. Joy)
- 1 indicates an emotion with high valence and low power (e.g. Relief)
- 2 indicates an emotion with low valence and low power (e.g. Sadness)
- 3 indicates an emotion with low valence and high power (e.g. Anger)

**Test Dataset.** 

The test set consists of two parts:
-	The **held-out-trials test** set contains 104 trials, with data coming from the 26 subjects seen during training.
-	The **held-out-subjects** test set contains 128 trials, with data coming from 8 subjects that are not in the training set.

The list of ids to use for inference is in the *splits_emotion_recognition.json* file.

**Target metric** 

The target metric is the average balanced accuracy score between the two test sets. This means we will compute separately the balanced accuracy score on both held-out-trials and held-out-subjects test sets. These two scores will be averaged together to obtain the final score.

**Baseline implementation**

We used pruned data as starting point and we applied minimal preprocessing involving:
- deletion of invalid values (nans and outliers)
- standardization with global per-channel statistics

We chose 3 well-known architectures as baselines
- EEGNet [1]
- SyncNet [2]
- EEGChannelNet [3] 

No significant changes were applied to the original architectures.

We created two small validation sets: 
- val_subjects excluding 2 subjects from the training data
- val_trial extracting 2 trials per subject from the training data.

Training and inference was performed as in task 1 except that we used a majority voting, instead of the average logits.

The final model and hyperparameters (learning rate, batch size) were selected based on the target metric on our valdation sets. A grid search was conducted to optimize these parameters.

**Leaderboard**

| Team             | Held-out-trialr Bal. Acc. | Held-out-subject Bal. Acc. | Total Score |
|-------------------|---------------------------|----------------------------|-------------|
| <mark>TUM</mark>         | 46.53 |   36.15 |  41.34 |
| <mark>BCIGO</mark>    |    46.69 |  34.9  |        40.79 |
| GISP@HEU       |   44.65 | 31.95 |   38.3  |
| MindReader     |         40.88 |           34.81 |        37.85 |
| Neural Harmony |         38.22 |           34.4  |        36.31 |
| SAIL           |         43.54 |           25.43 |        34.49 |
| KONKUK_AICV    |         26.71 |           35.89 |        31.3  |
| WisdomDLUT     |         32.83 |           28.35 |        30.59 |
| TEAS           |         35.03 |           25.24 |        30.13
| EEGNet [1]     | 30.72       | 29.47    | 30.10       |
| ZeD            |         28.21 |           31.46 |        29.83 |
| NTUA-IRAL      |         27.43 |           27.9  |        27.66 |
| Hunan          |         29.57 |           23.25 |        26.41 |
| EMER_IITMZ     |         24.94 |           27.32 |        26.13 |
| EEGChannelNet [3] | 29.76   | 22.23       | 26.00       |
| SyncNet [2]   | 28.80       | 23.08          | 25.94       |
| iBrain         |         20.52 |           31.02 |        25.77 |
| CUSAP2         |         28.24 |           22.17 |        25.21 |
| WCQY           |         24.08 |           24.88 |        24.48 |
| IIP-HCI      |         22.94 |           24.47 |        23.7  |
| SIP Lab-IITH   |         21.34 |           25.83 |        23.58 |
| CherryBlossoms |         21.31 |           24.27 |        22.79 |
| NWPU EEG       |         21.87 |           23.38 |        22.63 |
| btbu-713       |         19.2  |           23.12 |        21.16 |
| NJUST_KMC      |         10.77 |           26.96 |        18.87 |

Results for [1], [2] and [3] come from our baselines. You can replicate results using our <a href='https://github.com/SalvoCalcagno/eeg-music-challenge-icassp-2025-baselines'>GitHub repository</a>.

---

[1] V j Lawhern et al., “EEGNet: a compact convolutional neural network for EEG-based brain–computer interfaces”, J. Neural Eng. 15/5, 2018.

[2] Y. Li et al, “Targeting EEG/LFP Synchrony with Neural Nets”, NeurIPS 2017.

[3] S. Palazzo, C. Spampinato, I. Kavasidis, D. Giordano, J. Schmidt and M. Shah, "“Decoding Brain Representations by Multimodal Learning of Neural Activity and Visual Features”, in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 43, no. 11, 2021.