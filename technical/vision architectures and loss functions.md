a dump + refresher to keep myself from getting mixed up

**CNNs** - just pass feature maps from one layer to the next
**dense CNN**
- pass feature maps from one layer to every layer after it
- crazy more expensive
**vision transformer**
- patches of images get compared to each other (attention mechanisms)
- makes sense for medical images where an issue somewhere causes change elsewhere (organ shapes, etc)
- in other words, detects global patterns better, CNNs better for small, isolated changes

all three of ^ need significant data

**SVM** (draws a hyperplane)
- works well on high-feature datasets, more explainable via the support vectors
- binary answer, compute friendly though
- if a clear boundary between classes is reasonable (little overlap or gray area in between-ness)

CLIP makes images and text share an embedding space, popular as the "eyes" of language models

**loss functions**
bce
- standard for binary classification
- and for multi-label classification by treating the labels independently of each other (needs sigmoid not softmax obviously)

focal
- intuitively achieves what weighted bce does but with a new parameter
- better for severe imbalance but for mild imbalance parameter tuning might not be worth

**another cool idea**
expensive encoders + cheap task heads 
has been popular bc economical