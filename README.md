jQuery Simple Presentation Plugin
=================================
Yet another jQuery presentation plugin.



Adrià Mercader - [http://amercader.net](http://amercader.net)


Description
-----------
This is a tiny jQuery plugin that allows you to easily build simple web
presentations. It has only a small set of features (i.e. the ones that I needed
for my presentation):

* Navigation buttons
* Keyboard shortcuts
* Incrementally showing slide elements
* Slide events


Usage
-----
Include the plugin script and CSS file:

    <link rel="stylesheet" href="js/slides/jquery.slides.css">
    <script src="js/slides/jquery.slides.js" type="text/javascript"></script>

Write your markup as shown:

    <div id="container">
       <div class="slide">
            <h2>Slide 1</h2>

            <!-- Slide contents -->

        </div>

        <div class="slide">
            <h2>Slide 2</h2>

            <!-- Slide contents -->
        </div>

        <!-- etc -->

    </div>

Create your slide from your script as follows:

    $("#container").slides();

These default options can be overridden:

    "first" : 1             // First slide to show
    "useNav":true           // Show navigators
    "useKeyboard":true      // Use keyboard shortcuts
    "centerContents":true   // Center contents vertically in slide

Increments
----------
Any element with the class "incremental" will be shown one step at the time:

    <div class="slide">
        <h2>Slide 1</h2>
        <div class="incremental">First point</div>
        <div class="incremental">Second point</div>
    </div>

    <div class="slide">
        <h2>Slide 2</h2>
        <ul>
            <li class="incremental">First point</li>
            <li class="incremental">Second point</liv>
            <li class="incremental">Third point</liv>
        </ul>
    </div>

    <div class="slide">
        <h2>Slide 3</h2>
        <div>Visible from the beginning</div>
        <img class="incremental" src="wow.png" alt="Will appear later" />
    </div>

Events
------
You can listen to two types of events. `show_slide.slide` will be fired every
time a slide is shown, but `load_slide.slide` only the first time.


    <div class="slide" id="slide-1">
        <h2>Slide 1</h2>

        <!-- Slide contents -->

    </div>


    $("#slide-1").bind("load_slide.slides",function(e,data){
        // This will be executed only the first time this slide is shown
    });

    $("#slide-1").bind("show_slide.slides",function(e,data){
        // This will be executed every time this slide is shown
    });

    $("#container").find("div").bind("show_slide.slides",function(e,data){
        // This will be executed every time a slide is shown

        console.log("You are on slide "+data.current+" of "+data.count)
    });

Apart from the event object, the callback will receive an object with the
following properties:

* `target`: A reference to the slides container
* `slides`: A reference to the array of slides
* `count`: The total number of slides
* `current`: The current slides
* `settings`: Initial settings
