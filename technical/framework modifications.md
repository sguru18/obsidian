convolutional CT scan aware transformer module and hybrid network of CNNs and transformers to use spatial and temporal dimensions. not longitudinal though more for 2d + 3d [[CH1.4.3 Transformer for medical image classification]]

[[Deep Lesion Tracker]] tracks center of a legion across multiple 3d ct images
- fuses anatomical map embeddings with 3d ct embeddings 


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