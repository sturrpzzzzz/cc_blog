---
title: Alice's Bizarre Coding Adventure.
published_at: 2024-03-12
snippet: Chapter 4.
disable_html_sanitization: true
---

So, I have watched a tutorial on making a tree before, I just never knew it was called recursion. This was not too much trouble for me, since I'm pretty much remaking a sketch.

# Process

What I did first is changing the `angleMode()` to degrees because we are using that to draw the leaves later. Then, I used `translate()` to move the starting point of the canvas to lower middle because that is going to be the root of my tree.

I created a new function called `drawBranch()` and gave it the argument len. len's value is the length of the tree trunk, which is always positive. I started off with drawing a line for the tree trunk: `line(0, 0, 0, -len);`. The first point of the line is the starting point of the canvas after `translate()`. The x coord of the second point is still 0 to ensure the trunk goes straight upwards. In this case, len must become negative. Since the y axis goes downwards, if len stays positive, the line will be drawn downwards and the whole tree will be upside down, hence -len for y2.

After drawing the trunk, I used another `translate()` to move the starting point to the (x2, y2) coord of the trunk line, so that the branches come out of the top of the line. Then, I used `rotate()` and gave it a random number, so that the branches turn in different directions every frame. At this point, the branches were moving every frame, so I used `noLoop()` in setup.
Then, I called `drawBranch()` again, giving it the argument of len * a random number < 1, so that the branches' lengths get shorter and shorter. However, the branches getting shorter doesn't stop them from looping endlessly, so I had to create a condition to stop drawing branches and instead drawing leaves. I used an if condition that states that as long as the line length is > 10, `drawBranch()` will keep getting called, but when its length is <10, the leaves will be drawn instead of more lines. To create custom shapes to make the leaves, I used `beginShape()` and `endShape()`. Now, to create the leaves' curves, I used `vertex()`. I'm drawing the leaves based on a part of a circle, like, less than half of a circle if that makes sense. To do that, I used a for loop: `for (let i = 45; i < 145; i++)`. So, i can range anywhere from > 0 to < 360, as long as it doesn't make a full circle, but for the sake of aesthetic, I prefer making i < 145. I declared variable rad = 15 for the size of the leaf. Then, I declared x = rad * cos(i), and y = rad * sin(i). So, neither of vertex()'s arguments can be a set number, because if they are both set numbers, it would be drawing a point, and if one of them is a set number, then we would be drawing straight lines. With the declared values of x and y, every point created by each set of (x, y) is connected, creating the part circle. I honestly don't know how to explain this, I hope that made sense. 

After that, I changed the value of the stroke weight depending on the length of the stroke, using `strokeWeight(map(len, 10, 100, 1, 6));`. I mapped len with the limit we gave the branch length: 10 to 100, to the stroke weight I want: 1 to 6, so that the shorter the branch is, the thinner it becomes. Then, I added a few `random()`s to make random colours for the leaves.

<iframe style="width: px; 700height: 742px; overflow: hidden;" src="https://editor.p5js.org/sturrpzzzzz/full/Ua7CX_zGq"></iframe>

# Thoughts

Recursion is great for creating organised chaos. Using recursion with `random()` can create great chaos-inducing sketches in my opinion. Even though I enjoy the idea of using recursion to create chaos, I don't want to limit the potential of creating chaos to recursion, if that makes sense. The way I think of it is that recursion is only one of all the ways to create chaos. There are so many other ways to implement chaos into my work, and I'm not sure recursion would be suitable for my idea. 