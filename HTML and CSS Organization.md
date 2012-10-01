HTML and CSS Organization
-------------------------

### HTML Organization




#### What to Put in <head>

There are a lot of things that you could put in your <head> tags, but don't. Obviously just put in What you need. I provide the bare minimum, but everything else as well only commented out:

[ADD GITHUB LINK HERE]

For an explanation on what this stuff is/does check out these two sources:

<https://gist.github.com/1981339>
<http://html5boilerplate.com/docs/html-head/>




[Modernizr HTML5-Cross-browser-Polyfills][]


#### Naming Conventions

When naming HTML files try to stay within REST conventions, i.e. index.html.haml, show.html.haml, etc.. When naming outside of REST be short and concise, use names that indicate what the files function or purpose is. Keep in mind that file names tend to trickle down to classes.

When naming HTML files separate words with underscores: a_great_file_name.html.haml

For partials, if there are several related to an individual file, group them by using the parent files name or abbreviation. If there is no parent file per se, use a common function or purpose to group the partials, for example:

    _tabs.html.haml
    _tabs_sub_nav.html.haml

#### Where to Put Things

Partials are great to use to:

1.  Increase readability of your code
2.  Keep things organized
3.  Reuse code, i.e. keep things DRY
4.  Encapsulate logic, although helper methods are preferred

The key is not to go knots and partial everything. If you do that, finding things becomes a wild goose chase.

So starting from the top, separate your layout/application.html.haml into partials like:

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

#### IE 6

These days most people like to just forget about IE 6, it's old, "We're not supporting it, those users need to update!" ...But here's the problem, those users are still out there, even if they don't want to be. Have you ever been in your local library and checked out the super old machines people have to use there? So what I propose is a compromise. Don't waste your time developing for IE 6 but give those users notice and ability via [Chrome Frame][]. Add the following partial to your layouts folder:

    /[if lt IE 7 ]
      %p.chromeframe
        Your browser is
        %em ancient!
        %a{:href => "http://browsehappy.com/"} Upgrade to a different browser or
        %a{:href => "http://www.google.com/chromeframe/?redirect=true"} install Google Chrome Frame to experience this site.

Here is the corresponding helper method:

    def chromeframe
      render :partial => 'layouts/chromeframe'
    end

So now your application layout file will look like this:

    !!!
    = head
    %body
      = chromeframe
      %header{:id => 'hd', :role => "banner"}
        = render :partial => 'shared/logo'
        = render :partial => 'shared/navigation'
      #main{:role => "main"}
        = yield
      = render :partial => 'shared/footer'
    = scripts

#### %head and Boilerplate

There is so much you can put in your %head that it can get pretty confusing. I base all of my projects off of parts of [HTML5 Boilerplate][]. To learn more check out [HTML head options][], all of the research on best practices and why has been done for you. Just pick and choose what works for you. You can use my haml template to start:

https://github.com/maxxiimo/base-files/blob/master/_head.html.haml

Everything is nice and neat in haml and with only the ones I think you should use (plus all the other options commented out).

[<head> Examples][]

#### The Title

    %title= content_for?(:title) ? yield(:title) : "XXX"

#### JavaScript

Generally it is best to put JavaScript at the very bottom of the page. Doing so will allow the page to render before scripts are loaded, but some scripts such as modernizr need to load before your HTML so naturally I include them in _head.html.haml. To accommodate all other JavaScript files I use a _scripts.html.haml partial located in the layout folder.


[Chrome Frame]:         https://developers.google.com/chrome/chrome-frame/
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[HTML head options]:    http://html5boilerplate.com/docs/html-head/
[<head> Examples]       https://gist.github.com/581868


### CSS Organization

I can't stress how important it is to start a project with some kind of organizational structure in place. Even if you don't know what shape the application is going to take, it will serve you well to have a basic structure and styles in place like the one I'm going to share with you here. As you move along you will fill in all the placeholders and partials, and the styles are common to almost any project.

#### Rails Manifest vs. Sass Partials

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
    @import "layout";
    // @import "grid";
    
    
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

1.  Group related partials together by either prefixing related partials with a common subject:

        _subject1.
        
        _subject1_

2.  Group related snippets of code together in larger themed partials:


3.  Group things in folders:


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

#### Use Labeling System

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

##### Subtitle Examples

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

#### Naming Conventions

I have my way of naming styles, and I've seen things all over the board.  Here's My Recommendation, keep it semantic, short, and use underscores between words. Of course with everything there's always caveats.

##### Semantic

I've never been too crazy for style names that really have no meaning like :class => 'H2603A'...Okay maybe I'm exaggerating, but I think you get the point. Try to use something that has meaning and can be recognized for what it is like :class => 'header', but by the same token try not to get super specific about the contents. Like it's probably not good to use something like, :class => 'johns_comments', because what happens if John gets fired in the comments becomes Frank's?

There is no sure hit formula for naming classes, just keep these things in mind.

I found these articles to be really eye-opening or interesting regarding the subject:



##### Short

Try to keep it under 10 characters! I've seen some pretty long class names out there in the wild, and I'm not too crazy about them. They take up too much room. On the flip side use caution when choosing something super super short.  For example I sometimes use :id => 'ft' to ID the footer. I feel fine doing this since the tag is called <footer>.

##### CamelCase, Underscores, Hyphens, Concatenated?

...whatever you use stick with it. Be consistent.

    :id => 'pageHeader'
    :id => 'page_header'
    :id => 'page-header'
    :id => 'pageheader'


Personally, I like to keep it simple and find one-worders that fit, then concatenate, but two words tops! ...and only when the words are small enough and distinguishable. Then if I must, I use one of the other methods above and only one throughout my styles and only if absolutely necessary, i.e. I don't have an opinion on which is better. My method isn't consistent enough for you? You're probably right, but I feel like I have mastered the art of class naming well enough that it feels and looks consistent (and pretty).

Here's some more opinions on the matter:

[CSS: camelCase vs under_score][aB vs. a_b]
[Hyphens or underscores in CSS and HTML identifiers?][Identifiers]
[CSS: CamelCase Seriously Sucks!][Sucks]

#### Keep it DRY!

Try not, no, Don't Repeat Yourself! In CSS this means consolidating where possible, using variables, includes, and mixins.

##### Consolidating

Suppose for example in this no duh! contrived example I have two major sections to my layout. One holds my main content, and the other is an aside (I'm using Twitter Bootstrap thus the .row and .span's):

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

So to keep it DRY:

    #main,
    .span3 aside
      padding: 0 19px
      background-color: $white
      border: 1px solid $border
      @include border-radius(8px)

...and we cut the number of lines of code in half! Do that wherever it makes sense. In this example both styles live in the same place in my stylesheet and are related to one another so combining them makes absolute sense.

##### Variables

While variables do not explicitly DRY up your code, they kind of do and here's how; in the code above I specify a variable for the background-color of $white. At first glance you might think why not just use #FFF or "white", as if in this case "6 in one hand, half a dozen in the other" holds true, but what if later in the applications lifecycle I want to use a different shade of white? For example #FCFCFC. I would have to find every single instance of either #FFF or "white" and swap it out with the new value. By using variables, which I always locate in my _define.sass style partial, I can make the change in one instance and affect styles everywhere the variable is used. Not quite DRY, but kinda.

##### Includes



##### Mixins



[aB vs. a_b]:           http://stackoverflow.com/questions/1437527/css-camelcase-vs-under-score
[Identifiers]:          http://stackoverflow.com/questions/1686337/hyphens-or-underscores-in-css-and-html-identifiers
[Sucks]:                http://csswizardry.com/2010/12/css-camel-case-seriously-sucks/