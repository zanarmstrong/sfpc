---
layout: post
title: Day 10 - Grace Hopper was Right
---

For Ramsey's class on programming languages, we were asked to play around with the language [Brainfuck](http://copy.sh/brainfuck/). As described on [Wikipedia](http://en.wikipedia.org/wiki/Brainfuck), Brainfuck has only 8 commands which are represented with simple symbols. There is a concept of loops, but you only escape the loop when the byte your pointer is pointing at is equal to 0. 

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

I could even write ZanArmstrong, although I've never before appreciated how so many of the letters in my last name are close to each other in the alphabet. 

    -[--->+<]>+++++.+++++++.+++++++++++++.>----[--->+<]>-------------------.<<++++.-----.++++++.+.--.---.-.-------.

That wasn't so terrible. 

In genearl I found that this pattern writes a letter, and then steps ahead to a new spot in memory. Adding + or - after the ]> allows you to change which letter you're printing out. 

    -[--->+<]>+++++.>

This pattern uses one spot of memory to catch the 0 and end the loop, and the other spot to keep track of the current value. 

    [--->+<]

Next goal: write the numbers 1 through 10. 

    -[----->+<]>--.+.+.+.+.+.+.+.+.--------.-.

If you're near the right place in the ascii, using + and - along with . is useful. 

Next Goal: Count from 1 to 100. 

Ouch!  That got painful fast. 

I managed to count from 1 to 30, but not in a pretty way. Using loops seems powerful, but fairly arbitrary as adding a single "-" before or in the loop radically changes were it ends. Perhaps I could test a bunch of loops to see where they escape to and start making a mapping between values and escapes. 

    -[----->+<]>--.+.+.+.+.+.+.+.+.--------.-.>-[----->+<]>--.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>+.<<---------->>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>.<<+.>>+.

It would be quite nice to have a way to get out of a loop without having to keep a counter going until it runs into 0 at exactly the time your other counter hits the desired value. Having to time two different variables to be in sync-ish is just painful. 

At this point, if I were to continue, I think I'd rather work on writing a script to generate the Brainfuck code than trying to write the code itself.

All in all, **this experience makes me really appreciate Grace Hopper's insight that code would be much better if the command language was relatively human readable!**
