---
title: Treating WSIs as a Whole
description: The philosophy of treating WSIs as a whole, what this means and why it's important
weight: 20
---

WSI stands for 'whole slide image' so treating them 'as a whole' seems to be intuitive, in this section we will discuss what this means and why it is important.

So, WSI's are *big*. Very big. Too big to fit into a reasonable amount of memory. This means that when we analyse them we *have* to split them up into smaller chunks (often called "tiling the image") and then analyse these smaller chunks. There is nothing wrong in this approach and is also how SCEMATK handles these very large images. The problem comes when these tiles are processed differently from one another. If you are only interested in using one tile at a time, then this may not cause an issue, but the SCEMA-WSI isn't just interested in analysing the morphology of a single cell, it is interested in comparing and contrasting the morphologies of these cells to the cells that surround them. To effectively do this, all regions of the image need to have been processed in the same way. Here we hope to show you different examples of how tiling images separately can affect the results of your analysis.

