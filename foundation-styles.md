Foundation Styles
-----------------

Equally important to your application as foundation markup are foundation styles. HTML and CSS are the raw materials of the World Wide Web. We laid out our HTML, now let's square away our CSS. To do so we will review some of the options out there in terms of preprocessors and frameworks, and then best practices in stylesheet set up and maintenance. To learn these best practices we will implement the chapters [starter CSS][] which I have developed over the years with a lot of trial and error and OCD love. 

### Preprocessors

Probably the two most well-known dynamic stylesheet preprocessors in use today are [Sass][] and [Less][]. [Sass][] is the sister of [Haml][], and my preprocessor of choice as well as the default preprocessor in Rails 3.X. Besides being awesome, as a Rails front end developer you are going to predominantly see Sass used in projects you work on, so if you haven't dived in already, [you should][].

When using sass you have a choice in syntax; .sass or .scss. I prefer .sass. Most front end developers will probably go with the .scss syntax because it looks familiar (similar to CSS), and because that is what ships out-of-the-box in Rails, however, .sass is cleaner/terser (IMHO). To help you decide on the best syntax for you read this:

- [Sass vs. SCSS: Which Syntax is Better?][Sass vs. SCSS]

NOTE: When using Sass or Haml these two resources are absolutely indispensable:

- [css2sass][]
- [Html2Haml][]
- [html2haml Gem][]

In terms of other preprocessors, [Less][] is the runner-up. That's all I'm going to say about that (remember this is a manifesto which is opinionated by nature).

### Frameworks

Frameworks give you a whole boatload of base styles that are instantly accessible through your HTML tags or specified class names. Frameworks include base font sizes and rhythm, default formats for almost every kind of HTML tag, and by simply dropping in the frameworks class names you can add some great looking styles to your project that are built to work, with very few hitches, across all browsers. On top of that you get grid systems, prebuilt scripts for commonly used functions like pop-ups, modals and menu systems. The list goes on. Here are a few worth taking a look at for your project.

#### Compass

So right off the bat I have to say that I love [Compass][]. It's powerful, it's well-documented, it's widely used, there are a ton of extensions for it, and it generally makes life easier for me. What's not to like?

I'm pretty biased on this one, and all the [starter CSS ][] files we will use in our foundation styles incorporate Compass so there's not much else to say other than that it almost doesn't belong in this section since it's really not a framework but rather a utility. It's here though because you can add all kinds of framework components like:

- [Sassy Buttons][]
- [Responsive grids for Compass][]

...and essentially create your own look and feel. Most traditional frameworks on the other hand just give you styles. If you want to break free it takes some tinkering.

When working with Compass the following resource may be useful to you:

- [35 Great Resources for Compass and Sass][35 Great Resources]

#### Twitter Bootstrap

I like [Twitter Bootstrap][]. It's a great place to learn about best practices for any application or framework, and you can get some amazing designs in absolutely no time. It's well-documented, but here's the problem: it's built on [Less][], and use it and your site will look pretty much like everyone else's. Of course you can override styles, but I'm just sayin'.

Getting it to work with Rails is not impossible, hardly, but if you go this path there are some choices to consider:

- [Twitter Bootstrap, Less, and Sass: Understanding Your Options for Rails 3.1][Options]

#### Blueprint

[Blueprint][], in my opinion, is the granddaddy of all frameworks. I used to use Blueprint all of the time, and Compass makes it almost a part of the base system. It's tried-and-true, and a good choice, but I rarely use it these days. I'm not too crazy about the look and feel, and really it seems to be more of a minimalist framework which is not a bad thing.

#### YUI

> YUI is a free, open source JavaScript and CSS library for building richly interactive web applications. 
\- [YUI website][]

#### Foundation 3

> The most advanced responsive front-end framework in the world.
\- [Zurb website][]

#### Skeleton

> A Beautiful Boilerplate for Responsive, Mobile-Friendly Development
\- [Skeleton website][]

### Our Foundation

Now that we briefly reviewed preprocessors and frameworks it's time to build our foundation styles. Our [stylesheets][starter CSS] are written using Sass, but more important than the actual styles themselves � there are really not that many included � is the way they are organized. In my experience as you move along a Rails project and the project grows in complexity and different authors contribute; stylesheets can become behemoths, unmanageable, and downright confusing. To avoid this it's highly advisable to start a project with some kind of organizational structure in place from the get-go. The styles I provide do exactly this.

Before we begin will need to quickly set up  Compass.

#### Compass Set Up

1.  If you have not done so already, per the [Foundation Markup][] chapter, add "compass-rails" to your gemfile. For more explicit directions take a look at the [compass-rails][] gem source.

2.  Run...

        $ bundle exec compass init
        
    Compass will generate a configuration file and stylesheets. Delete the stylesheets. We're going to use our own.

3.  Delete your application.css file and replace it with [application.scss][].

    NOTE: Your base application file needs to use the .scss syntax, however, other partials can use the .sass syntax, which is my preference.

    IMPORTANT: Use @import to organize styles rather than Sprockets. You can use Sprockets' require syntax, however per the explanation found at of the [compass-rails][] gem source it is probably not a good idea.

4.  Add the following commented out code to your config/compass.rb file generated in step 1:

        # To allow compass to import partials from subdirectories per:
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
        # additional_import_paths = ["app/assets/stylesheets/<name>", "app/assets/stylesheets/<name>"]
        #
        # To compile in the necessary debugging information for FireSass.
        # sass_options = {:debug_info => true}

    If you have problems with subfolders within your assets/stylesheets folder, un-comment the first three lines. If you use Firefox I highly recommend using [FireSass][]. It allows you to see exactly where sass partial styles are coming from which is extremely helpful when debugging. Un-comment the last two lines if you plan to use FireSass.

That's it! You now have Compass and all that it brings available to you.

If you find your system has a problem with sass partial underscores when precompiling, add the following to your config/application.rb file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

Some additional resources for working with Compass include:

- [Getting Compass to Work With Rails 3.1 (and 3.2)][Getting Compass to Work]
- [How I Use Compass With Rails 3.1][How I Use Compass]
- [Sass, Compass, and the Rails 3.1 Asset Pipeline][Asset Pipeline]

### Stylesheet Set Up

Now that Compass is set up, let's set up our stylesheets. This task is pretty straightforward. Basically all you have to do is clone these files and subfolders exactly as they're laid out, and paste/merge them into your assets/styles directory:

- https://github.com/maxxiimo/base-css

Delete your application.css file if you have not done so already. It is being replaced with [application.scss][].

NOTE: Your base application file needs to use the .scss syntax, however, other partials can use the .sass syntax, which is my preference.

Simple as that, and if you have been following along from the last chapter, [Foundation Markup][], here is what your page will now look with the new stylesheets in place:

![][Basic HTML No Styles]

It's pretty basic, but much better than before.

### Organization

The [sample stylesheets][starter CSS] I provide are pretty sparse, and that's fine. What's important are the conventions I use and organizational structure of them. The styles I do provide are very common to most projects, and perhaps the bare minimum necessary to do things right.

I can't stress enough how important it is to start a project with some kind of organizational structure in place. Even if you don't know what shape the application is going to take, it will serve you well to have a basic structure. As you move along you will fill in all of the empty placeholders.

#### Style TOC

Our [application.scss][] file is kind of like a table of contents for partials. In addition to indexing your partials, this TOC layers in styles based on precedents. Styles in the last partial entry, i.e. import, will override styles in partials listed above it so long as the styles preceding it have the same class or ID and specificity, and/or tag.

The TOC for our [application.scss][] look something like this:

- DEFINITIONS
  - [_define.sass][]
- MIXINS
- RESETS
  - [normalize_h5bp.sass][]
  - [normalize.sass][]
  - [reset.sass][]
  - [reset_meyer.sass][]
- BASIC STRUCTURE
  - [_layout.sass][]
  - [_grids.sass][]
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
- DEVELOPERS - staging area, new styles belong here !!!DO NOT INTEGRATE!!!
  - [_staging.sass][]
- APPLICATION - ad hoc code under this line
- LAST - second part of HTML 5 Boilerplate
  - [normalize_h5bp_p2.sass][]
  - [normalize_h5bp_p2_print.sass][]

##### What's in Each Section

I use the above structure for most of my projects. What follows is a snippet of each section as they appear in [application.scss][] followed by a description:

    /*
    * Important! Do *not* use Sprockets "require" syntax.
    * Use @import to include other stylesheets and Compass mixins.
    */
    
    
    /* DEFINITIONS
    ============================================================================ */
    @import "define";

Use a "definitions" section to set global variables such as $base-font, $base-font-size, etc..

    /* MIXINS
    ============================================================================ */
    @import "compass";

If you do not plan to use Compass, remove this import.

    /* RESETS
    ============================================================================ */
    @import "resets/normalize_h5bp";
    // @import "resets/normalize";
    // @import "compass/reset";
    // @import "resets/reset_meyer";

I include four major reset styles in my application file and uncomment the one I plan to use for a particular project.

    /* BASIC STRUCTURE
    ============================================================================ */
    @import "layout";
    // @import "grids";

Use a "layout" section to style major elements and component areas such as html and body tags, or header and footer areas. This section is also a good place for grid styles, in major layout component. As you might have noticed, the partial grids is called in this example. This partial in some of my projects ports a sass version of a grid system. I also locate Compass' Grid Backgrounds which in a nutshell:

> The grid-background mixins allow you to generate fixed, fluid and elastic grid-images on-the-fly using css3 gradients. These can be used for testing both horizontal and vertical grids.

    /* TYPOGRAPHY
    ============================================================================ */
    @import "typography";

Use the "typography" section to style major typographical elements such as paragraphs, fonts, links, etc. These typographical styles are standard across all pages unless redefined in subsequent partials.

    /* MISCELLANEOUS
    ============================================================================ */
    @import "misc";
    @import "sprites";

"Miscellaneous" is a catchall for miscellaneous partials and styles that should appear earlier on in the stylesheet. I include two right off the bat; the first has an assortment of general styles I use for building a front end; and, the second is for sprites, whether I'm using Compass' built in sprite engine, or building them on my own.

    /* NAVIGATION
    ============================================================================ */
    @import "navigation";

"Navigation" could be part of another section, or even contained within another partial, however, experiences has taught me that a lot of things can happen in navigation. Styles can become quite large, and there can be more than one navigation design or type depending on user.

The main navigations parent tag \<nav> or more appropriately %nav does belong in the layout partial though since through it you might control layout factors such as position or width and height.

    /* FORMS
    ============================================================================ */
    @import "forms";

"Forms" is self-evident. One comment about forms, I really dislike any form generator that doesn't easily let you change its underlying HTML or where it's not that obvious where the underlying HTML lives. I have consulted for numerous companies who started with these kinds of plug-ins only to realize how boxed in they were later on. Just a word of caution.

    /* PAGES
    ============================================================================ */
    @import "pages";

"Pages" will hold the bulk of your code, i.e. each page or functional area of your application. You can organize them all within one partial, or perhaps separate them into their own partials depending on your needs, and then call them into the Pages partial, or a combination of this.

    /* STAGING - new styles belong here !!!DO NOT INTEGRATE!!!
    ============================================================================ */
    @import "staging";

The "staging" section is exactly what it says, a staging area for code. It's good to have a staging area for developers so that one individual or team can be the gatekeeper to code entering stylesheets. This ensures that things remain organized, DRY, follow the stylesheet standards, and at a bare minimum provide a form of quality control.

    /* APPLICATION - ad hoc code under this line
    ============================================================================ */

"Application" could be a place for anything that did not fit in anywhere else and doesn't need to take precedence over preceding styles.

    /* LAST - second part of HTML 5 Boilerplate
    ============================================================================ */
    @import "resets/normalize_h5bp_p2";
    @import "resets/normalize_h5bp_p2_print";

"Last" is a reminder that those Normalize styles need to appear last.

NOTE: Why the "=" underlines? It helps me find things, or see the organization, when I browse CSS output from a browser.

#### Resets

The granddaddy of all resets is Eric Meyer's "[Reset CSS][]".

Sometimes I use compass' [reset utilities][] which are based on Eric Meyer's work, but lately my preference has been to use [Normalize.css][]. HTML 5 boilerplate uses normalize.css with slight variations and style additions. The author of Normalize.css describes what it does best:

> Normalize.css is a customisable CSS file that makes browsers render all elements more consistently and in line with modern standards. We researched the differences between default browser styles in order to precisely target only the styles that need normalizing.

I converted Eric Meyer's, and both the original Normalize.css and HTML 5 Boilerplate's normalize styles to .sass and .scss here:

- https://github.com/maxxiimo/base-resets

In the case of [H5BP's normalize][], I have commented out some of the typographic styles to give myself the option to keep them or move them into more appropriate partials.

The following article briefly outlines the changes in resets moving into HTML 5: 

- [HTML5 Reset Stylesheet][HTML5 Resets]

### Moving Forward

You will add a lot more to the structure above. As you do so, here are some tips to keep things as organized as I have laid out above in the [starter CSS][].

#### Modularize Styles

Modularizing your styles is a great way to keep things organized. The degree of separation/modularization depends on your personal and/or teams preferences and project needs. As you add more styles, and consequently partials, consider the following:

1.  Group related partials together with a common prefix:

        _homepage_form.sass
        
        _homepage_blog.sass

    Or...

2.  Group related styles together within a larger themed partial [preferred]:

        _homepage.sass

    Or...

3.  Group related partials in folders. Take for example our [resets][] files. I provide several different flavors of resets, some of which are subdivided into separate files, but all of them fall under the folder "resets".

#### Use a Labeling System

Within your stylesheets use a system of labeling in order to better organize/manage related styles.

NOTE: It's a good idea to precede the label name with "/* ". This way you can easily search for specific things like "/* Form" and not pick up every form item in your stylesheet.

Here is an example of one I use:

    /* MAJOR SECTION
      ============================================================================

    /* Heading
      -----------------------
    
    /* subdivision, description, comment

The same one using the .scss syntax:

    /* MAJOR SECTION
      ============================================================================ */
    
    /* Heading
      ----------------------- */
    
    /* subdivision, description, comment */


I like the above sequence, but some other examples include:

    /* =============================================================================
       Major Section
       ========================================================================== */
    
    
    /* =============================================================================
     * Major Section (same as previous but for .sass)
     * =============================================================================

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
    
Once upon a time ago I used to always use this:

    /* Title
    ------------------------------------------------------------------ */
    
    
    /* Subtitle
    -----------�--- */
    
    (use the same number of trailing dashes after the last letter for all subtitles - in this case 4.)


    /* further subdivision or comment */

Whatever you decide to use is totally up to you, but be consistent within a project.

##### Subtitle Examples

By far the most used labeling level in your stylesheets will be "subtitles". Use them to group like things or elements, and label them with an eye on searching for the label in the future. Here are some examples for form elements:

    /* common
    ------------- */
    
    
    /* labels
    ------------- */
    
    
    /* inputs
    ------------- */
    
    
    /* checks and radials
    ------------------------- */
    
    
    /* text areas
    ----------------- */
    
    
    /* selects
    -------------- */
    
    
    /* buttons
    -------------- */
    
    
    /* link buttons
    ------------------- */
    
    
    /* misc
    ----------- */

#### Naming Conventions

I have my way of naming styles, i.e. classes and IDs, and I've seen things all over the board. Here's My Recommendation:

- Keep it simple
- Keep it semantic
- Keep it short
- Use underscores between words

##### Semantic

I've never been too crazy for style names that really have no meaning like :class => 'H2603A'...Okay maybe I'm exaggerating, but I think you get the point. Try to use something that has meaning and can be recognized for what it is, like :class => 'header', but by the same token try not to get super specific about the contents. For example it would not be good to use something like, :class => 'johns_comments', because what happens if John gets replaced by Frank?

There is no sure hit formula for naming classes and IDs, just keep these things in mind.

When it comes to CSS, Chris Coyier is a maverick in the field. Here is an article on the subject:

- [What Makes For a Semantic Class Name?][Semantic Class Names]

The following articles may also give you some ideas:

- [About HTML semantics and front-end architecture][About Semantics]
- [Experimenting with component-based HTML/CSS naming and patterns][Experimenting]

##### Short

Try to keep it under 10 characters! I've seen some pretty long class names out there in the wild, and I'm not too crazy about them. They take up too much room. On the flip side, use caution when choosing something super super short.  For example I sometimes use :id => 'ft' to ID the footer. I feel fine doing this since the tag is called \<footer>.

##### CamelCase, Underscores, Hyphens, Concatenated?

Here are your choices:

    :id => 'page_header'
    :id => 'page-header'
    :id => 'pageHeader'
    :id => 'pageheader'

Obviously, one worders are best, but when nothing fits I personally use hyphens to separate words, and in some cases I concatenate, but not too often. I concatenate only when the words are small and distinguishable from one another. For example, .nowrap.

Some people like to use underscores because when you double-click on one of the words, all the words are selected.

Whatever your style is it's fine. I don't think it's worth a holy war with other developers, but do be consistent, i.e. if you're going to use hyphens, don't use underscores elsewhere and vice versa. I think it's okay to sprinkle in some concatenation like I described above.

Here's some more opinions on the matter:

[CSS: camelCase vs under_score][aB vs. a_b]
[Hyphens or underscores in CSS and HTML identifiers?][Identifiers]
[CSS: CamelCase Seriously Sucks!][Sucks]

#### Keep it DRY!

Try not ... no ... DON'T Repeat Yourself! In CSS this means consolidating where possible. There are also some other techniques that do not DRY up your code in output per se, but they do DRY things up when writing your stylesheets, before they are processed: variables and mixins.

##### Consolidate

Suppose for example in this no duh! contrived example I have two major sections to my layout. One holds my main content, and the other is an aside (I'm using Twitter Bootstrap in this example thus the .row and .span's):

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

So to keep it DRY we consolidate common code between the two:

    #main,
    .span3 aside
      padding: 0 19px
      background-color: $white
      border: 1px solid $border
      @include border-radius(8px)

...and in doing so we cut the number of lines of code in half! Do that wherever it makes sense. In this example both styles live in the same place in my stylesheet and are related to one another so combining them makes absolute sense.

##### Variables

While variables do not explicitly DRY up your code, they kind of do and here's how:

In the code above I specify a variable for the background-color of $white. At first glance you might think why not just use #FFF or "white", as if in this case "six in one hand, half a dozen in the other" holds true, but what if later in the applications lifecycle I want to use a different shade of white? For example #FCFCFC. I would have to find every single instance of either #FFF or "white" and swap it out with the new value.

By using variables, which I always locate in my _define.sass style partial, I can make the change in one instance and affect styles everywhere the variable is used. Not quite DRY, but kinda'.

##### Mixins

In a word, mixins are shortcuts.

> They�re shortcuts that allow you to apply a lot of css to a selector from only one line of Sass.

\- [Mixins in SASS][]

In other words if you have a bunch of lines of CSS that keep on appearing throughout your stylesheet, rather than repeating it throughout your stylesheet you can write it once and bring it in via a single line of sass, a shortcut. Our [starter CSS][] gives you two areas to include mixins, as a partial brought in through the MIXINS section of [application.scss][] or a snippet of code within [_define.sass][].

To best understand how to use variables and mixins check out the [Sass documentation][].

To see some great examples checkout:

- [Useful SASS Mixins][]
- [Custom User @mixins][]

### What We've Done

- We started this chapter by taking a look at preprocessors in general, and frameworks that significantly cut down on our front end development time.

- We then set up Compass and implemented the chapters [starter CSS][]. That in and by itself is all you need to start a project off right - in terms of foundation styles.

- We follow set up with the discussion on how our starter styles are organized, why, and how to keep it organized moving forward.

With all of this work you are more than ready to begin building an app with your best foot forward. If you want to go the extra mile, and I suggest you do, our [next chapter][] will focus on a solid foundation for small screens, i.e. mobile browsers.

[starter CSS]:          https://github.com/maxxiimo/base-css
[Foundation Markup]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
[Sass]:                 http://sass-lang.com/
[Less]:                 http://lesscss.org/
[Haml]:                 http://haml-lang.com/
[you should]:           http://css-tricks.com/redesigning-with-sass/
[Sass vs. SCSS]:        http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better
[css2sass]:             http://css2sass.heroku.com/
[Html2Haml]:            http://html2haml.heroku.com/
[html2haml Gem]:        https://github.com/haml/html2haml
[Compass]:              http://compass-style.org/
[Sassy Buttons]:        http://jaredhardy.com/sassy-buttons/
[Response Grids]:       http://susy.oddbird.net/
[35 Great Resources]:   http://fuelyourcoding.com/35-great-resources-for-compass-and-sass/
[Twitter Bootstrap]:    http://twitter.github.com/bootstrap/
[Options]:              http://rubysource.com/twitter-bootstrap-less-and-sass-understanding-your-options-for-rails-3-1/
[Blueprint]:            http://www.blueprintcss.org/
[YUI website]:          http://yuilibrary.com/
[Zurb website]:         http://foundation.zurb.com/
[Skeleton website]:     http://www.getskeleton.com/
[compass-rails]:        https://github.com/Compass/compass-rails
[FireSass]:             https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/
[Getting Compass to Work]: http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[How I Use Compass]:    http://austintech.com/blog/2011/08/19/how-i-use-compass-with-rails-3-1/
[Asset Pipeline]:       http://www.engineyard.com/blog/2011/sass-compass-and-the-rails-3-1-asset-pipeline/
[application.scss]:     https://github.com/maxxiimo/base-css/blob/master/application.scss
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[_forms.sass]:          https://github.com/maxxiimo/base-css/blob/master/_forms.sass
[_grids.sass]:          https://github.com/maxxiimo/base-css/blob/master/_grids.sass
[_layout.sass]:         https://github.com/maxxiimo/base-css/blob/master/_layout.sass
[_misc.sass]:           https://github.com/maxxiimo/base-css/blob/master/_misc.sass
[_navigation.sass]:     https://github.com/maxxiimo/base-css/blob/master/_navigation.sass
[_pages.sass]:          https://github.com/maxxiimo/base-css/blob/master/_pages.sass
[_sprites.sass]:        https://github.com/maxxiimo/base-css/blob/master/_sprites.sass
[_staging.sass]:        https://github.com/maxxiimo/base-css/blob/master/_staging.sass
[_typography.sass]:     https://github.com/maxxiimo/base-css/blob/master/_typography.sass
[resets]:               https://github.com/maxxiimo/base-css/tree/master/resets
[normalize_h5bp.sass]:  https://github.com/maxxiimo/base-css/tree/master/resets/normalize_h5bp.sass
[normalize.sass]:       https://github.com/maxxiimo/base-css/tree/master/resets/normalize.sass
[reset.sass]:           https://github.com/maxxiimo/base-css/tree/master/resets/reset.sass
[reset_meyer.sass]:     https://github.com/maxxiimo/base-css/tree/master/resets/reset_meyer.sass
[normalize_h5bp_p2.sass]: https://github.com/maxxiimo/base-css/tree/master/resets/normalize_h5bp_p2.sass
[normalize_h5bp_p2_print.sass]: https://github.com/maxxiimo/base-css/tree/master/resets/normalize_h5bp_p2_print.sass
[Reset CSS]:            http://meyerweb.com/eric/tools/css/reset/index.html
[reset utilities]:      http://compass-style.org/reference/compass/reset/utilities/
[Normalize.css]:        https://github.com/necolas/normalize.css/
[H5BP's normalize]:     https://github.com/maxxiimo/base-resets/blob/master/_normalize_h5bp.sass
[HTML5 Resets]:         http://html5doctor.com/html-5-reset-stylesheet/
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
[next chapter]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-foundation.md

[Basic HTML No Styles]: http://chrismaxwell.com/rails-views/assets/getting-started/base-html-files-with-styles.png