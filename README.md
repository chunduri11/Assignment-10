# Assignment-10

The network is a 3D reconstruction model of medical imaging, for better diagnosis. The paper uses 3D convolution layers for this purpose.
For the purpose of calculating Receptive filed, we will follow the same technique we used for 2D convolutions. It is just that we have additional 3rd dimention to the **kernals and feature maps.** 

In this 3D reconstruction model, we have input as 3D medical image and the output will have a 3D image with segmentation that will help in better diagnosis.

**As part of this assignment our job is to reason why from 6th convolution to 7th convolution there is a jump in receptive field, no layer before this has seen such a big jump.**

I am including only convolution layers(3x3) as part of the below table, not cosidering other layers like max pooling, BatchNormalization, Relu, 1x1 convolutions etc. Because they do not change the receptive field.

| Layer | Feature map | Reciptive Field |Jump |
| --- | --- | --- | --- |
| Conv(3x3) | 128×128×96 | 3x3x3 | 1 |
| Conv(3x3) S=2| 64x64x48 | 5x5x5 | 1 |
| Conv(3x3) | 64x64x48 | 9x9x9 | 2 |
| Conv(3x3) S=2| 32x32x24 | 13x13x13 | 2 |
| Conv(3x3) | 32x32x24 | 21x21x21 | 4 |
| Conv(3x3) S=2| 16x16x12 | 29x29x29 | 4 |
| Conv(3x3) | 16x16x12 | **45x45x45** | **8** |


The reason why the receptive filed jumps to 45 from 29 is very simple, the **jump** at that stage is **8** due to three strdided concolutions of stride 2 each before this layers. Including this in the receptive field calculation will give us 45 as the receptive field at this layer.

![title](https://cdn-images-1.medium.com/max/1200/1*gtEtvAQqaAubgvfQycgnyQ.png)
