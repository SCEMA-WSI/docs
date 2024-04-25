---
title: Connecting to a Cluster
description: How to connect to a cluster and supercharge SCEMATK
weight: 20
---

This tutorial is not really about SCEMATK, it's more about Dask and Dask JobQueue, but is an important part of using SCEMATK. All of the workflows in SCEMATK are built upon Dask to make the processing both memory efficient and parallelisable. Having done this though, it also makes these workflows distributable across an HPC or cloud computing service.

## Connecting to a Cluster

The connection to the cluster is done through the `dask_jobqueue` package. The documentation on how to do this can be found [here](https://jobqueue.dask.org/en/latest/). A simple explanation of what you need to do is find out what type of cluster you were using and then how to request resources for that cluster. For example, SCEMATK was developed at the University of Edinburgh that uses an SGE cluster called Eddie. This is the code that you would use to connect to Eddie:

```python
from dask_jobqueue import SGECluster

cluster = SGECluster(
    memory='8 G',
    cores=1,
    resource_spec='h_vmem=8G',
    worker_extra_args=['--lifetime', '25m', '--lifetime-stagger', '4m']
)
```

Here I am connecting to the cluster, the `memory` argument is saying that I want 8GB of RAM per submission, the `cores` argument is saying that I want 1 core for each submission and the `resource_spec` is a respecification of memory that you have to make on SGE clusters. We recommend that you run the cluster in adaptive mode and the `worker_extra_args` argument tells the scheduler to request jobs that will last for 25 minutes and stagger the start of the jobs by 4 minutes. As we want to run an adaptive cluster, this means that when a node comes to the end of its time it will be brought down and a new one will be brought up. The staggering means that the nodes will not all come down at the same time and the cluster will be more stable.

If you have any more questions about how to connect to a cluster, read that [Dask Jobqueue documentation](https://jobqueue.dask.org/en/latest/) or contact your institution's HPC support team.

## Preconfigured Connections

To make connecting to HPC's easier, SCEMATK was some preconfigured connections for HPC's submitted by users. Here is an example of connecting to the University of Edinburgh's Eddie cluster using the premade profile:

```python
from scematk.cluster import quick_connect

cluster = quick_connect('eddie', 390, 400)
```

This will connect to the Eddie cluster scheduler with a minimum of 390 workers and a maximum of 400 workers. The `quick_connect` function will return a Dask client object that you can use to submit jobs to the cluster.

You can check if your institution has a preconfigured connection by looking [here](), if it is not there please do make a GitHub pull request or GitHub Issue to add it.