---
title: Graphics Challenge Project - Fried Egg
tags: [Projects, Javascript, Graphics]
style: fill
color: 
description: Creating an image of a fried egg in a pan
---

This project was in the middle of two sections of our learning. We were both figuring out how to place objects on the Javascript canvas and practicing pair programming to our coding. This project, drawing an egg in a pan, shows our use of both skills. Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/graphics-challenge.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
var PAN_RADIUS = getWidth()/3;
var HANDLE_WIDTH = getWidth()/2;
var HANDLE_HEIGHT = HANDLE_WIDTH/4;
var PAN_COLOR = Color.GRAY;

var PAN_BOTTOM_RADIUS = PAN_RADIUS-20;
var PAN_BOTTOM_COLOR = Color.BLACK;

var EGG_RADIUS = PAN_BOTTOM_RADIUS/4;
var EGG_WHITE_COLOR = Color.WHITE;
var EGG_YOLK_COLOR = Color.YELLOW; 

var HIGHLIGHT_RADIUS = EGG_RADIUS/4;
var HIGHLIGHT_COLOR = Color.WHITE;


function start() {
    makePan();
    addEggWhites();
    addEggYolk();
}

function makePan() {
    var handle = new Rectangle(HANDLE_WIDTH, HANDLE_HEIGHT);
    handle.setPosition(getWidth() / 2, getHeight() / 2 - HANDLE_HEIGHT / 2);
    handle.setColor(PAN_COLOR);
    add(handle);
    
    var pan = new Circle (PAN_RADIUS);
    pan.setPosition(getWidth() / 2, getHeight() / 2);
    pan.setColor(PAN_COLOR);
    add(pan);
    
    var panBottom = new Circle (PAN_BOTTOM_RADIUS);
    panBottom.setPosition(getWidth() / 2, getHeight() / 2);
    panBottom.setColor(PAN_BOTTOM_COLOR);
    add(panBottom);
}

function addEggWhites() {
    var eggWhite = new Circle(EGG_RADIUS);
    eggWhite.setPosition(getWidth() / 2, getHeight() / 1.8);
    eggWhite.setColor(EGG_WHITE_COLOR);
    add(eggWhite);
    
    var eggWhite = new Circle(EGG_RADIUS);
    eggWhite.setPosition(getWidth() / 1.7, getHeight() / 2);
    eggWhite.setColor(EGG_WHITE_COLOR);
    add(eggWhite);
    
    var eggWhite = new Circle(EGG_RADIUS);
    eggWhite.setPosition(getWidth() / 2.5, getHeight() / 1.8);
    eggWhite.setColor(EGG_WHITE_COLOR);
    add(eggWhite);
    
    var eggWhite = new Circle(EGG_RADIUS);
    eggWhite.setPosition(getWidth() / 2.5, getHeight() / 2.1);
    eggWhite.setColor(EGG_WHITE_COLOR);
    add(eggWhite);
    
    var eggWhite = new Circle(EGG_RADIUS);
    eggWhite.setPosition(getWidth() / 1.9, getHeight() / 2.2);
    eggWhite.setColor(EGG_WHITE_COLOR);
    add(eggWhite);
}

function addEggYolk() {
    var eggYolk = new Circle(EGG_RADIUS);
    eggYolk.setPosition(getWidth() / 2, getHeight() / 2);
    eggYolk.setColor(EGG_YOLK_COLOR);
    add(eggYolk);
    
    var eggHighlight = new Circle(HIGHLIGHT_RADIUS);
    eggHighlight.setPosition(getWidth() / 1.95, getHeight() / 2.1);
    eggHighlight.setColor(HIGHLIGHT_COLOR);
    add(eggHighlight);
}
{% endhighlight %}