---
layout: post
title: Reordering Pixels
---

I played with reordering pixels in an image based on their brightness or color. It's not particularly novel, but I thought it would be fun. 

I started with black/white/grey images since ordering on a greyscale is straightforward while ordering color is not. 

The first attempt reordered horizontally, as shown below and in the code [here](https://github.com/zanarmstrong/open-frameworks-sketches/tree/master/reorderGreyPiexles). 

![](https://lh4.googleusercontent.com/-O-JjIy74UHo/VHEFjlAkUHI/AAAAAAAAaEA/R9rlqHvLiAo/w1118-h385-no/Screen%2BShot%2B2014-11-22%2Bat%2B4.51.47%2BPM.png)

and

![](https://lh3.googleusercontent.com/-t3H27xqO6gw/VHEF-FA1qyI/AAAAAAAAaEQ/3-P-TJUBHr0/w922-h460-no/Screen%2BShot%2B2014-11-22%2Bat%2B4.53.39%2BPM.png)

However, I thought a circle would be more appealing. Implementing this was non-trivial, as I had to figure out how to assign the ordered colors into a spiral in the final image. 

It was tempting to try to figure out how to map the i<sup>th</sup> color in the ordered color list to some particular x/y coordinate in the final image. Instead, I ended up ordering the x/y coordinate pairs in the final image based on "spiral order." Then I used a for loop to go through the color list and assign each color to the matching element in the sorted vector of x-y pairs. This way I never needed to figure out a mapping to a particular pixel, but rather just match up each color and pixel in order. 

This code shows how I created and walked through the color list. 

```
    vector <int> colors;
    
    for (int i = 0; i < width * height; i++){
        colors.push_back(pixOrig[i]);
    }

    ofSort(colors);

    // create a vector of all pixels, and sort them by spiral order from center
    vector <ofVec2f> coords;
    
    for (int i = 0; i < width; i++){
        for (int j = 0; j < height; j++){
            // redefine coordinates from center for sorting, note the offset needed for the center
            coords.push_back(ofVec2f(float(i) - width / 2,float(j) - height / 2));
        }
    }
    
    // sort the ordered pairs of pixels into a spiral, using function declared above
    ofSort(coords, orderPixels);
    
    // walk through the vector of ordered pixels and assign colors in order
    for (int i = 0; i < colors.size(); i++){
        ofVec2f k = coords[i];
        pixFinal[int((k.y + height/2) * width + (k.x + width/2))] = colors[i];
    }
```

And, this is the sorting function "orderPixels" which was used to sort the vector of ordered pairs of coordinates. 

```
bool ofApp::orderPixels(ofVec2f a, ofVec2f b){
    // goal: return true if a > b
    
    // check if radius a is larger than radius b, using pythagorian theorem
    if(sqrt(a.x * a.x + a.y * a.y) > sqrt(b.x * b.x + b.y * b.y) + 1){
        return true;
    //check if radius b is larger than radius a
    } else if (sqrt(a.x * a.x + a.y * a.y) + 1 < sqrt(b.x * b.x + b.y * b.y)){
        return false;
    // if the radius is within 1, check the angles
    } else {
        // both points below midpoint?
        if(a.y < 0 and b.y < 0){
            // and further left?
            if(a.x < b.x){
                return true;
            } else {
                return false;
            }
        // both points above midpoint?
        } else if(a.y > 0 and b.y > 0){
            // and further right?
            if(a.x > b.x){
                return true;
            } else {
                return false;
            }
        // one point above midpoint, and the other below?
        } else if(a.y > b.y){
            return true;
        } else {
            return false;
        }
    }
}
```

The rest of the code is [here](https://github.com/zanarmstrong/open-frameworks-sketches/tree/master/reorderGreyPixelsCircle).

The result is this: 

![](https://lh3.googleusercontent.com/-M-EDQtc9N24/VHJvfQjlXwI/AAAAAAAAaGc/s0VsfkpK-lc/w917-h457-no/Screen%2BShot%2B2014-11-23%2Bat%2B6.29.52%2BPM.png)

and 

![](https://lh6.googleusercontent.com/-LKXKKdH6scg/VHJvftUKipI/AAAAAAAAaGo/nm7HJStBhZ0/w1118-h384-no/Screen%2BShot%2B2014-11-23%2Bat%2B6.30.17%2BPM.png)

and 

![](https://lh3.googleusercontent.com/-okMJ1TvFrxc/VHKkD8Q03lI/AAAAAAAAaH4/i0gno38c-cA/w1117-h413-no/Screen%2BShot%2B2014-11-23%2Bat%2B10.18.46%2BPM.png)

and 

![](https://lh5.googleusercontent.com/-CbQMqWkkjWg/VHKkD-6yzfI/AAAAAAAAaH0/8L3s4iwtfY0/w986-h300-no/Screen%2BShot%2B2014-11-23%2Bat%2B10.19.48%2BPM.png)

I also played with reversing the order: 

![](https://lh3.googleusercontent.com/-ZnjmtmMnAv4/VHKoCXJA70I/AAAAAAAAaIQ/S3MoyGv6TfY/w986-h304-no/Screen%2BShot%2B2014-11-23%2Bat%2B10.36.15%2BPM.png)

and 

![](https://lh4.googleusercontent.com/-Lm6b0kdSHTQ/VHKoClwwCBI/AAAAAAAAaIc/bhYY4kQMYrI/w921-h462-no/Screen%2BShot%2B2014-11-23%2Bat%2B10.36.56%2BPM.png)

Next up will be defining functions to order color. This harkens back in a way to the [color interpolation tests I did in D3/JS](http://bl.ocks.org/zanarmstrong/raw/c0f07275634de1f12769/) last year.  

