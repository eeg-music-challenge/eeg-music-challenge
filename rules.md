---
layout: default
---

# Rules

## Registration

Teams who want to join the challenge can register sending an email to salvatore.calcagno@phd.unict.it or simone.carnemolla@phd.unict.it indicating the team name and for each participant:
- name
- surname
- affiliation
- email
  
## Evaluation Criteria and Methodology

The performance of the submitted models will be evaluated using the following criteria:
1.	For task 1 (subject identification), we will compute balanced accuracy score on the held-out-trials test set.
2.	For task 2 (emotion recognition), we will compute baalanced accuracy score separately on both held-out-trials and held-out-subjects test sets. These two scores will be averaged together to obtain the final score.

In the event of a tie, the originality of the approach will be used as an additional criterion, with the organizers taking responsibility for the final decision.

Participants are allowed to submit results for one or both tasks. We will select the top-5 performing teams, based on the distribution of participants among the tasks.

Please note that the held-out trials test set for task 1 and task 2 are not completely identical. Please use only IDs specified in the JSON files.

## Guidelines for participants

- Participants can submit their predictions up to five times. Only the last one is considered. Participants can submit to either one track or both. All submissions should be accompanied by a brief (1-page) description of the employed method.
- The top 5 ranked teams will be invited to submit a 2-page paper, to be presented at ICASSP-2025, which should be submitted before the camera-ready deadline. 
- Participants will be ranked according to the best performance for every single task. If two teams get the same score, the ranking will be determined by the innovation of the employed methods.
- The top 5 teams will be selected based on the participants’ distribution among the tasks. This means that the top 2 teams will be selected for track 1 and the top 2 teams for track 2. The fifth team will be chosen as the third-ranking team in the task with the most submissions
- Each participant can only be included in one participating team.
- Participants can use the full training set to train the models for both tasks. Stimulus information can be used for training (information can be deduced based on the Spotify ID).
- Test data cannot be used during training. The test sets can be used only to provide output predictions. All parameters should be tuned on the training set. Participants can derive validation sets from the training set. 
<!-- - Our baseline implementation also comes with the definition of two validation sets. You can use validation data during training. -->
- For the emotion recognition task, although the held-out trial test set does not contain information about the subject identity, participants are allowed to infer this information (e.g. using a model trained for subject identification).
- We encourage all teams to publicly share their code at the end of the contest.
- The use of external data (both training data and/or pretrained models) is allowed, if all conditions are met:
  - The datasets, or pretrained models, are publicly and freely available. 
  - Datasets/pretrained models must be available before the start of this challenge.
  - Datasets/model weights used to generate predictions must be cited in the final description and in the final paper.
  - Public pretrained models, trained on private data can be used only after the approval of the organizers.