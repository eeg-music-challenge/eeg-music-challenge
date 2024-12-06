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

| Team             | Balanced Accuracy |
|:----------------|-------------:|
| <mark>SIP Lab-IITH</mark>    |    100.00       |
| <mark>Neural Harmony</mark>  |    100.00       |
| <mark>NTUA-IRAL</mark>       |    100.00       |
| MindReader     |    100.00       |
| SHINE           |    100.00       |
| GISP@HEU        |    100.00       |
| ABCD            |    100.00       |
| KONKUK_AICV     |     99.45   |
| NWPU EEG        |     99.36   |
| T1040           |     99.36   |
| IIP-HCI         |   99.36     |
| ZeD             |     99.36   |
| USTC Challenger |     98.49   |
| Team-CSL        |     98.17   |
| Hunan           |     97.85   |
| WCQY            |     97.76   |
| CherryBlossoms  |     96.25   |
| btbu-713        |     96.25   |
| SAIL            |     94.87   |
| BCIGO           |     90.00       |
| EEGChannelNet [3] | 88.09             |
| EEGNet [1]        | 65.91             |
| SyncNet [2]       | 18.53             |
| TEAS            |      6.17 |
| iBrain          |      5.16 |
| gdl4bci         |      3.11 |

Results for [1], [2] and [3] come from our baselines. You can replicate results using our <a href='https://github.com/SalvoCalcagno/eeg-music-challenge-icassp-2025-baselines'>GitHub repository</a>.

---

[1] V j Lawhern et al., “EEGNet: a compact convolutional neural network for EEG-based brain–computer interfaces”, J. Neural Eng. 15/5, 2018.

[2] Y. Li et al, “Targeting EEG/LFP Synchrony with Neural Nets”, NeurIPS 2017.

[3] S. Palazzo, C. Spampinato, I. Kavasidis, D. Giordano, J. Schmidt and M. Shah, "“Decoding Brain Representations by Multimodal Learning of Neural Activity and Visual Features”, in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 43, no. 11, 2021.
