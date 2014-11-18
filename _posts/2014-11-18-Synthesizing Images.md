---
layout: post
title: Synthesizing Images
---

It's been two weeks since I've posted. Opps! Last week I was in Paris for InfoVis, including presenting my research on [Visualizing Statistical Mix Effects and Simpson's Paradox](http://research.google.com/pubs/pub42901.html). But, more on that later. For now, just want to dive back into class, Open Frameworks, and this week's topic of synthesizing images.  

The goal was to create an empty greyscale image, and use functions to write to it's pixels in memory.  

```
  for (int i = 0; i < myImg.getWidth(); i++){
        for (int j = 0; j < myImg.getHeight(); j++){
            pixels[ (int)(j * 800 + i)] = sin(i * j)  * 178.0 + 178.0;
        }
    }
```

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416242475748_Screen%20Shot%202014-11-17%20at%2011.39.45%20AM.png)
