---
title: Documentation
linkTitle: Docs
menu: {main: {weight: 20}}
weight: 20
---

Welcome to SCEMA-WSI: Single Cell Extraction and Morphological Analysis of Whole Slide Images! This is a set of tools for efficiently and quickly working with Whole Slide Images (WSI's) with the aim of morphologically profiling individual cells in the tissue. Furthermore, all of the tools here are designed such that once the morphological profiles have been calculated they can be spatially analysed to understand the spatial distribution of different cell phenotypes in the tissue.

The core of SCEMA-WSI is built around SCEMATK (or the SCEMA ToolKit), this is a Python package that allows users to open up and visualised WSI's in Python as well as apply a range of image processing algorithms. SCEMATK is built using Dask to speed up the analysis of WSI's using parallel processing. For the best results we recommend using `dask_jobqueue` or a similar package to connect to an HPC or a cloud computing service to unlock the full potential of SCEMATK. Some institutions have already added profiles to SCEMATK to make connecting to the HPC as easy as one line of code, have a look in the cluster section of the documentation for more information.