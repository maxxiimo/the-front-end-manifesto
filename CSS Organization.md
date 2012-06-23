CSS Organization
----------------

I can't stress how important it is to start a project with some kind of organizational structure in place. Even if you don't know what shape the application is going to take, it will serve you well to have a basic structure and styles in place like the one I'm going to share with you here. As you move along you will fill in all the placeholders and partials, and the styles are common to almost any project.

### Rails Manifest vs. Sass Partials

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

### Use Labeling System

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
    -----------�--- */
    
    (use the same number of trailing dashes after the last letter for all subtitles - in this case 4.)


    /* further subdivision or comment */

#### Subtitle Examples

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

### Naming Conventions

I have my way of naming styles, and I've seen things all over the board.  Here's My Recommendation, keep it semantic, short, and use underscores between words. Of course with everything there's always caveats.

#### Semantic

I've never been too crazy for style names that really have no meaning like :class => 'H2603A'...Okay maybe I'm exaggerating, but I think you get the point. Try to use something that has meaning and can be recognized for what it is like :class => 'header', but by the same token try not to get super specific about the contents. Like it's probably not good to use something like, :class => 'johns_comments', because what happens if John gets fired in the comments becomes Frank's?

There is no sure hit formula for naming classes, just keep these things in mind.

I found these articles to be really eye-opening or interesting regarding the subject:



#### Short

Try to keep it under 10 characters! I've seen some pretty long class names out there in the wild, and I'm not too crazy about them. They take up too much room. On the flip side use caution when choosing something super super short.  For example I sometimes use :id => 'ft' to ID the footer. I feel fine doing this since the tag is called <footer>.

#### CamelCase, Underscores, Hyphens, Concatenated?

Use underscores, but whatever you use stick with it. Be consistent.

    :id => 'pageHeader'
    :id => 'page_header'
    :id => 'page-header'
    :id => 'pageheader'

Why use underscores? Well, CamelCase really belongs to Controllers, and hyphens really belong to images, and concatenation can sometimes be hard to distinguish... so that leaves underscores. Not very scientific, and really it's just a matter of preference.

Personally, I like to keep it simple and fine one-worders, then concatenate, but two words tops and only when the words are small enough and distinguishable. Then if I must I use underlines. Not consistent enough for you? You're probably right, but I feel like I have mastered the art of class naming well enough that it feels and looks consistent (and pretty).