---
layout: post
title: Testing that something fails if it's supposed to
---

This week's homework for [Ramsey's class](http://radicalcomputerscience.tumblr.com/) is to take a "language" that doesn't work and add grammer statements until it does. Examples are given with the desired output, and our job is to set up a grammer such that the output comes through correctly. 

To add some context, Ramsey has written a [tool](https://github.com/nasser/pltjs) in Javascript called plt.js which "is an environment for writing and testing programming language grammars." It "compiles" your new language into Javascript based on the grammars you've defined.

From a learning perspective, we generally take for granted that the computer can interpret what we write and somehow do something with it. But, at some point the text we write must be translated into something at a higher level that can be interpreted. By building up a grammar, and later building up our own grammars, to define a language we have to engage with the idea of programming from the level of intepreting a string of text. 

The most interesting part of this exercise was when I accidentally tested something that shouldn't have worked, and still got an output. For example, I meant to type (+ (* 2 3) 10) but instead typed (+ (2 * 3) 10). I forget now what answer I got, but it definitely wasn't the 16 that I'd meant to get. What had happened is that I'd let my algorithm be too generous in either reading or ignoring parenthesis. Because of this, it was operating on numbers in quite unexpected ways when it should have instead thrown an error. I went back to the grammar and found a way to be more strict, to ensure that my parenthesis evaluated in pairs. 

The take home message is that it's important that, in addition to checking that the things we want to happen actually work, **it's also valuable to check that things that *should fail* actually do.** 
