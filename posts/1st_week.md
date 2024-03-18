---
title: Alice's Bizarre Coding Adventure.
published_at: 2024-03-06
snippet: Week 1 progress.
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




