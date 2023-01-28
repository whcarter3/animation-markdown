# Animation using HTML, CSS & Javascript/jQuery

## Learning Goals

* Hear a story from the history of animation
* Learn how the history relates to digital animation
* Learn why animation is a powerful tool when used correctly
* Explore practical examples of animation on the web
* Learn the difference between CSS Transitions & @keyframes
* See how jQuery can be used for animations
* Build a functioning dropdown menu from scratch

## A story from the history of animation

There is a large and storied history of animation which in itself could fill an entire course.

One of my favorite pieces of that history is a story involving [**Eadweard Muybridge**](https://en.wikipedia.org/wiki/Eadweard_Muybridge).

In the late 1800s, Muybridge had a bet with a professor at a university.

The professor bet Muybridge that a horse in full running motion always had one of it's limbs touching the ground. Muybridge thought he was wrong, so he set out to prove he was right.

He set up a series of cameras along a long stretch of road. As the horse was running, he triggered the camera to catch the horse in various positions of its run.

![Eadweard Muybridge studies a horse in motion](https://upload.wikimedia.org/wikipedia/commons/7/73/The_Horse_in_Motion.jpg)

Ultimately you can see, Muybridge was right. And, he essentially created a study of motion through capturing different **frames** over a given period of **time**.

![Horse in motion](https://upload.wikimedia.org/wikipedia/commons/0/07/The_Horse_in_Motion-anim.gif)

Without knowing it, Muybridge became the inventor of a technique that was used in one of the most successful movie franchises of all time. **The Matrix**. Yes, Muybridge just invented bullet-time, and he didn't even know it.

![Camera setup](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcQePS3UhFEADaX8vexn_Ionk8hg8rsTh5NgOcw9CF4JtogtOox_QA) ![Compilation](http://sabia.tic.udc.es/gc/Contenidos%20adicionales/trabajos/Peliculas/FX/imagenes/ejemplos/matrix_montage_html.jpg)

## How that awesome story relates to digital animation

Clearly, technology has advanced. 

Companies like Pixar are so good at animation they can simulate individual hair strands, albeit over a very long period of [time](https://www.insidescience.org/content/brave-features-hair-raising-animations/689). See Brave, 2012.

The way computers work now, you only need 3 basic things to make an animation

1. Starting frame
2. Ending frame
3. Duration (usually in seconds or milliseconds)

If I have a `<div></div>` with `position: absolute`, `height: 50px` and `width: 50px`, and I want to animate it to go diagonally downward across the page, I only need to have:

1. First frame: ``` top: 0, left: 0 ```
2. Ending frame: ``` top: 300px, left: 300px ```
3. Duration: ```animation-duration: 5s```

The computer will draw all the frames necessary for the animation to have the **illusion** of motion.


## A powerful tool when used correctly

"With great power comes great responsibility" - Spiderman's Uncle Ben

First let's look at someone that used it incorrectly.

[DON'T DO THIS](http://gochat.us)

This immediately makes me want to leave the page.

1. The information is difficult to decipher
2. The animation provides no meaning 
3. You force the user to make unintended choices

#### 2 great examples of meaningful animation

Apple produts are ripe with examples of good animation

1. Have everyone put their computers to sleep and try to log in with the wrong password
    * The animation gives immediate feedback of my action
    * It's grounded in a human element
    * With no written or verbal cue, I know I need to re-enter my password
2. Send an email with apple mail
    * Same reasons as above
    * you feel as if the mail is actually being physically sent away
    
#### Examples of animation on the web
1. [Shameless self-promotion](http://looking.la/projects.php)
2. [Val Head - queen of animation](http://alistapart.com/article/ui-animation-and-ux-a-not-so-secret-friendship)

## CSS Transitions and @keyframes

2 main ways of achieving animation via CSS is the `transition` property, and the `@keyframes` selector

#### The `Transition` Property

Transition property is used to animate property changes on an element most commonly used with the `:hover` psuedo-selector

`transition: <property> <duration> <timing-function> <delay>;`

HTML:

```
	<div class="box"></div>
```
CSS:

```
	.box{
		width: 80px;
  		height: 80px;
  		background-color: orange;
  		transition: background-color 5s /*=== add first ===*/, transform 1s /*==== add second ====*/;
  		margin: 40px auto;
	}
	
	/* add all below */
	.box:hover{
  		background-color: green; /* first */
  		transform: rotate(180deg) scale(2); /* second */
	}
```
Shorten transition to use `all` and stay **DRY**!

```
	.box{
		width: 80px;
  		height: 80px;
  		background-color: orange;
  		transition: all 5s;
  		margin: 40px auto;
	}
	
	.box:hover{
  		background-color: green;
  		transform: rotate(180deg) scale(2);
```

Add `timing-function` to control flow of animation

1. ease: default, provides fairly smooth animation
2. ease-in: slow at first, then speeds up at the end
3. ease-out: normal speed at first, the slows down at the end

```
.box{
	width: 80px;
 	height: 80px;
	background-color: orange;
 	transition: all 5s ease-out;
 	margin: 40px auto;
}

.box:hover{
 	background-color: green;
 	transform: rotate(180deg) scale(2);
}
```

#### The Keyframes property

[Lessons from thoughtbot](https://robots.thoughtbot.com/css-animation-for-beginners)

```
@keyframes awesome-animation {
  0%{
    background-color: orange;
  }
  
  100%{
    background-color: green;
    transform: rotate(180deg);
  }
}

.box{
  width: 80px;
  height: 80px;
  background-color: orange;
  margin: 40px auto;
  animation: awesome-animation 2s ease-in forwards 3s;
}
```
