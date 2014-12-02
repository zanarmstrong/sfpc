---
layout: post
title: Opening a link from a data visualization
---

Love that [Sarah's D3 scatterplot example](https://github.com/sarahgp/cuny-examples) shows how easy it is to click to open a relevant URL from within a data visualization.  The scatterplot shows some meta data about Van Gogh's paintings, and if you click on the dot you're redirected to an image search result for that painting.  The visualization was designed as a tutorial rather than a finished work in order to demonstrate some of what is possible with D3, the internet, and dataviz.  

The relevant snippet is: 

```.on('click', function(d){
        window.open('https://www.google.com/search?site=imghp&tbm=isch&q=van+gogh+'+d.Title);
});```
