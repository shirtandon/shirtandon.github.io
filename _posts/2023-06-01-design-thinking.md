---
title: Design Thinking Project - Graphing Calulator Simulation
tags: [Projects, Javascript, Graphics, Partner]
style: fill
color: 
description: How to use a TI-Nspire CX II CAS Graphing Calculator
---

This project was done with a partner, in my case Andy. Together, we prototyped, designed, tested, and presented a program that simulated a graphing calulator in ordert to get users to learn how to use it. Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/design-thinking.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
var sceneCounter = 0;

var SCREEN_X = 135;
var SCREEN_Y = 135;
var SCREEN_WIDTH = 130;
var SCREEN_HEIGHT = 95;

var time = 0;

function start() {
    var welcome = new Text("How to Use a TI-Nspire CX II CAS Graphing Calculator", "12pt Arial");
    welcome.setPosition(
        getWidth() / 2 - welcome.getWidth() / 2,
        welcome.getHeight()
    );
    add(welcome);
    
    var bg = new Rectangle(300, 40);
    bg.setPosition((getWidth() - bg.getWidth()) / 2, (getHeight() - bg.getHeight()) / 2);
    bg.setColor(Color.black);
    add(bg);
    
    var click = new Text("Click anything yellow (like me!) to continue", "12pt Arial");
    click.setPosition(
        getWidth() / 2 - click.getWidth() / 2,
        getHeight() / 2
    );
    click.setColor(Color.yellow);
    add(click);
    
    mouseClickMethod(drawNextScene);
}

function printTime() {
    time++;
}

function drawNextScene(e) {
    var elem = getElementAt(e.getX(), e.getY());
    if (elem != null && elem.getColor() == Color.yellow) {
        sceneCounter++;
        removeAll();
        drawScene(sceneCounter);
    }
}

function drawScene(num) {
    drawCalculator();
    var screen;
    if (num == 1) {
        screen = new Rectangle(SCREEN_WIDTH, SCREEN_HEIGHT);
        screen.setPosition(SCREEN_X, SCREEN_Y);
        add(screen);
        drawSelectCircle(10, 260, 250);
        drawText("Turn the calculator on!", 0, 50);
        setTimer(printTime, 1);
    }
    if (num == 2) {
        screen = new WebImage("https://i.imgur.com/2r7l8Oj.jpeg");
        screen.setSize(SCREEN_WIDTH, SCREEN_HEIGHT);
        screen.setPosition(SCREEN_X, SCREEN_Y);
        add(screen);
        drawSelectRect(40, 8, 138, 155);
        drawSelectCircle(5, 157, 404);
        drawText("Go to the scratchpad!", 0, 50);
    }
    if (num == 3) {
        screen = new WebImage("https://i.imgur.com/eu6VrN1.png");
        screen.setSize(SCREEN_WIDTH, SCREEN_HEIGHT);
        screen.setPosition(SCREEN_X, SCREEN_Y);
        add(screen);
        drawSelectRect(110, 80, 160, 320);
        drawText("Add a calculation!", 0, 50);
    }
    if (num == 4) {
        screen = new WebImage("https://i.imgur.com/Qa44GGK.jpeg");
        screen.setSize(SCREEN_WIDTH, SCREEN_HEIGHT);
        screen.setPosition(SCREEN_X, SCREEN_Y);
        add(screen);
        drawSelectCircle(10, 142, 265);
        drawText("Go to the graph page!", 0, 50);
    }
    if (num == 5) {
        screen = new WebImage("https://i.imgur.com/gtQdheC.jpeg");
        screen.setSize(SCREEN_WIDTH, SCREEN_HEIGHT);
        screen.setPosition(SCREEN_X, SCREEN_Y);
        add(screen);
        drawSelectRect(110, 80, 160, 320);
        drawText("Add a graph!", 0, 50);
    }
    if (num == 6) {
        drawText("Congrats!", 0, 50);
        stopTimer(printTime);
        println(time + " \"milliseconds\"");
    }
}

function drawSelectCircle(radius, x, y) {
    var circle = new Circle(radius);
    circle.setPosition(x, y);
    circle.setColor(Color.yellow);
    circle.opacity = 0.5;
    add(circle);
}

function drawSelectRect(width, height, x, y) {
    var rect = new Rectangle(width, height);
    rect.setPosition(x, y);
    rect.setColor(Color.yellow);
    rect.opacity = 0.5;
    add(rect);
}

function drawText(text, x, y) {
    var txt = new Text(text, "30pt Arial");
    txt.setPosition(x, y);
    add(txt);
}

function drawCalculator() {
    var calc = new WebImage("https://m.media-amazon.com/images/I/61c8jg5GogL.jpg");
    calc.setSize(300, 400);
    calc.setPosition(47, getHeight() - 400);
    add(calc);
}
{% endhighlight %}