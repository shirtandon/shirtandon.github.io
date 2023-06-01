---
title: Control Structures Project - Snake Eyes
tags: [Projects, Javascript, Control Structures]
style: fill
color: 
description: Simulating two dice and rolling until you get snake eyes
---

For this unit, we were learning how to control our code using loops, if statements, and much more. In this project, I used a simulation of two dice ad a loop-and-a-half structure to find out how many times it takes to roll snake eyes (two 1s). Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/graphics-challenge.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
function start(){
	var SENTINEL = 2;
	var i = 1;
	while(true) {
	    var roll1 = Randomizer.nextInt(1,6);
	    var roll2 = Randomizer.nextInt(1,6);
	    println("Rolled: " + roll1 + " " + roll2);
	    if(roll1+roll2 == SENTINEL) {
	        break;
	    }
	    i++;
	}
	println("It took you " + i + " rolls to get snake eyes.");
}
{% endhighlight %}