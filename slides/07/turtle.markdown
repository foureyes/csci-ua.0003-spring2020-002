---
layout: slides
title: Turtle Graphics 
---
<section markdown="block" class="title-slide">
#  Turtle Graphics
{% include title-slide-footer.html %}
</section>

<section markdown="block">
##  Turtle

__turtle__ is a Python module...

* that allows you to draw programmatically
	* think of a virtual [pen plotter](https://www.youtube.com/watch?v=iziP0cQhOFY&feature=youtu.be&t=20s)
	* commands are given to a movable pen
	* that pen can move and draw on a two dimensional plane
	* the pen is called a turtle!
* it's essentially a Python implementation of another language called [Logo](http://en.wikipedia.org/wiki/Logo_(programming_language))

</section>

<section markdown="block">
##  Some History

So, what's this __Logo__ thing about?

* Logo is an __educational__ language
* one of its most well-known features is turtle graphics 
* built on theory of constructionist learning
	* learning by experimentation
	* learning by making tangible things!
* created in the mid 60's(!) by a group of computer scientists: Daniel G. Bobrow, Wally Feurzeig, Seymour Papert and Cynthia Solomon
</section>

<section markdown="block">
##  Seymour Papert

* Papert, in particular, is well known for his work in education and computing
* developed an influential theory on learning called _[constructionism](http://en.wikipedia.org/wiki/Constructionist_learning)_
* was the director of the MIT Artificial Intelligence Laboratory
* besides inventing Logo, also collaborated with Lego (it's not confusing that that's one vowel away from Logo) on a robotics kit called [Mindstorms](http://en.wikipedia.org/wiki/Lego_Mindstorms)

</section>



<section markdown="block">
##  Great, So... Why Turtle?

Imagine you have a turtle hanging out on the beach...

<div class="img-container" markdown="block">![Turtle](../../resources/img/turtle.jpg) 
</div>
</section>

<section markdown="block">
##  Turtles Drawing Stuff

* imagine further that it's a robotic turtle (__AWESOME!__)
* ...that you can give commands to
	* move forward
	* turn around
* as it moves, it leaves tracks on the ground
* turtle graphics _simulates this_ (seriously)
	* your window is a sandy beach
	* the turtle, is... well... um... a turtle (a virtual robotic one)
</section>

<section markdown="block">
##  What Does That Mean for Us?

So... in Python, we now have access to our own drawing turtle

* we can draw by writing code
* that code is analogous to the commands that we would give the turtle (or pen, or pointer, or _whatever_)
	* move forward
	* turn around
* but in addition, we can also
	* change colors
	* ask for user input
	* etc.
</section>

<section markdown="block">
##  Hello Turtle
<aside>Enough Talk.  What Does This Code Actually Look Like?</aside>

This draws a line (that's exactly 200 pixels).  (exciting).  Let's try running it.
<pre><code data-trim contenteditable>
{% include classes/13/hello.py %}
</code></pre>
</section>

<section markdown="block">
##  About the Drawing Environment

* obviously, we're drawing on a two-dimensional plane
* the turtle starts at the center
* the turtle is facing right (imagine that it's looking east)
* __can you guess what the coordinates (x and y values) are at the center__?
* __where are the positive x values... and the positive y values__?

</section>

<section markdown="block">
##  About the Drawing Environment Continued

* you can use __leo.forward(200)__ as a clue!
* if that drew a 200 pixel line, then, maybe
* the center is at (0, 0)
* positive x values are to the right of the origin, positive y, above
* (yeah, maybe that's obvious, but some graphics packages have a different coordinate plane)
</section>

<section markdown="block">
##  Let's Dissect That Code

bring in the turtle module
<pre><code data-trim contenteditable>
import turtle
</code></pre>
create a Screen object (this provides a canvas to draw on, and some window related commands)
<pre><code data-trim contenteditable>
wn = turtle.Screen()
</code></pre>
create a Turtle object to draw with
<pre><code data-trim contenteditable>
leo = turtle.Turtle()
</code></pre>
</section>

<section markdown="block">
##  Let's Dissect That Code Continued
tell the turtle to move forward 200 pixels
<pre><code data-trim contenteditable>
leo.forward(200)
</code></pre>
start the program!
<pre><code data-trim contenteditable>
wn.mainloop()
</code></pre>
</section>

<section markdown="block">
##  Objects

So... I used the word __object__ there a few times.  What does that actually mean?

* __object__ - a _thing_ that a variable name can refer to, like a screen or a turtle
* ...in fact, all of the values in Python are things
* they're objects too: "hello" is a str object, 42 is an int object
* an __object__ can have __attributes__ ...data associated with an object
* an __object__ can have __methods__ ...which are basically things that the object can do
</section>

<section markdown="block">
##  Methods

* a __method__ is essentially a function that's associated with a particular object
* you can _call_ a method just like a function... but you have to use the dot operator
* object.method() - it's similar to using a method in a module!
* for example: leo.forward(200) 
* ...means I'm calling the forward() function on the turtle object called leo
* in fact... we can see some methods on objects that we've used before!

<pre><code data-trim contenteditable>
dir("hello")
</code></pre>
</section>

<section markdown="block">
##  Let's Look at That Code Again...
<pre><code data-trim contenteditable>
{% include classes/13/hello.py %}
</code></pre>
</section>

<section markdown="block">
##  The Basic Steps Are...

What did we have to do?

1. bring in the __turtle module__
2. create a __Screen object__
3. create at least one __Turtle object__
4. tell the __Screen object__ to start the program
</section>

<section markdown="block">
##  So, That's Some Boilerplate Stuff

We should probably convert our hello program into a template.  You'll need to write this stuff every time you create a program with turtle:

<pre><code data-trim contenteditable>
{% include classes/13/template.py %}
</code></pre>
</section>

<section markdown="block">
##  A Note On Names

* in the template, I use __t__ as the variable name for my turtle.  
* it's just a variable name; it can be anything you want (same with __wn__, but you have to change wn everywhere you see it)
* in fact, in my previous programs, I called the turtle leo, in honor of one of these guys


</section>


<section markdown="block">
##  Basic Turtle Methods

These are all methods that you can call on your __Turtle__ object.

* __forward__(_distance_) - move the turtle forward by the specified _distance_
* __right__(_angle_) - turn the turtle right by _angle_ degrees
* __left__(_angle_) - turn the turtle left by _angle_ degrees
* __back__(_distance_) - move the turtle back by the specified _distance_

<pre><code data-trim contenteditable>
t.forward(200)
t.right(45)
</code></pre>
</section>

<section markdown="block">
##  Forward, Right, Left, Back - Code

__BTW... what do you think this draws? &rarr;__

<pre><code data-trim contenteditable>
{% include classes/13/basic.py %}
</code></pre>
</section>

<section markdown="block">
##  Screen and Pen Drawing Attributes

Methods you can call on your __Turtle__ object:

* __color__(_colorstring_) - change the color of your _pen_ to _colorstring_, which can be "red", "green", etc.
* __pensize__(_size_) - change the size of your pen to _size_

<pre><code data-trim contenteditable>
t.color("blue")
</code></pre>

Methods you can call on your __Screen__ object

* __setup__(width, height) - window dimensions (default is 50% and 75% of screen)
* __bgcolor__(_colorstring_) - change the background color of your window to _colorstring_

<pre><code data-trim contenteditable>
wn.bgcolor("pink")
</code></pre>
</section>

<section markdown="block">
##  Color, Background and Pen Size
<pre><code data-trim contenteditable>
{% include classes/13/color.py %}
</code></pre>
</section>

<section markdown="block">
##  Moving Without Drawing

Methods you can call on your __Turtle__ object:

* __up__() - pick the pen up so that the turtle object doesn't draw when it moves
* __down__() - put the pen down so that the turtle object draws when it moves
<pre><code data-trim contenteditable>
t.up()  # picks the pen up, doesn't draw when the turtle moves
</code></pre>
</section>


<section markdown="block">
##  Pen Up, Pen Down

__BTW... what do you think this draws? &rarr;__

<pre><code data-trim contenteditable>
{% include classes/13/pen.py %}
</code></pre>
</section>

<section markdown="block">
##  Going Somewhere?

A method you can call on your __Turtle__ object:

__goto__(_x_, _y_) - move the turtle to the specified coordinates ..._x_ and _y_.  Note that if the pen is down, it will draw up to that coordinate.

<pre><code data-trim contenteditable>
t.goto(200, 200)  # picks the pen up, doesn't draw when the turtle moves
</code></pre>
</section>

<section markdown="block">
##  Goto

__BTW... what do you think this draws? &rarr;__

<pre><code data-trim contenteditable>
{% include classes/13/goto.py %}
</code></pre>
</section>

<section markdown="block">
##  A Confused Turtle

A quick demo using goto: __let's try incorporating random elements to our drawings!__ &rarr;

<div class="fragment" markdown="block">
<pre><code data-trim contenteditable>
{% include classes/13/confused.py %}
</code></pre>
</div>
</section>
<section markdown="block">
##   Let's Use What We Know to Create a Square!

__How would we tell the turtle to create a square with the upper left corner at the origin? Each side should be 200px long.  We just learned goto, so let's try that.&rarr;__

<div class="fragment" markdown="block">
<pre><code data-trim contenteditable>
{% include classes/13/square_goto.py %}
</code></pre>
</div>
</section>

<section markdown="block">
##  Another Square!

__Same thing, but this time, just use forward or back and either left or right.  &rarr;__

<div class="fragment" markdown="block">
<pre><code data-trim contenteditable>
{% include classes/13/square_basic.py %}
</code></pre>
</div>
</section>

<section markdown="block">
##  For a Square....

__How can we simplify the previous version?  There was a lot of repeated code! &rarr;__

<div class="fragment" markdown="block">
Clearly, this calls for a __for loop__!

<pre><code data-trim contenteditable>
{% include classes/13/square_with_loops.py %}
</code></pre>
</div>
</section>


<section markdown="block">
##  Enough With Squares

__Long live pentagons!__ More sides equals _more_ better, right!?

But first. Some geometry

* __sum of interior angles__ of a polygon are: 
	* (number of sides - 2) × 180°
* to get each __interior angle__ of a polygon, divide the sum of interior angles by number of sides:
	* sum of interior angles / sides
* so, the turtle has to turn 180 - the interior angle

</section>

<section markdown="block">
##  Planning for a Pentagon

So, for a pentagon, __when we apply the calculations from the previous slide...__ &rarr;

* sum_interior_angles = (5 - 2) * 180 = 540
* interior_angle = 540 / 5 = 108
* turtle_angle = 180 -108 = 72
</section>


<section markdown="block">
##  Pentagons

Ok, so that means we have 5 sides, and the turtle has to turn 72 degrees. __Let's draw one!__ &rarr;

<div class="fragment" markdown="block">
<pre><code data-trim contenteditable>
for i in range(5):
	t.forward(side_length)
	t.right(72)

</code></pre>
</div>
</section>

