<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h1 id="title">JS Animations - Website Development, Libraries, &amp; Sample Scripts</h1>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Page scrolling</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Page scrolling is one of the most popular uses for JavaScript-based
animation. A recent trend in web design is to create long webpages that
animate new pieces of content into view as the page is scrolled down.
JavaScript animation libraries, such as Velocity, provide simple
functions for scrolling elements into view:</p>

```
$element.velocity("scroll", 1000);
```

<p>This scrolls the browser toward the top edge of $element over a
duration of 1000ms using Velocity’s "scroll" command. Notice that
Velocity’s syntax is nearly identical to jQuery’s `$.animate()` function,
which is covered later in this module.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Animation reversal</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Animation reversal is a useful shorthand for undoing an element’s
previous animation. By invoking the reverse command, you’re instructing
an element to animate back to its values prior to its last animation. A
common use for reversal is animating a modal dialogue into view, then
hiding it when the user presses to close it.</p>
<p>An unoptimized reversal workflow consists of keeping track of the
specific properties that were last animated on each element that may later
be subjected to reversal. Unfortunately, keeping track of prior animation
states in UI code quickly becomes unwieldy. In contrast, with the
reverse command, Velocity remembers everything for you.
Mimicking the syntax of Velocity’s scroll command, the reverse
command is called by passing "reverse" as Velocity’s first argument:</p>

```
// First animation: Animate an element's opacity toward 0
$element.velocity({ opacity: 0 });

// Second animation: Animate back toward the starting opacity value of 1
$element.velocity("reverse");
```

<p>When it comes to JavaScript’s animation timing control, there’s more
than just reversal: JavaScript also allows you to globally slow down or
speed up all JavaScript animations currently running. You’ll learn more
about this powerful feature in Chapter 4, “Animation Workflow.”</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Physics-based motion</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The utility of physics in motion design reflects the core principle of what
makes for a great user experience (UX) on your site: interfaces that flow
naturally from the user’s input. Put another way, interfaces that pay
tribute to how objects move in the real world.</p>
<p>As a simple yet powerful introduction to physics-based motion Velocity
offers an easing type based on spring physics. (We’ll fully explore the
concept of easing in the next chapter.) With typical easing options, you
pass in a string corresponding to a predefined easing curve (for example,
"ease" or "easeInOutSine"). The spring physics easing type, in
contrast, accepts a two-item array.</p>

```
// Animate an element's width to "500px" using a spring physics easing of 500 tensions 
// units and 20 friction units
$element.velocity({ width: "500px" }, { easing: [ 500, 20 ]
});
```

<p>The first item in the easing array represents the tension of the
simulated spring and the second item represents friction. A higher tension
value increases the total speed and bounciness of the animation. A lower
friction value increases the vibration speed at the tail end of the
animation. By tweaking these values, you can give each animation on your
page a unique movement profile, which helps to reinforce the
differentiation between their individual behaviors.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Maintainable workflows</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Designing animation is an experimental process that requires repeated
tweaking of timing and easing values to achieve a uniform feel across the
page. Inevitably, just when you’ve perfected your design, a client will
request significant changes. In these situations, maintainable code
becomes critical.</p>

<p>The JavaScript-based solution to this workflow problem is wonderfully
elegant, and it’s covered in depth in Chapter 4, “Animation Workflow.”</p>

<p>For now, here’s the short explanation: There are techniques for chaining
together individual JavaScript animations—all with differing durations,
easings, and so on—such that the timing of one animation does not affect
another. This means you can change individual durations without redoing
math and you can go back and easily set animations to run either in
parallel or consecutively.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Wrapping up</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>When designing animations in CSS, you’re inherently limited to the
features that the CSS specification provides. In JavaScript, because of the
very nature of programming languages, third-party libraries have an
infinite amount of logical control over motion design. Animation engines
leverage this to provide powerful features that drastically improve
workflow and expand the possibilities of interactive motion design. That’s
what this book is all about: Designing beautiful animations as efficiently
as possible.</p>

<p>The next chapter explains how to use this book’s JavaScript animation
engine of choice: Velocity.js. In mastering Velocity.js, you’ll understand
how to leverage the features we’ve just introduced, and many more.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Types of JavaScript animation libraries</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>There are many types of JavaScript animation libraries. Some replicate
physics interactions in the browser. Some make WebGL and Canvas
animations easier to maintain. Some focus on SVG animation. Some
improve UI animation—this last type is the focus of this book.</p>

<p>The two popular UI animation libraries are GSAP (download it at
GreenSock.com) and Velocity (download it at VelocityJS.org). You’ll work
with Velocity throughout this book since it’s free under the MIT license
(GSAP requires licensing fees depending on a site’s business model), plus it
boasts incredibly powerful features for writing clean and expressive
animation code. It’s in use on many popular sites, including Tumblr, Gap,
and Scribd.</p>

<p>Oh, and it was created by the author of this book!</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Installing jQuery and Velocity</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>You can download jQuery from jQuery.com, and Velocity from
VelocityJS.org. To use them on your page—as with any JavaScript library
—simply include <script></script> tags pointing toward the
respective libraries before your page’s </body> tag. If you’re linking to
pre-hosted versions of the libraries (as opposed to local copies on your
computer), your code might look like this:</p>

```
<html>
  <head>My Page</head>
  <body>
    My content.
    <script src="//code.jquery.com/jquery-2.1.1.min.js"></script>
    <script src="//cdn.jsdelivr.net/velocity/1.1.0/velocity.min.js"> </script>
  </body>
</html>
```

<p>When using jQuery and Velocity together, include jQuery before Velocity.
That’s it! Now you’re ready to roll.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Using Velocity: Basics</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>To get oriented to Velocity, we’ll start with the basic components:
arguments, properties, values, and chaining. Since jQuery is so ubiquitous,
it is also important to look at the relationship between Velocity and
jQuery.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Velocity and jQuery</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Velocity functions independently of jQuery, but the two can be used in
combination. It’s often preferable to do so to benefit from jQuery’s
chaining capabilities: When you’ve preselected an element using jQuery,
you can extend it with a call to .velocity() to animate it:</p>

```
// Assign a variable to a jQuery element object
var $div = $("div");
// Animate the element using Velocity
$div.velocity({ opacity: 0 });
This syntax is identical to jQuery's own animate function:
$div.animate({ opacity: 0 });
```

<p>All the examples in this website use Velocity in combination with jQuery,
and therefore follow this syntax.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Arguments</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Velocity accepts multiple arguments. Its first argument is an object that
maps CSS properties to their desired final values. The properties and their
accepted value types correspond directly to those used in CSS (if you’re
unfamiliar with basic CSS properties, pick up an introductory HTML and
CSS book before reading this one):</p>

```
// Animate an element to a width of "500px" and to an opacity of 1.
$element.velocity({ width: "500px", opacity: 1 });
```

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Tip</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In JavaScript, if you’re providing a property value that contains letters (instead 
of only integers), put the value in quotes.
You can pass in an object specifying animation options as a second argument:</p>

```
$element.velocity({ width: "500px", opacity: 1 }, { duration:
400, easing: "swing" });
```

<p>There’s also a shorthand argument syntax: Instead of passing in an
options object as a second argument, you can use comma-separated
argument syntax. This entails listing values for duration (which accepts an
integer value), easing (a string value), and complete (a function value) in
any comma-separated order. (You’ll learn what all of these options do
momentarily.)</p>

```
// Animate with a duration of 1000ms (and implicitly use the
default easing value of "swing")
$element.velocity({ top: 50 }, 1000);
// Animate with a duration of 1000ms and an easing of "ease-
in-out"
$element.velocity({ top: 50 }, 1000, "ease-in-out");
// Animate with an easing of "ease-out" (and implicitly use
the default duration value of 400ms)
$element.velocity({ top: 50 }, "ease-out");
// Animate with a duration of 1000ms and a callback function
to be triggered upon animation completion
$element.velocity({ top: 50 }, 1000, function() {
alert("Complete.") });
```

<p>This shorthand syntax is a quick way of passing in animation options
when you only need to specify the basic options (duration, easing, and
complete). If you pass in an animation option other than these three, you
must switch all options to the object syntax. Hence, if you want to specify
a delay option, change the following syntax:</p>

```
$element.velocity({ top: 50 }, 1000, "ease-in-out");
```

<p>to this syntax:</p>

```
// Re-specify the animation options used above, but include a delay value of 500ms
$element.velocity({ top: 50 }, { duration: 1000, easing:
"ease-in-out", delay: 500 });
```

<p>You can’t do this:</p>

```
// Incorrect: Divides animation options between the comma-separated syntax and the object syntax
$element.velocity({ top: 50 }, 1000, { easing: "ease-in-out", delay: 500 });
```

<h3>Properties</h3>

<p>There are two differences between CSS-based and JavaScript-based property animation.</p>

<p>First, unlike in CSS, Velocity accepts only a single numeric value per CSS property. So, 
you can pass in:</p>

```
$element.velocity({ padding: 10 });
```

<p>or</p>

```
$element.velocity({ paddingLeft: 10, paddingRight: 10 });
```

<p>But you can’t pass in:

```
// Incorrect: The CSS property is being passed more than one numeric value.
$element.velocity({ padding: "10 10 10 10" });
```

If you do want to animate all four padding values (top, right,
bottom, and left), list them out as separate properties:

```
// Correct
$element.velocity({
  paddingTop: 10,
  paddingRight: 10,
  paddingBottom: 10,
  paddingLeft: 10
});
```

<p>Other common CSS properties that can take multiple numeric values
include margin, transform, text-shadow, and box-shadow.
Breaking up compound properties into their sub-properties for the
purposes of animation gives you increased control over easing values. In
CSS, you can specify only one property-wide easing type when animating
multiple sub-properties within the parent padding property, for example.</p>

<p>In JavaScript, you can specify independent easing values for each sub-
property—the advantages of this will become apparent during the
discussion of CSS transform property animation later in this chapter.
Listing out independent sub-properties can also make your animation
code easier to read and easier to maintain.</p>
<p>The second difference between CSS-based and JavaScript-based
property animation is that JavaScript properties drop the dashes between
words and all words past the first must be capitalized. For example,
padding-left becomes paddingLeft, and background-color
becomes backgroundColor. Further note that JavaScript property
names should not be in quotes:</p>

```
// Correct
$element.velocity({ paddingLeft: 10 });

// Incorrect: Uses a dash and doesn't capitalize
$element.velocity({ padding-left: 10 });
// Incorrect: Uses quotes around the JavaScript-formatted property name
$element.velocity({ "paddingLeft": 10 });
```

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Velocity supports the px, em, rem, %, deg, vw, and vh units. If you don’t provide a 
unit type with a numeric value, an appropriate one is automatically assigned based on 
the CSS property type. For most properties, px is the default unit, but a property that 
expects a rotation angle, such as rotateZ for example, would be automatically assigned 
the deg (degree) unit:</p>

```
$element.velocity({
  top: 50, // Defaults to the px unit type
  left: "50%", // We manually specify the % unit type
  rotateZ: 25 // Defaults to the deg unit type
});
```

<p>Explicitly declaring unit types for all property values increases your code’s legibility 
by making the contrast between the px unit and its alternatives more obvious when quickly 
eyeballing your code.</p>

<p>Another advantage of Velocity over CSS is that it supports four value
operators that can be optionally prefixed to a property value: +, -, *, and /.</p>

<p>These directly correspond to their math operators in JavaScript. You
can combine these value operators with an equals sign (=) to perform
relative math operations. Refer to the inline code comments for examples:</p>

```
$element.velocity({
  top: "50px", // No operator. Animate toward 50 as expected.
  left: "-50", // Negative operator. Animate toward -50 as expected.
  width: "+=5rem", // Convert the current width value into its rem equivalent and add 5 more units.
  height: "-10rem", // Convert the current height value into its rem equivalent and subtract 10 units.
  paddingLeft: "*=2" // Double the current paddingLeft value.
  paddingRight: "/=2" // Divide the current paddingLeft value into two.
});
```

<p>Velocity’s shorthand features, such as value operators, retain animation
logic entirely within the animation engine. This not only keeps the code
more concise by eliminating manual value calculation, but also improves
performance by telling Velocity more about how you plan to animate your
elements. The more logic that is performed within Velocity, the better
Velocity can optimize your code for higher frame rates.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Chaining</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>When multiple Velocity calls are chained back-to-back on an element (or a
series of elements), they automatically queue onto one another. This
means that each animation begins once the preceding animation has
completed:</p>

```
$element
// Animate the width and height properties
.velocity({ width: "100px", height: "100px" })
// When width and height are done animating, animate the top property
.velocity({ top: "50px" });
```

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Using Velocity: Options</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>To round out this introduction to Velocity, let’s run through the most commonly used 
options: duration, easing, begin and complete, loop, delay, and display.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Duration</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>You can specify the duration option, which dictates how long an animation call takes to 
complete, in milliseconds (1/1000th of a second) or as one of three shorthand durations: 
"slow" (equivalent to 600ms), "normal" (400ms), or "fast" (200ms). When specifying a 
duration value in milliseconds, provide an integer value without any unit type:</p>

```
// Animate with a duration of 1000ms (1 second)
$element.velocity({ opacity: 1 }, { duration: 1000 });
```

<p>or</p>

```
$element.velocity({ opacity: 1}, { duration: "slow" });
```

<p>The advantage to using the named shorthand durations is that they express the tempo of an 
animation (is it slow or is it fast?) when you’re reviewing your code. If you use these 
shorthands exclusively, they’ll also naturally lead to more uniform motion design across 
your site, since all of your animations will fall into one of three speed categories 
instead of each being passed an arbitrary value.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Easing</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Easings are the mathematical function.</p>

<hr>
<hr>
<hr>
<hr>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Animation libraries & web sites</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Animation makes us be able to tell stories and communicate emotions and ideas in 
a unique way. Here are 30 JavaScript animation libraries to use in your projects today.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>
<ol>
  <li><a href="https://greensock.com/">Greensock</a><br>
    <p>A JavaScript library for building high-performance animations that work in every major browser.</p></li>
  <li><a href="http://velocityjs.org/">VelocityJS</a><br>
    <p>Velocity is a lightweight animation engine with the same API as jQuery's $.animate().</p></li>
  <li><a href="https://github.com/alexfoxy/laxxx">Lax.js</a><br>
    <p>Simple & lightweight vanilla javascript plugin to create smooth & beautiful animations when you scroll!</p></li>
  <li><a href="https://github.com/dixonandmoe/rellax">Rellax.js</a><br>
    <p>A buttery smooth, super lightweight, vanilla javascript parallax library.</li>
  <li><a href="https://github.com/mrdoob/three.js/">three.js</a><br>
    <p>An easy to use, lightweight, 3D library with a default WebGL renderer.</p></li>
  <li><a href="https://wowjs.uk/">wow.js</a><br>
    <p>Reveal Animations When You Scroll.</p></li>
  <li><a href="http://chocolat.insipi.de/">Chocolat.js</a><br>
    <p>Free lightbox plugin.</p></li>
  <li><a href="https://michalsnik.github.io/aos/">Animate on Scroll</a><br>
    <p>Animate on scroll library to reveal animations when You scroll.</p></li>
  <li><a href="https://gijsroge.github.io/tilt.js/">TiltJS</a><br>
    <p>A tiny requestAnimationFrame powered 60+fps lightweight parallax hover tilt effect for jQuery.</p></li>
  <li><a href="https://roughnotation.com/">Rough Notation</a><br>
    <p>Rough Notation is a small JavaScript library to create and animate annotations on a web page.</p></li>
  <li><a href="https://particles.matteobruni.it/">tsParticles</a><br>
    <p>A lightweight library for creating particles, an improved version of the abandoned and obsolete particles.js.</p></li>
  <li><a href="https://vincentgarreau.com/particles.js/">Particles.js</a><br>
    <p>A lightweight JavaScript library for creating particles.</p></li>
  <li><a href="https://mojs.github.io/">mo.js</a><br>
    <p>The motion graphics toolbelt for the web.</p></li>
  <li><a href="https://lokeshdhakar.com/projects/lightbox2/">Lightbox2</a><br>
    <p>A small JS library to overlay images on top of the current page.</p></li>
  <li><a href="https://kenwheeler.github.io/slick/">Slick</a><br>
    <p>Fully responsive carousel.</p></li>
  <li><a href="https://barba.js.org/">Barba.js</a><br>
    <p>Create fluid and smooth transitions between your website’s pages.</p></li>
  <li><a href="https://locomotivemtl.github.io/locomotive-scroll/">Locomotive Scroll</a><br>
    <p>A simple scroll library that provides detection of elements in viewport & smooth scrolling with parallax.</p></li>
  <li><a href="https://owlcarousel2.github.io/OwlCarousel2/">Owl Carousel</a><br>
    <p>Free responsive jQuery carousel.</p></li>
  <li><a href="https://swiperjs.com/">SwiperJS</a><br>
    <p>Free, Open Source, Modern Slider without jQuery. Available for Vanilla JS and all modern frameworks like React, 
	  Vue, Angular etc.</p></li>
  <li><a href="https://splidejs.com/">Splide</a><br>
    <p>Free, pure JS library for carousels and sliders.</p></li>
  <li><a href="https://simpleparallax.com/">Simple Parallax</a><br>
    <p>The easiest way to get a parallax effect with javascript.</p></li>
  <li><a href="https://sarcadass.github.io/granim.js/index.html">Granim.js</a><br>
    <p>Create fluid and interactive gradient animations with this small javascript library.</p></li>
  <li><a href="https://popmotion.io/">Popmotion</a><br>
    <p>Simple animation libraries for delightful user interfaces.</p></li>
  <li><a href="https://maxwellito.github.io/vivus/">Vivus</a><br>
    <p>Vivus is a lightweight JavaScript class (with no dependencies) that allows you to animate SVGs, giving them 
	  the appearence of being drawn.</p></li>
  <li><a href="https://mattboldt.com/demos/typed-js/">Typed.js</a><br>
    <p>A JavaScript Typing Animation Library.</p></li>
  <li><a href="https://kimmobrunfeldt.github.io/progressbar.js/">Progress Bar JS</a><br>
    <p>Responsive and slick progress bars with animated SVG paths.</p></li>
  <li><a href="https://animejs.com/">AnimeJS</a><br>
    <p>Lightweight JavaScript animation library with a simple, yet powerful API.</p></li>
  <li><a href="https://anijs.github.io/">AniJS</a><br>
    <p>A Library to Raise your Web Design without Coding.</p></li>
  <li><a href="https://www.remotion.dev/">Remotion</a><br>
    <p>This is not an animation library per se but you can use this to make videos by writing Javascript code.</p></li>
</ol>
</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>More Animations</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>
<ol start="30">
  <li><a href="https://gsap.com/">GSAP</a><br>
    <p>A wildly robust JavaScript animation library built for professionals.</p></li>
  <li><a href="http://paperjs.org/">Paper.js</a><br>
    <p>Paper.js is an animation library with a strict focus on animating vector graphics.</p></li>
  <li><a href="https://web-animations.github.io/web-animations-demos/">Web Animatons</a><br>
    <p>This library is a direct JavaScript port of the Web Animation API. The library integrates directly with 
    the Element.animate() specification, letting you use animation features typically written using CSS logic</p></li>
  <li><a href="https://drawcall.github.io/Proton/">Proton</a><br>
    <p>Javascript particle animation engine.</p></li>
  <li><a href="https://mojs.github.io/">Mo.js</a><br>
    <p>mo.js developer tools helps you when you are building and debugging your animations.</p></li>
  <li><a href="https://p5js.org/">P5.js</a><br>
    <p>p5.js is a JavaScript library for creative coding, with a focus on making coding accessible and 
      inclusive for artists, designers, educators, beginners, and anyone else! </p></li>
  <li><a href="https://www.framer.com/motion/">Motion</a><br>
    <p>Complete documentation of the Framer Motion animation library. A production-ready motion library for React.</p></li>
  <li><a href="https://popmotion.io/">Pop Motion</a><br>
    <p>The animator’s JavaScript toolbox.</p></li>
</ol>
</h4>

