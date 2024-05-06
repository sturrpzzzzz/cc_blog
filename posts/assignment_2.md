---
title: Alice's Bizarre Coding Adventure.
published_at: 
snippet: Assignment 2.
disable_html_sanitization: true
---

# Design Concept

My design represents the personal experience of someone going through a bad trip (when high), or an overdose, portrayed through their eyes and the thoughts going on inside their head.

I struggled to find inspiration for my design at first, because when you speak of chaos, there are so many things that come to mind. I also second-guessed myself a lot on whether my idea was chaotic or just randomised organisation, if that makes sense. My final idea came through when one of my friends talked to me about this one time they almost got an overdose, and I thought that was a great example of chaos: they were trying their best to control themselves - maintain order, as their consciousness slipped away and their brain went on autopilot. Of course, I got their permission to use their story in my design :D

# Experimental Sketches

Before I came up with my final design concept, I made a few sketches to play around with the idea of chaotic. I won't be going in-depth on my process of making them, since they are sketches I learned from guides and more like a way for me to work up my brain.

First one is a shooting text sketch, in which when you click on the canvas, random words shoots out from your cursor in different directions.

<iframe style="width: 400px; height: 400px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/_BueDvs99"></iframe>

Second is an oscillating sphere made up of dots. I unfortunately lost the link to the video I learnt this from, since it was not on YouTube but another platfrom.

<iframe style="width: 540px; height: 960px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/sHkwspOB5"></iframe>

Last one was not chaotic in my opinion, but it was worth learning. It was inspired by p5js's example on [flocking](https://p5js.org/examples/simulate-flocking.html).

<iframe style="width: 400px; height: 400px; overflow: hidden;"  scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/fy3tlq-si"></iframe>

# Research

I had a few different ideas regarding my approach to this sketch. I was thinking of making a whole face with bezier curves, with the hair and eyeballs made up of cells that change character every frame. Another approach was to make only the eyes, nose and mouth, but as the mouse go upwards, the eyeballs start moving up and *blood* starts dripping off the nose. Finally, I decided on just making the eye but detailed, with background effects.

This assignment had a lot of going with the flow moments, in which my initial idea was fairly simple, but as I worked on it, more ideas came in and I executed *most* of them. This will be talked about in depth in my process.

Same approach on assignment 1: I make different elements of my sketch in different smaller sketches, then put them together.

## Moving eyeball in accordance to mouse position

This one was pretty simple. I made the eye corners using bezier curves, then declared 2 variables with values of the map method of the mouse co-ord between the canvas width/height and the *box* (using variable r) that the iris is contained in. Then, these variables are used as arguments for the iris ellipse's arguments.

<iframe style="width: 800px; height: 800px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/3x6J7uizf"></iframe>

## Pulsation

This was an idea I got from stackoverflow (reference commented in source code). I wanted to include this effect as my friend described that their iris was widening and shrinking (I'm not sure what the correct term for this is, apparently this is one of the symptoms of overdosage).

<iframe style="width: 640px; height: 480px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/psFjtqFNF"></iframe>

## Oscillating Sphere

I learnt about the oscillating sphere not long before I started working on this assignment, and thought it was a good idea to implement it in my sketch because, idk, the oscillating sphere is super fascinating. I learnt from the [tutorial from Patt Vira](https://www.youtube.com/watch?v=atNUa7MdhYs&t=130s). All the process explanation is in the comments of my final sketch. While I was at it, I decided to apply the pulsation and the colour change in accordance to mouse position. The colour change was pretty simple, using map method, just the exact same thing as moving iris position, just applied to stroke colour. I wanted to make the iris turn from green to red as the mouse goes up. Combined with the moving iris, the sketch is going to start with the green iris looking down, representing consciousness, and the iris turns red as it goes up, representing how their eyes roll up and their health gets progressively endangered as a consequence of overdosage.

<iframe style="width: 600px; height: 642px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/NRFP_-JR2"></iframe>




