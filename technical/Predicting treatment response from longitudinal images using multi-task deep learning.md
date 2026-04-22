---
tags:
  - paper
year: "2021"
modality: MRI (could be used still probably)
task: simultaneous tumor segmentation and response prediction
dataset_size: 2568 scans from 321 patients
link: https://www.nature.com/articles/s41467-021-22188-y
---

## Problem
simultaneous tumor segmentation and response prediction

## Method
"We design two Siamese subnetworks that are joined at multiple layers, which enables integration of multi-scale feature representations and in-depth comparison of pre-treatment and post-treatment images."

"Here, we propose a multi-task deep learning approach to predict treatment response and test the model in multi-institution cohorts of rectal cancer patients" HUGE

evaluation of post treatment images more meaningful than baseline - makes sense. using both caused 14-19% increase in AUC

"The network consists of two main components: (1) a convolutional encoding/decoding sub-network for feature extraction and tumor segmentation, and (2) a multi-stream Siamese subnetwork for response prediction"
U nets with shared parameters for segmentation + subsequent comparison

also combined 5 discrete patient response groups which impacted results positively
multi scale features

**basically the multi-task approach is tumor segmentation and then treatment response using that** if i am understanding correctly

interpretable!

## Results
very good very good

## Limitations
retrospective so subject to selection bias they say

## My Take
extremely relevant
perfect correlation with our data

## Links
- Concept notes: [[framework modifications]]
- Related papers: [[]]