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

Our strategy yields the following results that serve as baseline

| Model             | Held-out-trialr Bal. Acc. | Held-out-subject Bal. Acc. | Total Score |
|-------------------|---------------------------|----------------------------|-------------|
| EEGNet [1]        | 30.72                     | 29.47                      | 30.10       |
| EEGChannelNet [3] | 29.76                     | 22.23                      | 26.00       |
| SyncNet [2]       | 28.80                     | 23.08                      | 25.94       |

You can replicate results using our <a href='https://github.com/SalvoCalcagno/eeg-music-challenge-icassp-2025-baselines'>GitHub repository</a>.

---

[1] V j Lawhern et al., “EEGNet: a compact convolutional neural network for EEG-based brain–computer interfaces”, J. Neural Eng. 15/5, 2018.

[2] Y. Li et al, “Targeting EEG/LFP Synchrony with Neural Nets”, NeurIPS 2017.

[3] S. Palazzo, C. Spampinato, I. Kavasidis, D. Giordano, J. Schmidt and M. Shah, "“Decoding Brain Representations by Multimodal Learning of Neural Activity and Visual Features”, in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 43, no. 11, 2021.