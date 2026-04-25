---
tags:
  - paper
  - to-read
year: "2020"
modality:
task: predict future tumor volumes, cell density, and CT intensity numbers
dataset_size: 33 patients
link: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8848835
---

## Problem
What gap or challenge are they addressing?


## Method
We extend ConvLSTM into the spatio-temporal domain (ST-ConvLSTM) by jointly learning the inter-slice 3D contexts and the longitudinal or temporal dynamics from multiple patient studies. Our approach can incorporate other non-imaging patient information in an end-to-end trainable manner
- how and what non-imaging patient info? sounds relevant to us

"Last, we demonstrate the generalizability of ST-ConvLSTM by employing it in 4D medical image segmentation task, which achieves an averaged Dice score of 86.3%**±**1.2% for left-ventricle segmentation in 4D ultrasound with 3 seconds per patient case."
- exactly relevant, 3 seconds is a little short but maybe we can extrapolate this structure
- wait no nvm this is just one scan we want to compare across two
- can compare embeddings

## Results
Key numbers, what baseline they beat
Dice score of 83% +- 5%
4d segmentation (3 sec ultrasound) Dice score of 86% +- 1%

## My Take
4d structure should be relevant

## Links
- Concept notes: [[framework modifications]]
- Related papers: [[]]