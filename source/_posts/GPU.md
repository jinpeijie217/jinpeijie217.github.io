---
layout: optimizer
title: GPU
date: 2019-07-22 17:27:30
tags:
---
**optimizer**
1. stochastic gradient is unbiased estimation of real gradient
2. momentum is simliar with mini-batch SGD , but make the neighbouring steps more consistent
3. AdaGrad allows the learning rate of each variable to adapt and decrease independently
5. RMSProp is modified from AdaGrad to fix the too small learning rate in the subsequent step
6. AdaDelta is designed to deal with the subsequent weakness of AdaGrad as well, without an initial learning rate
7. Adam combines the momentum and RMSProp, each moment has its own leanring rate and it uses the biased modification

**computation**
1. imperative programming: simple and comprehensive
2. symbolic programming: more efficient and easy to implant
3. Hybrid programming: both, from MXNet
4. Asynchronic parallelling computation: 
5. data parallelling is used to implement the multiple GPU. 
	- step1: copy models to multiple GPU, 
	- step2: split data into several sets. 
	- step3: add all the local gradients. 
	- step4: broadcast to all GPUs