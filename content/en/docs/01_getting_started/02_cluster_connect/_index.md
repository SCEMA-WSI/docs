---
title: Connecting to a Cluster
description: How to connect to a cluster and supercharge SCEMATK
weight: 20
---

This tutorial is not really about SCEMATK, it's more about Dask and Dask JobQueue, but is an important part of using SCEMATK. All of the workflows in SCEMATK are built upon Dask to make the processing both memory efficient and parallelisable. Having done this though, it also makes these workflows distributable across an HPC or cloud computing service.

## Connecting to a Cluster

The connection to the cluster is done through the `dask_jobqueue` package. The documentation on how to do this can be found [here](https://jobqueue.dask.org/en/latest/).