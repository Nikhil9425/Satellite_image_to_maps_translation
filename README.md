# Satellite_image_to_maps_translation

## Pix2Pix
Pix2Pix is a Generative Adversarial Network, or GAN, model designed for general purpose image-to-image translation.
The GAN architecture is an approach to training a generator model, typically used for generating images. A discriminator model is trained to classify images as real (from the dataset) or fake (generated), and the generator is trained to fool the discriminator model.

The Conditional GAN, or cGAN, is an extension of the GAN architecture that provides control over the image that is generated, e.g. allowing an image of a given class to be generated. Pix2Pix GAN is an implementation of the cGAN where the generation of an image is conditional on a given image.

## Pix2Pix Architecture detail

The Pix2Pix GAN architecture involves the careful specification of a generator model, discriminator model, and model optimization procedure.

Both the generator and discriminator models use standard Convolution-BatchNormalization-ReLU blocks of layers as is common for deep convolutional neural networks.
Image-to-image translation is the controlled conversion of a given source image to a target image.An example might be the conversion of black and white photographs to color photographs.

The Pix2Pix GAN is a general approach for image-to-image translation. It is based on the conditional generative adversarial network, where a target image is generated, conditional on a given input image. In this case, the Pix2Pix GAN changes the loss function so that the generated image is both plausible in the content of the target domain, and is a plausible translation of the input image.

The generator model is provided with a given image as input and generates a translated version of the image. The discriminator model is given an input image and a real or generated paired image and must determine whether the paired image is real or fake. Finally, the generator model is trained to both fool the discriminator model and to minimize the loss between the generated image and the expected target image.

Both the generator and discriminator models use standard Convolution-BatchNormalization-ReLU blocks of layers as is common for deep convolutional neural networks. 


### U-Net Generator Model
The generator model takes an image as input, and unlike a traditional GAN model, it does not take a point from the latent space as input.Instead, the source of randomness comes from the use of dropout layers that are used both during training and when a prediction is made.

### PatchGAN Discriminator Model
The discriminator model takes an image from the source domain and an image from the target domain and predicts the likelihood of whether the image from the target domain is a real or generated version of the source image.

The PatchGAN discriminator model is implemented as a deep convolutional neural network, but the number of layers is configured such that the effective receptive field of each output of the network maps to a specific size in the input image. The output of the network is a single feature map of real/fake predictions that can be averaged to give a single score. A patch size of 70×70 was found to be effective across a range of image-to-image translation tasks.

### Weights updates in Generator
![gentrain](https://user-images.githubusercontent.com/68101064/222049294-8bcd67f3-6865-4d9a-a3c4-d9ec1ac61bf4.png)

### Weights updates in Discriminator
![disctrain](https://user-images.githubusercontent.com/68101064/222049405-a3e10d4a-9388-43fd-b2c5-59f95942e8e3.png)

