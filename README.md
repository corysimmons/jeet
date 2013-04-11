![alt text](https://raw.github.com/CorySimmons/jeet/master/jeet_logo.jpg "Jeet CSS Framework")


Jeet takes the best of the open source HTML5/CSS3 World and combines it into a lightweight, semantic, responsive, and blazing fast framework.

[Check out demos, documentation, and screencasts at http://jeetframework.com](http://jeetframework.com/)

[Watch Jeet develop an entire IE7+ responsive website in 3 minutes while dramatically improving code quality.](http://www.screenr.com/u3c7)

[Watch the very popular webdesign.tutsplus.com screencast tutorial on Jeet](http://webdesign.tutsplus.com/tutorials/htmlcss-tutorials/working-with-jeet-an-alternative-responsive-framework/)

[Follow me on Twitter! @ccccory](https://twitter.com/ccccory)
[Follow my company on Twitter! @PressedWeb](https://twitter.com/PressedWeb)


Quick Start
=

#### Stylus
  - Install [nodejs](http://nodejs.org)
  - Install [Stylus](http://learnboost.github.com/stylus/) globally (npm install stylus -g)
  - Install [nib](http://visionmedia.github.com/nib/) globally (npm install nib -g)
  - Navigate to your /css directory via terminal
  - Run this line to have [Stylus](http://learnboost.github.com/stylus/docs/executable.html) *use* nib, *watch* your .styl file, and *compress* it

    stylus -u nib -w -c

#### Compass
  - Install [Compass](http://compass-style.org/install/)
  - Navigate to your [/css] directory via terminal
  - Run this command to have Compass watch your file for changes `compass watch`
  - Edit [/css/config.rb] to *compress* or *expand* css output

Features
=

- Responsive
- Lightweight
- Semantic
- Highly customizable
- IE7+
- Fluid
- Lightweight


Moving Parts
=

- [Semantic.gs](http://semantic.gs/)
- [Stylus](http://learnboost.github.com/stylus/) / [nib](http://visionmedia.github.com/nib/)
- [HTML5 Boilerplate](http://html5boilerplate.com/)
- [Modernizr](http://modernizr.com/)
- [respond.js](https://github.com/scottjehl/Respond) (makes IE use media queries)
- [placeholder.js](https://github.com/mathiasbynens/jquery-placeholder) (gives you cross-browser access to placeholder attributes in inputs)
- [boxsizing.htc](https://github.com/Schepp/box-sizing-polyfill) (so Box-Sizing works in IE browsers)
- [Bootstrap](http://twitter.github.com/bootstrap/) (if you'd like, feel free to omit it completely)
- Much more heavily customized stuff to make it all work seamlessly together.


FAQ
=

**Q** Why "Jeet"?

**A** Named after Bruce Lee's, Jeet Kune Do. Mr. Lee combined the best of every martial art into his own fighting style. Jeet Framework does the same by taking the best parts and leaving out the bloat.

**Q** Do you have plans to port this to LESS and SASS?

**A** Yes definitely. In the meantime, try it out on Stylus. Stylus is incredibly underrated.

**Q** Goals for this project?

**A** I'd like to continue fixing bugs as they pop up, and implement as many feature requests as possible until this framework rules them all. Leave suggestions in the [issue tracker](https://github.com/CorySimmons/jeet/issues).