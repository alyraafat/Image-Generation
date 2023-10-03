# Face Generation using DCGAN

This repository focuses on generating realistic human faces using Deep Convolutional Generative Adversarial Networks (DCGAN). The notebook provides an in-depth exploration of the DCGAN architecture, specifically highlighting the generator and discriminator components. We train our model using binary crossentropy loss and incorporate advanced techniques like label smoothing and flipping fake labels during generator weight updates to enhance the model's performance.

## Table of Contents

- [Introduction](#introduction)
- [DCGAN Architecture](#dcgan-architecture)
  - [Generator](#generator)
  - [Discriminator](#discriminator)
- [Loss Function](#loss-function)
- [Training Loop](#training-loop)
- [Results & Insights](#results--insights)

## Introduction

Generative Adversarial Networks (GANs) have revolutionized the field of image synthesis. DCGANs, an extension of the GAN architecture, leverage convolutional layers to generate high-quality images, making them suitable for tasks like face generation.

## DCGAN Architecture

### Generator

The generator model of our DCGAN takes as input a sample from normal distribution and starts with a dense layer and reshapes its output to produce feature maps. This is followed by a series of transposed convolutional layers (sometimes called "deconvolutional" layers), each paired with a batch normalization and a LeakyReLU activation. The final layer uses a tanh activation to produce images in the range [-1, 1].

### Discriminator

The discriminator employs convolutional layers to process the images. After each convolutional layer, we use batch normalization and a LeakyReLU activation. The final layer of the discriminator is a dense layer with a sigmoid activation, classifying inputs as real or fake.

## Loss Function

Our DCGAN utilizes the **Binary Crossentropy Loss (BCE Loss)**. This loss function measures the difference between the predicted probabilities and the actual labels, making it suitable for binary classification tasks, which is inherent to the discriminator's role in GANs.

## Training Loop

The training process for DCGANs is nuanced:

1. **Label Smoothing**: Instead of having hard labels (1s for real images and 0s for fake), we use smoothed labels. This prevents the discriminator from becoming overly confident, which can hamper the training process.
  
2. **Flipping Fake Labels when Updating Generator**: Occasionally, when updating the generator weights, we flip the labels for the fake images to avoid the problem of vanishing gradients.

3. **Discriminator Update**: The discriminator is trained to differentiate between real and fake images.
  
4. **Generator Update**: The generator is trained to fool the discriminator. During this phase, the discriminator's weights are kept constant.

This iterative process continues until the generator produces satisfactory results or a specified number of epochs is reached.

## Results & Insights

Our DCGAN, equipped with label smoothing and occasional label flipping, produces high-quality face images. Detailed visual results and insights into the model's performance over epochs are showcased within the folder called generated. You can definitely run for more epochs so that the faces would be much more realistic.
