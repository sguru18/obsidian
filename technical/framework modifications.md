convolutional CT scan aware transformer module and hybrid network of CNNs and transformers to use spatial and temporal dimensions. not longitudinal though more for 2d + 3d [[CH1.4.3 Transformer for medical image classification]]

[[Deep Lesion Tracker]] tracks center of a legion across multiple 3d ct images
- fuses anatomical map embeddings with 3d ct embeddings 
[[Predicting treatment response from longitudinal images using multi-task deep learning]] is fantastic exact same longitudinal setup, not huge dataset
- uses MRI instead of CT but should be modifiable 
- might want to use something from deep lesion tracker related to anatomical constraints, ie. their "anatomical signal encoder" and fuse here
- this already does segmentation though so much of deep lesion tracker of finding center not necessary anymore, just maybe the idea of giving it bounds to use could be useful, or maybe if segmentation doesn't perform well but should be fine probably not necessary
**fundamental difference** the MRI is not 4d though like our post info is
need to find approaches using 4d data specifically over 1/1.5min or something and then could modify this?? we do have the single post CT so this is valuable but we can get more from our data

wonder how to use perfusion data / dose map info


relevant data for overall task
- 2 4d perfusion ct scans pre-treatment and 2/3 month-post
- 3 cone beam CT scans (1 per treatment day)
- (pre-treatment )GTV — the gross tumor volume w contours
- (pre-treatment) GTV_H — high-dose target within the tumor (the lattice peaks)
- (pre-treatment) GTV_L — low-dose region of the tumor (the lattice valleys)
- dose distribution within tumor
- planning ct (1 is contrast enhanced)


goal is each data type gets an encoder appropriate to its dimensionality and characteristics 
---> encoders output embeddings that get fused 
---> fusion feeds into your prediction head (response classification, volumetric change, or both)

would be extra cool to relate dose map to location of change in perfusion. probably latent in a treatment response prediction task but could remodel later to be explicitly interpretable to better understand lattice RT effects