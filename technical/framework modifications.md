convolutional CT scan aware transformer module and hybrid network of CNNs and transformers to use spatial and temporal dimensions. not longitudinal though more for 2d + 3d [[CH1.4.3 Transformer for medical image classification]]

[[deep lesion tracker]] tracks center of a legion across multiple 3d ct images
- fuses anatomical map embeddings with 3d ct embeddings 
[[longitudinal multi-task deep learning]] is fantastic exact same longitudinal setup, not huge dataset
- uses MRI instead of CT but should be modifiable 
- might want to use something from deep lesion tracker related to anatomical constraints, ie. their "anatomical signal encoder" and fuse here
- this already does segmentation though so much of deep lesion tracker of finding center not necessary anymore, just maybe the idea of giving it bounds to use could be useful, or maybe if segmentation doesn't perform well but should be fine probably not necessary
**fundamental difference** the MRI is not 4d though like our post info is
need to find approaches using 4d data specifically over 1/1.5min or something and then could modify this?? we do have the single post CT so this is valuable but we can get more from our data

wonder how to use perfusion data / dose map info
oh we don't have info on where the tumor is for the post treatment perfusion scan so might need DLT here. our contours are only for pretreatment

starting to get an overall idea in my head
pre/post CT scans can use [[longitudinal multi-task deep learning]] type of setup to compare them
pre-treatment perfusion scan has contours already
post-treatment can get contours using [[deep lesion tracker]] 
and then use remodeled ConvLSTM for 2x 90 sec perfusion scan and compare their embeddings or something? 
- can we give convLSTM dose map info??
- actually i think dose info is better as context in fusion stage (what's a spatial attention mask?)
and then how in the world to merge all this stuff
- late fusion
- fusion with attention module could be more performant but needs individual components validated first / harder to use overall

we are predicting global response assessment category right?

one level lower and [[Self-supervised pre-training with contrastive and masked autoencoder methods for dealing with small datasets in deep learning for medical imaging]] seems to have important info for how to actually initialize and train pieces of this



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