---
layout: default
---

# Task 1 - Person Identification

In this task participants are asked to infer the identity of 26 subjects.

**Test Dataset.** 

For this task the test set consists of 144 trials, with data coming from the 26 subjects seen during training.
  -	104 trials present the same data provided for training (i.e. stimulus and emotional information).
  - 44 additional trials lack the stimulus information and/or the self-assessed emotion is lacking.

The list of ids to use for inference is in the *splits_subject_indentification.json* file.

**Target metric** 

The target metric is the balanced accuracy score.

**Baseline implementation**

We used pruned data as starting point and we applied minimal preprocessing involving:
- deletion of invalid values (nans and outliers)
- standardization with train global per-channel statistics

We chose 3 well-known architectures as baselines
- EEGNet [1]
- SyncNet [2]
- EEGChannelNet [3] 

No significant changes were applied to the original architectures.

We created a small validation set (val_trial) by extracting 2 trials per subject from the training data.

Models were trained using the Adam optimizer for 500 epochs. During training, the model was provided with a random window of 1280 timepoints. For validation, we first segmented each sample into smaller windows of 1280 timepoints, excluding the final segment. The model was then fed all the windows, and the average logits were used to determine the final prediction.

The final model and hyperparameters (learning rate, batch size) were selected based on the highest  balanced accuracy on val_trial set. A grid search was conducted to optimize these parameters.

For inference, same as for validation, each sample was first segmented into smaller windows of 1280 timepoints, excluding the final segment. The same voting scheme applied in validation was used to generate the final prediction.

**Leaderboard**

Our strategy yields the following results that serve as baseline

| Model             | Balanced Accuracy |
|-------------------|-------------------|
| EEGChannelNet [3] | 88.09             |
| EEGNet [1]        | 65.91             |
| SyncNet [2]       | 18.53             |

You can replicate results using our <a href='https://github.com/SalvoCalcagno/eeg-music-challenge-icassp-2025-baselines'>GitHub repository</a>.

---

[1] V j Lawhern et al., “EEGNet: a compact convolutional neural network for EEG-based brain–computer interfaces”, J. Neural Eng. 15/5, 2018.

[2] Y. Li et al, “Targeting EEG/LFP Synchrony with Neural Nets”, NeurIPS 2017.

[3] S. Palazzo, C. Spampinato, I. Kavasidis, D. Giordano, J. Schmidt and M. Shah, "“Decoding Brain Representations by Multimodal Learning of Neural Activity and Visual Features”, in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 43, no. 11, 2021.
