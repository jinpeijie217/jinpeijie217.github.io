---
title: CNN
date: 2019-07-16 16:10:00
tags:
---

**About input and output**
1. input and output of conv layer are (sample,channel,height,width),like(1,64,112,112); input and output of dense layer are (sample, feature),like(1,4096)
2. About the Channel:
   - the initial channels is up to the type of picture, like RGB;
   - in_channels of cnn layer is the number of feather map( the depth of kernel), which is equal to the out_channels of the previous kernel;
   - out_channels depends on the number of kernels, and will produce the same number of feature maps which is the next kernel's in_channels.

---
**About CNN models**
1. Lenet
2. AlexNet
3. VGG: 
	- vgg_block: Conv2D + MaxPool2D
	- 8 conv + 3 Dense
4. NiN
	- Nin_block: Conv2D + Con2D(kernel_size = 1) * 2
	- reduce the size of model
	- increase the training time, compared to VGG
	- turn 4-D output into 2-D output with setting the channel size of nin_block(10) to the number of labels. 
	- using nn.GlobalAvgPool2D() and nn.Flatten()
5. GoogleNet
	- inception block
	- parallelized 
	- 5 blocks, connected with nn.MaxPool2D(pool_size = 3, strides = 2, padding = 1)
	- end up with Dense(10)
	- complexity is relatively low
6. ResNet
	- designed to deal with higher loss after adding more layers
	- residual block: two 3*3 Conv2D, one 1*1 Conv2D
	- similar structure to GoogleNET, much easier to modify
7. DenseNet
	- compare to Resnet using addition to connect, DenseNet uses junction 
	- include dense block (nd.concat(X,Y,dim = 1)) + transition layer
	- dense block: define the concatenation of input and output, transition layer: control the numbe rof channels, simplify the model

---
**batch normalization**
1. for dense
2. for conv : between conv and activation
```[python][norm]
net.add(nn.Conv2D(16,kernel_size = 5),BatchNorm(16,num_dims = 4), nn.Activation('sigmoid'))
```
3. for prediction

- could make the intermediate output of neuron network more stable
- BatchNorm class from Gluon could be useful and auto

<!--more-->



