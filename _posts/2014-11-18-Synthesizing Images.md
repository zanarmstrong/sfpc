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

I started to play with this basic formula: 
```
(i - j)*(i+j);
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416251264520_Screen%20Shot%202014-11-17%20at%202.06.34%20PM.png)

```
(i/2.0 - j/2.0 + 5)*(i/3.0+j/1.0 + 100);
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416252757864_Screen%20Shot%202014-11-17%20at%202.32.12%20PM.png)

```
k = rand() % 30 - 15;
pixels[ (int)(j * myImg.getWidth() + i)] = (i/10.0 - j/10.0 + 5)*(i/10.0+j/10.0) + k;
```

Andrew described this one as "harvest the noise."

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416253354882_Screen%20Shot%202014-11-17%20at%202.42.02%20PM.png)

```
     k = rand() % 80 - 40;
      pixels[ (int)(j * myImg.getWidth() + i)] = (i/10.0 - j/10.0 + 5)*(i/10.0+j/10.0) + k;
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416253433442_Screen%20Shot%202014-11-17%20at%202.43.05%20PM.png)

```
  unsigned char * pixels = myImg.getPixels();
    float w = myImg.getWidth();
    
    for (float i = 0; i < myImg.getWidth(); i++){
        for (float j = 0; j < myImg.getHeight(); j++){
            k = rand() % 100;
            float norm = 255.0 / w;
            pixels[ (int)(j * w + i)] = i * norm + j * norm + k ;
        }
    }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416253818031_Screen%20Shot%202014-11-17%20at%202.49.54%20PM.png)

Playing with only showing the brightest of the colors, but also lost the ones that were bright but negative (and wrapped around).  

```
float w = myImg.getWidth();
    
    for (float i = 0; i < myImg.getWidth(); i++){
        for (float j = 0; j < myImg.getHeight(); j++){
            k = rand() % 40;
            float norm = 255.0 / w;
            bool z = (int)((i - j)*(i+j)) % 255 > 220;
            if(z){
                pixels[ (int)(j * w + i)] = (i - j)*(i+j);
            } else {
                pixels[ (int)(j * w + i)] = 0;
            }
        }
    }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416254341490_Screen%20Shot%202014-11-17%20at%202.58.22%20PM.png)

And, this brings it back...

```
  k = rand() % 40;
            float norm = 255.0 / w;
            bool z = (int)((i - j)*(i+j))% 255 < -230 ||(int)((i - j)*(i+j))% 255  > 230  ;
            if(z){
                pixels[ (int)(j * w + i)] = (i - j)*(i+j);
            } else {
                pixels[ (int)(j * w + i)] = 0;
            }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416255179411_Screen%20Shot%202014-11-17%20at%203.12.36%20PM.png)

The last challenge was to start creating something that looked organic, even though defined by functions. Here is an early attempt at a star field. 

``` 
  if(rand() % 500 < 1) {
                pixels[ (int)(j * w + i)] = 255;
            } else {
                pixels[ (int)(j * w + i)] = 0;
            }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416282367555_Screen%20Shot%202014-11-17%20at%2010.44.25%20PM.png)

And, here it varies the brightness by varying the greyness. 

```
 if(rand() % 500 < 1) {
                pixels[ (int)(j * w + i)] = 255 - rand() % 200;
            } else {
                pixels[ (int)(j * w + i)] = 0;
            }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416282556159_Screen%20Shot%202014-11-17%20at%2010.48.48%20PM.png)
