---
title: Morphological Profiling
description: Measuring morphological properties in SCEMATK
weight: 50
---

Morphological profiling is the process of taking an image and a label mask to generate a set of measurements describing the appearance of a cell. SCEMATK does not currently support nucleus segmentation and the suggested method for generating nucleus masks is to use the "big" implementation of stardist in Python to generate a zarr file. More information on this can be found [here](https://github.com/stardist/stardist/blob/main/examples/other2D/predict_big_data.ipynb).