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

<iframe style="width: 400px; height: 442px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/_BueDvs99"></iframe>

Second is an oscillating sphere made up of dots. I unfortunately lost the link to the video I learnt this from, since it was not on YouTube but another platfrom.

<iframe style="width: 540px; height: 1002px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/sHkwspOB5"></iframe>

Last one was not chaotic in my opinion, but it was worth learning. It was inspired by p5js's example on [flocking](https://p5js.org/examples/simulate-flocking.html).

<iframe style="width: 400px; height: 442px; overflow: hidden;"  scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/fy3tlq-si"></iframe>

# Research

I had a few different ideas regarding my approach to this sketch. I was thinking of making a whole face with bezier curves, with the hair and eyeballs made up of cells that change character every frame. Another approach was to make only the eyes, nose and mouth, but as the mouse go upwards, the eyeballs start moving up and *blood* starts dripping off the nose. Finally, I decided on just making the eye but detailed, with background effects.

This assignment had a lot of going with the flow moments, in which my initial idea was fairly simple, but as I worked on it, more ideas came in and I executed *most* of them. This will be talked about in depth in my process.

Same approach on assignment 1: I make different elements of my sketch in different smaller sketches, then put them together.

## Moving eyeball in accordance to mouse position

This one was pretty simple. I made the eye corners using bezier curves, then declared 2 variables with values of the map method of the mouse co-ord between the canvas width/height and the *box* (using variable r) that the iris is contained in. Then, these variables are used as arguments for the iris ellipse's arguments.

<iframe style="width: 800px; height: 842px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/3x6J7uizf"></iframe>

## Pulsation

This was an idea I got from stackoverflow (reference commented in source code). I wanted to include this effect as my friend described that their iris was widening and shrinking (I'm not sure what the correct term for this is, apparently this is one of the symptoms of overdosage).

<iframe style="width: 640px; height: 522px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/psFjtqFNF"></iframe>

## Oscillating Sphere

I learnt about the oscillating sphere not long before I started working on this assignment, and thought it was a good idea to implement it in my sketch because, idk, the oscillating sphere is super fascinating. I learnt from the [tutorial from Patt Vira](https://www.youtube.com/watch?v=atNUa7MdhYs&t=130s). All the process explanation is in the comments of my final sketch. While I was at it, I decided to apply the pulsation and the colour change in accordance to mouse position. The colour change was pretty simple, using map method, just the exact same thing as moving iris position, just applied to stroke colour. I wanted to make the iris turn from green to red as the mouse goes up. Combined with the moving iris, the sketch is going to start with the green iris looking down, representing consciousness, and the iris turns red as it goes up, representing how their eyes roll up and their health gets progressively endangered as a consequence of overdosage.

<iframe style="width: 600px; height: 642px; overflow: hidden;" scrolling="no" frameborder="0" src="https://editor.p5js.org/sturrpzzzzz/full/NRFP_-JR2"></iframe>

## Matrix Effect

For this sketch, I used Co_Dart's [Matrix Digital Rain tutorial](https://www.youtube.com/watch?v=13Ip2brYPto). There were not much struggle because I was following the tutorial step by step at first. All explanation is included in my sketch's comments.

<iframe style="width: 800px; height: 842px; overflow: hidden;" scrolling="no" frameborder="0"src="https://editor.p5js.org/sturrpzzzzz/full/njV_9jNw9"></iframe>

After that, I thought it would be a good idea to make the drops only come from the eyes, so that it looks like the person is crying. To do that, I would need to limit the spawn position of the drops to a set of values. There were a few trials and errors, but I figured it out in the end, using 

```js
    this.y += 2
    if (this.y > innerHeight) {
         this.y = random(300, 350);
       }
    if (this.x > 500 || this.x < 200) {
    	   this.x = random(200, 500);
       }
    text(this.symbol, this.x, this.y);
```

y's value increments by 2 to make the drops gradually fall downwards. If the drop reaches the end of the canvas, the drop spawns somewhere between 300 and 350 on the y axis, because you know, tears don't drop on a straight line. With `this.x > 500 || this.x < 200`, I make sure the drops' spawn point doesn't go outside (200, 500) on the x axis. Here is the result:

<iframe style="width: 800px; height: 842px; overflow: hidden;" scrolling="no" src="https://editor.p5js.org/sturrpzzzzz/full/K8XCsITUJ"></iframe>

Looks pretty underwhelming in my opinion. It had a pretty nice element of chaos, but I don't think it looked aesthetically pleasing, so I scrapped the idea and stuck with the original instead. Instead of tears, they would be drops of sweat trickling down the face.

## Decay Effect

I stumbled upon [this sketch](https://editor.p5js.org/andreiongd/sketches/Fit4bu_Z4) while looking for matrix effect guides. It was really fascinating, but the code was pretty confusing, so I asked Thomas for explanation and apparently more than half the variables declared weren't even used in the text arguments. Nonetheless, it was extremely helpful to learn that I could use `translate()` with push and pop, since I was struggling with aligning the elements in my code.

This is my version of the sketch.

<iframe style="width: 800px; height: 842px; overflow: hidden;" scrolling="no" src="https://editor.p5js.org/sturrpzzzzz/full/6TettVls3"></iframe>

I love using `map()`, as I can use this method anywhere and it is great for creating interactive elements. You are going to see me using `map()` several times in my sketch, but in this one specifically, I used it to change the colour of the words.

## Combining sketches

As I mentioned before, I was struggling to align my elements due to the oscillating sphere using its own `translate()`, so when I integrated the decay effect, the whole text box were misaligned. However, after learning that `translate()` can be used with push and pop, everything was resolved. God bless push pop!

Right so, this is when I should explain each element in my sketch:
1 - The iris is an oscillating sphere. The higher the iris goes - imitating eye rolled up -, the redder it becomes, and the faster the iris pulsates, signifying critical health condition and portraying symptoms of overdosage. To achieve the pulsation-in-accordance-to-mouse-coord effect, I used `map()` (again).

```js
for (i = 0; i < 15; i++) {
       r = map(cos(i * frameCount * mouseY/230), -1, 1, minSize, maxSize);
    }
```

2 - The drop cells say 'FAKE'. My friend told me when they were high, their brain could tell that every hallucination was fake, but they were experiencing it with their senses, so it was really contradicting and confusing, and I found that really fascinating.

3 - The decay background says random nonsense characters. My friend talked about how while they could *almost* understand and process their thoughts, they could not control them. This resulted in a trippy experience where they kinda experienced all the random thoughts in their mind, if that makes sense.

# Final sketch. 

<iframe style="width: 1000px; height: 1042px; overflow: hidden;" scrolling="no" src="https://editor.p5js.org/sturrpzzzzz/full/shzmbOMaz"></iframe>

I'm not really sure how to set the width and height if the canvas size is (innerWidth, innerHeight).


