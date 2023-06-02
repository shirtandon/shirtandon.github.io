---
title: Functions and Parameters Project - Ghosts
tags: [Projects, Javascript, Graphics, Functions]
style: fill
color: 
description: Spooky ghosts!
---

This project was in a unit in which we were learning how functions worked. javascript graphics can get complicated, so this project showed that complicated drawings can become as simple as a single function. We had to create and use a function that drew an entire ghost with "legs" and eyes. Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/functions-and-parameters.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
// Constants for main ghost body
var HEAD_RADIUS = 35;
var BODY_WIDTH = HEAD_RADIUS * 2;
var BODY_HEIGHT = 60;
var NUM_FEET = 3;
var FOOT_RADIUS = (BODY_WIDTH) / (NUM_FEET * 2); 

// Constants for eyes
var PUPIL_RADIUS = 4;
var PUPIL_LEFT_OFFSET = 8;
var PUPIL_RIGHT_OFFSET = 20;
var EYE_RADIUS = 10;
var EYE_OFFSET = 14;

/* Write a comment here about your overall program */
function start(){
	var centerX = getWidth()/2;
    var centerY = getHeight()/2;
    drawGhost(centerX, centerY, Color.red);
    drawGhost(100,100, Color.green);
    drawGhost(300, 200, Color.black);
    drawGhost(40, 300, Color.orange);
    drawGhost(300, 50, Color.yellow);
}

function drawGhost(centerX, centerY, color){
    // Draw body
    drawCircle(HEAD_RADIUS, color, centerX, centerY);
    drawRectangle(BODY_WIDTH, BODY_HEIGHT, color, (centerX - BODY_WIDTH / 2), centerY);
    
    // Draw eyes
    drawCircle(EYE_RADIUS, Color.white, (centerX - EYE_OFFSET), centerY);
    drawCircle(EYE_RADIUS, Color.white, (centerX + EYE_OFFSET), centerY);
    
    // Draw pupils
    drawCircle(PUPIL_RADIUS, Color.blue, (centerX - PUPIL_LEFT_OFFSET), centerY);
    drawCircle(PUPIL_RADIUS, Color.blue, (centerX + PUPIL_RIGHT_OFFSET), centerY);
    
    // Draw feet
    drawCircle(FOOT_RADIUS, color, (centerX - 2 * FOOT_RADIUS), (centerY + BODY_HEIGHT));
    drawCircle(FOOT_RADIUS, color, centerX, (centerY + BODY_HEIGHT));
    drawCircle(FOOT_RADIUS, color, (centerX + 2 * FOOT_RADIUS), (centerY + BODY_HEIGHT));
}

function drawCircle(radius, color, centerX, centerY) {
    var circle = new Circle(radius);
    circle.setPosition(centerX, centerY);
    circle.setColor(color);
    add(circle);
}

function drawRectangle(width, height, color, x, y) {
    var rect = new Rectangle(width, height);
    rect.setPosition(x, y);
    rect.setColor(color);
    add(rect);
}
{% endhighlight %}