---
layout: post
title: First Tasks for Learning Javascript & D3
---

### Small Tasks that "Scaffold"
Last night in Amit's class on learning and teaching code, we discussed the role of "small tasks" or "puzzles" as an early stage of learning to code. 

### Martin's Challenges
Last year when I was working with Google's Big Picture Data Viz research team in Cambridge, Martin Wattenberg helped me learn Javascript by posing a few small challenges. It was a fantastic way to learn, as I really started to understand what was going on in the DOM (Document Object Model) and how I could use Javascript to control the SVG elements. I also started to see how I could use trigonometry and math to define the object's properties efficiently. And, when I started to bring in functions from D3 it was to gain efficiency/control and felt like the solution rather than confusing magic.

I documented some of the process at the time, so have included links to those posts. Unfortunately some of the image links in the posts seem to have broken (Wordpress weirdness?), but I was able to fix many of them.

### Small Steps to Learning Javascript/D3
First: [draw a smily face using SVG](http://learningdynamicdataviz.wordpress.com/2013/07/23/documenting-my-journey-learning-dynamic-visualization-on-the-web-svgjavascripthtmlcssd3-step-1-draw-a-smily-face/). 

Second: do the same, but [use Javascript to control the SVG](http://learningdynamicdataviz.wordpress.com/2013/07/23/learning-2-create-smiley-using-javascript-to-create-the-svg-objects/).  

At this point, I took a detour into [creating polygons of arbitrary types](http://learningdynamicdataviz.wordpress.com/2013/07/23/learning-3-twinkle-those-stars-or-not/) and making them spin because I wanted my smily face to have spinning stars for eyes. More steps [here](http://learningdynamicdataviz.wordpress.com/2013/07/23/star-algorithm-as-i-still-cling-to-r/) & [here](http://learningdynamicdataviz.wordpress.com/2013/07/23/star-algorithm-built-out-using-javascript-to-define-the-svg-elements/) & [here](http://learningdynamicdataviz.wordpress.com/2013/07/23/putting-it-all-together/).

Third: use Javascript (no D3) to create a bar chart, aka - draw lots of rectangles :). Blog posts [one](http://learningdynamicdataviz.wordpress.com/2013/07/24/next-up-bar-charts-histograms-w-generated-data/), [two](http://learningdynamicdataviz.wordpress.com/2013/07/24/bars-step-1-creating-random-data/), [three](http://learningdynamicdataviz.wordpress.com/2013/07/24/bars-step-2-learning-from-the-web/).

From there I made a [histogram](http://learningdynamicdataviz.wordpress.com/2013/07/25/histogram-success/), [learned to read in real data](http://learningdynamicdataviz.wordpress.com/2013/07/30/reading-in-real-data/), and [highlighting days of the week](http://learningdynamicdataviz.wordpress.com/). A bit later, I started playing with [colors](http://learningdynamicdataviz.wordpress.com/2013/08/16/color-interpolation/) and building in [more and more D3](http://learningdynamicdataviz.wordpress.com/2013/08/23/transitions-update-in-d3/).

### Looking Back
Looking back,it makes me smile to re-read this progression and see how nice it was to celebrate the small successes. Small steps, put together, really can take you a long way :). 

Since then I've made a fully fledged analysis tool in D3/javascript hosted on AppEngine shown in Figure 10 of [this research paper](http://research.google.com/pubs/pub42901.html). I also now feel like I can ["sketch" in Javascript and D3](http://bl.ocks.org/zanarmstrong) in a way that seemed hard to imagine a year ago. While it might have been faster to take examples and adapt them, I'm so glad that I took the time to start from the basics because I understand what D3 is manipulating, because I worked through the tedium of drawing element by element. I feel like I can build what I sketch on paper instead of being constrained to what others have done.
