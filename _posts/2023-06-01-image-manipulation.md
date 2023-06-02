---
title: Image Manipulation Project - Darken Filter
tags: [Projects, Javascript, Graphics, Images]
style: fill
color: 
description: How are images modified?
---

This unit showd us how images are translated into code and how to edit them. In this project, we had to iterate through the pixels of an image and darken only half of the RGB values. Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/image-manipulation.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
// Constants for the image
var IMAGE_URL = "https://codehs.com/static/img/about/goldengate.jpg";
var IMAGE_WIDTH = 350;
var IMAGE_HEIGHT = 250;
var IMAGE_X = getWidth() / 2 - IMAGE_WIDTH / 2;
var IMAGE_Y = getHeight() / 2 - IMAGE_HEIGHT / 2;

// Constants for the filter
var DARKENING_FACTOR = 25;
var MIN_PIXEL_VALUE = 0;

// Constants for pixel indices
var RED = 0;
var GREEN = 1;
var BLUE = 2;

// We need to wait for the image to load before modifying it
var IMAGE_LOAD_WAIT_TIME = 50;

// Filter that takes an image as a parameter 
// and darkens the pixels in the left half of the image
function darkenFilter(image) {
    for(var x = 0; x < image.getWidth() / 2; x++) {
        for(var y = 0; y < image.getHeight(); y++) {
            // Get the current pixel
            var pixel = image.getPixel(x, y);
            
            // Modify it
            var newPixel = darken(pixel);
            
            // Update the image with the modified pixel
            image.setRed(x, y, newPixel[RED]);
            image.setGreen(x, y, newPixel[GREEN]);
            image.setBlue(x, y, newPixel[BLUE]);
        }
    }
}

function darken(pixel) {
    // Get the color values from the pixel array
    var red = pixel[RED];
    var green = pixel[GREEN];
    var blue = pixel[BLUE];
    
    // Add brightening factor to each color
    var newRed = red - DARKENING_FACTOR;
    var newGreen = green - DARKENING_FACTOR;
    var newBlue = blue - DARKENING_FACTOR;
    
    // If the value is over 255, set it to 255
    newRed = Math.max(newRed, MIN_PIXEL_VALUE);
    newGreen = Math.max(newGreen, MIN_PIXEL_VALUE);
    newBlue = Math.max(newBlue, MIN_PIXEL_VALUE);
    
    // Modify the pixel with the brightened color values
    pixel[RED] = newRed;
    pixel[GREEN] = newGreen;
    pixel[BLUE] = newBlue;
    
    // Return the modified pixel
    return pixel;
}

function start() {
    // Set up the image
    var image = new WebImage(IMAGE_URL);
    image.setSize(IMAGE_WIDTH, IMAGE_HEIGHT);
    image.setPosition(IMAGE_X, IMAGE_Y);
    
    // Add it to the canvas
    add(image);
    
    // Wait for it to load before applying the filter
    setTimeout(function(){
        darkenFilter(image);
    }, IMAGE_LOAD_WAIT_TIME);
}
{% endhighlight %}