---
title: Alice's Bizarre Coding Adventure.
published_at: 
snippet: Assignment 1.
disable_html_sanitization: true
---

# Design Concept

My sketch consists of an interactive character who reacts differently based on how close the user's mouse is from him, on a background with bubbles.

## Research

First of all, I started looking for inspiration for what is appropriate to add in my sketch. I searched for generative art projects on Reddit and YouTube, and it was a fascinating experience because I never knew that you could do so many things with Javascript. There are designs for literally anything. For this research specifically, I was looking for something that I considered cute or could integrate into my code. 

The project that really complimented mine was [springy](https://editor.p5js.org/sturrpzzzzz/sketches/qqZt0QgM0). It's a copy because I wanted to add some comments to understand what was going on in the code. 

## Character design

![original ideas](static/womp_character_design/20240408_025456.jpg)

Here is a collection of the sketches I drew for the initial design of Womp.

![default state](static/womp_character_design/20240408_031120.jpg)

This was the shape I chose for Womp's default state. I chose this over the thumb-like shape because it reminds me of a block of Jell-O :joy:. I liked the furry idea the most honestly, but I would have to make his fur move as the spring bounces and I have no idea how to do that... I decided to put his eye on one side because perfectly symmetrical objects are overrated and pretty boring in my opinion, especially when it comes to cuteness. I believe "flaws" make the character or object more charming, relatable, and vulnerable, thus making it more lovable and personal.

![reactions](static/womp_character_design/20240408_031136.jpg)

His default colour is green, which means he is happy and at peace! When your mouse invades his personal space, he turns blue, which signifies that he is slightly annoyed and upset. When your mouse touches him, he becomes red, which means he is mad as hell >:(

# Sketch development

Similarly to how I break down the definition of effective complexity, for my sketch, I'm breaking it down to different smaller sketches, making sure that these small sketches work properly, then combining them altogether into my final sketch. 

## Mouse hover - colour change

### Attempt 1

![mouseOver](static/Screenshot 2024-03-23 170020.png)

I tried using `mouseOver()` because it was the first thing that came up when I searched for mouse interactions in the p5js reference. However, I never really figured out how to use it, as it keeps giving me the error "mouseOver() can't be called as a function", and I still haven't figured out how to use it to this day...

### Attempt 2

![co-ords](static/Screenshot 2024-03-23 170053.png)

For this attempt, I just used conditional statements to specify what the mouse co-ords must be for the rectangle to change colour. Pretty straightforward, but seemed restrictive in my opinion, especially when my character is going to be moved.

### Attempt 3

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/ocNRP9SDh"></iframe>

This was a pretty roundabout way to do it in my opinion. I just created a div and made it so that when I hover over it, it changes colour. However, this wouldn't work in my code because again, my object is going to be bouncing... I'm sure there would be a way for the div to bounce but ...why?

### Attempt 4

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/APVxOVWPj"></iframe>

This was a method recommended by Thomas. While it was a great way to do it, I didn't use it in my final design because I wanted my rectangle's top corner radius and bottom corner radius to be different.

## Womp's expressions

![trouble](static/Screenshot 2024-03-24 235756.png)

I struggled a little bit at first because I didn't expect `strokeWeight()` to be applied to the rectangle as well. It didn't take long for me to realise I needed to use `push()` and `pop()` to apply seperate properties for each shape. 

![pushpop](static/Screenshot 2024-03-24 235955.png)

Look at this cutie, all wide-eyed.

![mad](static/Screenshot 2024-03-25 020805.png)


