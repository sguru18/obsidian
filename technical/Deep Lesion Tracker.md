---
tags:
  - paper
year: "2021"
modality:
task: Monitoring Lesions in 4D Longitudinal Imaging Studies
dataset_size:
link: https://openaccess.thecvf.com/content/CVPR2021/papers/Cai_Deep_Lesion_Tracker_Monitoring_Lesions_in_4D_Longitudinal_Imaging_Studies_CVPR_2021_paper.pdf
---
## Method
structure based on Siamese networks ([[correlation filter and Siamese nets]])
on registration: "For example, pre-registering will have minimal effect on the translation-invariant cross-correlation." what
use a 3d image encoder + anatomical signal encoder which takes an anatomy signal map 
then fuse image + anatomy features
then do fast cross correlation at three scales and get a probability map
index of global max is predicted lesion center

We use a pre-trained model, OneClick [50] that takes the image Is and the predicted lesion center µp as its inputs and regresses the RECIST diameters of the target lesion. **what does it mean to regress a diameter**

self supervised learning of the model: The key insight is that effective visual representation for object recognition can be learned by comparing the template image, It, with its augmented counter-parts. 
is that relevant 

We use both the widely used rigid affine registration method [36] and DEEDS [22] deformable registration. **what are these and why is DLT compared to them. i thought registration is just aligning. so images dont need to be registered to use DLT? or maybe it's guessing where to align them by**

## Dataset
- Size: 3891 lesion pairs (follow up CBCTs?)
- Modality: CT resized to isotropic resolution of 2mm

## Results
lot of results provided with accuracy
would be curious about precision

## My Take
could we run some of our lesion pairs on their model??
**so this is good at finding the centers of lesions at different points in time, which can then be passed into measurement tools** 

## Links
- Concept notes: [[framework modifications]]
- Related papers: [[]]