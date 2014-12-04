# Ellen’s Grid (README is not up to date yet)

> The grid system is an aid, not a guarantee. It permits a number of possible uses and each designer can look for a solution appropriate to his personal style. But one must learn how to use the grid; it is an art that requires practice.
>
> — Josef Müller-Brockma

Grids are needed in order to arrange media and content elements such as text, images or video. It makes it easier to design clearly, consistently and with an eye to continuity. The grid is the foundation of any solid design.

## No rocket science
My grid consists of basic responsive HTML and CSS, with a bit of Sass pre-processing. It's no rocket science ... In this latest version I tried to make the HTML as self-explanatory as possible, for the guys who refuse to read manuals ;)

These are the features:

- Ribbon containers
- Ribbons
- Restrainers
- Grid containers
- Grids
- Module containers
- Modules
- Outer gutters
- Inner gutters
- Islands

Which looks like this when all features are in use:

    <div class="ribbon-container">
        <div class="ribbon">
            <div class="restrainer">
                <div class="grid-container">
                    <div class="grid-1of2">
                        <div class="module-container">
                            <div class="module gutter-outer gutter-inner island">
                            </div>
                        </div>
                    </div>
                    <div class="grid-1of2">
                        <div class="module-container">
                            <div class="module gutter-outer gutter-inner island">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>


### Demo
[http://ellenoneill.github.io/ellens-grid](http://ellenoneill.github.io/ellens-grid)

### Restrainers
The sole purpose of a restrainer is to restrain content to a custom width and to horizontally align this content. No further styling is to be applied.

### Containers
The purpose of a container is to contain multiple grids. The container class can be applied to something more sematic then a `div`, like a `main` or `sidebar`. For better responsive control define a custom class on the wrapper.

    <div class="container your-container">
    	<div class="grid">	
        	<div class="module">
            	<div class="gutter">
            	</div>
        	</div>
        </div>     
    </div>

### Grids
Grids are defined by proportion, for instance `grid-1of2` (one half), `grid-1of3` (one third), `grid-2of3` (two thirds) and can be easily re-used as many times as you like, even when nested or applied to something more sematic then a `div`, like a `section` or `article`. Just make sure the module fractions add up to 1. It's not advisable to add custom classes to the grid.

    <div class="container your-container">
    	<div class="grid grid-1of3">	
        	<div class="module">
            	<div class="gutter">
            	</div>
        	</div>
        </div>     
    	<div class="grid grid-2of3">	
        	<div class="module">
            	<div class="gutter">
            	</div>
        	</div>
        </div>     
    </div>

### Modules
A module can be applied to something more sematic then a `div`, like a `section` or `article`. For better responsive control define a custom class on the module.

    <div class="container your-container">
    	<div class="grid grid-1of3">	
        	<div class="module your-module">
            	<div class="gutter">
            	</div>
        	</div>
        </div>     
    	<div class="grid grid-2of3">	
        	<div class="module your-module">
            	<div class="gutter">
            	</div>
        	</div>
        </div>     
    </div>

#### Floats
I moved back from inline-block elements to floats due to a white-space bug on Android. This means they need to be cleared with clearfix solutions or `overflow: hidden;`. I used the `:nth-child` pseudo-selector to clear floated elements at certain breakpoints.

#### Offset
Grids can be offset by adding the `.offset-left`, `.offset-right` or `.offset-both` (= centered) class, thereby adding whitespace equal to the width of a module or sidebar. In the example below the width of a `.grid-1of6` is added as left margin.

    <div class="grid grid-5of6 offset-left">
    	<div class="module">
        	<div class="gutter">
        	</div>
    	</div>
    </div>

### Gutters
The biggest stumbling block to grids are gutters. The grid is flexible by using percentages for widths. I keep things relatively simple by using fixed margins for gutters. The distance between modules will remain equal at every breakpoint. Since the gutter doesn't have any semantic meaning, I've used a `div` to allow margins to be mixed with paddings. The margins and paddings can be adapted to the desired values. It's not advisable to add custom classes to the gutter.

#### Islands
I extended the `.module` class by adding a modifier to it, the `.island` class. This class is used to box in content, leaving it closed on all sides like an island. It adds a padding to the gutter, you can define a background color or border. This serves primarily as an example, you might as well use a custom class.

    <div class="module island">
        <div class="gutter">
        </div>
    </div>

### Responsive
This grid is fully responsive [^2] with a __mobile first__ [^3] approach. 

[^2]: [Responsive Web Design by Ethan Marcotte](http://www.abookapart.com/products/responsive-web-design)  
[^3]: [Mobile First by Luke Wroblewski](http://www.abookapart.com/products/mobile-first)

#### Breakpoints
The media query breakpoints used are as follows. Of course you're free to define your own breakpoints.

Size   | Breakpoint | Default
:----- | :--------- | :-----:
Tiny   | < 480px    | x
Small  | > 480px    | 
Medium | > 768px    | 
Large  | > 996px    | 
Huge   | > 1280px   | 

### Browser support
Works in latest versions of Google Chrome, Safari, Firefox and Internet Explorer 9 and above.

#### Polyfills
To enable the responsive grid in Internet Explorer 8 you need to add the Respond.js polyfill for min/max-width CSS3 media queries [^4] and the Selectivizr polyfill for CSS3 selectors [^5].

[^4]: [Respond.js by Scott Jehl](https://github.com/scottjehl/Respond)  
[^5]: [Selectivizr by Keith Clark](http://selectivizr.com)

### Quick tip
Don't kick-off your project with the homepage, homepages usually contain a lot of 'out of the box' modules. It's better to build a solid foundation first.

### About
Whipped together by [Ellen O'Neill](http://twitter.com/eliun), creative front-end developer at Dutch internet agency [Mirabeau](http://www.mirabeau.nl).
