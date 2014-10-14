---
layout: post
title: Day 10 - Grace Hopper was Right
---

For Ramsey's class on programming languages, we were asked to play around with the language [Brainfuck](http://copy.sh/brainfuck/). 

Goals included:

    Write out your name
    Print out the numbers from 1 to 10
    Print out the numbers from 1 to 99
    Write out 99 bottles of beer on the wall
    Make a game

In each one, try and make your code as short as possible!


Goal #1: Write my name (Zan)
-[--->+<]>+++++.>-[--->+<]>++++++++++++.>-[--->+<]>+++++++++++++++++++++++++.
or
-[--->+<]>+++++.+++++++.+++++++++++++.

I can even write ZanArmstrong, although I've never before appreciated how so many of the letters in my last name are close to each other in the alphabet. 
-[--->+<]>+++++.+++++++.+++++++++++++.>----[--->+<]>-------------------.<<++++.-----.++++++.+.--.---.-.-------.

That wasn't so terrible. 

I noticed that this pattern writes a letter, and then steps ahead to a new spot in memory. 
-[--->+<]>+++++.>

And, this pattern uses one spot to catch the 0 and end the loop, and the other spot to keep track of the current value. 
[--->+<]

Next goal: write the numbers 1 through 10. 
-[----->+<]>--.+.+.+.+.+.+.+.+.--------.-.

If you're near the right place in the ascii, using + and - along with . is useful. 

Goal: Count from 1 to 100. 

Ouch!  That got painful fast. 

I managed to count from 1 to 30, but not in a pretty way. Using loops seems arbitrary. Perhaps could test a bunch of loops to see where they escape to. 
-[----->+<]>--.+.+.+.+.+.+.+.+.--------.-.>-[----->+<]>--.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>+.<<---------->>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>+.

All in all, this experience makes me really appreciate Grace Hopper's insight that code would be much better if the command language was relatively human readable!
