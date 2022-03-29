# RBC segmentation and object filter

The code in this repository documents the process to segment and detect red blood cells (RBC): 

1. A number of simple morphological operators are used to detect RBC-candidate objects. In short, edges and contours are detected using a Canny edge detector and filtered based on size, colour and elongation (ratio between the major and minor axis of a fitted elipse) to ensure that other objects (platelet clumps, groups of RBCs or individual WBCs) are not detected as RBCs. This ensures that only RBCs whose morphology is not affected by its neighbouring cells are detected/extracted.
2. Each RBC-candidate object is filtered 