---
layout: post
title: Sarah's revelation - dictionaries, D3, and attributes
---

Sarah told me today that instead of defining attributes in D3 like this: 

{% highlight javascript %}
var k = svg.selectAll(".squares")
           .data(setUpRandData())
           .enter()
           .append('rect')

k.attr("x", function(d) {
          return d.x * sideLength;
  })
  .attr("height", sideLength)
  .attr("y", function(d) {
          return d.y * sideLength;
  })
  .attr("width", sideLength)
  .attr("class", 'squares')
{% endhighlight %}

You can use a dictionary to hold the attributes, and define them like this:

{% highlight javascript %}// define attributes for rectangles using a dictionary
var squareAttr = {
	"x": function(d) {return d.x * sideLength;},
	"y": function(d) {return d.y * sideLength;},
	"height": sideLength,
	"width": sideLength,
	"class": 'squares'
};

// apply the attributes from the dictionary to the rectangle
svg.selectAll(".squares")
	.data(setUpRandData())
	.enter()
	.append('rect')
	.attr(squareAttr);
{% endhighlight %}

Example of this in practice [here](http://bl.ocks.org/zanarmstrong/73ce430053eabd1b70fe).

So nice!
