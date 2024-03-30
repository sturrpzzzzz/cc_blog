---
title: Alice's Bizarre Coding Adventure.
published_at: 2024-03-06
snippet: Chapter 1.
disable_html_sanitization: true
---

# Creating grids.

## Train of thoughts.

To create grids, we can either use lines or squares. In this sketch, I'm going to use lines. I will make a square version when I have time.

The syntax for drawing lines is `line(x1,y1,x2,y2)`

If I want to create a 10x10 grid, I would need 11 horizontal lines and 11 vertical lines of the same length, and the same distance from each other. 

That means if I want to create a 10x10 grid with each line being 10 pixels away from each other, the requirements for the loop must be i = 0; i < 101, i+=10. In this case, I want the grid lines to be seperate from the edge of the canvas, so I made (x1, y1) of the first vertical line (5, 5). Because we need 11 lines, the co-ords must be less than or equal 105. I just use i < 106.

```javascript
{
for (let i = 5; i < 106>; i + 10) {
    line (i, 5, i, 105);
}

}
```
The y coordinates of the vertical lines stay the same to ensure that they are of the same length.

## Final sketch.

<iframe width="300" height="342" src="https://editor.p5js.org/sturrpzzzzz/sketches/nbPJmblp-"></iframe>

# RR recreation: [thisgrey](thisgrey.com)

## Train of thoughts.

At first, I thought of using for loop because I thought it was a loop of colours. My idea was to write something like

```js
{
    for (let i = 0; i < 256; i += 7) {
        if (i > 0; i < 256) {
            fill (256 / i);
        } else {
            fill (i / 256);
        }
    }
}
```

Honestly, I'm not sure if this code makes any sense. I was just trying to have i go from 0 to 256 and back, but then I realised that the greyscale values do not go in a loop, they go up and down and repeat. So I decided to seperate this process in 2 parts: one for making the value go up, one for making it go down.

### Attempt 1

[thisgrey Sketch 1.](https://editor.p5js.org/sturrpzzzzz/sketches/hIGysEzHU)

I decided to use an everchanging value in my for loop, in this case, it's `frameCount`. I just had frameCount divided with a random number to change how fast the colour was changing. Limiting the value of i between 0 and 255 and i incrementing, I pretty much assigned it to a (also) random math equation `bgColour = color(i * (t + 0.5));`, and it worked! The background colour went from black to white.

While knowing that this would not work because I didn't need a loop, I pushed it and used the for loop anyway.

```js
{
    for (let i = 0; i < 256; i++) {
    if (i = 255) {
        bgColour = color(i * (t + 0.5));
    } else {
        bgColour = color(i / (t + 0.5));
    }
    }
}
```

And evidently, it didn't work so...

### Attempt 2

[thisgrey Sketch 2.](https://editor.p5js.org/sturrpzzzzz/sketches/TXxgN_d9F)

I used a different approach for this one. I declared the variable counter and made it so that when i reaches 255, counter is true, and when counter is true, i's value decrements. When i reaches 1, counter is false, and i's value increments. That was the idea anyway, because it didn't work and froze my browser instead.

```js
{
    let counter = 0;
  for (let i = 0; i < 256;) {
    bgColour = color(i);
    if (i == 255){
      counter = 1;
    }
    if(counter == 0) {
      i++
    } else if (counter == 1){
      i--
    }
}
```

### Attempt 3

[thisgrey Sketch 3.](https://editor.p5js.org/sturrpzzzzz/sketches/1lUqdx7n7)

<iframe src="https://editor.p5js.org/sturrpzzzzz/full/1lUqdx7n7"></iframe>

After asking for Thomas's feedback, for this sketch, I used sine waves to change the greyscale value. I declared several variables and stored them the values of `frameCount * [random number]`, using them to differ the colour changing speed. For each variables declared, I declared a constant and gave them the value of `[variable name] * TAU`. Because the phase signal is between 0 and 1, the values of all constants are between 0 and TAU. 

Declaring the variable `sinusoid` and assigning it the value of sin, with sin's value always limited between -1 and 1, `sinusoid =+ 1` is always limited between 0 and 2, and `sinusoid =* 128` is always limited between 0 and 256, which is the greyscale limit. After that, I assign the value of sinusoid to the shapes' colours.

```js
{
  let p = frameCount * 0.2 // changes the speed
  p %= 60 // limit value at 60
  p /= 60 // phase signal is between [ 0, 1 ]
  
  const angle = p * TAU    // [ 0, TAU ]
  
  let sinusoid = sin (angle) // [ -1, 1 ]
  sinusoid += 1              // [  0, 2 ]
  sinusoid *= 128 // amplitude  [  0, 256]
  
  background(sinusoid);
}
```


