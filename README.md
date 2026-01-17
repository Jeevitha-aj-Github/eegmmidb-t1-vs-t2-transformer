# EEG Motor Imagery: T1 vs T2 (Cross-Subject) – Transformer Baseline

Goal: Build a simple, reproducible baseline that classifies motor imagery EEG (T1 vs T2) and evaluates cross-subject generalisation.

## Dataset
EEG Motor Movement/Imagery Dataset (PhysioNet, eegmmidb).
- 64 channels, 160 Hz
- Labels from annotations: T1 and T2
- We focus on motor imagery runs.

## Task
Binary classification:
- T1 vs T2 during motor imagery

## Evaluation
Cross-subject split:
- Train on a set of subjects
- Test on unseen subjects

## Plan
1) Download data (subset first)
2) Convert EDF + events into windows
3) Train baseline model (simple Transformer)
4) Report accuracy and confusion matrix

## Results

We evaluated motor imagery classification (T1 vs T2) under a strict cross-subject setting using the EEG Motor Movement/Imagery Dataset (PhysioNet eegmmidb).

### Experimental Setup
- Subjects: S001–S006
- Training subjects: S001–S005
- Test subject: S006 (unseen during training)
- Runs used: R04, R08, R12 (motor imagery)
- Windowing: 2-second windows after event onset
- Channels: 64 EEG channels
- Sampling rate: 160 Hz
- Standardisation: Per-channel z-score normalisation using training data only

### Baselines
A linear baseline model collapsed to predicting a single class under cross-subject evaluation, achieving near-chance performance (~0.53 accuracy), highlighting the difficulty of subject-invariant motor imagery decoding.

### Transformer Model
A lightweight Transformer encoder was trained on windowed EEG sequences:
- 2 Transformer encoder layers
- 4 attention heads
- Model dimension: 64
- Global average pooling over time
- Cross-entropy loss

### Performance (Cross-Subject)
- Test accuracy: ~0.75 (single run)
- Test class distribution: T1 = 24, T2 = 21
- Predicted class distribution: T1 = 13, T2 = 32

Unlike linear baselines, the Transformer did not collapse to a single class and demonstrated improved generalisation to an unseen subject, suggesting that sequence models can capture subject-invariant temporal structure in motor imagery EEG.

### Notes
This experiment is intended as a reproducible baseline rather than a fully optimised model. Future work will explore longer temporal windows, bandpass filtering in the motor imagery frequency range, and subject-adaptive pretraining strategies.
