# The Grid
`A Digital Frontier`

> The grid system is an aid, not a guarantee. It permits a number of possible uses and each designer can look for a solution appropriate to his personal style. But one must learn how to use the grid; it is an art that requires practice.
>
> — Josef Müller-Brockma

Grids are needed in order to arrange media and content elements such as text, images or video. It makes it easier to design clearly, consistently and with an eye to continuity. The grid is the foundation of any solid design.

## No rocket science
This grid consists of basic responsive HTML and CSS, no pre-processing applied (yet). It's no rocket science, use it as an inspiration rather than straight out.

There are four features:

- Wrappers
- Modules
- Gutters
- Islands

### Demo
[http://ellenoneill.github.io/the-grid](http://ellenoneill.github.io/the-grid)


### Wrappers
Wrappers can be defined by proportion, for instance `wrapper-1of2` (one half), `wrapper-1of3` (one third), `wrapper-2of3` (two thirds) [^1] and can be easily re-used as many times as you like, even when nested or applied to something more sematic then a `div`, like a `main` or `sidebar`. Just make sure the fractions add up to 1.

[^1]: You can use a more generic class for defining proportions on wrappers and modules like `width-1of2`, I prefer the semantic naming. 

    <div class="wrapper">
        <div class="module island">
            <div class="gutter">
            </div>
        </div>
    </div>

### Modules
Modules are defined by proportion, for instance `module-1of2` (one half), `module-1of3` (one third), `module-2of3` (two thirds) and can be easily re-used as many times as you like, even when nested or applied to something more sematic then a `div`, like a `section` or `article`. Just make sure the module fractions add up to 1.

For better responsive control define a custom class on the wrapper. If it is not wrapped, define it on the module. You can define custom classes on both the wrapper and the modules. It's not advisable to add classes to the gutter.

    <div class="wrapper your-wrapper">
        <div class="module module-1of3 your-module">
            <div class="gutter">
            </div>
        </div>
        <div class="module module-2of3 your-module">
            <div class="gutter">
            </div>
        </div>
    </div>  
    
You don't have to use the proportional classes, you can customize the grid by using your own semantic classes, like `.sidebar` or `.main`.

    <div class="wrapper">
        <div class="module sidebar">
            <div class="gutter">
            </div>
        </div>
        <div class="module main">
            <div class="gutter">
            </div>
        </div>
    </div>

Just make sure to add the classes to the styles with the desired width, keeping your grid styles grouped together.

    .module-1of3,
    .sidebar {
        width: 33.33%;
    }

Keep in mind that if you need to move a module to another place, it won't be as easy as pick up and drop. You'll have to move classes to adjust it to its new home as well.

#### Floats
I moved back from inline-block elements to floats due to a white-space bug on Android. This means they need to be cleared with clearfix solutions or `overflow: hidden;`. I used the `:nth-child` pseudo-selector to clear floated elements at certain breakpoints.

#### Offset
Modules can be offset by adding the `.offset` class, thereby adding whitespace equal to the width of a module or sidebar to the left. In the example below the width of a `.module-1of6` is added as left margin.

    <div class="module module-5of6 offset">
        <div class="gutter">
        </div>
    </div>

### Gutters
The biggest stumbling block to grids are gutters. The grid is flexible by using percentages for widths. I keep things relatively simple by using fixed margins for gutters. The distance between modules will remain equal at every breakpoint. Since the gutter doesn't have any semantic meaning, I've used a `div` to allow margins to be mixed with paddings. The margins and paddings can be adapted to the desired values.

#### Islands
I extended the `.module` class by adding a modifier to it, the `.island` class. This class is used to box in content, leaving it closed on all sides like an island. It adds a padding to the gutter, you can define a background color or border. This serves primarily as an example, you might as well use a custom class.

    <div class="module island">
        <div class="gutter">
        </div>
    </div>

#### No gutter
Gutterless modules can be achieved by using the `.no-gutter` class on the wrapper, this adds a padding to the wrapper. I kept the gutter `div` in place because it's likely some padding is still needed.

    <div class="wrapper no-gutter">
        <div class="module module-1of3">
        	<div class="gutter">
        	</div>
        </div>
        <div class="module module-2of3">
        	 <div class="gutter">
        	</div>	        
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
