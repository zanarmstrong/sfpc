---
layout: post
title: Synthesizing Images Part II
---

Continuing on the path of Sythesizing images, this time using noise functions to help make it look more organic.

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416330395405_Screen%20Shot%202014-11-18%20at%2011.24.44%20AM.png)

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416330591308_Screen%20Shot%202014-11-18%20at%2012.09.17%20PM.png)

Code snippet: 

int val = ofNoise( i / 50.0, j / 50.0) * ofNoise( i / 500.0, j / 500.0) * 2000 + 1;
            if(rand() % val < 2) {
                        pixels[ (int)(j * w + i)] = 255 - rand() % 200;
                        } else {
                        pixels[ (int)(j * w + i)] = 0;
}

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416336453011_Screen%20Shot%202014-11-18%20at%201.45.38%20PM.png)

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Sj61nBYJxjG_p.232391_1416336453000_Screen%20Shot%202014-11-18%20at%201.46.43%20PM.png)


Code snippet: 
            int val = ofNoise( i / 200.0, j / 200.0) * ofNoise( i / 100.0, j / 100.0) * 2000 + 1;
            
                if(rand() % val < 2) {
                        pixels[ (int)(j * w + i)] = 255 - rand() % 200;
                    } else {
                        pixels[ (int)(j * w + i)] = 0;
                    }


