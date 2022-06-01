---
layout: post
title: A Failed Experiment with a Carousel
categories:
- Experiments
excerpt: |
    When trying to make an inline configuration carousel, I realized while it's a great idea in a UIView, it's a dumb idea in AR
feature_image: "/Resources/IMG_0351.jpg"
---

When trying to make an inline configuration carousel, I realized while it's a great idea in a UIView, it's a dumb idea in AR.

So I was trying to recreate the experience in my [previous post](https://arplaykit.com/experiments/2019/02/13/3D-carousel/) in AR. I drew a crappy picture to show what I was trying to accomplish
{% include figure.html image="/Resources/IMG_0351.jpg" alt="Drawing of carousel under vase" %}
I realized that using the chair in the example would be very difficult as it's a big chair and where would I put the carousel? That should have given me a clue, ugh. I swapped out the model with a vase given in [Apple's Quick Look gallery](https://developer.apple.com/arkit/gallery/) to try and make it a bit more manageable. I even implemented a custom UICollectionViewLayout to shrink non-focused cells (seen in the video below).

<iframe width="640" height="564" src="https://player.vimeo.com/video/324952116" frameborder="0" allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>

Alas, as I struggled with it, I eventually came to the conclusion that this wasn't going to work. Even with the shrinking cells, the carousel would need to be huge to fit the model. This is the vase on my desk in AR
{% include figure.html image="/Resources/IMG_0350.jpg" alt="AR Vase on desk" %}

In AR, realistic models like the chair and vase need to be real-world sizes and especially with a limited window of a phone screen, you can't expect a user to wave their phone around to see that a model has a carousel to change its color. That field of view will get bigger with AR glasses/goggles but even then, what if you were looking at a car? (Excuse my terrible Photoshop skills)
{% include figure.html image="/Resources/carCarousel.jpg" alt="Diagram of AR carousel under car" %}
Your field of view would be about the green rectangle and the carousel could span the red rectangle on the ground. You can't be expected to swivel your head to see all the options in the carousel, configurations like this should be easy to view so you can choose your option quickly

I would still like to make a color picker 'attached' to the model in 3D space instead of a 2D collectionView stuck in a corner. Hopefully I can get it right in the next post