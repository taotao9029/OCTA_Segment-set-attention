# Temporal Attention Network for OCTA Stroke Classification

[中文说明 / Chinese overview](#中文说明)

This repository implements a temporal-attention neural classifier for OCTA stroke classification. Event-derived vascular descriptors are encoded and reweighted by attention to model discriminative temporal microcirculation patterns. The code preserves fixed split manifests, threshold provenance, checkpoint hashes and runtime metadata for reproducible research.

## Architecture

`video -> event stream -> vessel filtering -> interpretable event features -> classifier`



The experimental protocol includes full-feature training and controlled ablations. Original-only predictions and test-time augmentation (TTA) are reported separately; thresholds are selected from inner OOF predictions only.

## Installation



Python 3.10+ is recommended. GPU is optional for these models, but a consistent locked environment should be used for publication results.

## Data format

Event CSV files must contain , , , and , arranged as  (control) and  (stroke). Keep original and augmented views under a stable . The fixed five-fold split is read from ; never regenerate folds during evaluation.

## Reproducible workflow



Review the YAML/config snapshot before training. Outer-test data are used once for final reporting; model selection, epoch selection and threshold selection use inner folds only.

## Outputs

 contains standardized predictions, , , , , , , , and . Report ROC-AUC, PR-AUC, accuracy, balanced accuracy, F1, sensitivity and specificity.

## Ablation and external validation

Feature ablations are defined by the training script and must use the same split manifest and threshold policy as the full model. For date-based external validation, provide  and run the group-out entry point without using held-out dates for tuning.

## 中文说明

本项目分别实现 OCTA 事件特征时序注意力网络，用于脑卒中二分类。流程包括事件流生成、血管区域过滤、特征提取、固定五折嵌套验证、特征消融和日期外部验证，并输出完整运行清单与哈希记录。

## Citation

Please cite the associated study and report the model version, split manifest, configuration hash and Git commit.

## Copyright

Copyright (c) 2025 Taotao9029. All rights reserved.
