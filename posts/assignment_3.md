---
title: Alice's Bizarre Coding Adventure.
published_at: 2024-03-06
snippet: Assignment 3.
disable_html_sanitization: true
---

# Design Concept

I am creating an audio visualiser for psytrance music events.

Audio visualisers are extremely important to music events, especially electronic music, because they add emphasis on the beat, and create a listening experience not just auditory, but also visually. They create a tangible drawing of the beats in front of our eyes.

This idea started when my friends invited me to a rave 2 weeks ago. I always knew I would create something audio reactive for this assignment. I had not listened to electronic music for years, and this was my first rave ever, so I just stood there awkwardly, observing other people dancing and having fun. I remember thinking the visualisers for the event were so sophisticated and added so much hype to the music, and ended up spending the whole night just analysing the visuals and how they corresponded to the music. Then, my friend invited me to another rave, and I thought it would be a great idea to create a visualiser of my own to add my own touch to the listening experience.

# Research

First of all, I did research on psytrance itself. It is important to understand what I am working with before I create something to accommodate it. From what I have learnt and my own experience, psytrance has intensely repetitive beats, high BPM, along with really melodic tunes and acid tones. 

I have never worked with audio before, so it was a pretty novel experience for me. First, I read through the whole p5.sound library. Then, I just searched up p5 sound projects on YouTube and Google to have an idea of what can be done with sound. I think what taught me the most about sound was [Patt Vira's Sound Mini Series](https://www.youtube.com/playlist?list=PL0beHPVMklwjNRGtN74Mp6JCub4Dd_y5w). The Coding Train also had really insightful videos on sound. On top of that, I looked at other people's p5 sound sketches that I found on Google. 

I also researched on audio visualisers at big electronic music events, such as Tomorrowland, Excision, or Knockout, and just psytrance visuals in general on YouTube. I noticed that the visuals for this music genre is really insubstantial - the way it is always portrayed by shapes, lines, and colours, instead of actual objects -, trippy, accommodated by repetitive patterns and very diverse colours. While researching, I found a mechanic that perfectly fits the portrayal of psytrance: the chromatrope.

A chromatrope is a type of magic lantern slide that is set in motion by rotating two painted glass discs in opposite directions. This results in glassy, dazzling, colorful geometrical patterns. I want this mechanic to be the center of my visualiser.

![Chromatrope GIF](https://www.luikerwaal.com/bewegend/chr_draaiend.gif)

## Creating chromatrope effect in P5js

This was pretty simple as I found out about `blendMode()`. It is basically editing pictures in Photoshop, just with coding. For this sketch, I put two similar pattern images on top of each other, one flipped backwards. Then, I used `blendMode(DIFFERENCE)` to create the layered effect. To make the images rotate, I declared variable r = 0, and made r = r + 1. Then, I used `rotate(radians(r * x))` on one image, and -r on the other so that they rotate in opposite directions. Now, the images are rotating, but since the starting point of the images are on their top left corner, they are rotating around that corner instead of in the middle of themselves. To fix that, I used `imageMode(CENTER)`. Now, they are rotating around themselves, but since I had the images drawn at (0, 0), I changed the focal point of the canvas to the middle of it instead,using `translate(width/2, height/2)`.

Now, the images are working exactly how chromatrope mechanics operate. However, I want the images to react to sound as well. At first, I wanted the images to rotate to the amplitude of the sound, so I declared variable amplitude and assigned it the value of `mic.getLevel()`. Then, instead of r = r + 1, I used r = r + amplitude. So, the images' rotation is responding to the audio. However, as I mentioned, psytrance has really intense, repetitive beats, so in order to portray that, I am going to make the image sizes correspond to the amplitude of the sound. I declared a few variables: size - for the image's default size, minSize, maxSize, and sizeSpeed - to decide how fast the size changes. I am going to use a sine wave to map the changes in size, so that the transition is smoothed out. The method I used for this is `size = map(sin(amplitude * sizeSpeed), -1, 1, minSize, maxSize);`, with amplitude added so that the change is dependent on the mic amplitude.

<iframe style="width: 700px; height: 742px; overflow: hidden;" scrolling="no" src="https://editor.p5js.org/sturrpzzzzz/full/KF-29r49P"></iframe>

## Creating the visualiser background

For the background, I want it to be something simple so that the focus is on the chromatrop, but it still has to respond to the audio. I used [this tutorial](https://www.youtube.com/watch?v=x_aGtSZMEUA) for my background, since it is audio-responsive(of course), with simple, repetitive patterns. I added my own tweaks to it by changing the colour array to complete grayscale.

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/gGYbzrK-0"></iframe>

## Final sketch

For my final sketch, I combined the two sketches above, then added `blendMode(BLEND)` to the background so that it reacts nicely to the images. 

<iframe style="width: 610px; height: 652px; overflow: hidden;" scrolling="no" src="https://editor.p5js.org/sturrpzzzzz/full/RC7ZLfBT0"></iframe>

The only problem with my sketch is that I needed to use `mic.getLevel() * 1000` because my laptop has trouble detecting mic sound. However, on other devices, the mic detection would be too sensitive and cause the visualiser to go a lot more intensely than intended.

## Deploying to Deno

So, I thought that was over. However, when I downloaded the sketch and viewed it locally, my sketch would not run. There was an error in which audioContext() was not allowed to start automatically. Thank god Thomas was there to help me out, and we ended up adding a button that allows audioContext() to run. Thank you Thomas!!!






