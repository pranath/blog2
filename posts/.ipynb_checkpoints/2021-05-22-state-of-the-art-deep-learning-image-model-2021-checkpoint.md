---
aliases:
- /deep-learning-theory/2021/05/22/state-of-the-art-deep-learning-image-model-2021
categories:
- deep-learning
date: '2021-05-22'
description: In this article we are going to look at some of the most advanced techniques
  available in 2021 for training deep learning vision models.
image: https://github.com/pranath/blog/raw/master/images/deep1.jpg
layout: post
title: State-of-the-art Deep Learning image model techniques in 2021
toc: true

---

## Introduction

In this article we are going to look at some of the most advanced techniques available in 2021 for training deep learning vision models. These go beyond the basics of mini-batch gradient descent, learning rates, pre-sizing, transfer learning, discriminative learning rates, and mixed-precision training.

## Library and Dataset

I will be using the [fastai](https://www.fast.ai) deep learning library for code examples, as well as the fastai curated *Imagenette* dataset which is a specially curated subset of the well known ImageNet dataet of 1.3 million images from 1,000 categories. The Imagenette dataset consists of a much smaller set of images and just 10 categories.

We will define a baseline model here using the dataset to then compare the effect of each advanced technique.

## Normalisation

When training a model, its helpful to ensure the image data is normalised. This ensures that different images end up with data that is in the same range of values, which helps the model better focus more on the content on the images. So here by normalised we mean we want the image data values to have a mean of 0 and a standard deviation of 1.

The fastai library will automatically normalise images per batch, and this is suitable for models that we might train from scratch. When using transfer learning this default approach is not a good idea, because a pre-trained model has been trained on image data with a particular mean and standard deviation. So to use a pre-trained model with new images, we need to ensure these new images are normalised to the same mean and standard deviation that the original model data was trained with.

We can do this my specifying normalisation stats in fastai, which already knows the stats for many common datasets, including of course fastai's own Imagenette dataset which makes it much easier.

We can also define a function **get_dls()** which will make it quicker to define different types of data loader i.e. with different batch or image sizes.

After applying our normalisation, we can see the mean and standard deviation are approximatly 0 and 1 respectively on a test batch of images.

Lets now try this normalised data and train our model.

While normalisation here hasn't made a huge improvement over our baseline model, normalisation does make a bigger difference especially with bigger models and more data.

## Progressive resizing

Progressive re-sizing is another technique pioneered by fastai. Essentially this involves training models on smaller versions of the images first, before continuing training on bigger images. This has 2 major benefits:

- Model training time is much faster
- Model accuracy ends up better than if we trained the model only on bigger images

How can this be the case? lets remember that with convolutional deep learning models, early layers focus on recognising primitive features like lines and edges, and later layers more composite features such as eyes or fur. So if we change the image size during training, our earlier model will still have learnt many useful things applicable to bigger and higher resolution images.

In a way, this is a bit like training a model in one area then re-using that model on a similar area - which might sound familiar? As it should since this is very much what transfer learning is about as well, which works very well. So we should perhaps not be so surprised that this could work.

Another benefit of using lower resolution/smaller versions of the images first is that this is another kind of data augmentation - which should also help our models generalise better.

So lets use our *get_dls()* function that we defined earlier to define a data loader for our smaller lower resolution images and train the model for a few epochs.

We will then define a new data loader for bigger images, and continue to train our model with these.

So we can see we are already getting much better results than our baseline with just a few epochs, and much more quickly. It's worth considering for the desired task, if transfer learning can in some cases harm performance. This might happen for example if the pre-trained model is trained on images already quite similar to the new ones you want to recognise - as in this case the model parameters are likely already quite close to what is needed, and progressive resizing could move the parameters further away from this and good results. If the use case for the pre-rained model is very different to what it was originally trained on i.e. very different sizes, shapes, styles etc - then progressive resizing here might actually help.

In either case, trying things experimentally would probably be the best way to determine which was the better approach.

## Test time augmentation

Training time data augmentation is a common technique to help improve model training by providing different versions of the same images to improve the way the model generalises and with less data. Common techniques include random resize crop, squish, stretch, and image flip for example.

Test time augmentation (TTA) is an interesting approach of using augmentation when using the model for inference. Essentially at inference time for a given image, different augmentations of the same image will be predicted on by the model, then we can use either the average or maximum of these versions as a measure of model performance. This can give us a better idea of the models true performance, and often results in improvements in performance.

In the fastai library its quite easy to apply TTA.

While this does not add any extra time to training, it does make inference slower.

## Mixup

Mixup is a technique introduced in the paper [mixup: Beyond Empirical Risk Minimization](https://arxiv.org/abs/1710.09412) by Hongyi Zhang et al. It's a powerful data augmentation technique that seeks to address the weaknesses of many previous methods such as crop-resize, squishing etc. One of the key drawbacks to previous approaches was needing some expert knowledge of when those techniques were applicable or nor as well as how to apply them.

For example, take the flip method that augments by flipping the image vertically or horizontally - should one apply that one way or the other? it will probably depend on the kind of images you have. Also flipping is limited i.e. you can just apply it one way or the other, there are no 'degrees of flipping' for example. Having 'degrees of' or gradation of augmentation can be very useful for giving the model a rich variety of images along the spectrum to allow it to better learn and generalise.

Mixup essentially takes two images and combines them, with a randomly selected weight of transparency for each image for the combined image. We will then take a weighted average (using the same random weights) applied to the labels of each image, to get the labels for the mixed image.

So the combined image will have labels that are in proportion to the amount of each original image.

Here the third image is built from 0.3 of the first one and 0.7 of the second one. The one-hot encoded labels for the first and second images and final mixed image would be say:

- Image 1: [0, 0, 1, 0, 0, 0, 0, 0, 0, 0]
- Image 2: [0, 0, 0, 0, 0, 0, 0, 1, 0, 0]
- Mixed:   [0, 0, 0.3, 0, 0, 0, 0, 0.7, 0, 0]

We can use this Mixup technique in the fastai library in the following way.

This model is likely going to be harder and longer to train, for all the many examples 'in between' that this method will generate, but it should allow the model to generalise better. The beauty of this approach is that unlike many previous approaches this doesn't require extra knowledge about the dataset to use - the 'appropriateness' of each image is present in the augmentation - so its the degrees of which we vary here really. This also opens this method to use in other areas beyond even vision models, to NLP for example.

Mixup also helps with another problem. A 'perfect' dataset with perfect labels say of only 1 and 0, pushes the model to train towards a sense of 'perfection' and absolute confidence, this is of course the ideal that the cross-entropy loss function does well to optimise for. By removing 'perfection' from our labels, we force our model to train to become less absolutely confident in its predictions, we train it to become more nuanced and subtle in its predictions that err towards partial than perfect probabilities for label prediction.

## Label smoothing

Deep learning vision models train for perfection, this is especially due to the nature of the most common classification loss function cross-entropy loss. For example, because our labels are often perfect i.e. 1 or 0 despite how perfect the expression of that label is in the image, the model will keep pushing for the perfection of 1 or 0 i.e. even 0.999 will not be good enough. This can lead to overfitting, and is a consequence of this kind of training and loss function. In practice, images often do not conform to the perfection of the labels assigned them.

With **label smoothing** rather than use perfect labels of 1 and 0, we use a number a bit less than 1 and a number a bit more than zero. By doing this we encourage our model to become less confident, more robust (e.g. if there is mislabelled data). This model should generalise better. This technique was introduced in the paper [Rethinking the Inception Architecture for Computer Vision](https://arxiv.org/abs/1512.00567) by C Szegedy et al. .

We can use this technique in the fastai library in the following way.

As with Mixup, you generally won't see significant improvements with this technique until you train more epochs.

## Conclusion

In this article we have covered 5 state-of-the-art techniques for training deep learning vision models using the fastai deep learning library, each of which can significantly help produce the best results currently possible for vision models in 2021.
