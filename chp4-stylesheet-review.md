Stylesheet Review
=================

In the [last chapter][Chapter 3] we took a look at preprocessors in general, and frameworks that significantly cut down on our front end development time. We then set up Compass and implemented the chapters [starter CSS][]. In this chapter we will explore how our starter styles are organized, why, and how to keep it organized moving forward.

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
  - [h5bp_normalize_v111.scss][]
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
  - [h5bp_helpers.scss][]
  - [h5bp_print.scss][]

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

Major mixins such as Compass and homebrewed mixins. Included in our starter CSS is a base set of media queries (to be discussed in [Chapter 5 - Media Queries][Media Queries]) and a blank file to place mixins into.

    /* RESETS
    ============================================================================ */
    @import "boilerplate/h5bp_normalize_v111";

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
    // @import "susy";
    @import "desktop/layout";

Use "basic structure" section to style major elements and component areas such as html and body tags, or header and footer areas. The compass plug-in Susy is included by default and will be discussed in[Chapter 5 - Susy][Susy].

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

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/the-manifesto.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md

[starter CSS]:          https://github.com/maxxiimo/base-css

[application.scss]:     https://github.com/maxxiimo/base-css/blob/master/application.scss
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[_media_queries.sass]:  https://github.com/maxxiimo/base-css/blob/master/_media_queries.sass
[h5bp_normalize_v101.sass]: https://github.com/maxxiimo/base-css/blob/master/boilerplate/_h5bp_normalize_v111.scss
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
[h5bp_helpers.sass]:    https://github.com/maxxiimo/base-css/tree/master/_h5bp_helpers.scss
[h5bp_print.sass]:      https://github.com/maxxiimo/base-css/tree/master/_h5bp_print.scss

[Media Queries]:        https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-mobile-on-rails.md#3-media-queries
[Reset CSS]:            http://meyerweb.com/eric/tools/css/reset/index.html
[reset utilities]:      http://compass-style.org/reference/compass/reset/utilities/
[Normalize.css]:        https://github.com/necolas/normalize.css/
[H5BP's normalize]:     https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v101.sass
[HTML5 Resets]:         http://html5doctor.com/html-5-reset-stylesheet/
[Susy]:                 https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-mobile-on-rails.md#using-susy

[resets]:               https://github.com/maxxiimo/base-resets

[Semantic Class Names]: http://css-tricks.com/semantic-class-names/
[About Semantics]:      http://nicolasgallagher.com/about-html-semantics-front-end-architecture/
[Experimenting]:        https://gist.github.com/1309546

[aB vs. a_b]:           http://stackoverflow.com/questions/1437527/css-camelcase-vs-under-score
[Identifiers]:          http://stackoverflow.com/questions/1686337/hyphens-or-underscores-in-css-and-html-identifiers
[Sucks]:                http://csswizardry.com/2010/12/css-camel-case-seriously-sucks/


[Mixins in SASS]:       http://thecodingdesigner.com/tutorials/mixins-sass
[Sass documentation]:   http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html
[Useful SASS Mixins]:   http://sachagreif.com/useful-sass-mixins/
[Custom User @mixins]:  http://css-tricks.com/custom-user-mixins/
