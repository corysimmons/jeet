<p align="center">
<img width="190px" src="https://mojotech.github.io/jeet/img/jeet-logo-color.svg" title="Jeet Grid System">
</p>

[Jeet](http://jeet.gs) is the most advanced, yet intuitive, grid system on the market today. You can think of it like the spiritual successor to [Semantic.gs](http://semantic.gs/).

By making use of the power of pre-processors, we can now pass real fractions (or float numbers) as context that generates a percentage based width and gutter for grids. We're able to do this while maintaining a consistently sized infinitely nestable gutter.

Check out [this presentation](http://corysimmons.github.io/presentations/jeet-5) to learn more about what sets Jeet above other grid systems, then enjoy one of Jeet's many pre-processor flavors:

- [Stylus](stylus)
- [SCSS](scss)

Want to sandbox it right this very second? Fork some examples on [CodePen](http://codepen.io/collection/eilAH/).

Explore [Jeet Integrations](INTEGRATIONS.md) to see some community-backed plugins to your favorite frameworks and libraries.

#### Browser Support
- IE9+ and all major browsers without polyfills like Selectivizr
- With a nice boilerplate like [Boy](http://github.com/corysimmons/boy), seamless and responsive in IE7+ ([gallery](http://imgur.com/a/Z0YPD))

#### Using Ember.js or similar?

If you're using Ember.js or another framework that adds tags to your DOM (metamorph tags in the case of Ember), you may need to add:

    whatever:last-of-type {
      margin-right: 0;
    }
    
Or when your layout is stacked:

    whatever:nth-of-type(number of columns in your row) {
      margin-right: 0;
    }

In order to preserve Jeet's excellent formatting.

---

##### Jeet is curated by loving hands at...
<a href="http://mojotech.com"><img width="140px" src="https://mojotech.github.io/jeet/img/mojotech-logo.svg" title="MojoTech's Hiring"></a> <sup>(psst, [we're hiring](http://www.mojotech.com/jobs))</sup>

##### Thanks to all the [awesome contributors](https://github.com/mojotech/jeet/graphs/contributors)
