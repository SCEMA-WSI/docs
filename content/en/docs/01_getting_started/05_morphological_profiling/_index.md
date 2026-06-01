---
title: Morphological Profiling
description: Measuring morphological properties in SCEMATK
weight: 50
---

Morphological profiling is the process of taking an image and a label mask to generate a set of measurements describing the appearance of a cell. SCEMATK does not currently support nucleus segmentation and the suggested method for generating nucleus masks is to use the "big" implementation of stardist in Python to generate a zarr file. More information on this can be found [here](https://github.com/stardist/stardist/blob/main/examples/other2D/predict_big_data.ipynb).

Once this file has been created, move it to the current project directory, then load up the deconvolved image from the last tutorial

```python
deconv_img = read_zarr_ubimg('./deconv_image/image.zarr', './deconv_image/meta.json', channel_names=['Hematoxylin', 'Eosin'])
```

Then load up the nucleus masks created using stardist

```python
nuc_mask = read_zarr_lbl_mask('./path/to/mask.zarr', './deconv_image/meta.json', mask_names=['Nuclei'])
```

This creates a mask object and uses the metadata of the original image to gain information about microns per pixel.

Then we need to create a morphological profiler object

```python
from scematk.morphology import MorphologicalProfiler

mp = MorphologicalProfiler(modules=["AreaShape"])
```

The morphological profiler can then measure the cells by calling the `measure` command

```python
data = mp.measure(deconv_img, nuc_mask)
```

Running this will create a dask dataframe object that contains all the instructions for calculating the morphologies, but will not actually calculate it. To calculate the results run the following command

```python
data.to_csv("./morphological_profiles.csv", index=False, one_file=True)
```
