# RBC segmentation and object filter

The code in this repository documents the process to segment, detect and filter red blood cells (RBC): 

1. A number of simple morphological operators are used to detect RBC-candidate objects. In short, edges and contours are detected using a Canny edge detector and filtered based on size, colour and elongation (ratio between the major and minor axis of a fitted elipse) to ensure that other objects (platelet clumps, groups of RBCs or individual WBCs) are not detected as RBCs. This ensures that only RBCs whose morphology is not affected by its neighbouring cells are detected/extracted.
2. Each RBC-candidate object is morphologically characterized (in terms of shape, texture and colour distribution)
3. Each RBC-candidate is filtered using an XGBoost algorithm trained on over 1,000 RBC to classify objects as "RBC" or "not RBC"

Step `1.` generates several RBC candidates with 1 out of every 7 RBC candidates being likely being a false positive. Using steps `2.` and `3.`, however, reduces this to approximately 1 in 300 (estimated based on the observed rate of false positives from `1.` and on the performance of the model stated in `3.`). 