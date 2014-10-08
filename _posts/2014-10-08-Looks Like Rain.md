---
layout: post
title: Looks Like Rain
---

On Monday Ramsey asked us to go to [Great Art Twitter bot](https://twitter.com/greatartbot), choose an image, and describe in text how you might recreate it.  

I liked this image because I thought it looked like rain. 

![](http://bl.ocks.org/zanarmstrong/raw/73ce430053eabd1b70fe/image.png)

Having a little fun, I wrote [an example in D3](http://bl.ocks.org/zanarmstrong/raw/73ce430053eabd1b70fe) to create images in the same style. Each time you refresh or click on the text you can get a new image. 

![](https://lh5.googleusercontent.com/-yChWslkKZq8/VDVmYgs1ELI/AAAAAAAAYbc/Uku0BVFgeSo/w462-h595-no/likerain.png)

I would like to update the algorithm for randomness, so that it tends towards a mean rather than being a random walk. Currently I'm using essentially randon walk on which I've put constraints so that the switch between greyscales doesn't stray too high or too low. But, there must be much better algorithms for this.
