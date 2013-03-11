Foundation Styles
=================

HTML and CSS are the rebar of the World Wide Web. Equally important to your application as [foundation markup][Chapter 1] are foundation styles. We laid out our HTML, now let's square away on CSS. To do so we will review some of the options out there in terms of preprocessors, CSS authoring utilities, frameworks and grid systems. For our foundation styles we'll implement this chapters [starter CSS][] – developed over the years with a lot of OCD love, then conclude with best practices in stylesheet set up and maintenance. Lets get started.

Preprocessors
-------------

Probably the two most well-known dynamic stylesheet preprocessors in use today are [Sass][] and [Less][]. Sass is the sister of [Haml][], my preprocessor of choice, and the default preprocessor in Rails 3.X. As a Rails front end developer you are going to find Sass in many projects you work on as a consultant or as a new member of an existing team and project.

If your new to preprocessors the following articles will give you a great overview on why Sass is great, and more importantly, Sass in Rails:

- [David Walsh on Redesigning with Sass][Redesigning with Sass]
- [An Introduction to Sass in Rails 1][Sass in Rails 1]
- [An Introduction to Sass in Rails 2][Sass in Rails 2]

When using Sass you have a choice in syntax; .sass or .scss. I prefer .sass. Most front end developers will probably go with the .scss syntax because it looks familiar (similar to CSS), and because that is what ships out-of-the-box in Rails, however, .sass is cleaner/terser (IMHO). To help you decide on the best syntax for you, check out the article: "[Sass vs. SCSS: Which Syntax is Better?][Sass vs. SCSS]."

NOTE: When using Sass or Haml these resources are absolutely indispensable:

- [css2sass][]
- [Html2Haml][]
- [html2haml Gem][]

So what about [Less][]? Well it's the runner-up. That's all I'm going to say about that (remember this is a manifesto which is opinionated by nature).

Compass
-------

So right off the bat I have to say that I love [Compass][]. It's based on Sass, powerful, well-documented, widely used, there are a ton of extensions for it, and it generally makes life easier.

> Compass is an open-source CSS Authoring Framework.

\- [Compass][]

All the [starter CSS][] files we will use in our foundation styles incorporate Compass.

In the next section will take a brief look at CSS Frameworks and Grid Systems, but only a brief look because we are not going to use them. Through Compass you can add all kinds of framework components like:

- [Susy][] or [Zen Grids][]
- [Sassy Buttons][] or [Fancy Buttons][]

...and essentially create your own framework with a unique look and feel. Traditional frameworks on the other hand just give you styles. If you want to break free it takes some tinkering.

When working with Compass the following resource may be useful to you:

- [35 Great Resources for Compass and Sass][35 Great Resources]

CSS Frameworks and Grid Systems
-------------------------------

Although my preference is to use Compass, I don't want to discourage you from adopting a framework in your project. Frameworks can be extremely helpful, especially when starting a new project. They give you a whole boatload of base styles that are instantly accessible through your HTML tags and/or specified class names. They include base font sizes and rhythm, default formats for almost every kind of HTML tag, and by simply dropping in the frameworks class names you can add some great looking styles to your project that are built to work, with very few hitches, across all browsers. On top of that you get prebuilt scripts for commonly used functions like pop-ups, modals and menu systems. The list goes on.

You'll find a roundup of the most well-known [frameworks][] in the Appendix.

Pretty much every framework has a grid systems incorporated into it, but there are also a number of standalone grid systems that might be useful to you. If you're not 100% positive what a grid system is, take a look at:

- [Grids Are Good][]

Why use a grid system? The following quote most succinctly answers this question:

> After a few minutes of griddy thinking, the benefits become clear: designers gain a rational, structured framework for organizing content and users gain well-organized, legible sites.

\- [Fluid Grids by Ethan Marcotte][Fluid Grids]

You'll also find a comprehensive roundup of [grid systems][] in the Appendix for you to review and choose from.

Our Foundation
--------------

It's time to build our foundation styles. Our [stylesheets][starter CSS] are written using Sass, but more important than the actual styles themselves – there are really not that many included – is the way that they are organized.

In my experience, as you move along a Rails project and the project grows in complexity, as different authors contribute, stylesheets can become behemoths, unmanageable, and downright confusing. To avoid this I highly recommend that you start a project with some kind of organizational structure in place from the get-go. The styles we will use in this chapter do exactly this.

Before we begin will need to quickly set up Compass.

### Compass Set Up

1.  If you have not done so already, per [Chapter 1][], add "compass-rails" to your gemfile. For more explicit directions take a look at the [compass-rails][] gem source.

2.  Run...

        $ bundle exec compass init

    Compass will generate a configuration file and stylesheets. Delete the stylesheets. We're going to use our own.

3.  Delete your *application.css* file and create and replace it with a blank *application.scss*.

    IMPORTANT: Use @import to organize styles rather than Sprockets. You can use Sprockets' require syntax, however per the explanation found at of the [compass-rails][] gem source this is not a good idea.

4.  Add the following commented out code to your *config/compass.rb* file generated in step 1:

        # To allow compass to import partials from subdirectories per:
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
        # additional_import_paths = ["app/assets/stylesheets/<name>", "app/assets/stylesheets/<name>"]

        # To compile in the necessary debugging information for FireSass.
        # sass_options = {:debug_info => true}

    If you have problems with subfolders within your assets/stylesheets folder, un-comment the first three lines.

    If you use Firefox I highly recommend using [FireSass][]. It allows you to see exactly where sass partial styles are coming from which is extremely helpful when debugging. Un-comment the last two lines if you plan to use FireSass.

5.  Edit *config/application.rb*:

    Un-comment the following:

        if defined?(Bundler)
          # If you precompile assets before deploying to production, use this line
          Bundler.require(*Rails.groups(:assets => %w(development test)))
          # If you want your assets lazily compiled in production, use this line
          Bundler.require(:default, :assets, Rails.env)

    If you find your system has a problem with sass partial underscores when precompiling, add the following:

        # Precompile *all* assets, except those that start with underscore per:
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
        config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

That's it! You now have Compass and all that it brings available to you.

Some additional resources for working with Compass include:

- [Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work]
- [How I Use Compass With Rails 3.1][How I Use Compass]
- [Sass, Compass, and the Rails 3.1 Asset Pipeline][Asset Pipeline]

### Stylesheet Set Up

Now that Compass is set up, let's set up our stylesheets. Clone this books [starter CSS][]:

        git clone git@github.com:maxxiimo/base-css.git

Setting up our CSS is pretty straightforward. Basically, all you have to do is copy into your project the cloned files and subfolders exactly as they are laid out, in their entirety. You will only need to replace the blank *application.scss* file, otherwise you should have no other files in your stylesheets directory, unless you forgot to delete *application.css* when setting up Compass.

Your stylesheet file structure should now look like this:

![][stylesheets]

Simple as that, and here is what your page will now look with the new stylesheets in place:

![][Basic HTML No Styles]

It's pretty basic, but much better than [before][].

NOTE: You may have noticed that only our base application file uses the .scss syntax, while all other other partials use the .sass syntax. This is perfectly fine and done so because of my own personal preference to use .sass where I can.

NOTE: Why the "desktop" subfolder? To better organize desktop/tablet specific files. In the [next chapter][Chapter 3] we will create another subfolder called "mobile". Files outside of these two folders are common to both device types.

Organization
------------

If you dig around our new stylesheets you'll find that they are pretty sparse, and that's fine, they are that way by design. What's important are the conventions used and organizational structure. The few styles provided are common to many projects, and perhaps the bare minimum necessary for this book.

I can't stress enough how important it is to start a project with some kind of organizational structure in place. Even if you don't know what shape the application is going to take, it will serve you well to have a basic structure in mind. As you move along you will fill in all of the empty placeholders.

> Be consistent, keep code well organized, readable and DRY.

\- [Manifesto][]

### application.scss

The heart of our organizational structure is [application.scss][]. This file reminds me of a table of contents for partials. In addition to indexing your partials, it layers in styles based on precedents. Styles in the last partial listed override styles in partials listed above it – so long as the styles preceding it have the same class or ID and specificity (and/or tag).

Our hierarchy looks like this:

- DEFINITIONS
  - [_define.sass][]
- MIXINS
  - [_media_queries.sass][]
- RESETS
  - [h5bp_normalize_v101.sass][]
- BASIC STRUCTURE
  - [_layout.sass][]
  - [_grids.sass][]
  - [_mixins.sass][]
- TYPOGRAPHY
  - [_typography.sass][]
- MISCELLANEOUS
  - [_misc.sass][]
  - [_sprites.sass][]
- NAVIGATION
  - [_navigation.sass][]
- FORMS
  - [_forms.sass][]
- PAGES
  - [_pages.sass][]
- DEVELOPERS
  - [_staging.sass][]
- APPLICATION
- LAST
  - [h5bp_helpers.sass][]
  - [h5bp_print.sass][]

### Detailed Explanation

What follows is a snippet of each section of *application.scss* followed by a description of what the section should be used for:

    /* DEFINITIONS
    ============================================================================ */
    @import "define";

Use the "definitions" section to set global variables for the entire project such as $base-font or $base-font-size.

    /* MIXINS
    ============================================================================ */
    @import "compass";
    @import "media_queries";
    @import "mixins";

Major mixins such as Compass and homebrewed mixins. Included in our starter CSS is a base set of media queries (to be discussed in [Chapter 3 - Media Queries][Media Queries]) and a blank file to place mixins into.

    /* RESETS
    ============================================================================ */
    @import "boilerplate/h5bp_normalize_v102";

    // To counter normalize indentation of lists.
    ol, ul {
      padding-left: 0;
    }

The granddaddy of all resets is Eric Meyer's "[Reset CSS][]".

Sometimes I use compass' [reset utilities][] which are based on Eric Meyer's work, but my preference is to use [Normalize.css][]. HTML5 boilerplate uses normalize.css. The author of Normalize.css describes what it does best:

> Normalize.css is a customisable CSS file that makes browsers render all elements more consistently and in line with modern standards. We researched the differences between default browser styles in order to precisely target only the styles that need normalizing.

You can find Eric Meyer's, and both the original Normalize.css and HTML 5 Boilerplate's normalize styles here (a few converted to sass for you):

- https://github.com/maxxiimo/base-resets

The following article briefly outlines the changes in resets moving into HTML 5:

- [HTML5 Reset Stylesheet][HTML5 Resets]

NOTE: Notice the ad hoc code following the import above? Feel free to add code anywhere throughout *application.scss*. Rules of CSS precedence apply here.


    /* BASIC STRUCTURE
    ============================================================================ */
    @import "desktop/layout";

Use "basic structure" section to style major elements and component areas such as html and body tags, or header and footer areas.

    /* TYPOGRAPHY
    ============================================================================ */
    @import "desktop/typography";

Use the "typography" section to style major typographical elements such as paragraphs, fonts, links, etc. These typographical styles are standard across all pages unless redefined in subsequent partials.

    /* MISCELLANEOUS
    ============================================================================ */
    @import "desktop/misc";
    @import "sprites";

"Miscellaneous" is a catchall for miscellaneous partials and styles that should appear earlier on in the stylesheet. "desktop/misc" has an assortment of general helper styles; "sprites" obviously is for sprites, whether using Compass' built in sprite engine, or building them on my own.

    /* NAVIGATION
    ============================================================================ */
    @import "desktop/navigation";

"Navigation" could be part of another section, or even contained within another partial, however, experiences has proven that a lot of things can happen in navigation. Styles can become quite large, and there can be more than one navigation design or user driven type.

    /* FORMS
    ============================================================================ */
    @import "desktop/forms";

"Forms" is self-evident. One comment about forms.

TIP: I dislike any form generator that do not easily allow you to change its underlying HTML, or not that obvious where the underlying HTML lives. I have consulted for numerous companies who started with these kinds of plug-ins only to realize how boxed in they were later on. Just a word of caution.

    /* PAGES
    ============================================================================ */
    @import "desktop/pages";

"Pages" will hold the bulk of your code, i.e. each page or functional area of your application. You can organize them all within one partial, separate them into their own partials, or a combination of this, depending on your needs.

    /* STAGING - new styles belong here !!!DO NOT INTEGRATE!!!
    ============================================================================ */
    @import "staging";

The "staging" section is a staging area for code and allows an individual or team to be the gatekeeper to code entering stylesheets. This ensures that stylesheets remain organized, DRY, follow the stylesheet standards, and at a bare minimum provide a form of quality control.

    /* APPLICATION - ad hoc code under this line
    ============================================================================ */

"Application" could be a place for anything that did not fit in anywhere else and doesn't need to take precedence.

    /* LAST
    ============================================================================ */
    @import "boilerplate/h5bp_helpers";
    @import "boilerplate/h5bp_print";

"Last" is a reminder that those styles need to appear last.

Moving Forward
--------------

You will add a lot more to the structure outline above. As you do, here are some organizational tips to keep in mind.

### Modularize Styles

Modularizing styles is a great way to keep things organized. The degree of separation/modularization depends on your personal and/or teams preferences and project needs.

> Provide intelligent and semantically correct hooks and code snippets for backend teams.

\- [Manifesto][]

As you add more styles, and consequently partials, consider the following:

1.  Group related partials together with a common prefix:

        _homepage_form.sass

        _homepage_blog.sass

    Or...

2.  Group related styles together within a larger themed partial [preferred]:

        _homepage.sass

    Or...

3.  Group related partials in folders. Take for example our [resets][] files. I provide several different flavors of resets, some of which are subdivided into separate files, but all of them fall under the folder "resets".

### Use a Labeling System

A labeling system will help you better organize/manage related styles. Doing so will also help developers, including yourself, locate styles and see the general organization of stylesheets, especially when browsing CSS output.

> Be consistent, keep code well organized, readable and DRY.

\- [Manifesto][]

Here is the labeling system used in our starter CSS:

    /* MAJOR SECTION
      ============================================================================ */

    /* Heading
      ----------------------- */

    /* subdivision, description, comment */

I like the above sequence, but some other examples include:

    /* =============================================================================
       Major Section
       ========================================================================== */

    or

    /* =============================================================================
     * Major Section
     * ========================================================================== */

For descriptions:

    /* -----------------------------------------------------------------------

     Something major in here. Maybe a long description?

    ----------------------------------------------------------------------- */

    /*
     * Comment in here, title, description, etc.
     */

    /* Comment in here, title, description, etc.
     * Yada yada yada.
     * And a 3rd line maybe. */

Whatever you decide to use is up to you, but be consistent within a project.

NOTE: By far the most used labeling level in your stylesheets will be "subtitles". Use them to group like things or elements, and label them with an eye on searching for the label in the future.

### Naming Conventions

I have my way of naming classes and IDs, and I've seen things all over the board. Here are the guidelines I follow:

- Keep it simple
- Keep it semantic
- Keep it short
- Use underscores between words

> Provide intelligent and semantically correct hooks and code snippets for backend teams.

> KISS (keep it simple stupid)

\- [Manifesto][]

#### Semantic

I've never been too crazy for style names that really have no meaning like :class => 'H2603A'...Okay maybe I'm exaggerating, but I think you get the point. Try to use something that has meaning and can be recognized for what it is, like :class => 'header', but by the same token try not to get super specific about the contents. For example it would not be good to use something like, :class => 'johns_comments', because what happens if John gets replaced by Frank?

There is no sure hit formula for naming classes and IDs. Here is an article that may help you define your own style:

- [What Makes For a Semantic Class Name?][Semantic Class Names]

The following articles may also give you some ideas:

- [About HTML semantics and front-end architecture][About Semantics]
- [Experimenting with component-based HTML/CSS naming and patterns][Experimenting]

#### Short

Try to keep it under 10 characters! I've seen some pretty long class names out there in the wild, and I'm not too crazy about them. They take up too much room. On the flip side, use caution when choosing something super super short.

#### CamelCase, Underscores, Hyphens, Concatenated?

Here are your choices:

    :id => 'page_header'
    :id => 'page-header'
    :id => 'pageHeader'
    :id => 'pageheader'

Obviously, one worders are best, but when nothing fits I personally use hyphens to separate words, and in some cases I concatenate, but not too often. I concatenate only when the words are small and distinguishable from one another. For example, .nowrap.

Some people like to use underscores because when you double-click on one of the words, all the words are selected.

Whatever your style is I don't think it's worth a holy war with other developers, but do be consistent, i.e. if you're going to use hyphens, don't use underscores elsewhere and vice versa. Again, I think it's okay to sprinkle in some concatenation like I described above.

Here's some more opinions on the matter:

[CSS: camelCase vs under_score][aB vs. a_b]
[Hyphens or underscores in CSS and HTML identifiers?][Identifiers]
[CSS: CamelCase Seriously Sucks!][Sucks]

Keep it DRY!
------------

Try not ... no ... DON'T Repeat Yourself! In CSS this means consolidating where possible. There are also some other techniques that do not DRY up your code in output per se, but they do DRY things up when writing your stylesheets, before they are processed: Variables and Mixins.

### Consolidate

Suppose for example in this no duh! contrived example I have two major sections to my layout. One holds my main content, and the other is an aside:

    .container
      .row
        .span9
          #main{:role => "main"}
            = yield
        .span3
          %aside
            <Some content here.>

The corresponding styles:

    #main
      padding: 0 19px
      background-color: $white
      border: 1px solid $border
      @include border-radius(8px)

    .span3 aside
      padding: 0 19px
      background-color: $white
      border: 1px solid $border
      @include border-radius(8px)

(I'm using Twitter Bootstrap in this example thus the .row and .span's)

To keep the code DRY we consolidate common code between the two:

    #main,
    .span3 aside
      padding: 0 19px
      background-color: $white
      border: 1px solid $border
      @include border-radius(8px)

...and in doing so we cut the number of lines of code in half! Consolidate wherever it makes sense. In this example both styles live in the same place in my stylesheets and are related to one another so combining them makes absolute sense.

### Variables

While variables do not explicitly DRY up your code, they kind of do and here's how:

In the code above I specify a variable for the background-color of "$white". At first glance you might think why not just use #FFF or "white", as if in this case "six in one hand, half a dozen in the other" holds true, but what if later in the applications lifecycle I want to use a different shade of white? For example #FCFCFC. I would have to find every single instance of either #FFF or "white" and swap it out with the new value.

By using variables, which I always locate in my *_define.sass* style partial, I can make the change in one instance and affect styles everywhere the variable is used. Not quite DRY, but kinda'.

### Mixins

In a word, mixins are shortcuts.

> They’re shortcuts that allow you to apply a lot of css to a selector from only one line of Sass.
\- [Mixins in SASS][]

When you Notice a a bunch of lines of CSS that keep on appearing throughout your stylesheet, through mixins you can write it once and pull it in via a single line of sass; a shortcut. Our [starter CSS][] gives you two areas to include mixins, as a partial brought in through the MIXINS section of [application.scss][] or a snippet of code within [_define.sass][].

To best understand how to use variables and mixins check out the [Sass documentation][].

To see some great examples checkout:

- [Useful SASS Mixins][]
- [Custom User @mixins][]

What We've Done
---------------

- We started this chapter by taking a look at preprocessors in general, and frameworks that significantly cut down on our front end development time.

- We then set up Compass and implemented the chapters [starter CSS][]. That in and by itself is all you need to start a project off right - in terms of foundation styles.

- We follow set up with a discussion on how our starter styles are organized, why, and how to keep it organized moving forward.

With all of this work you are almost ready to begin building an app with our best foot forward. [Chapter 3][] will conclude [Section I - Setting up a Foundation][Section I] by presenting different choices for a solid foundation for mobile.

[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
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
[frameworks]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-2.md#frameworks
[Grids Are Good]:       http://www.subtraction.com/pics/0703/grids_are_good.pdf
[Fluid Grids]:          http://www.alistapart.com/articles/fluidgrids/
[grid systems]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-3.md#grid-systems
[compass-rails]:        https://github.com/Compass/compass-rails
[FireSass]:             https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[How I Use Compass]:    http://patrickward.com/code/2011/08/19/how-i-use-compass-with-rails-3-dot-1/
[Asset Pipeline]:       http://www.engineyard.com/blog/2011/sass-compass-and-the-rails-3-1-asset-pipeline/
[application.scss]:     https://github.com/maxxiimo/base-css/blob/master/application.scss
[before]:               https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md#end-result
[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/the-manifesto.md
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[h5bp_normalize_v101.sass]: https://github.com/maxxiimo/base-css/blob/master/boilerplate/_h5bp_normalize_v101.sass
[_media_queries.sass]:  https://github.com/maxxiimo/base-css/blob/master/_media_queries.sass
[_layout.sass]:         https://github.com/maxxiimo/base-css/blob/master/desktop/_layout.sass
[_grids.sass]:          https://github.com/maxxiimo/base-css/blob/master/desktop/_grids.sass
[_mixins.sass]:         https://github.com/maxxiimo/base-css/blob/master/_mixins.sass
[_typography.sass]:     https://github.com/maxxiimo/base-css/blob/master/desktop/_typography.sass
[_misc.sass]:           https://github.com/maxxiimo/base-css/blob/master/desktop/_misc.sass
[_sprites.sass]:        https://github.com/maxxiimo/base-css/blob/master/_sprites.sass
[_navigation.sass]:     https://github.com/maxxiimo/base-css/blob/master/desktop/_navigation.sass
[_forms.sass]:          https://github.com/maxxiimo/base-css/blob/master/desktop/_forms.sass
[_pages.sass]:          https://github.com/maxxiimo/base-css/blob/master/desktop/_pages.sass
[_staging.sass]:        https://github.com/maxxiimo/base-css/blob/master/desktop/_staging.sass
[h5bp_helpers.sass]:    https://github.com/maxxiimo/base-css/tree/master/_h5bp_helpers.sass
[h5bp_print.sass]:      https://github.com/maxxiimo/base-css/tree/master/_h5bp_print.sass
[Media Queries]:        https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md#3-media-queries
[Reset CSS]:            http://meyerweb.com/eric/tools/css/reset/index.html
[reset utilities]:      http://compass-style.org/reference/compass/reset/utilities/
[Normalize.css]:        https://github.com/necolas/normalize.css/
[H5BP's normalize]:     https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v101.sass
[HTML5 Resets]:         http://html5doctor.com/html-5-reset-stylesheet/
[resets]:               https://github.com/maxxiimo/base-resets
[aB vs. a_b]:           http://stackoverflow.com/questions/1437527/css-camelcase-vs-under-score
[Identifiers]:          http://stackoverflow.com/questions/1686337/hyphens-or-underscores-in-css-and-html-identifiers
[Sucks]:                http://csswizardry.com/2010/12/css-camel-case-seriously-sucks/
[Semantic Class Names]: http://css-tricks.com/semantic-class-names/
[About Semantics]:      http://nicolasgallagher.com/about-html-semantics-front-end-architecture/
[Experimenting]:        https://gist.github.com/1309546
[Mixins in SASS]:       http://thecodingdesigner.com/tutorials/mixins-sass
[Sass documentation]:   http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html
[Useful SASS Mixins]:   http://sachagreif.com/useful-sass-mixins/
[Custom User @mixins]:  http://css-tricks.com/custom-user-mixins/
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md
[Section I]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/section-1.md

[Basic HTML No Styles]: http://chrismaxwell.com/manifesto/getting-started/base-html-files-with-styles.jpg
[stylesheets]:          http://chrismaxwell.com/manifesto/stylesheets.gif
