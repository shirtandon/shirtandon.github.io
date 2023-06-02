---
title: Winter Break Project - Winter Wonderland
tags: [Projects, Javascript, Graphics]
style: fill
color: 
description: Randomly generated winter scenes!
---

For winter break, we were allowed to have creative freedom and design a scene of our own creation. I decided to make a nornal-looking winter scene with snow and a tree, but the image is randomly generated! Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/winter-break.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
var SNOW_RADIUS = 3;
var treeX = Randomizer.nextInt(50, (getWidth() - 50));
drawRect(getWidth(), getHeight(), "CadetBlue", 0, 0);
drawRect(getWidth(), getHeight() / 4, "AliceBlue", 0, (3/4) * getHeight());

var tree = new Polygon();
tree.addPoint(treeX - 50, 325);
tree.addPoint(treeX, 175);
tree.addPoint(treeX + 50, 325);
tree.setColor("ForestGreen");
add(tree);
drawRect(30, 35, "SaddleBrown", treeX - 15, 325);
drawCircle(10, Randomizer.nextColor(), treeX, 245);
drawCircle(10, Randomizer.nextColor(), treeX - 10, 275);
drawCircle(10, Randomizer.nextColor(), treeX + 10, 305);

for(var i = 0; i < 100; i++) {
    drawCircle(SNOW_RADIUS, "AliceBlue", Randomizer.nextInt(SNOW_RADIUS, (getWidth() - SNOW_RADIUS)), Randomizer.nextInt(SNOW_RADIUS, ((getHeight()*3/4) - SNOW_RADIUS)))
}

// Draw a circle with given radius and color at the given point
function drawCircle(radius, color, x, y) {
    var circle = new Circle(radius);
    circle.setColor(color);
    circle.setPosition(x, y);
    add(circle);
}

// Draw a rectangle with given width, height, and color at the given point
function drawRect(width, height, color, x, y) {
    var rect = new Rectangle(width, height);
    rect.setColor(color);
    rect.setPosition(x, y);
    add(rect);
}
{% endhighlight %}