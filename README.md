![alt text](https://raw.github.com/CorySimmons/jeet/master/jeet_logo.jpg "Jeet CSS Framework")

Version 2
-

Jeet takes the best of the open source HTML5/CSS3 World and combines it into a lightweight, semantic, responsive, and blazing fast framework. You can use Stylus, or SCSS, **OR BOTH!**

[Check out mini-demos at http://jeetframework.com](http://jeetframework.com/)

[Watch a screencast on Jeet 2](http://www.youtube.com/watch?v=mf-XRFTMI7M)

Quick Start
=

- Install [Ruby](http://rubyinstaller.org) (if you're on Windows)
- Add Ruby to your PATH if you're on Windows
    - Find the folder Ruby/bin folder (usually under C:/), copy this path
    - Right click on "My Computer", "Properties"
    - Advanced System Settings
    - Environment Variables
    - Global
    - Path
    - Append a semi-colon and the path to Ruby/bin
- Install [Compass](http://compass-style.org/install/)
- Install [NodeJS](http://nodejs.org/)
- Install [LiveReload Browser Extension](http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-) of your choice
- Open up a terminal and type `npm install -g jeet`
- Type `jeet -h`
- Navigate to any directory you want, type `jeet create JeetProject`
- `cd JeetProject`
- `jeet watch`
- Open `index.html` in the browser of your choice and activate LiveReload by opening Settings > Tools > Extensions and checking `Allow access to file URLs` then clicking the icon (the dot in the middle should be dark)
- Edit either `css/scss/style_scss.scss` or `css/styl/style_styl.styl`
- Enjoy


Features
=

- Responsive
- Lightweight
- Semantic
- Highly customizable
- IE7+
- Fluid
- Blazing fast

Moving Parts
=

- [Semantic.gs](http://semantic.gs/)
- [Stylus](http://learnboost.github.com/stylus/) / [nib](http://visionmedia.github.com/nib/) **or** [SCSS](http://sass-lang.com/) / [Compass](http://compass-style.org/)
- [HTML5 Boilerplate](http://html5boilerplate.com/)
- [Modernizr](http://modernizr.com/)
- [respond.js](https://github.com/scottjehl/Respond) (makes IE use media queries)
- [placeholder.js](https://github.com/mathiasbynens/jquery-placeholder) (gives you cross-browser access to placeholder attributes in inputs)
- [boxsizing.htc](https://github.com/Schepp/box-sizing-polyfill) (so Box-Sizing works in IE browsers)
- Heavy customization stuff to make it all work seamlessly together

Docs
=

*Note*: Since Jeet works with either Stylus or SCSS I'll be refering to their respective directories as "preprocessor" and their extensions as "ext". In the function definitions **I'll be using Stylus syntax**, but it's pretty identical to SCSS.

Everything in Jeet is sized in percentages. Go into `css/preprocessor/style_ext.ext` and add any styling you want. Open a Terminal, cd to your project directory, and type `jeet watch`.
This will compile both preprocessors. Your changes should be reflected in your page.

### center(max_width = 1410px)

`center()` allows you to create a wrapping container that centers everything inside it on your page.

`max_width` - The default `max_width` is specified in your framework files and just sets the maximum width of your container. You can change this on the fly like so: `center(980px)`.

**Usage:**

    #full_width_header
        background blue
        > div
            center()

---

### column(ratio = 1, nested = false, parent_ratio = 1, g = gutter) [column, col]

The `column()` and `span()` functions have been completely rewritten. Specify a fraction of your containing element, for instance applying `col(1/2)` to 2 `divs` in a container will set them to 48% width with a 1% gutter on each side of them.

If you are nesting elements inside another element, you should set `nested` to `true`.

`ratio` - specify a fraction here, for instance `col(3/4)` or `col(0.75)`. Any float number will also work so you have as much control as you want. The math is easier if you maintain a common denominator between your elements (see usage), but you don't have to.

`nested` - setting this to `true` will remove the left gutter from the first element, and the right gutter from the last element.

`parent_ratio` - when specified it will create equidistant nested column gutters. If the column is nested multiple times you'll need to multiply all the parent ratios until you get back to the root (see usage).

`g` - allows you to create custom-sized gutters

**Usage:**
        
    aside
        col(1/5)
    article
        col(4/5)


    header
        a
            col(1/4)
        nav
            col(3/4)
            a
                col(1/2, nested: true, 3/4)
            div
                col(1/2, nested: true, 3/4)
                a
                    col(1/3, nested: true, 3/4*1/2) //Both parent's ratios are multiplied

---

### span(ratio = 1)

Use `span()` to specify you don't want gutters applied to this element. This is great for things like horizontal navigation buttons or anything that you want to sit side-by-side.

`ratio` - specify a fraction here, for instance `span(1/3)`.

**Usage:**
    
    #navigation a
        span(1/6)

---

### offset(ratio = 0, nested = false, parent_ratio = 1, left_or_right = left, col_or_span = column, g = gutter) [off]

Offset is used to add a mathematically generated `margin-left` or `margin-right` to the element. In this way, you can put accurate space between elements by pushing off of them with any element.

`ratio` - specify a fraction here.

`nested` - set this to `true` if you're offsetting a nested column.

`parent_ratio` - set this when you're offsetting a nested column, this works the same way as the `parent_ratio` argument for `col()`.


`left_or_right` [left, right, l, r] - decides if the element will have a margin-left or right

`col_or_span` [column, col, c, span, s] - decides whether you want your margin to have spacing with gutters added to it or not. Typically set this to whatever elements are surrounding it. For instance, if you have a few `div`s sized with `column()` then you would set your `offset()` to something like: `offset(1/4, left_or_right: r, col_or_span: c)`. If the surrounding elements are `span()` then your syntax would be `offset(1/4, left_or_right: r, col_or_span: s)`.

`g` - use this to set the gutter if you've used a custom gutter amount for the other elements in the row.

Be mindful to make your fractions leave you with space to apply offsets without tossing elements to the next row down. For instance:


**Usage:**

    #list_of_three_blocks
        div
            col(1/4)
        div.second
            offset(1/4)

---

### get(ratio = 1, nested = false, col_or_span = column, g = gutter)

You can now return percentage sizes for use anywhere in your styles. Specify a fraction then pick whether you want the gutter included sizing or not. This has limited uses, but nevertheless, it's available to you if you should need it. This is also good if you don't trust `col()` or `span()` for whatever reason and want to set floats and such independent of a framework.

`ratio` - specify a fraction here

`nested` - set to `true` if you're calculating widths for nested elements.

`col_or_span` [column, col, c, span, s] - do you want gutter widths included in your returned value

`g` - set a custom gutter size for this calculation.

**Usage:** 

    .post img
        width get(1/3, col_or_span: s)

---

### bp(w = 705px, mobile_first = false) *and* endbp()

`bp()` specifies a display breakpoint. This basically opens a media query on the fly for you that you must close with `endbp()`. You can add as many `bp()` calls as you want anywhere in your code.

`w` - Accepts a specified width. By default this is 705px but it's recommended you manually contract your browser width to see when things start breaking and specify a `bp()` at a few pixels above the browsers breaking width.

`mobile_first` [f, mf] - If you set `mobile_first` to `mf` like so `bp(705px, mf)` then this will change your media query from `max-width` to `min-width` effectively giving you the tools to design for mobile first.

`endbp()` - Accepts no parameters, it just closes your media queries and is required anytime you use `bp()`.

---

### stack(align = c)

This mixin lets you quickly specify an element to be "stacked". It effectively sets the width of the element to 100% and gives it a margin-bottom of 2%. If you don't want margin-bottom, you can overwrite that after your `stack()` call, but it generally looks good.

`align` [c, l, r] - Sets the text alignment of the element to center, left, or right, depending on your needs. Defaults to centered text which reads well on mobile.

**Usage:**

    bp()
    #nav, #masthead, #article
        stack()
    endbp()

---

### btn(bg_color = #eee, radius = 10px, style = flat)

`btn()` was added as an example to show users how to quickly create custom reusable elements. If you end up making some cool, reusable elements, please [submit them](https://github.com/CorySimmons/jeet/pulls) and we can add them.

`btn()` effectively lets you create custom [Bootstrap-like buttons](http://twitter.github.io/bootstrap/base-css.html#buttons) on the fly.

`bg_color = #eee` [hex, rgb, or hsl value] - Specify whatever color you'd like your button to be.

`radius = 10px` [any size] - Set the border radius.

`style = flat` [flat, glossy] - Set the style of button you want. Flat creates a very subtle gradient whereas glossy creates a sharp gradient.

**Usage:**

    button
        btn(yellow, 3px, glossy)

*Note*: Color math in programming is pretty complicated so sometimes you'll get some screwy text color associated with your button (try `btn(blue)` for an example). If this happens, just overwrite it with the color you want. It's not optimal, but color math is a whole *thing*. Feel free to go the extra mile, fix this, and submit a pull request.

**Example:**

    button
        btn(blue)
        color #fff

---

### edit()

`edit()` mode sets:

    *
        transition 200ms ease all

Why? Because when you're editing with LiveReload and hit save, you'll see blocks fly into position like [Isotope](http://isotope.metafizzy.co/) which is totally sweet and helps visualize the structure of your site.

---

### pxfix()

Safari and Opera like to round percentages down. As a result, 33.333333% turns into 33%. Mathematically this is correct, but in the web world, this results in missing pixels here and there. Usually at the end of a row of elements. `pxfix()` cures this with Nicole Sullivan's fix for last elements in a row.

**Warning** This will cause the last element in a container to take up the remaining width of the container. `pxfix()` works best when applied to the last element in a row.

**Usage:**

    .row
        &:last-child
            pxfix()

Troubleshooting
=

**Q** `npm install -g jeet` throws permission errors

**A** You probably already installed something to your node_modules directory with root permissions so the root user took control of that directory. You can either run `sudo npm install -g jeet` (sucks) or actually **fix the problem** by running `sudo chown YOURUSERNAME /wherever/you're/getting/the/permission/error/node_modules` then uninstalling all the stuff in that folder (`sudo npm uninstall -g foo`) then reinstalling it all as a normal user (`npm install -g foo`). This will fix all kinds of stuff Jeet will work great.

**Q** My SCSS is being overwritten by my Stylus!

**A** Swap these two lines in your index.html

    <link rel="stylesheet" href="css/scss/style_scss.css">
    <link rel="stylesheet" href="css/styl/style_styl.css">

**Q** I get SCSS compilation errors on `jeet watch`

**A** I'll bet my soul you don't have Ruby installed and in your PATH, or you don't have Compass. Test these by typing `ruby` in your Command Prompt and then `compass`. If these don't throw errors and Jeet still is having problems, submit a bug in the Issue tracker.

FAQ
=

**Q** Where can I ask Jeet related questions?

**A** Several places! The fastest way is to Tweet [@jeetframework](http://twitter.com/jeetframework); if you're not in a hurry, it'd be nice if you posted questions on Stack Overlow under the [CSS-Frameworks tag](http://stackoverflow.com/questions/tagged/css-frameworks); if you believe there's an underlying bug or problem with the framework, open or comment on an issue at the [issue tracker](https://github.com/CorySimmons/jeet/issues).


**Q** Why "Jeet"?

**A** Named after Bruce Lee's, Jeet Kune Do. Mr. Lee combined the best of every martial art into his own fighting style. Jeet Framework does the same by taking the best parts and leaving out the bloat.

**Q** Who's in charge here?!

**A** Jeet was originally created and is maintained by [Cory Simmons](http://twitter.com/ccccory). Since then [Oskar Zamorowski](http://twitter.com/ozamorowski) stepped up to maintain the [SCSS port](https://github.com/CorySimmons/jeet/tree/master/web/css/scss) and just generally be a big help with the website and docs. The incredible [Gabriel Manricks](http://twitter.com/GabrielManricks) was nice enough to build and maintain the awesome [npm package](https://npmjs.org/package/jeet).

**Q** Goals for this project?

**A** I'd like to continue fixing bugs as they pop up, and implement as many feature requests as possible until this framework rules them all. The next big update are really flexible styling functions. Think the `btn()` command, on crack, for typography, form styling, buttons, tables, etc. Leave suggestions in the [issue tracker](https://github.com/CorySimmons/jeet/issues).
