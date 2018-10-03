---
layout: post
title:  "Stealth Puzzle Game in 1 Week"
categories: Game-Dev
comments: true
tags: Game-a-Week Game-Development UnityEngine stealth puzzle game
description: This was the first game of my game a week project. All things told it was a bit of a failure in terms of actual gameplay...
---

> ![Game Screenshot]({{site.url}}/assets/images/Stealth_Puzzle.png)

# [Check out the game on Github!](https://github.com/bwy-dev/1weekpuzzle)
&nbsp;

This was the first game of my game a week project. All things told it was a bit of a failure in terms of actual gameplay, however I learned a lot from the experience.

## How to play:

&nbsp;

You play as a suspiciously mobile orange box (or the contents therein) , get to the green victory square without entering the line of site of the security guards! You can move to any adjacent panel by clicking on it, and wait a turn by clicking on the panel you currently occupy.


## A post-mortem:

&nbsp;

### The pros:
&nbsp;

-   It works! - I was half expecting to fail to make a working game at the end of that first the week, so the fact that it runs at all and has 2 playable levels is a good success.
-   In terms of planned features I managed to fit the vast majority in.
-   I learned a lot about Unity in this short space of time, I hadn't used it a huge amount before, and I had never taken a game - however short and simple - from start to finish like this.

### The cons:
&nbsp;

-   The levels are far too easy - in my head I was going to make about 5-6 levels for it, getting progressively harder, I actually had 4 levels fully planned out, but was only able to get 2 actually working for the deadline. Looking back on it this was a bad way to go about things and I instead should have worked on 1 or 2 harder puzzles, and showcased all the features I had planned properly.
-   No animations - I had planned to have the guards animated, as well as the player, as it stands it is hard to tell what the player is supposed to be (a person hiding in a box) and the guards are just T-posed. This is mostly fine however since it is just meant to be a prototype, so the real failing was in spending any time planning those things out, I may as well have just used a cube for the main character and a capsule for the guards.
-   no feedback - there is nothing to show which spaces you can move to, which spaces the guard is looking at, where the guard will go next etc this makes it feel bad to play.

### The Take-aways:
&nbsp;

-   I am not very good at designing puzzles (would have been good to know beforehand!) .
-   I overestimate how much I can do in a week (I sort of knew this already, which was why I started this project in the first place)
-   I should focus on getting all gameplay working with placeholders as the very first step, all else is secondary.
-   WRITE A QUICK DESIGN DOC - my mind is unreliable and on multiple occasions I wish I had planned out roughly what I would need beforehand instead of just jumping in and altering as I went. A week is too much of a short time to risk the kinds of delays that come with that style of development.

&nbsp;

This was a fun little project, all of the code I wrote for it was really basic, but I learned some interesting tricks within Unity itself, and found some handy solutions to problems I came across. For instance the guards follow a set path, and I found the easiest way to program this path was simply to make a `public List<GameObject>` , then fill it in-editor with the movement panels in the order I wanted them to travel, and iterate over it in code. As someone who had hardly used Unity before this helped me realise how useful public objects can be in Unity for interacting in editor.