Front End Code Manifesto
========================

by Chris Maxwell

High-performing, efficient,
Un-bloated,
Modularized and Organized

Front End Code


Personal views and direction on front end coding, from a Ruby on Rails perspective.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/">
  <img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png" /></a>
<br />This work is licensed under a 
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License</a>.


Attribution-NonCommercial-ShareAlike 
CC BY-NC-SA 3.0

*******************************************************************************************

Table of Contents
=================

- Use a Preprocessor
  - Compress
- CSS Organization
  - Rails Manifest vs. Sass Partials
  - Use Labeling System
  - Naming Conventions
- Mobile First
  - Where Do Styles Go?
  - User Agents or Media Queries
- HTML Organization
  - Where to Put Things
- Image Organization
  - Choosing an Image Format
  - Spriting
- Optimization
- Refactoring
- Tools
- Getting Started
  - HTML5
  - CSS
- Accessibility
  - Standardize Your Links
  - Use ARIA Roles
- Email Coding
- .gemfile
- .gitignore
- Resets
- Getting the Fonts Right
- Optimization
- Search Engine Optimization
- Style Guides
- Good Advice
- JavaScript Libraries
- Layout
  - Organization
  - content_for and :yield
- Navigation
  - Types
  - CSS
  - Context Awareness Patterns


*******************************************************************************************

When I code I will:

1. Seek perfection/excellence.

2. Write beautiful code.

3. Future proof my code.

4. Test across all major browsers.

5. Test in front of "real-life" users.

6. Provide for the mobile experience.

7. Employ progressive enhancements.

8. Be consistent.

9. Keep my code well organized.

10. Keep my code DRY.

11. Think in terms of all use cases including and especially accessibility.

12. Provide intelligent and semantically correct hooks and snippets of code for my backend team.

13. Abstract logic out of views, and keep view code out of controllers.

14. Design/architect/code for the end user, not for me or my team.

15. KISS (keep it simple stupid)

16. Sufficiently comment or document my code (in a style guide) so that the next person can make sense of it.


I will not use third-party plug-ins that do not allow me to easily style an application and/or change the underlying HTML like Formtastic or jQuery UI. I'm just sayin' - Besides, this is a manifesto!


*******************************************************************************************

Use a Preprocessor
==================

I use [Sass][]. Long before using a CSS preprocessor I was hooked on Sass's brother [Haml][] and naturally made the progression. More importantly, for you, it is now the default preprocessor in Rails 3.X. Besides being awesome, you are more than likely going to predominantly see Sass used in projects you work on, or by other front-end developers you work with.

If you do use it, go with .sass. The file and rank will probably go with .scss because it looks familiar, and because that is what ships out-of-the-box in Rails, however, .sass is cleaner/terser.

To help you decide, read this:

[Sass vs. SCSS: Which Syntax is Better?][Sass vs. SCSS]

Note: These two resources are absolutely indispensable:

[css2sass][]

[Html2Haml][]

In terms of other preprocessors, [Less][] is the runner-up.

[Twitter Bootstrap, Less, and Sass: Understanding Your Options for Rails 3.1][Options]

Compress
--------

Why compress? Byte savings, increase load times.

In the old days I might have used something like these:

[CSS Compressor & Minifier][CSS compressor]
[Google Minify][]
[Online JavaScript/CSS Compression Using YUI Compressor][YUI Compressor]

Compass also provides this ability. But these days with the asset pipeline, all you need to do now is precompile:

    bundle exec rake assets:precompile

> The asset pipeline has three goals:
> precompile, concatenate and minify assets into one central path.
>
> [Asset Pipeline for Dummies][Asset Pipeline]

---------------------------------------
[Sass]:                 http://sass-lang.com/
[Haml]:                 http://haml-lang.com/
[Sass vs. SCSS]:        http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better
[css2sass]:             http://css2sass.heroku.com/
[Html2Haml]:            http://html2haml.heroku.com/
[Less]:                 XXXX
[Options]:              http://rubysource.com/twitter-bootstrap-less-and-sass-understanding-your-options-for-rails-3-1/
[CSS Compressor]:       http://www.minifycss.com/css-compressor/
[Google Minify]:        https://code.google.com/p/minify/
[YUI Compressor]:       http://www.refresh-sf.com/yui/
[Asset Pipeline]:       http://coderberry.me/blog/2012/04/24/asset-pipeline-for-dummies/
                        "The Rails asset pipeline from the ground up."

Using Compass
=============

Setting up your application:

1. Add 'compass-rails' to your gemfile, follow the directions here: [compass-rails][]

2. After you run "bundle exec compass init" delete the 3 stylesheets generated by Compass.

3. Add the following commented out code to your config/compass.rb file generated in step one:

    # To allow compass to import partials from subdirectories per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    # additional_import_paths = ["app/assets/stylesheets/<name>", "app/assets/stylesheets/<name>"]
    
    # To compile in the necessary debugging information for FireSass.
    # sass_options = {:debug_info => true}

...You may need these things, and definitely check out [FireSass][].

4. Delete your application.css file and replace with application.scss. 

NOTE: Your base application file needs to use the .scss syntax, however, other partials can use the .sass syntax, which is my preference.

5. Use @import to organize styles rather than Sprockets, and add the following reminder at the top of application.scss:

    /*
     * Important! Do *not* use Sprockets "require" syntax.
     * Use @import to include other stylesheets and Compass mixins.
     */

I use the structure found in the CSS Organization section below.

NOTE: You can use sprockets require syntax, however per [compass-rails][] it is probably not a good idea.

6. If I were you I would just use my [CSS base][], or parts of it.

7. If you have a problem with the underscores and precompiling, add the following code to your config/application.rb file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

8. And that's pretty much it. Don't forget to reference in your application layout. The HTML section below covers how I organize my layouts and shared files.

This is a great resource:

[Getting Compass to Work With Rails 3.1 (and 3.2)][Getting Compass to Work]

Here are some other resources that I have found useful:

[How I Use Compass With Rails 3.1][How I Use Compass]
[Sass, Compass, and the Rails 3.1 Asset Pipeline][Asset Pipeline]

---------------------------------------
[compass-rails]:           https://github.com/Compass/compass-rails
[FireSass]:                https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/
[CSS base]:                https://github.com/maxxiimo/css-base
[Getting Compass to Work]: http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[How I Use Compass]:       http://austintech.com/blog/2011/08/19/how-i-use-compass-with-rails-3-1/
[Asset Pipeline]:          http://www.engineyard.com/blog/2011/sass-compass-and-the-rails-3-1-asset-pipeline/


CSS Organization
================

I can't stress how important it is to start a project with some kind of organizational structure in place. Even if you don't know what shape the application is going to take, it will serve you well to have a basic structure and styles in place like the one I'm going to share with you here. As you move along you will fill in all the placeholders and partials, and the styles are common to almost any project.

Rails Manifest vs. Sass Partials
--------------------------------

There is nothing wrong with using Rails manifest capabilities, however, since we're using sass my preferred method of organizing is to use application.scss as a partials manifest file, almost like a table of contents. I use the following structure for most of my projects:

    application.scss
    
    /*
     * Important! Do *not* use Sprockets "require" syntax.
     * Use @import to include other stylesheets and Compass mixins.
     */
    
    
    /* DEFINITIONS
      ============================================================================ */
    @import "define";
    
    
    /* MIXINS
      ============================================================================ */
    @import "compass";
    
    
    /* RESETS
      ============================================================================ */
    @import "resets/normalize_h5bp";
    // @import "resets/normalize";
    // @import "compass/reset";
    // @import "resets/reset_meyer";
    
    
    /* BASIC STRUCTURE
      ============================================================================ */
    // @import "layout";
    // @import "yui-grid";
    
    
    /* TYPOGRAPHY
      ============================================================================ */
    @import "typography";
    
    
    /* MISCELLANEOUS
      ============================================================================ */
    @import "misc";
    @import "sprites";
    
    
    /* NAVIGATION
      ============================================================================ */
    @import "navigation";
    
    
    /* FORMS
      ============================================================================ */
    @import "forms";
    
    
    /* PAGES
      ============================================================================ */
    @import "pages";
    
    
    /* DEVELOPERS - staging area, new styles belong here !!!DO NOT INTEGRATE!!!
      ============================================================================ */
    @import "developers";
    
    
    /* APPLICATION - ad hoc code under this line
      ============================================================================ */
    
    
    
    
    
    
    
    /* LAST - second part of HTML 5 Boilerplate
      ============================================================================ */
    @import "resets/normalize_h5bp_p2";
    @import "resets/normalize_h5bp_p2_print";


Why the "=" underlines? It helps me find things when I browse CSS output.

I can't stress enough the importance of modularizing your styles. Use partials. Doing so will keep things organized. The degree of separation/modularization depends on your personal and/or teams preferences and project needs.

1. Group related partials together by either prefixing related partials with a common subject:

    _subject1.

    _subject1_


2. Group related snippets of code together in larger themed partials:


3. Group things in folders:


See the section on "Resets" for an overview on which resets are available to you. I include four major reset styles in my application file, uncomment the one I plan to use for a particular project.

Use a "definitions" section to set global variables such as $base-font, $base-font-size, etc. Here is an example of a definition structure I usually start with:

[Upload to Github.]

Use a "layout" section to style major elements and component areas such as html and body tags, or header and footer areas. This section is also good place for grid styles. As you might have noticed, the partial grid is called in this example. This partial in some of my projects ports a sass version of YUI grids, and also Compasses Grid Backgrounds which in a nutshell:

"The grid-background mixins allow you to generate fixed, fluid and elastic grid-images on-the-fly using css3 gradients. These can be used for testing both horizontal and vertical grids."

Use the "typography" section to style major typographical elements such as paragraphs, fonts, links, etc. These typographical styles are standard across all pages unless redefined in subsequent partials.

"miscellaneous" is a catchall for things you would like to appear earlier on in the stylesheet. I include two write off the bat. The first has an assortment of general styles I use while I'm building a front end. The second is for sprites, whether I'm using compasses built in Sprite engine, or building them on my own.

"navigation" could be part of another section, or even contained within another partial, however, experiences has shown me that a lot of things can happen to it, styles can become quite large, and there can be more than one navigation or even type of medication depending on user, so it's best to give it its own section. The main navigations parent tag <nav> or more appropriately %nav does belong in the layout partial since through it you might control layout factors such as position or width.

"forms" it is self-evident. One comment about forms, I really dislike any form generator that doesn't easily let you change its underlying HTML structure, or is not that obvious as to where the underlying structure lies. I have consulted for numerous companies who started with such plug-ins only to realize how boxed in they were later on. Just a word of caution. Anyway, forms oftentimes get pretty complicated so here are some labeling title ideas you can use within your forms partial:

"pages" will hold the bulk of your code, i.e. each page or functional area of your application. You can organize them all within one partial, or separate them into their own partials and call them in the pages section, or a combination of this.

The "developers" section is exactly what it says, a staging area for code. It's good to designating the area as a staging area so that one team or individual can be the gatekeeper to code entering stylesheets. This ensures that things remain organized, DRY, follow the stylesheet standards, and at a bare minimum provide a form of quality control.

"application" could be a place for anything that did not fit in or really needs to trump all styles before it.

"last" is  a reminder that those styles need to appear last.


Use Labeling System
-------------------

Within stylesheets use a system of labeling in order to modularize and better organize/manage related styles. It's good to precede the title name with "/* ". This way you can easily search for specific things like "/* Form" and not pick up every form item in your styles. 

    /* MAJOR SECTION IN SASS
      ============================================================================

    /* Heading in sass
      -----------------------
    
    /* subdivision, description, comment in sass

    

    /* MAJOR SECTION IN SCSS
      ============================================================================ */
    
    /* Heading in scss
      ----------------------- */
    
    /* subdivision, description, comment in scss */


I like the above sequence, but some other examples include:

    /* -----------------------------------------------------------------------
    
     Something major in here. Maybe a long description?
    
    ----------------------------------------------------------------------- */
    
    
    /* =============================================================================
       Major Section
       ========================================================================== */
    
    
    /* =============================================================================
     * Major Section (famous previous but for .sass)
     * =============================================================================
    
    
    /*
     * Comment in here, title, description, etc.
     */
    
    
    /* Comment in here, title, description, etc.
     * More of the same.
     * And a 3rd line maybe. */
    
    
    Once upon a time ago I used to always use this:

    /* Title
    ------------------------------------------------------------------ */
    
    
    /* Subtitle
    -----------–--- */
    
    (use the same number of trailing dashes after the last letter for all subtitles - in this case 4.)


    /* further subdivision or comment */

### Subtitle Examples

By far the most used labeling level in your stylesheets will be "subtitles". Try to group like things or elements and label them with an eye on searching for the title in the future. Here are some examples for form elements:


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
    
    
    /*  buttons
    -------------- */
    
    
    /* link buttons
    ------------------- */
    
    
    /* misc
    ----------- */

Naming Conventions
------------------

I have my way of naming styles, and I've seen things all over the board.  Here's My Recommendation, keep it semantic, short, and use underscores between words. Of course with everything there's always caveats.

### Semantic

I've never been too crazy for style names that really have no meaning like :class => 'H2603A'...Okay maybe I'm exaggerating, but I think you get the point. Try to use something that has meaning and can be recognized for what it is like :class => 'header', but by the same token try not to get super specific about the contents. Like it's probably not good to use something like, :class => 'johns_comments', because what happens if John gets fired in the comments becomes Frank's?

There is no sure hit formula for naming classes, just keep these things in mind.

I found these articles to be really eye-opening or interesting regarding the subject:



### Short

Try to keep it under 10 characters! I've seen some pretty long class names out there in the wild, and I'm not too crazy about them. They take up too much room. On the flip side use caution when choosing something super super short.  For example I sometimes use :id => 'ft' to ID the footer. I feel fine doing this since the tag is called <footer>.

### CamelCase, Underscores, Hyphens, Concatenated?

Use underscores, but whatever you use stick with it. Be consistent.

:id => 'pageHeader'
:id => 'page_header'
:id => 'page-header'
:id => 'pageheader'

Why use underscores? Well, CamelCase really belongs to Controllers, and hyphens really belong to images, and concatenation can sometimes be hard to distinguish... so that leaves underscores. Not very scientific, and really it's just a matter of preference.

Personally, I like to keep it simple and fine one-worders, then concatenate, but two words tops and only when the words are small enough and distinguishable. Then if I must I use underlines. Not consistent enough for you? You're probably right, but I feel like I have mastered the art of class naming well enough that it feels and looks consistent (and pretty).


Mobile First
============

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing application and turned it into a mobile app (pre-smartphones). The result was a precise definition of the applications basic information architecture, no more no less. As an Information Architect with this experience, and knowing that today more than likely most of my users have or will have a smart phone soon, I like to architect with the mobile user in mind first, or in the very least simultaneously. Doing so allows me to architect with less fluff and develop mobile styles right from the get-go.

It's not easy doing it this way, especially after years in years where mobile was an afterthought, or not even considered at all.

Where Do Styles Go?
-------------------

Some argue that including mobile and print* styles in the same partials will help you remember that they are there. I personally won't forget about mobile styles, and neither will you. I think mobile styles should be a separate beast altogether, and here is why: 

- Keep them separate and you can serve lighter, device specific stylesheets.
- As applications grow and user needs change, it might become necessary to add someone to your team who specializes in mobile. No need to clutter up their work.
- Mobile and desktop are different beasts, and these divergent paths require significantly different view approaches.

User Agents or Media Queries
----------------------------

Personally, I prefer to use user agents to serve up the correct styles and HTML. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" does a great job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. To get you started, if you're not sure where to begin, take a look at Ryan Bates screencast "[Mobile Devices] []".

* It is not uncommon to generalize print styles in a separate stylesheet.


????
"Because the assets all concatenate into one file, there are no seperate files to be included on a view-by-view basis." [Asset Pipeline for Dummies][Asset Pipeline]


---------------------------------------
[Media Queries]:        http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices


HTML Organization
=================

Where to Put Things
-------------------

Separate your layout/application.html.haml into partials like:

1. _head.html.haml
2. _script.html.haml
    
3. _logo.html.haml
4. _navigation.html.haml
5. _footer.html.haml

For the first two partials locate these in the same layout folder as application.html.haml -- NOT in the shared folder --- because they are essentially integral to the layout/application.html.haml file. Use helper methods to pull them in:

    def head
      render :partial => 'layouts/head'
    end
    
    def scripts
      render :partial => 'layouts/scripts'
    end

For the second three locate these in the shared folder. I separate logo and navigation into their own partials rather than use something like _banner.html.haml or _header.html.haml to hold them because often times logos and navigation vary between clients or functional areas within an application. When you start  the project you don't necessarily see this coming, but needs do change so you might as well lay them out in such a way that you can easily get at them in the future.

Do all this, and your application.html.haml file might look something like this:

    !!!
    = head
    %body
      %header{:id => 'hd', :role => "banner"}
        = render :partial => 'shared/logo'
        = render :partial => 'shared/navigation'
      #main{:role => "main"}
        = yield
      = render :partial => 'shared/footer'
    = scripts

Concise and simple. Also note the use of [ARIA roles][]. It's good practice to always consider users that require assistive technology to browse your application.


Image Organization
==================

Start off by creating some basic folders to hold things as you develop such as:

* Regarding the name "constructs", I used to call this "assets" before the asset pipeline, but constructs will do until I think of a better name. It holds things like shims, navigation-pipes, horizontal dividers, basically things that are used to construct an application/page.

Usually my root level folder "images" contains sprites, and the sprite components remain in their appropriate folders like icons.

So now my images might look like this:

- assets

  - images
    - buttons
    - constructs*
    - icons
      icon1.gif
      icon1.png
      icon2.gif
      icon2.png
      icon3.gif
      icon3.png
    - logos
    icon-sprite.png
    icon-sprite.gif

  - javascripts
  - stylesheets

Everything has a place to go, and easily find later. as sites grow your image folders can get out of hand so start with an organization plan in mind.

Choosing an Image Format
------------------------

When saving images I always save a .gif version in addition to a .png, just in case. Ideally images will be displayed as .PNG's, but because of issues with older browsers and other edge cases in which PNG fixes won't suffice I have found having them on hand is a great thing. Creating them is rather easy for your designer. I'll go even so far as to serve them up for IE6 as a default.

[Notes on Using PNGS][PNGS]

.jpg's are really reserved for photos and not efficient for things like sprites, structural imagery, plus they do not preserve alpha transparencies which become an issue if backgrounds change in the future (kind of following in a roundabout way the old adage; "measure twice, cut once."). This article gives a good explanation of which to use and when: [Gif Png Jpg Which One To Use][Image Choice]

Spriting
--------

I let Compass do all the sprite creation work. Ryan Bates provides an excellent tutorial on [Compass & CSS Sprites][Sprites]. If you or a designer are creating them in most cases it actually is better on the implementation side to have icon sprites line up horizontally (as opposed to vertically). Line up the top edge of each icon on an equidistant grid line whose coordinate is a multiple of 5 pixels, and not picas. For example, the horizontal grid line coordinates for 4 icons that are 16px x 16px might be:

0 (first image)
20px
40px
60px

Using these coordinates make it easier for front end people to map them, so the coresponding code in my stylesheet would use the following XY values for positioning:

0, 0
0, -20px
0, -40px
0, -60px

???? The reason for horizontal alignment is that side-by-side requires a specifically sized element to display the icon in, whereas one single horizontal line of icons can use a specific element to display, or background positioning in the greater containing element such as an anchor tag or a list item. This in turn minimizes the amount of code served and provides for better organization and element manipulation on the coding side. It also marginally future proofs any design changes.

Since yours are:

"Icons for Impact area are ."

Experience has shown me that having extra pixels of blankness between icons can be beneficial. For example, if icons are 28px x 28px, 35px or even 40px gridlines would be good, but not 30px. 

---------------------------------------
[ARIA roles]            http://www.w3.org/TR/wai-aria/roles#landmark_roles
[PNGS]:                 http://html5boilerplate.com/docs/Using-PNG/
[Sprites]:              http://railscasts.com/episodes/334-compass-css-sprites
                        "Learn how to make CSS sprites with Compass."
[Image Choice]          http://blogs.sitepoint.com/gif-png-jpg-which-one-to-use/


Optimization
============

Optimize browser rendering
https://developers.google.com/speed/docs/best-practices/rendering

Writing efficient CSS
https://developer.mozilla.org/en/Writing_Efficient_CSS


Refactoring
===========

Refactoring >14,000 lines of CSS into Sass (4/16/12)
http://wildbit.com/blog/2012/04/16/refactoring-14000-lines-of-css-into-sass/


Develop a marker that you can use via search/grep, a bundle package, or IDE capability, to find code you need to revisit. I like to use the following. Add your initials to distinguish yourself from other developers:

    // FIXME ccm: 
    /* FIXME ccm: regular comments will show up in your output if comments are not stripped out.


Tools
=====

I use Firebug, and if you do too I highly recommend installing FireSass [https://github.com/nex3/firesass]. This will allow you to locate what Sass partial a particular style is generated from.


Getting Started
===============

HTML5
-----

The best place to get started with your underlying HTML5 is:

[HTML5 Boilerplate][]
[An Unofficial Guide to the HTML5 Boilerplate][Unofficial Guide]
[Guide to HTML5 Boilerplate for Rails Developers][Boilerplate for Rails]

Here's my implementation, and all in Haml:

[ADD LINK HERE]

### What to Put in <head>

There are a lot of things that you could put in your <head> tags, but don't. Obviously just put in What you need. I provide the bare minimum, but everything else as well only commented out:

[ADD GITHUB LINK HERE]

For an explanation on what this stuff is/does check out these two sources:

<https://gist.github.com/1981339>
<http://html5boilerplate.com/docs/html-head/>




[Modernizr HTML5-Cross-browser-Polyfills][]

---------------------------------------
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[Unofficial Guide]:     http://railsapps.github.com/rails-html5-boilerplate.html
[H5BP for Rails]:       http://railsapps.github.com/rails-html5-boilerplate.html


CSS
---

There are 4 base styles I highly recommend using:

1) Compass [http://compass-style.org/]

The following resources will prove to be extremely helpful to you…

compass-rails
https://github.com/Compass/compass-rails/blob/master/README.md

Getting Compass to Work With Rails 3.1 (and 3.2)
http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/

35 Great Resources for Compass and Sass
http://fuelyourcoding.com/35-great-resources-for-compass-and-sass/

2) Blueprint [http://www.blueprintcss.org/]

3) 

4)


Accessibility
=============

Standardize Your Links
----------------------

I find on some projects I work on links are not clearly defined or standardized. It's not obvious to me and probably the end-user that links are links, or links may not be consistent across the application or even the same page. For example; some links are blue, some are green, some links are underlined, some links are not underlined.

It's important to define your links early on in your project – like before you write any code! The [Guidelines for Visualizing Links][Visualizing Links] will give you a great overview on the best direction for you to take in clearly defining and standardizing your links, but generally:

1. Use one consistent color throughout your application.
2. If possible choose a color that is generally recognized as a link, i.e. shades of blue, but this is not absolutely necessary.
3. Use a second color to indicate that a link has been visited, e.g. purple.
4. Provide visual cues such as underlines or titles.
5. When making a title a link, provide an alternative link like "more" or "details", or in the least underline on hover.
5. Borrow from the best.

Use ARIA Roles
--------------

[ARIA][]

---------------------------------------
[Visualizing Links]:    http://www.useit.com/alertbox/20040510.html
[ARIA]:                 http://www.w3.org/TR/wai-aria/roles#landmark_roles


Email Coding
============

"[Optimizing your email for mobile devices with the @media query][Optimizing for Email]"

---------------------------------------
[Optimizing for Email]: http://www.campaignmonitor.com/blog/post/3163/optimizing-your-emails-for-mobile-devices-with-media/


.gemfile
========



.gitignore
==========

Here's what I use, mostly borrowed from [HTML 5 Boilerplate][H5BP .gitignore] and Michael Hartl's [Ruby and Rails Tutorial][RoR Tutorial]:

    # Ignore bundler config
    /.bundle

    # Ignore the default SQLite database
    /db/*.sqlite3

    # Ignore all logfiles and tempfiles
    /log/*.log
    /tmp

    # Numerous always-ignore extensions
    *.diff
    *.err
    *.orig
    *.log
    *.rej
    *.swo
    *.swp
    *.vi
    *~
    *.sass-cache

    # OS or Editor folders
    .DS_Store
    Thumbs.db
    .cache
    .project
    .settings
    .tmproj
    *.esproj
    nbproject
    *.sublime-project
    *.sublime-workspace

    # Dreamweaver added files
    _notes
    dwsync.xml

    # Komodo
    *.komodoproject
    .komodotools

    # Folders to ignore
    .hg
    .svn
    .CVS
    intermediate
    publish
    .idea
    doc/

    # Local
    scratch.*
    public/source

The last section contains files or folders I like to use to save things within the application, but only on my local machine.

- I use scratch.* as a code graveyard: snippets of code I am no longer using but not yet ready to completely get rid of.

- The public/source folder is an area I put original files or source code from 3rd parties that I have integrated
  into my application, Photoshop files, original images, etc.. Basically the original copies of where things came from.

Some additional useful ideas:

[Ignore files][]
[A Collection of Useful .gitignore Templates][.gitignore]

---------------------------------------
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[RoR Tutorial]:         http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
                        "An augmented .gitignore file"
[Ignore files]:         http://help.github.com/ignore-files/
[.gitignore]:           https://github.com/github/gitignore


Resets
======

The granddaddy of all resets is Eric Meyer's "Reset CSS". [http://meyerweb.com/eric/tools/css/reset/index.html]

Sometimes I use compass' reset utilities [http://compass-style.org/reference/compass/reset/utilities/] which are based on Eric Meyer's work, but lately my preference has been to use Normalize.css [https://github.com/necolas/normalize.css/]. HTML 5 boilerplate uses normalize.css with slight variations and style additions. The author of Normalize.css describes what it does best:

"Normalize.css is a customisable CSS file that makes browsers render all elements more consistently and in line with modern standards. We researched the differences between default browser styles in order to precisely target only the styles that need normalizing."

I converted Eric Meyer's, and both the original normalize.css and HTML 5 Boilerplate styles to .sass and .scss here:

https://github.com/maxxiimo/sass-resets

In the case of H5BP, I have commented out some of the typographic styles to give myself the option to keep them or move them into more appropriate partials (per the organization section of this manifesto). Here is an example how I might use them:

[Upload to Github.]

The following article briefly outlines the changes in resets moving into HTML 5: 

HTML5 Reset Stylesheet [http://html5doctor.com/html-5-reset-stylesheet/]



Getting the Fonts Right
=======================



Optimization
============

[Making the Web Fast(er)][]

---------------------------------------
[Fast(er)]:             http://www.igvita.com/slides/2012/railsconf-making-the-web-faster/#1
                        "RailsConf 2012"


Search Engine Optimization
==========================

[Google SEO Starter Guide][Google SEO]

---------------------------------------
[Google SEO]:           http://googlewebmastercentral.blogspot.com/2008/11/googles-seo-starter-guide.html


Style Guides
============

[Front-end Style Guides][Style Guides]

---------------------------------------
[Style Guides]:         http://24ways.org/2011/front-end-style-guides


Good Advice
===========

[Subliminal User Experience][User Experience]

---------------------------------------
[User Experience]:      http://24ways.org/2011/subliminal-user-experience


JavaScript Libraries
====================

[Zepto][]

---------------------------------------
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+nettuts+%28Nettuts%2B%29



*******************************************************************************************
*******************************************************************************************


STORY TELLING
People understand and remember stories.

For me Information Architecture (IA) is the "where" and "how" blocks of related information are grouped and then placed to tell the *story* of the site:

  - in a logical way: makes absolute sense to the end user
  - invites/entices/causes the end user to take the next step, i.e. turn the page in the story

Before you define blocks of information you have to have a story.

For example, the story might be: "I'm a great Web site for finding a job...a job that is perfect for you, you should join me, if you do you will have access to tons of perfect jobs and your life will change for the better forever!"


BLOCKS OF INFORMATION

In this short story I see 3 blocks of information: 1) what is the site in 10 words or less, 2) how do I join - a sign-up section, 3) and an area that describes the benefits of the site - maybe user testimonials.

Aside from the main story, also consider the basic information blocks that most Web sites require:

 - a logo
 - legalese (Copyright, ToS, Privacy)
 - non-legal footer type info (Feedback, About, Contact, Site Map).


PLACEMENT

This is obvious but worth spending time on. After I define blocks of information, I start to think about where they will be placed. I want to call attention to different parts of the story depending on its relevance and importance in the story.

Basically I think like a newspaper layout editor. I also "borrow from the best" to get ideas about my layout by seeing what’s out there on the Web.

I highly recommend the book:

"Don't Make Me Think" by Steve Krug - http://www.sensible.com/index.html

It’s a good read and everything he says is so darn obvious, and all there in one great reference.


FEEDBACK

One very important thing to practice when designing interfaces is do nothing in isolation, and consider everything you think as intuitive to be wrong! (until proven otherwise)

You have to get feedback from your end users and refine. If you can't get to them, then ask your neighbor, a friend, or try something like:

http://www.conceptfeedback.com

Iterating is key.


Finally when architecting remember that less is more and KISS (Keep It Simple Stupid).


*******************************************************************************************
*******************************************************************************************

[Modernizr]:            https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills 
                        "A list of all shims, fallbacks, and polyfills in order to implant html5 functionality in browsers that don't natively support them."



http://api.rubyonrails.org/classes/ActionView/Helpers/AssetTagHelper/JavascriptTagHelpers.html#method-i-javascript_include_tag

http://guides.rubyonrails.org/asset_pipeline.html

