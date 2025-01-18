<h1 id="title">JS Animations - Website Development, Libraries, &amp; Sample Scripts</h1>

<h3>Page scrolling</h3>
Page scrolling is one of the most popular uses for JavaScript-based
animation. A recent trend in web design is to create long webpages that
animate new pieces of content into view as the page is scrolled down.
JavaScript animation libraries, such as Velocity, provide simple
functions for scrolling elements into view:
Click here to view code image
```
$element.velocity("scroll", 1000);
```
This scrolls the browser toward the top edge of $element over a
duration of 1000ms using Velocity’s "scroll" command. Notice that
Velocity’s syntax is nearly identical to jQuery’s $.animate() function,
which is covered later in this chapter.
Animation reversal
Animation reversal is a useful shorthand for undoing an element’s
previous animation. By invoking the reverse command, you’re instructing
an element to animate back to its values prior to its last animation. A
common use for reversal is animating a modal dialogue into view, then
hiding it when the user presses to close it.
An unoptimized reversal workflow consists of keeping track of the
specific properties that were last animated on each element that may later
be subjected to reversal. Unfortunately, keeping track of prior animation
states in UI code quickly becomes unwieldy. In contrast, with the
reverse command, Velocity remembers everything for you.
Mimicking the syntax of Velocity’s scroll command, the reverse
command is called by passing "reverse" as Velocity’s first argument:
Click here to view code image
// First animation: Animate an element's opacity toward 0
$element.velocity({ opacity: 0 });
// Second animation: Animate back toward the starting opacity
value of 1
$element.velocity("reverse");
When it comes to JavaScript’s animation timing control, there’s more
than just reversal: JavaScript also allows you to globally slow down or
speed up all JavaScript animations currently running. You’ll learn more
about this powerful feature in Chapter 4, “Animation Workflow.”
Physics-based motion
The utility of physics in motion design reflects the core principle of what
makes for a great user experience (UX) on your site: interfaces that flow
naturally from the user’s input. Put another way, interfaces that pay
tribute to how objects move in the real world.
As a simple yet powerful introduction to physics-based motion Velocity
offers an easing type based on spring physics. (We’ll fully explore the
concept of easing in the next chapter.) With typical easing options, you
pass in a string corresponding to a predefined easing curve (for example,
"ease" or "easeInOutSine"). The spring physics easing type, in
contrast, accepts a two-item array.
Click here to view code image
// Animate an element's width to "500px" using a spring
physics easing of 500 tensions units and 20 friction units
$element.velocity({ width: "500px" }, { easing: [ 500, 20 ]
});
The first item in the easing array represents the tension of the
simulated spring and the second item represents friction. A higher tension
value increases the total speed and bounciness of the animation. A lower
friction value increases the vibration speed at the tail end of the
animation. By tweaking these values, you can give each animation on your
page a unique movement profile, which helps to reinforce the
differentiation between their individual behaviors.
Maintainable workflows
Designing animation is an experimental process that requires repeated
tweaking of timing and easing values to achieve a uniform feel across the
page. Inevitably, just when you’ve perfected your design, a client will
request significant changes. In these situations, maintainable code
becomes critical.
The JavaScript-based solution to this workflow problem is wonderfully
elegant, and it’s covered in depth in Chapter 4, “Animation Workflow.”
For now, here’s the short explanation: There are techniques for chaining
together individual JavaScript animations—all with differing durations,
easings, and so on—such that the timing of one animation does not affect
another. This means you can change individual durations without redoing
math and you can go back and easily set animations to run either in
parallel or consecutively.
Wrapping up
When designing animations in CSS, you’re inherently limited to the
features that the CSS specification provides. In JavaScript, because of the
very nature of programming languages, third-party libraries have an
infinite amount of logical control over motion design. Animation engines
leverage this to provide powerful features that drastically improve
workflow and expand the possibilities of interactive motion design. That’s
what this book is all about: Designing beautiful animations as efficiently
as possible.
The next chapter explains how to use this book’s JavaScript animation
engine of choice: Velocity.js. In mastering Velocity.js, you’ll understand
how to leverage the features we’ve just introduced, and many more.

<hr>
<hr>
<hr>
<hr>
<h3>Animation libraries & web sites</h3>

<p>Animation makes us be able to tell stories and communicate emotions and ideas in a unique way. Here are 30 JavaScript animation libraries to use in your projects today.</p>

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
    <p>Free, Open Source, Modern Slider without jQuery. Available for Vanilla JS and all modern frameworks like React, Vue, Angular etc.</p></li>
  <li><a href="https://splidejs.com/">Splide</a><br>
    <p>Free, pure JS library for carousels and sliders.</p></li>
  <li><a href="https://simpleparallax.com/">Simple Parallax</a><br>
    <p>The easiest way to get a parallax effect with javascript.</p></li>
  <li><a href="https://sarcadass.github.io/granim.js/index.html">Granim.js</a><br>
    <p>Create fluid and interactive gradient animations with this small javascript library.</p></li>
  <li><a href="https://popmotion.io/">Popmotion</a><br>
    <p>Simple animation libraries for delightful user interfaces.</p></li>
  <li><a href="https://maxwellito.github.io/vivus/">Vivus</a><br>
    <p>Vivus is a lightweight JavaScript class (with no dependencies) that allows you to animate SVGs, giving them the appearence of being drawn.</p></li>
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

<h3>More Animations</h3>
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

