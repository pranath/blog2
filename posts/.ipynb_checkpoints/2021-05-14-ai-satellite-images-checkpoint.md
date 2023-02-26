---
aliases:
- /opinion/2021/05/14/ai-satellite-images
categories:
- opinion
date: '2021-05-14'
description: Many of the greatest challenges the world faces today are global in nature,
  AI and satellite images is a powerful technology that holds huge potential for helping
  us solve many problems we face.
image: https://github.com/pranath/blog/raw/master/images/sat6.jpg
layout: post
title: An Eye in the Sky - How AI and Satellite Imagery can help us better understand
  our changing world

---

## Introduction

Many of the greatest challenges the world faces today are global in nature, climate change being one of the clearest examples. While we also have huge amounts of data of different kinds, trying to make sense of all this data to help us make better decisions can be a significant challenge in itself when attempted by humans alone. AI is a powerful technology that holds huge potential for helping us use this data more easily, to help us make better decisions for the problems we face.

In the water industry where I work, satellite image data and AI holds great potential for helping solve a number of problems, such as the [detection of leaks](https://earthi.space/press/severn-trent-water-enlists-earth-i-to-identify-and-combat-water-leaks-using-sophisticated-data-analytics-from-satellite-imagery/), [water resource management](https://www.devex.com/news/how-satellite-images-could-improve-water-management-in-africa-96807) to ensure on ongoing water supply accounting for changes in population and climate change, [water quality monitoring](https://jncc.gov.uk/media/4681/eo4water_resources_website_final.pdf), and [flood protection](https://reliefweb.int/report/world/fusing-ai-satellite-image-analysis-inform-rapid-response-floods-un-global-pulse).

Beyond the water industry, satellite images and AI are working together to provide critical insights in many diverse areas such as [disaster response and recovery](https://development.asia/insight/how-ai-can-boost-disaster-response-and-recovery), [the discovery of hidden archaeological sites](https://scitechdaily.com/discovering-hidden-archaeological-sites-with-ai-and-satellite-images/), [city infrastructure monitoring](https://development.asia/insight/using-artificial-intelligence-city-infrastructure-monitoring), [combating illegal fishing](https://news.microsoft.com/on-the-issues/2019/06/06/ocean-mind-illegal-fishing/), and [predicting crop yields](https://www.theverge.com/2016/8/4/12369494/descartes-artificial-intelligence-crop-predictions-usda).

But how does this technology work? and can you understand the basics of how it works without any technical knowledge? The answer is I believe yes, and I will try to illustrate this by describing a recent project I completed using this approach.

## Using AI to automatically recognise Woodlands and Water areas

In a recent project, I used satellite imagery from Poland to train an AI to automatically recognise areas in the images such as woodlands and water. So AI is just about throwing some data at it and some magic happens? Actually not quite! This is a common myth about how AI actually works. 

![](https://github.com/pranath/blog/raw/master/images/sat1.png "Satellite images with different regions, seasons, time of day, weather, lighting conditions, etc.")

The key requirement for using AI is not just using any data, but something called labelled data. **Labelled data** is data that has been tagged with one or more labels that describe things inside the data. So in this project, the labels used for these satellite images were woodlands and water: if an image contains one of these things, the image would have a label or tag for that. This is how the AI learns, it looks at each satellite image, see's which labels it has, and tries to learn what in the image indicates each label. So it's not really magic how an AI learns at all, an AI just learns from examples of labelled things - that's it basically.

Here are some more examples of the satellite images, now with labels. The labels are colours filled in, so for example water areas are coloured in pink and woodland areas in red.

![](https://github.com/pranath/blog/raw/master/images/sat2.png "Satellite images with label colouring")

How do these images get their coloured labels? well some poor human has to painstakingly spend hours carefully colouring them all in with the right colours. But its well worth it, since we can train the AI to use these labelled satellite images (just 33 images) to learn to recognise these things in them, and once it can do this, we can then use the AI to recognise these things in new satellite images, as many times as we like. This is the real power of AI systems, which can learn to do things only humans could previously do, and then do them far more efficiently and quickly than a human could ever do, millions of times, without needing even a coffee break!

So how well does the AI learn to recognise these things? after running the training process a while, these are some of the results I got when I tested the AI on images it had never seen. Here the 'Target' on the left are the labels for images the AI has never seen, and the 'Prediction' on the right are what the AI thinks the label colour areas should be in the image.

![](https://github.com/pranath/blog/raw/master/images/sat3.png "New satellite image targets to test our AI on the left, which makes predictions on the right")

So I'd say the AI has done a pretty good job. You can see in these examples it seems to have recognised the correct water areas (in pink) and woodland areas (in red) pretty well? The AI was only trained for a limited time, most likely if I had trained it for longer it would have done even better. I could now use this AI on any new satellite images, and know it would do quite well at recognising woodland and water areas fairly accurately. Because the labels here are actually coloured dots on the image, we could add up all the dots for water or woodland on an image and get a fairly accurate measure for how much water or woodland there was there.

Just imagine what we could do with even this fairly simple AI. For example, we could use it to estimate the woodland and water areas of different parts of a country quite accurately, anywhere in the world. If we took different satellite photos of the same area over time, we could estimate how the water or woodland areas were changing over time, and by how much, all automatically. The possibilities are endless.

## Conclusion

In this article I've introduced how satellite images and AI are a powerful new technology being used to provide valuable insights to a range of different challenges and tasks we face in the world today. By describing my own project using AI to recognise woodland and water areas in satellite images, I hope I have given you a better understanding of how this technology actually works, and of its huge potential for humanity.
