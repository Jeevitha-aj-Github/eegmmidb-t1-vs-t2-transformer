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
