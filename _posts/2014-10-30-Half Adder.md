---
layout: post
title: Half Adder
---

Last Thursday I derived how to make a half adder out of 4 NANDs and a transitor, plus some switches, wire, and resistors on a breadboard. A "half adder" is able to add 0 plus 0, 0 plus 1, 1 plus 0, and 1 plus 1. To make it a full adder, we'd also need to be able to take in a carry digit: so effectively add up to 3 where each thing being added is either 0 or 1. But, this day was all about the half-adder.  

The goal is to be able to take two inputs, each either 'on' or 'off', which we can think of as 0 and 1s. The goal is to be able to add these (in binary). So, 0 + 0 = 0, 0 + 1 = 1, 1 + 0 = 1, and 1 + 1 = 10 which is equal to 2 in decimal. 

So, we want the following logic:  

| Input A       |  Input B       |  Output 2cd digit |  Output 1st digit |
| ------------- |:-------------:| -----:| ----:|
| 0      | 0 | 0 | 0 |
| 0     | 1      |   0| 1 |
| 1 | 0     |    0 | 1 |
| 1 | 1     |    1 | 0 |

But, we'll use switches for inputs and LEDs to represent the output. In terms of switches and lights, we're looking for this: 

| Switch A       | Switch B       | LED 2cd digit | LED 1st digit |
| ------------- |:-------------:| -----:| ---:|
| 'off'      | 'off' | 'off' | 'off' |
| 'off'     | 'on'     |   'off'| 'on'   |
| 'on'   | 'off'     |    'off' | 'on'   |
| 'on'   | 'on'       |    'on'   | 'off' |

The LED 2cd digit is essentially an "AND" gate. It's only "on" when both switches are "on". 

The LED for the 1st digit in an "exclusive or" logic gate. It's "on" if *exactly one of the inputs* is "on".

The raw materials were an Integrated Circuit with 4 NAND (Not AND) logic gates, and a transitor. The first challenge was to figure out how to construct an 'AND' and an 'Exclusive OR' logic gates from these matericals. This was a very interesting challenge, as it required thinking forward from what possible inputs I had, considering what "operations" (NAND), and working backwards from what I needed as an output. Eventually I saw how to make it meet in the middle :).

The second challenge was to branch off an AND. I was inspired by my friend Andrew's note that a NAND plus a transitor to invert the signal (make a Not) is an 'AND'. So, I branched off from my initial NAND and added a transistor.  

The result is below, with the associated sketch on the right. 

[Half Adder!](https://lh6.googleusercontent.com/-WtVmFeUdp8U/VEnIi3WnICI/AAAAAAAAY2g/KIkkg7ug4RI/w350-h621-no/IMG_20141023_160225531_HDR.jpg)
