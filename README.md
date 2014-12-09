# Ellen’s Grid

> The grid system is an aid, not a guarantee. It permits a number of possible uses and each designer can look for a solution appropriate to his personal style. But one must learn how to use the grid; it is an art that requires practice.
>
> — Josef Müller-Brockma

Grids are needed in order to arrange media and content elements such as text, images or video. It makes it easier to design clearly, consistently and with an eye to continuity. The grid is the foundation of any solid design.

## Features
My grid consists of basic responsive HTML and CSS, with a bit of Sass pre-processing. I tried to make the HTML as self-explanatory as possible for guys who refuse to read manuals ;)

These are the features:

- Ribbon container
- Ribbon
- Restrainer
- Grid container
- Grid
- Module container
- Module
- Outer gutter
- Inner gutter
- Island

Which looks like the HTML below when all features are in use. I know ... kind of ugly, but your visitors won't inspect the source and at least it clearly tells developers what it does.

    <div class="ribbon-container">
        <div class="ribbon your-ribbon-class">
            <div class="restrainer">
                <div class="grid-container your-grid-container-class">
                    <div class="grid-1of2">
                        <div class="module-container">
                            <div class="module gutter-outer gutter-inner island your-module-class">
                            	...
                            </div>
                        </div>
                    </div>
                    <div class="grid-1of2">
                        <div class="module-container">
                            <div class="module gutter-outer gutter-inner island your-module-class">
                            	...
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>


## Demo
[http://ellenoneill.github.io/ellens-grid](http://ellenoneill.github.io/ellens-grid)

### Examples
The `all-modules` template features all possible modules, an example without outer gutters and one example with nested grids.

The `example-with-sidebar` template features a content page with a sidebar. Grid containers are outlined.

The `example-homepage` template features a homepage layout. Grid containers are outlined.

### Stylesheets
`grid.scss` contains all grid styling. You could use it as is or tweak the breakpoints and module widths to your liking.

`config.scss` contains configuration settings, mainly the restrainer width and gutter sizes, adjust to your liking.

`demo.scss` sole purpose is to add some styling to demonstrate my grid. You can throw this out the window and add your own styling.

## Ribbon container and ribbon
A ribbon is a horizontal strip, stretching from the left side of the page all the way to the right side. Ribbons can vary in colour.

    <div class="ribbon-container">
        <div class="ribbon your-ribbon-class">
            ...
        </div>
    </div>

### Ribbon container
The ribbon container prevents margins from collapsing.

### Ribbon
Background colour, paddings and margins are applied to the `ribbon` class. Define a custom class on the ribbon to apply a different background colour for instance.

## Restrainer
The sole purpose of a restrainer is to restrain content to a custom width and to horizontally align this content. No further styling is to be applied.

	<div class="restrainer">
    	...
	</div>

## Grid container and grid

    <div class="grid-container your-grid-container-class">
        <div class="grid-1of2">
            ...
        </div>
        <div class="grid-1of2">
            ...
        </div>
    </div>

### Grid container
The purpose of a grid container is to contain a group of grids and to clear floats. The `grid-container` class can be applied to something more sematic then a `div`, like a `main` or `sidebar`. For better responsive control define a custom class on the grid container.

### Grid
Grids are defined by proportion, for instance `grid-1of2` (one half), `grid-1of3` (one third), `grid-2of3` (two thirds) and can be easily re-used as many times as you like, even when nested or applied to something more sematic then a `div`, like a `section` or `article`. Just make sure the fractions add up to 1. It's not advisable to add custom classes to the grid.

#### Floats
I moved back from inline-block elements to floats due to a white-space bug on Android. This obviuously means they need to be cleared.

#### Offset
Grids can be offset by adding the `offset-left`, `offset-right` or `offset-both` (= centered) class, thereby filling up the space so the fractions add up to 1. In the example below the width of a `grid-1of6` is added as left margin.

    <div class="grid-5of6 offset-left">
    	...
    </div>

## Module container, module, outer gutter, inner gutter and island

    <div class="module-container">
        <div class="module gutter-outer gutter-inner island your-module-class">
            ...
        </div>
    </div>

### Module container
The module container prevents margins from collapsing and clears floats.

### Module
A module can be applied to something more sematic then a `div`, like a `section` or `article`. Define a custom class on the module.

### Gutters
The biggest stumbling block to grids are gutters. The grid is flexible by using percentages for widths. I keep things relatively simple by using fixed margins for gutters. The distance between modules will remain equal at every breakpoint. The margins and paddings can be adapted to the desired values in `config.scss`.

#### Outer gutter
In principle, all modules feature an outer gutter (margin), except when a row of modules should stick to eachother, this is when the `.gutter-outer` class can be removed.

#### Inner gutter
Only modules that need an inner gutter (padding), feature the `gutter-inner` class, the _island_ (see below) is such a module. Of course the inner gutter or padding can be applied as CSS to the modules custom class, instead of adding the the `gutter-inner` class to the HTML.

### Island
I extended the `module` class by adding a modifier to it, the `island` class. This class is used to box in content, leaving it closed on all sides like an island. You can define a background color or border. This serves primarily as an example, you might as well use a custom class.

## Responsive
This grid is responsive [^2] with a __mobile first__ [^3] approach. 

[^2]: [Responsive Web Design by Ethan Marcotte](http://www.abookapart.com/products/responsive-web-design)  
[^3]: [Mobile First by Luke Wroblewski](http://www.abookapart.com/products/mobile-first)

### Breakpoints
The media query breakpoints used are as follows. Of course you're free to define your own breakpoints.

Size   | Breakpoint | Default
:----- | :--------- | :-----:
Tiny   | < 480px    | x
Small  | > 480px    | 
Medium | > 768px    | 
Large  | > 996px    | 
Huge   | > 1280px   | 

### Nested grids
The responsiveness of nested grids can't be guaranteed. Define a custom class on the grid container for better responsive control.

## Browser support
Works in latest versions of Google Chrome, Safari, Firefox and Internet Explorer 9 and above.

### Polyfills
To enable the responsive grid in Internet Explorer 8 you need to add the Respond.js polyfill for min/max-width CSS3 media queries [^4] and the Selectivizr polyfill for CSS3 selectors [^5].

[^4]: [Respond.js by Scott Jehl](https://github.com/scottjehl/Respond)  
[^5]: [Selectivizr by Keith Clark](http://selectivizr.com)

## Quick tip
Don't kick-off your project with the homepage, homepages usually contain a lot of 'out of the box' modules. It's better to build a solid foundation first.

## About
Whipped together by [Ellen O'Neill](http://twitter.com/eliun), creative front-end developer at Dutch internet agency [Mirabeau](http://www.mirabeau.nl).
