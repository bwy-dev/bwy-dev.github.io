---
layout: post
title:  "Fishing Minigame in 1 Week"
categories: Game-Dev
tags: Game-a-Week Game-Development UnityEngine minigame Lambda-Expressions Coroutines SQLite
description: So second week into my game a week project and I have failed to end with a playable game...
---

# [Check out the github repo here](https://github.com/bwy-dev/1weekFishing)

&nbsp;

So second week into my game a week project and I have failed to end with a playable game, between illness and college work I had so little time for this that it never really stood a chance.

### The Concept

The plan was to make a relatively involved fishing minigame, where the player would initially have to cast the line by pressing A at the optimal time on a slider bar that moved up and down. How close the player got to the "sweet spot" would determine which loot table the fish was drawn from. The fish is determined at this point because it determines how hard the next stage of the minigame is. 
From there the player would need to rotate the left stick while tapping either X, Y or B (with the player avatar moving the rod to correspond to the direction of the button being tapped) , changing at random intervals, in order to lower a bar down to zero, if the bar hits max the fish gets away.

### The Reality

In total I managed to implement a simplified version everything other than the stick rotation to reel. The final version I have of this game also has nothing happening once the player wins the minigame.

### You Learn From Your Mistakes

&nbsp;

#### SQLite

During this brief development time I learned how to set up an SQLite database in Unity from a [great guide](https://ornithoptergames.com/how-to-set-up-sqlite-for-unity/) I came across. From this I have started writing my own SQLite library for Unity which you can find [here](https://github.com/bwy-dev/SQLiteUnity3D) , I will be writing about it soon.

&nbsp;

#### Return Values from a Coroutine

Grabbing a value from a Coroutine can be a pain because returning an `IEnumerator` is a requirement for them. Thankfully Lambda Expressions can help us with that:

Simply take a `System.Action<>` as an argument:

{% highlight c# %}
public IEnumerator StartMinigame(KeyCode fishingKey = KeyCode.Space, System.Action<bool> callback = null)
{
	while (true)
	{
		if (Input.GetKey(fishingKey))
		{
			//start fishing
			callback(true);
			break;
		}
		else
		{
			callback(false);
		}
		yield return new WaitForEndOfFrame();
	}
}
{% endhighlight %}

*(please ignore the casual `while(true)` , I was being lazy)*

Then when starting the Coroutine use a Lambda Expression where the `System.Action<>` argument is taken:

{% highlight c# %}
bool recievedInput;

StartCoroutine(input.StartMinigame(KeyCode.Space, (returnValue) =>
{
	recievedInput = returnValue;
}));
{% endhighlight %}

This method can be useful for maintaining nicer code. It would be possible to achieve the same thing by referencing the main script in the input script, and then doing something like `main.recievedInput = true;` but that doesn't feel right.

### The Take-Aways

- Finding the time to make a game in a week while in college and ill is an exercise in futility.
- Using prototyping blocks and prebuilt assets is fine and preferable for this --project - I am sure I would have finished this game in time were it not for college work taking priority, but I most certainly would NOT have succeeded if I had tried to model everything myself. These games are prototypes, they dont have to look finished, they just have to work at the end of the week and be as fun as possible.

&nbsp;

*Next week  I will be continuing this game a week project, this time by trying to make a new spin on an old game, though I haven't decided what yet.* 

