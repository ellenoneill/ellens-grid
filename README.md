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
- Columns
- Gutters
- Islands

Marked up like this:

	<div class="wrapper">
		<div class="column island">
			<div class="gutter">
			</div>
		</div>
	</div>

### Wrappers
Block level elements by default adjust to the width of the parent element. Think of it as 100% wide. The wrapper doesn't have any semantic meaning, it's a generic wrapper, so a div will do. The wrapper is used for fixing the white-space issue on inline-blocks. A single column doesn't need a wrapper.

	<div class="column">
		<div class="gutter">
		</div>
	</div>

### Columns
Columns are defined by proportion, for instance `column-1of2` (one half), `column-1of3` (one third), `column-2of3` (two thirds) and can be easily re-used as many times as you like, even when nested or applied to something other then a div, like a link. Just make sure the column fractions add up to 1.

For better responsive control define a custom component class on the wrapper. If it is not wrapped, define it on the column. You can define custom classes on both the wrapper and the columns. It's not advisable to add classes to the gutter.

	<div class="wrapper your-wrapper">
		<div class="column column-1of3 your-column">
			<div class="gutter">
			</div>
		</div>
		<div class="column column-2of3 your-column">
			<div class="gutter">
			</div>
		</div>
	</div>	
	
You don't have to use the presentational classes, you can fully customize the grid by using your own semantic classes, like 'menu' or 'sidebar'.

	<div class="wrapper">
		<div class="column sidebar">
			<div class="gutter">
			</div>
		</div>
		<div class="column main">
			<div class="gutter">
			</div>
		</div>
	</div>

Make sure to add the classes to the styles with the desired width, keeping your grid styles grouped together.

	.column-1of3,
	.sidebar {
		width: 33.33%;
	}

Just keep in mind that if you need to move a module to another place, it won't be as easy as pick up and drop. You'll have to move classes to adjust it to its new home as well.

#### Inline-block
I use inline-block elements instead of floats. Inline-blocks stay in the document flow, they don’t need to be cleared so no clearfix solutions or `overflow: hidden;`. Inline-blocks let their parent affect their horizontal and vertical position. By default they align on the baseline, I use `vertical-align:top;`. All of a sudden vertical centering is an option.

A drawback when using inline-block is that it takes whitespace into account. Any white space, new lines for instance, in the markup will be displayed with a space between them. To work around this issue I set the font-size of the wrapper to zero. A font-size of zero means the space would also be equal to zero, and then reset the required font-size on the column. [^1]

[^1]: [Fighting the Space Between Inline Block Elements](http://css-tricks.com/fighting-the-space-between-inline-block-elements/)

#### Indented
Columns can be indented by adding the `.indent` class, thereby adding whitespace equal to the width of a column or sidebar to the left. In the example below the width of a `.column-1of6` is added as left margin.

	<div class="column column-5of6 indent">
		<div class="gutter">
		</div>
	</div>

### Gutters
The biggest stumbling block to grids are gutters. The grid is flexible by using percentages for widths. We're keeping things relatively simple by using fixed margins for gutters. The distance between columns will remain equal at every breakpoint. We've used a dedicated div for the gutter to allow margins to be mixed with paddings.

#### Islands
This object is a single `.island` class used to box in content, leaving it closed on all sides like an island with padding added for extra whitespace.

	<div class="column island">
		<div class="gutter">
		</div>
	</div>

#### No gutter
Gutterless columns can be achieved by using the `.no-gutter` class on the wrapper, this class may very well be your own custom component class. I have removed the gutter div, but you could leave it in for any future adjustments.

	<div class="wrapper no-gutter">
		<div class="column column-1of3">		
		</div>
		<div class="column column-2of3">
		</div>
	</div>

### Responsive
This grid is fully responsive [^2] with a __mobile first__ [^3] approach. 

[^2]: [Responsive Web Design by Ethan Marcotte](http://www.abookapart.com/products/responsive-web-design)  
[^3]: [Mobile First by Luke Wroblewski](http://www.abookapart.com/products/mobile-first)

#### Respond.js
To enable the responsive grid in Internet Explorer 8, I added a fast & lightweight polyfill, Respond.js by Scott Jehl, for min/max-width CSS3 media queries. [^4]

[^4]: [A fast & lightweight polyfill for min/max-width CSS3 Media Queries (for IE 6-8, and more)](https://github.com/scottjehl/Respond) 

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
Works in Internet Explorer 8 and above. Internet Explorer 7 has a few issues with inline-block. If you need support for Internet Explorer 7, you can add this by declar­ing `zoom: 1; display: inline;` using conditional classes. [^5]

[^5]: [Introducing “safe CSS hacks”](http://mathiasbynens.be/notes/safe-css-hacks)

### About
Whipped together by [Ellen O'Neill](http://twitter.com/eliun), creative front-end developer at Dutch internet agency [Mirabeau](http://www.mirabeau.nl).
