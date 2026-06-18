# C.elegans-Vision-AI-Tracker-based-on-U-net
Bright Field Image 또는 Video에서 C.elegans의 연령 L1, L4, Adult의 Feature를 U-net 기반 Vision AI 모델을 이용해서 검출하는 프로젝트

# C.elegans-Vision-AI-Tracker-based-on-U-Net

## Overview

C.elegans-Vision-AI-Tracker는 Bright Field Microscopy Image 및 Video에서 C. elegans를 자동으로 검출하고, 연령(Stage)을 분류하며, 향후 Tracking 및 Behavioral Analysis까지 수행하기 위한 Vision AI 기반 분석 플랫폼이다.

본 프로젝트는 U-Net 기반 Semantic Segmentation Model을 활용하여 개별 선충을 Pixel-Level로 검출하고, 각 개체의 Developmental Stage를 자동으로 분류하는 것을 목표로 한다.

## Motivation

C. elegans는 노화(Aging), 유전학(Genetics), 신경과학(Neuroscience), 독성평가(Toxicity Assessment), 신약개발(Drug Discovery) 등 다양한 분야에서 가장 널리 사용되는 Model Organism 중 하나이다.

하지만 대부분의 실험은 여전히 연구자가 직접 현미경 영상을 관찰하며 다음과 같은 작업을 수행한다.

* Worm Counting
* Stage Classification
* Lifespan Analysis
* Behavioral Analysis
* Drug Screening

이러한 과정은 매우 많은 시간과 인력이 필요하며 연구자 간 주관적인 차이가 발생할 수 있다.

본 프로젝트는 Deep Learning 기반 Vision AI를 활용하여 이러한 분석 과정을 자동화하고, 대규모 Biological Data를 효율적으로 처리할 수 있는 기반 기술을 구축하는 것을 목표로 한다.

---

## Key Features

### Semantic Segmentation

* U-Net 기반 Worm Segmentation
* Pixel-Level Detection
* Stage-Specific Segmentation

## Label Definition

| Class      | Color |
| ---------- | ----- |
| Background | Black |
| Egg        | Red   |
| L1         | Green |
| Adult      | Blue  |

---

## Dataset

Dataset은 Bright Field Microscopy 환경에서 촬영된 C. elegans 영상 및 이미지로 구성된다.

Annotation 방식은 Semantic Segmentation 기반 Pixel-Level Labeling을 사용한다.

현재 Annotation Class

* Background
* Egg
* L1
* Adult

## Model Architecture

### Network

* U-Net
* ResNet34 Encoder

### Training Strategy

<img width="512" height="512" alt="frame_00000" src="https://github.com/user-attachments/assets/0c7c1079-b218-449b-8261-486b2faabd7a" />
<img width="512" height="512" alt="frame_00000m" src="https://github.com/user-attachments/assets/11e5e497-b195-42d2-a23b-609b26896d94" />


현미경 영상에서는 Worm가 이미지 전체에서 차지하는 비율이 매우 작기 때문에 Background Dominance 문제가 발생한다.

이를 해결하기 위해 다음 전략을 적용하였다.

* Worm-Centered Patch Extraction
* Blob-Based Patch Generation
* Dice Loss
* Focal Loss
* Patch-Based Semantic Segmentation

이를 통해 모델이 배경보다 Worm Feature를 집중적으로 학습할 수 있도록 설계하였다.

---

## Workflow

```text
Microscopy Video
        ↓
Frame Extraction
        ↓
Manual Annotation
        ↓
Patch Generation
        ↓
U-Net Training
        ↓
Semantic Segmentation
        ↓
Overlay Visualization
        ↓
Human Verification
        ↓
Ground Truth Refinement
        ↓
Model Improvement
```

---

## Applications

본 플랫폼은 다음과 같은 연구 분야에 활용될 수 있다.

### Aging Research

* Lifespan Analysis
* Healthspan Analysis

### Drug Discovery

* Drug Screening
* Drug Response Quantification

### Toxicity Assessment

* Chemical Toxicity Screening
* Environmental Toxicity Analysis

### Behavioral Analysis

* Movement Tracking
* Behavioral Phenotyping

### Space Biology

* Microgravity Experiment Analysis
* Fluorescence Quantification
* Automated Space Bioinformatics

---

## Future Development

### Tracking

* Multi-Object Tracking
* Individual Worm Tracking
* Trajectory Analysis

### Biological Analysis

* Lifespan Prediction
* Behavioral Phenotyping
* Drug Response Analysis
* Automated Toxicity Assessment

### Platform Expansion

장기적으로는 C. elegans를 시작으로 다양한 Model Organism 분석 플랫폼으로 확장하는 것을 목표로 한다.

지원 예정 대상:

* Zebrafish
* Daphnia
* Stem Cell Organoid
* Cell Imaging Data

---

## Long-Term Vision

본 프로젝트의 최종 목표는 단순한 Worm Segmentation Model 개발이 아니다.
Vision AI 기술을 활용하여 다양한 Biological Imaging Data를 자동으로 분석할 수 있는 AI-Powered Biological Analysis Platform을 구축하는 것이다.
이를 통해 연구자들이 반복적인 영상 분석 작업에서 벗어나 보다 본질적인 BIO 연구에 집중할 수 있도록 지원하고자 한다.
장기적으로는 Drug Discovery, Toxicity Screening, Precision Medicine, Space Biology 분야까지 확장 가능한 범용 AI 분석 플랫폼 구축을 목표로 한다.
