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

To be completely honest, when I first looked at the code, I had no idea what was going on. I decided to break down whatever I could understand or do research on for now first, and note down what I didn't.

So `faller.colours` means assigning the variable `colours` to the `fallers` object, giving it 2 `rand_col()` values. The same goes for `faller.start_points` and `faller.end_points`. The values inside these 2 arrays are self-explanatory, just the co-ords of the start and end points.

`new Array(7)` is used to make a new array with 7 values. `.fill()` fills the empty values with `null`. `.map(rand_curve)` replaces every null value with the values returned by the function `rand_curve()` made below. After that, the array of 7 random values is assigned to the `.curves` attribute of `faller` object. Similarly, `faller.phase = 0` assigns 0 to the `phase` attribute of `faller`.

`frameCount % 40 == 0` means every 40 frames. 

I start getting confused at
```js
{
    fallers.reverse ()
    fallers.push (new_faller)
    fallers.reverse ()
}
```
because I'm not sure if this reverses an existing set of values or just random values. I kind of have an idea of what the 2 reverses do, but I thought push needs to be used with pop.

I'm pretty much lost on this whole part:

```js
{
    fallers.forEach ((f, i) => {
    colorMode (RGB)
    fill (lerpColor (f.colours[0], f.colours[1], f.phase))
    beginShape ()
    vertex (0, height)
    f.start_points.forEach ((s, i) => {
      const p = find_point (s, f.end_points[i], f.phase ** f.curves[i])
      vertex (p.x, p.y)
    })
    vertex (width, height)
    endShape ()
    f.phase += 0.008
    if (f.phase > 1) redundant.push (i)
  })
  
  redundant.forEach (n => fallers.splice (n, 1))
}
```

The rest are just custom functions, which are pretty simple to understand.

### Falling Falling solution

I noted everything down in the Falling Falling sketch in class.

<iframe src="https://editor.p5js.org/sturrpzzzzz/sketches/yxWt4HNBu"></iframe>

