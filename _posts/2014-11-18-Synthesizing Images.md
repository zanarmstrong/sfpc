---
layout: post
title: Synthesizing Images
---

It's been two weeks since I've posted. Opps! Last week I was in Paris for InfoVis, including presenting my research on [Visualizing Statistical Mix Effects and Simpson's Paradox](http://research.google.com/pubs/pub42901.html). But, more on that later. For now, just want to dive back into class, Open Frameworks, and this week's topic of synthesizing images.  

The goal was to create an empty greyscale image, and use functions to write to it's pixels in memory. I started with an 800x800 image. I used a 2-d for loop (i for width and j for height) to define the pixels, as shown below. 

```
  for (int i = 0; i < myImg.getWidth(); i++){
        for (int j = 0; j < myImg.getHeight(); j++){
            pixels[ (int)(j * 800 + i)] = sin(i * j)  * 178.0 + 178.0;
        }
    }
```

The key thing that changes from image to image is the function used to define the color of each pixel.  In this case, it's: 

```
sin(i * j)  * 178.0 + 178.0;
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416242475748_Screen%20Shot%202014-11-17%20at%2011.39.45%20AM.png)

This example takes input from the mouse location:

```
pixels[ (int)(j * 800 + i)] = (i - mouseX) * (j - mouseX) / 5.0;
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416242568872_Screen%20Shot%202014-11-17%20at%2011.42.34%20AM.png)

This example also takes input from the mouse, seemingly revealing only a circle with radius 200px around the mouse like a flashlight.  

```
       float distance = ofDist(i, j, mouseX, mouseY);
            if(distance < 200){
                pixels[ (int)(j * myImg.getWidth() + i)] = sin((i + j + 1) / 20.0) * 178.0 + 178.0;
            } else {
                pixels[ (int)(j * myImg.getWidth() + i)] = 0;
            }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416243461210_Screen%20Shot%202014-11-17%20at%2011.57.02%20AM.png)

Playing with sin & cos:

```
      pixels[ (int)(j * myImg.getWidth() + i)] = sin((i +1) / 50.0) * 100.0 + cos((j +1) / 40.0) * 100.0 + 150.0;
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416244060816_Screen%20Shot%202014-11-17%20at%2012.07.08%20PM.png)

