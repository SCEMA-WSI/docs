---
title: Processing Images
description: Processing images with SCEMATK
weight: 30
---

Processors and processes are integral to how SCEMATK works. SCEMATK considers most basic image trasnformations and manipulations as processes. This can include processes such as blurring and image, adjusting the contrast or converting and image to greyscale. These are typical operations you might want to perform on an image before you try segmenting it or performing stain deconvolution. A processor is just an object that contains a list of processes that you want to perform on an image and will perform them sequentially when asked.

## Processes

