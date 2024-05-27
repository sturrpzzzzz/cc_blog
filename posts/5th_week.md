---
title: Alice's Bizarre Coding Adventure.
published_at: 2024-03-12
snippet: Chapter 5.
disable_html_sanitization: true
---

# Glitch

```
const cnv = document.getElementById (`glitch_self_portrait`)
cnv.width = cnv.parentNode.scrollWidth
cnv.height = cnv.width * 9 / 16
cnv.style.backgroundColor = `deeppink`
```

cnv is the canvas element with the ID glitch_self_portrait. 
cnv.width sets the canvas width to its parent's scroll width.
`cnv.height = cnv.width * 9 / 16`: set canvas height to a 9:16 ratio dependent on canvas width.
Last line sets canvas background colour to deep pink.

```
const draw = i => ctx.drawImage (i, 0, 0, cnv.width, cnv.height)

const img = new Image ()
img.onload = () => {
    cnv.height = cnv.width * (img.height / img.width)
    draw (img)
    img_data = cnv.toDataURL ("image/jpeg")
    add_glitch ()
}
img.src = `/240405/pfp_glasses.jpg
```

In the first line, function draw() is declared with argument i, which executes `ctx.drawImage (i, 0, 0, cnv.width, cnv.height)`. The parameters for drawImage() is drawImage(image, dx, dy, dWidth, dHeight), which means the image drawn is scaled to fit the canvas width and height.
img is a new image object.
In the third line, when image is loaded:
    cnv.height = cnv.width * (img.height / img.width) which means cnv.height / cnv.width = img.height / img. width => this line sets the height of the image to the canvas ratio, then the image is drawn. Its data is converted to jpeg. img.src sets the source of the image.
    add_glitch() is a function declared later in the code, and is called when the image is loaded.

```
const rand_int = max => Math.floor (Math.random () * max)
```
With Math.random() on its own returning a value between 0 and < 1, rand_int is a function that returns a random interger between 0 and max - 1.

```
const glitchify = (data, chunk_max, repeats) => {
    const chunk_size = rand_int(chunk_max / 4) * 4
    const i = rand_int(data.length - 24 - chunk_size) + 24 
    const front = data.slice (0, i)
    const back = data.slice (i + chunk_size, data.length)
    const result = front + back
    return repeats == 0 ? result : glitchify (result, chunk_max, repeats - 1)
}
```
rand_int(chunk_max / 4) * 4 means Math.floor (Math.random() * (chunk_max / 4)) => chunk_size is a random multiple of 4, up to chunk_max / 4.
Variable i represents the starting index of the chunk of data that needs to be removed to create the glitch effect. `rand_int(data.length - 24 - chunk_size) + 24` ensures that i is not too close to the start and end of the data string to avoid corrupting critical parts of the image that are essential for the image to be displayed correctly (thank you ChatGPT for helping me with this). By ensuring i is always at least 24 bytes from the start, the function avoids damaging the image data. data.length - 24 - chunk_size ensures that there is enough space at the end of the data string for the chunk size to be valid. If i were too close to the end, the chunk would extend beyond the data string's length, leading to an invalid operation. The additional + 24 ensures that the chunk doesn't wrap around and corrupt important data towards the end of the string. rand_int(data.length - 24 - chunk_size): Generates a random index ensuring the chunk fits within the data string.
data. length - 24 - chunk_size ensures there are at least 24 bytes after the end of the chunk, preventing it from going out of bounds. + 24: Shifts the starting index to be at least 24 bytes from the beginning, protecting the image headers.
data.slice (0, i) consists of values from 0 to i - 1. data.slice (i + chunk_size, data.length) consists of values from i + chunk_size to data.length - 1.
result combines the values of front and back.
`return repeats == 0 ? result : glitchify (result, chunk_max, repeats - 1)`
`repeats == 0` checks if variable repeats equals 0. `?` is the ternary operator that checks whether repeats = 0 is true or false. : seperates the 2 outcomes of the operator. If it is false, execute `glitchify (result, chunk_max, repeats - 1)`. `glitchify (result, chunk_max, repeats - 1)` is called inside glitchify function again, which is recursive, with the updated arguments. The recursion continues and repeats keeps decrementing until it reaches 0. The purpose of this line is to recursively apply the glitch effect a set number of times. Each time glitchify is called, it processes result until no repeats is left. This ensures that the glitch effect is applied multiple times, resulting in varied glitch effects in the final image.

```
const glitch_arr = [];

const add_glitch = () => {
   const i = new Image();
   i.onload = () => {
      glitch_arr.push(i);
      if (glitch_arr.length < 12) add_glitch();
      else draw_frame();
   };
   i.src = glitchify(img_data, 96, 6);
};
```
glitch_arr is an array storing the glitched images.
add_glitch creates a new glitched image, adds it to the array glitch_arr, and keeps adding until there are 12 glitched images. Once done, it starts the animation by calling draw_frame.

```
let is_glitching = false;
let glitch_i = 0;

const draw_frame = () => {
   if (is_glitching) draw(glitch_arr[glitch_i]);
   else draw(img);

   const prob = is_glitching ? 0.05 : 0.02;
   if (Math.random() < prob) {
      glitch_i = rand_int(glitch_arr.length);
      is_glitching = !is_glitching;
   }

   requestAnimationFrame(draw_frame);
};
```
is_glitching tracks whether the image currently displayed is glitched.
glitch_i is the index of the current glitched image in glitch_arr.
Function draw_frame checks whether the image displayed is glitching or not based on is_glitching. If is_glitching is true, the glitched image is shown. If not, the original image is shown.
prob sets the probability of displaying glitched or original images. If is_glitching is true, then prob is set to 0.05 (5% chance). If is_glitching is false, then prob is set to 0.02 (2% chance).
`glitch_i = rand_int(glitch_arr.length)` sets glitch_i to a random index within the glitch_arr array. Math.random() returns a value from 0 to <1. As long as that value is < prob, the following two lines of codes are executed. rand_int(glitch_arr.length) generates a random integer between 0 and glitch_arr.length - 1. glitch_arr is an array that holds the glitched images.
`is_glitching = !is_glitching`: if is_glitching was true, it becomes false, and vice versa.
The purpose of this code is to randomly switch between displaying the original image and a glitched image during the animation. When is_glitching is true, there is a 5% chance of the glitched image returning to the original image per frame, the vice versa but with 2% chance. This makes the glitched images appear and disappear seemingly randomly.

# Pixel Sort
```
const cnv  = document.getElementById('pixel_sort');
cnv.width  = cnv.parentNode.scrollWidth;
cnv.height = cnv.width * 9 / 16;

const ctx = cnv.getContext('2d');
const sorter = new PixelSorter(ctx);

const img = new Image();

img.onload = () => {
    cnv.height = cnv.width * (img.height / img.width);
    ctx.drawImage(img, 0, 0, cnv.width, cnv.height);
    sorter.init();
    draw_frame();
};

img.src = '/240408/kornerpark.jpg';
```
This part is similar to the previous code, so I won't be explaining it again (I'm lazy...).

```
let frame_count = 0;
const draw_frame = () => {
   ctx.drawImage(img, 0, 0, cnv.width, cnv.height);

   let sig = Math.cos(frame_count * 2 * Math.PI / 500);

   const mid = {
      x: cnv.width / 2,
      y: cnv.height / 2
   };

   const dim = {
      x: Math.floor((sig + 3) * (cnv.width / 6)) + 1,
      y: Math.floor((sig + 1) * (cnv.height / 6)) + 1
   };

   const pos = {
      x: Math.floor(mid.x - (dim.x / 2)),
      y: Math.floor(mid.y - (dim.y / 2))
   };

   sorter.glitch(pos, dim);

   frame_count++;
   requestAnimationFrame(draw_frame);
};
```
With `ctx.drawImage(img, 0, 0, cnv.width, cnv.height)`, the original image is drawn each frame, fitted to the canvas dimension.
`sig = Math.cos(frame_count * 2 * Math.PI / 500)`:
Math.PI * 2 is 360 degrees. frame_count * 2 * Math.PI results in an angle that changes over time as frame_count changes. Dividing by 500 slows down the change speed. This means sig completes a full cycle from 0 to 2 * PI every 500 frames. This angle gradually increases as frame_count increases, then resets every 500 frames. Math.cos oscillates between -1 and 1, so the whole thing gets the cosine of the angle, resulting in values that oscillate smoothly from -1 to 1 in 500 frames.
mid is an object that stores the co-ords of the middle of the canvas.
```
    x: Math.floor((sig + 3) * (cnv.width / 6)) + 1,
```
sig + 3 oscillates between 2 and 4. Using Math.floor converts it to a range that goes in accordance to the canvas width. I'm not too sure what + 1 does here, I think it ensures that the glitch dimension is always at least 1 pixel wide. The same goes for y, with sig + 1 oscillating between 0 and 2.
```
    x: Math.floor(mid.x - (dim.x / 2))
```
This one took me some time to understand. I kinda forgot that the starting point of the shape is the coords of its top left point, not the middle point. Now, when I got that figured out, it took me more time to figure out why dim.x / 2. To understand that, I had to give myself a specific example:
    Suppose x = 600, then mid.x = 300, and dim.x = 100. mid.x - (dim.x / 2) = 300 - 50 = 250. As dim.x = 100, the x coord of the top right value of the glitch area is 250 + 100 = 250, which is 250 pixels away from the right edge of the canvas.
This effectively centers the glitch area horizontally. The same goes for the y coord, centering the area vertically. Math.floor needed to be used because coord values must be an interger.
`sorter.glitch(pos, dim)`: sorter calls one PixelSorter class. glitch(pos, dim) applies the glitch effect to the dimension defined by the coords provided by pos and dim.
```
const quicksort = a => {
   if (a.length <= 1) return a

   let pivot = a[0]
   let left = []
   let right = []

   for (let i = 1; i < a.length; i++) {
      if (a[i].br < pivot.br) left.push (a[i])
      else right.push (a[i])
   }

   const sorted = [ ...quicksort (left), pivot, ...quicksort (right) ]

   return sorted
}
```
`if (a.length <= 1) return a` means that the condition is a.length being either 0 or 1, which means the array is already defined I think. I'm not too sure about this one.
The pivot is chosen as the first element of a array, which is 0 in this case.
Array left holds the values that are less than pivot.
Array right holds the values that are more than pivot.
For each a[i] element, if a[i].br > pivot.br, a[i] is added to the left array.
For each a[i] element, if a[i].br <> pivot.br, a[i] is added to the right array.
The function returns a final array consisting of all the elements that are inside left, pivot, and right.
I'm not sure if I got this right, and I'm not sure what this does so far, since I haven't read the whole code.
```
export class PixelSorter {
   constructor (ctx) {
      this.ctx = ctx
   }

   init () {
      this.width = this.ctx.canvas.width
      this.height = this.ctx.canvas.height
      this.img_data = this.ctx.getImageData (0, 0, this.width, this.height).data
   }


   glitch (pos, dim) {
      const find_i = c => ((c.y * this.ctx.canvas.width) + c.x) * 4 

      for (let x_off = 0; x_off < dim.x; x_off++) {
         const positions = []

         for (let y_pos = pos.y; y_pos < pos.y + dim.y; y_pos++) {
            positions.push (find_i ({ x: pos.x + x_off, y: y_pos }))
         }

         const unsorted = []

         positions.forEach (p => {
            const r = this.img_data[p]
            const g = this.img_data[p + 1]
            const b = this.img_data[p + 2]
            const a = this.img_data[p + 3]
            const br = r * g * b
            unsorted.push ({ r, g, b, a, br })
         })

         const sorted = quicksort (unsorted).reverse ()

         let rgba = []

         sorted.forEach (e => {
            rgba.push (e.r)
            rgba.push (e.g)
            rgba.push (e.b)
            rgba.push (e.a)
         })

         rgba = new Uint8ClampedArray (rgba)

         const new_data = this.ctx.createImageData (1, dim.y)
         
         new_data.data.set (rgba)

         this.ctx.putImageData (new_data, pos.x + x_off, pos.y)
      }
   }
}
```
The first few lines define the constructor for PixelSorter class.
```
init () {
    this.width = this.ctx.canvas.width
    this.height = this.ctx.canvas.height
    this.img_data = this.ctx.getImageData (0, 0, this.width, this.height).data
}
this.width and this.height store the dimension of the canvas.
I'm not sure what the `.data` does in this case either.
```
const find_i = c => ((c.y * this.ctx.canvas.width) + c.x) * 4;
```
find_i is a function that calculates the starting index of a pixel in the img_data array based on its coords.
c.y is the vertical position of the pixel. this.ctx.canvas.width is the total number of pixels in one row of the canvas. Multiplying c.y by the canvas width gives the total number of pixels in all rows above the current row. Adding c.x gives the total number of pixels from the start of the image to the current pixel. I'm not sure what * 4 does in this case.
This is as far as I could go because I didn't understand what was happening in the rest of the code...

#







