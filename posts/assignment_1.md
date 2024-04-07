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

Then, I started drawing Womp's face when mad. It was simple, literally just two half circles inside each other.

![mad](static/Screenshot 2024-03-25 020805.png)

Womp's mildly annoyed face was a little more complicated to make, but was simple enough regardless.

![annoyed](static/Screenshot 2024-03-25 020914.png)

Then, to give each shape different stroke widths and fill colours, I used `push()` `pop()` inside the conditional operators.

[pushpopagain](static/Screenshot 2024-03-25 021234.png)

Here is the sketch for Womp's expressions.

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/jy-kGvP1L"></iframe>

## Bubbles

The bubbles were simple because I had made them before, so I'm not sure what to comment on this. I'm just saying, being able to click out bubbles is my childhood dream and I am now happy.

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/YfJ0ad8ai"></iframe>

## Combined sketch

Like I said, my idea was inspired by a spring sketch, so here were the original variables copied from the originl spring sketch. The variables and variables' values change as my sketch gets developed.

![original variables](static/Screenshot 2024-03-25 032331.png)

It took me a while to understand everything that was going on in the [original spring sketch](https://editor.p5js.org/sturrpzzzzz/sketches/qqZt0QgM0). Everything that I needed to note down to explain the code are in the comments in my sketch, so I won't explain it again here.

There was a point when Womp wouldn't move because I didn't fully understand the code and didn't use the `baseWidth` variable in Womp's parameters. To word it correctly, I only used constants in Womp's parameters at first and wondered why he wasn't moving... but hey, we learn through mistakes, no matter how dumb they are.

![moved yay](static/Screenshot 2024-03-26 011451.png)

After I used `baseWidth` in Womp's parameters, everything was good to go :joy:

The same thing happened to Womp's eyeballs. At first, I only used constants in the ellipses' parameters, so they weren't moving with Womp's body. Then, I did the same thing and used `baseWidth` and now Womp's eye goes from his right to his left as gets stretched, which is very funny to me for some reason. Then, I added a cartoonish spring sound that plays every time Womp is released.

I did say that I wanted to use the same colour scheme as RR's website, but considering how Womp turns blue and the bubbles are transparent (as they should be), a blue background colour would overpower these colours, so I opted for a darker background instead. I didn't have any particular reason why I chose purple, I just like the purple sky, and it really helps the other elements of the sketch pop. However, a pure purple background seemed boring, because the sky is never one singular colour, so I made it a gradient instead. It turned out great in my opinion.

![musicfail](static/Screenshot 2024-03-26 213556.png)

This was my first attempt to playing and pausing the background music. I wanted the music to be autoplayed at first, so I didn't even bother to make a button, which was a very silly idea... The idea was that when the ":3" text box is clicked, the music would stop, but if not, the music would keep looping. It stayed an idea because obviously it didn't work...

So I ended up just making a button for it, because taking shortcuts isn't the way to go. I created a custom function for the audio toggle:

```js
{
    function togglePlaying() {
  if (!song.isPlaying()) {
    song.play();
    song.setVolume(0.3);
  } else {
    song.stop();
  }
}
}
```

And it worked. Yay. However, I realised that the spring sound would play no matter where I clicked on my sketch, so I added a condition in the function `mouseReleased()`
```js
{
    move = false;

    if (move) {
    springSound.play();
    }
}
```
which didn't work. So I asked Thomas and apparently I had it in the wrong order... It should have been 
```js
{
  if (move) {
   springSound.play();
  }
  
  move = false;
}
```
and with that, my assignment 1 is done.

Or so I thought, because on April 8th, I opened my sketch in fullscreen for the first time and realised the eye was completely off where it should have been. Awesome. Nothing I can do about it now...

# Final sketch

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/STA44SMMM"></iframe>