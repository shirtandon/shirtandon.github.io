---
title: Data Structures Project - Fried Egg
tags: [Projects, Javascript, Data Structures]
style: fill
color: 
description: Coin flipper simulation model
---

With this project, we were learning how to control arrays and iterate through them for useful applications. In this case, I made a model that simulated coin flips in an array then iterate through it and count the amount of heads or tails. Here's a video: 

<video width="600" controls="controls">
  <source src="/assets/vids/basic-data-structures.mp4">
</video>

Below you can also see the code used for the project: 

{% highlight javascript %}
var NUM_FLIPS = 100;

function start(){
	var flips = flipCoins();
	countHeadsAndTails(flips);
}

// This function should flip a coin NUM_FLIPS
// times, and add the result to an array. We
// return the result to the caller.
function flipCoins(){
	var flips = [];
	for(var i = 0; i < NUM_FLIPS; i++){
		if(Randomizer.nextBoolean()){
			flips.push("Heads");
		}else{
			flips.push("Tails");
		}
	}
	return flips;
}

function countHeadsAndTails(arr){
	
	var heads = 0;
	var tails = 0;
	
	for(var i = 0; i < arr.length; i++){
		if(arr[i] == "Heads") {
		    heads++;
		} else {
		    tails++;
		}
	}
	println("Heads: " + heads);
	println("Tails: " + tails);
}
{% endhighlight %}