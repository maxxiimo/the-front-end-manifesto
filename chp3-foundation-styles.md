Foundation Styles
=================

HTML and CSS are the rebar of the World Wide Web. In [Chapter 1][] we laid out our HTML, and in this chapter we will build a solid CSS foundation, our foundation styles. To do so I will review some of the tools out there to help us get the job done. For our base styles we then implement this chapters [starter CSS][], and conclude with an overvie of best practices in stylesheet set up and maintenance.

Lets get started.

Preprocessors
-------------

Probably the two most well-known dynamic stylesheet preprocessors in use today are [Sass][] and [Less][]. Sass is the sister of [Haml][], it is my preprocessor of choice, and the default preprocessor in Rails 3.X. As a Rails front end developer you are going to find Sass in many projects you work on – as a consultant or as a new member of an existing team and project – so it would be worth your while to get your head around it if you haven't already.

NOTE: If your new to preprocessors the following articles give an excellent overview on why Sass is great, and more importantly, an introduction to Sass in Rails:

- [David Walsh on Redesigning with Sass][Redesigning with Sass]
- [An Introduction to Sass in Rails 1][Sass in Rails 1]
- [An Introduction to Sass in Rails 2][Sass in Rails 2]

When using Sass you have a choice in syntax: .sass or .scss. I prefer the .sass syntax and throughout this chapter will use it. Most front end developers will probably prefer the .scss syntax because it looks familiar (it is similar to CSS), and because that is what ships out-of-the-box in Rails, however, the .sass syntax is cleaner/terser (IMHO). To help you decide on the best syntax for you, check out the article:

- [Sass vs. SCSS: Which Syntax is Better?][Sass vs. SCSS]

So what about [Less][]? Well it's the runner-up.

TIP: When using Sass or Haml the following resources are absolutely indispensable:

- [css2sass][]
- [Html2Haml][]
- [html2haml Gem][]

Compass
-------

Right off the bat I have to say that I love [Compass][]. It's based on Sass, powerful, well-documented, widely used, there are a ton of extensions for it, and it makes life easier. What's not to love?

> Compass is an open-source CSS Authoring Framework.

\- [Compass][]

All the [starter CSS][] files we will use in our foundation styles incorporate Compass.

In the next section will take a brief look at CSS frameworks and grid systems, but only a brief look because we are not going to use them in our foundation styles. Through Compass you can add all kinds of framework components like:

- [Susy][] or [Zen Grids][]
- [Sassy Buttons][] or [Fancy Buttons][]

Essentially, you can create your own framework with a unique look and feel. I'm not against using CSS frameworks, but I find at times they can be limiting; if you want to break free it takes some tinkering.

When working with Compass the following resource might be useful to you:

- [35 Great Resources for Compass and Sass][35 Great Resources]

CSS Frameworks and Grid Systems
-------------------------------

Although my preference is to use Compass, I don't want to discourage you from adopting a framework in your project. Frameworks can be extremely helpful, especially when starting a new project. They give you a whole boatload of base styles that are instantly accessible through HTML tags and/or IDs and class names. They include base font sizes and rhythm, default formats for almost every kind of HTML tag, and by simply following the frameworks parameters, or dropping in a specified class name, you can add some great looking styles to your project; that are built to work, with very few hitches, across all browsers. On top of that most CSS frameworks come with prebuilt scripts for commonly used functions like pop-ups, modals and menu systems. The list goes on.

You'll find a roundup of the most well-known [frameworks][Appendix 1] in the Appendices.

One thing to note about CSS frameworks is that pretty much all of them include a grid system, and if you don't want to use a CSS framework there are also a number of standalone grid systems that might be useful to you. If you're not 100% sure what a grid system is, take a look at:

- [Grids Are Good][]

Why use a grid system? The following quote most succinctly answers this question:

> After a few minutes of griddy thinking, the benefits become clear: designers gain a rational, structured framework for organizing content and users gain well-organized, legible sites.

\- [Fluid Grids by Ethan Marcotte][Fluid Grids]

You'll find a comprehensive roundup of [grid systems][Appendix 2] in the Appendices for you to review and choose from, just keep in mind though that in [Chapter 5][Chapter 5 - Susy] we will learn to use [Susy][].

Our Foundation
--------------

With a basic overview of Compass and CSS frameworks and grid systems behind us, it's time to build our foundation styles. As I mentioned previously, our [stylesheets][starter CSS] are written using Sass, but more important than the actual styles themselves – there are really not that many included – is the way that they are organized.

We will cover organization in great detail in [Chapter 4 - Stylesheet Review][Chapter 4], because in my experience, as you move along in developing and the project grows in complexity, as different authors contribute, stylesheets can become behemoths, unmanageable, and downright confusing. To avoid this I highly recommend that you start a project with some kind of organizational structure in place from the get-go. The styles we will use in this chapter do exactly this.

### Compass Set Up

1.  If you have not done so already per [Chapter 1][], add `gem 'compass-rails'` to your gemfile and run:

        $ bundle exec compass init

    Compass will generate a configuration file and stylesheets. Delete the stylesheets found in `app/assets/stylesheets`:

        - ie.css.scss
        - print.css.scss
        - screen.css.scss

    We're going to use our own.

    NOTE: For more explicit directions take a look at the [compass-rails][] gem source.

2.  Delete your `application.css` file and replace it with a blank `application.scss`.

    IMPORTANT: When using Compass always use @import to organize styles rather than Sprockets. You can use Sprockets require syntax, however per the explanation found at the [compass-rails][] gem source, this is not a good idea.

3.  Add the following commented out code to your `config/compass.rb` file generated in step 1:

        # To allow compass to import partials from subdirectories per
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/.
        # additional_import_paths = ["app/assets/stylesheets/<name>", "app/assets/stylesheets/<name>"]

        # To compile in the necessary debugging information for FireSass.
        # sass_options = {:debug_info => true}

    If you have problems with subfolders within your `assets/stylesheets` folder, uncomment the `additional_import_paths` line.

    If you use Firefox I highly recommend using [FireSass][]. It allows you to see exactly where sass partial styles are coming; from which is extremely helpful when debugging. Uncomment the `sass_options` line if you plan to use FireSass.

4.  Edit `config/application.rb`:

    Uncomment the following:

          # If you want your assets lazily compiled in production, use this line
          Bundler.require(:default, :assets, Rails.env)

    If you find your system has a problem with sass partial underscores when precompiling, add the following:

        # Precompile *all* assets, except those that start with underscore per:
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
        config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

    \- [Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work]

Commit your changes and that's it! You now have Compass and all that it brings available to you.

Some additional resources for working with Compass include:

- [Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work]
- [How I Use Compass With Rails 3.1][How I Use Compass]
- [Sass, Compass, and the Rails 3.1 Asset Pipeline][Asset Pipeline]

### Stylesheet Set Up

Now that Compass is set up, let's set up our stylesheets. Clone this books [starter CSS][]:

    git clone git@github.com:maxxiimo/base-css.git

Setting up our CSS is pretty straightforward. Basically, all you have to do is copy into your project the cloned files and subfolders exactly as they are laid out, in their entirety. You will only need to replace the blank `application.scss` file, otherwise you should have no other files in your stylesheets directory, unless you forgot to delete `application.css` when setting up Compass.

Your stylesheet file structure should now look like this:

app<br>
|-- assets<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-- stylesheets<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- boilerplate<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_h5bp_helpers.scss][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_h5bp_normalize_v102.scss][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_h5bp_normalize_v111.scss][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_h5bp_print.scss][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- desktop<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_forms.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_grids.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_layout.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_navigation.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_pages.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_staging.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_typography.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_define.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_media_queries.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_media_queries_px.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_misc.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_mixins.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_sprites.sass][]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [application.scss][]<br>

NOTE: You may have noticed that the base application file uses the .scss syntax, and other other partials use the .sass syntax. This is perfectly fine and done so in part because Rails needs this file to end in .scss, and with the boilerplate files to keep abreast of boilerplate changes is easier to use this syntax. Everything else and whenever possible I use the .sass syntax because of my own personal preference for it.

NOTE: Why the "desktop" subfolder? To better organize desktop specific files. In the [Chapter 5][] we will create another subfolder called "mobile". Files outside of these two folders are common to both desktop and mobile device types. This will become clear to you in Chapter 5.

And now with everything in place your page should now look something like this:

![][Basic Styles]

It's pretty basic, but much better than [before][]. More importantly and much like in [Chapter 1][], the greatest benefit of what we have done can be found under the hood. In this chapter it is the organization and structure of the stylesheets we imported into our project, a very solid foundation, and the tools we're using to help us write styles. In the [next chapter][Chapter 4] we will dissect and explain in detail our stylesheet structure and organization as well as explore best practices in stylesheet development and maintenance.

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md
[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp4-stylesheet-review.md
[Chapter 5]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-mobile-foundation.md
[Appendix 1]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-1
[Appendix 2]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-2
[starter CSS]:          https://github.com/maxxiimo/base-css

[Sass]:                 http://sass-lang.com/
[Less]:                 http://lesscss.org/
[Haml]:                 http://haml-lang.com/
[Redesigning with Sass]: http://css-tricks.com/redesigning-with-sass/
[Sass in Rails 1]:      http://rubysource.com/an-introduction-to-sass-in-rails/
[Sass in Rails 2]:      http://rubysource.com/an-introduction-to-sass-in-rails-2/
[Sass vs. SCSS]:        http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better
[css2sass]:             http://css2sass.heroku.com/
[Html2Haml]:            http://html2haml.heroku.com/
[html2haml Gem]:        https://github.com/haml/html2haml

[Compass]:              http://compass-style.org/
[Susy]:                 http://susy.oddbird.net/
[Zen Grids]:            http://zengrids.com/
[Sassy Buttons]:        http://jaredhardy.com/sassy-buttons/
[Fancy Buttons]:        http://brandonmathis.com/projects/fancy-buttons/
[35 Great Resources]:   http://fuelyourcoding.com/35-great-resources-for-compass-and-sass/

[Grids Are Good]:       http://www.subtraction.com/pics/0703/grids_are_good.pdf
[Fluid Grids]:          http://www.alistapart.com/articles/fluidgrids/
[Chapter 5 - Susy]:     https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-mobile-foundation.md#1-flexible-grids

[compass-rails]:        https://github.com/Compass/compass-rails
[FireSass]:             https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[How I Use Compass]:    http://patrickward.com/code/2011/08/19/how-i-use-compass-with-rails-3-dot-1/
[Asset Pipeline]:       http://www.engineyard.com/blog/2011/sass-compass-and-the-rails-3-1-asset-pipeline/

[_h5bp_helpers.scss]:   https://github.com/maxxiimo/base-css/blob/master/boilerplate/_h5bp_helpers.scss
[_h5bp_normalize_v102.scss]: https://github.com/maxxiimo/base-css/blob/master/boilerplate/_h5bp_normalize_v102.scss
[_h5bp_normalize_v111.scss]: https://github.com/maxxiimo/base-css/blob/master/boilerplate/_h5bp_normalize_v111.scss
[_h5bp_print.scss]:     https://github.com/maxxiimo/base-css/blob/master/boilerplate/_h5bp_print.scss
[_forms.sass]:          https://github.com/maxxiimo/base-css/blob/master/desktop/_forms.sass
[_grids.sass]:          https://github.com/maxxiimo/base-css/blob/master/desktop/_grids.sass
[_layout.sass]:         https://github.com/maxxiimo/base-css/blob/master/desktop/_layout.sass
[_misc.sass]:           https://github.com/maxxiimo/base-css/blob/master/desktop/_misc.sass
[_navigation.sass]:     https://github.com/maxxiimo/base-css/blob/master/desktop/_navigation.sass
[_pages.sass]:          https://github.com/maxxiimo/base-css/blob/master/desktop/_pages.sass
[_staging.sass]:        https://github.com/maxxiimo/base-css/blob/master/desktop/_staging.sass
[_typography.sass]:     https://github.com/maxxiimo/base-css/blob/master/desktop/_typography.sass
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[_media_queries.sass]:  https://github.com/maxxiimo/base-css/blob/master/_media_queries.sass
[_media_queries_px.sass]: https://github.com/maxxiimo/base-css/blob/master/_media_queries_px.sass
[_mixins.sass]:         https://github.com/maxxiimo/base-css/blob/master/_mixins.sass
[_sprites.sass]:        https://github.com/maxxiimo/base-css/blob/master/_sprites.sass
[application.scss]:     https://github.com/maxxiimo/base-css/blob/master/application.scss

[before]:               https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md#end-result

[Basic Styles]:         http://chrismaxwell.com/manifesto/chp-3/basic-styles.png
