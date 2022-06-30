# Image-Colorization
IMAGE-COLORIZATION



Overview:-
 Deep Learning is an upcoming subset of machine learning which makes use of artificial neural networks. These are inspired by the human brain and its immense structure and function. Here we make use of it to colorize black and white images
Methodology:-
•	The colorization of grayscale images can be thought of as an image-to-image translation task where we have the corresponding labels for the input grayscale image. A conditional GAN conditioned on grayscale images can be used to generate the corresponding colorized images.
•	The architecture of the model consists of a conditional generator with grayscale image inputs and a random noise vector and the output of the generator are two image channels a, b in the LAB image space to be concatenated with the L channel i.e. the grayscale input image.
•	As you might know, in a GAN we have a generator and a discriminator model which learn to solve a problem together. In our setting, the generator model takes a grayscale image (1-channel image) and produces a 2-channel image, a channel for *a and another for *b. The discriminator, takes these two produced channels and concatenates them with the input grayscale image and decides whether this new 3-channel image is fake or real. Of course the discriminator also needs to see some real images (3-channel images again in Lab color space) that are not produced by the generator and should learn that they are real.
So what about the "condition" we mentioned? Well, that grayscale image which both the generator and discriminator see is the condition that we provide to both models in our GAN and expect that the they take this condition into consideration.
•	Let's take a look at the math. Consider x as the grayscale image, z as the input noise for the generator, and y as the 2-channel output we want from the generator (it can also represent the 2 color channels of a real image). Also, G is the generator model and D is the discriminator. Then the loss for our conditional GAN will be:

![image](https://user-images.githubusercontent.com/97727617/176667670-ef4904b4-ec4c-43da-ac50-dd8335d8f9f5.png)

 

Loss function optimized:-
If we use L1 loss alone, the model still learns to colorize the images but it will be conservative and most of the time uses colors like "gray" or "brown" because when it doubts which color is the best, it takes the average and uses these colors to reduce the L1 loss as much as possible (it is similar to the blurring effect of L1 or L2 loss in super resolution task). Also, the L1 Loss is preferred over L2 loss (or mean squared error) because it reduces that effect of producing gray-ish images. So, our combined loss function will be:

![image](https://user-images.githubusercontent.com/97727617/176667760-9963f6f2-d81b-4153-a85b-22eb3c7a53a7.png)


 

Implementation:-
(1)	Loading image paths:-
![image](https://user-images.githubusercontent.com/97727617/176667791-8bd9d914-e20c-4b57-b6af-7859f8e731eb.png)

 

(2)Making Datasets and DataLoaders:-
![image](https://user-images.githubusercontent.com/97727617/176667823-34f5e0e3-2be9-45d4-bc9f-2655ec4bee8d.png)

 
(2)	U-net Generator:-
![image](https://user-images.githubusercontent.com/97727617/176667857-d2da6394-ead2-427c-8e44-e7108abe95c6.png)

 
(3)	Discriminator:-
![image](https://user-images.githubusercontent.com/97727617/176667881-8b8e476c-e01a-43f0-85ac-8ecd13f0c48f.png)

 
(4)	Model Initialization:-![image](https://user-images.githubusercontent.com/97727617/176668100-a7102748-8a47-45b4-b38b-7a444e63af2d.png)



FIND ATTACHED REPORT
References:

Original paper on Image-to-Image Translation (using U-Net generator & PatchGAN discriminator)
by Berkeley AI Research (BAIR) Laboratory, UC Berkeley
https://arxiv.org/pdf/1611.07004.pdf
For GANs (Introduction, GANs, C-GANs, Algorithm, etc.)
https://jonathan-hui.medium.com/gan-whats-generative-adversarial-networks-and-its-application-f39ed278ef09
https://jonathan-hui.medium.com/gan-cgan-infogan-using-labels-to-improve-gan-8ba4de5f9c3d

