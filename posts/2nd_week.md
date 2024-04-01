---
title: Alice's Bizarre Coding Adventure.
published_at: 2024-03-06
snippet: Chapter 2.
disable_html_sanitization: true
---

# RR's website recreation.

The website I chose for this week is [open this window](https://www.openthiswindow.com).

It was fairly simple to recreate the visuals of this website. I just applied a gradient on the background colour using `lerpColor()`. Then, I made a slider, and assigned the slider value to the variable g. I made a rectangle with the size of g and the browser's height, and lowered the alpha value to imitate the tinted window.

To change the volume of the music in accordance to the slider value, I declared variable h and give it the value of `map(g, 0, innerWidth, 100, 0);`, so that the value of h is g remapped from the slider value to the volume range. The volume range goes from 100 to 0 because the slider value being at max means the window is closed, therefore, the higher the slider value is, the lower the volume is.

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/uKwfya4NM"></iframe>

### Update

So I just found out that in RR's website, the window can be opened both ways and have no idea how to do that. I will try to figure it out and update here when I do.

## Falling Falling

To be completely honest, when I first looked at the code, I had no idea what was going on.



