Susy
====

In [Chapter 6][] we introduced the first component of Responsive Web Design, flexible grids, and in that introduction I mentioned [Susy][], a [Compass][]-based grid system that could handle all the heavy lifting of math calculations for you:

> Your markup. Your design. Our math.
>
> The web is a responsive place, from your lithe & lively development process to your end-user's super-tablet-multi-magic-lap-phone. You need grids that are powerful yet custom, reliable yet responsive.

\- [Susy][]

In this chapter we will implement Susy.

Set Up
------

Set up is pretty straightforward:

*Step 1:* Add the following to *config/compass.rb*:

    require "susy"

*Step 2:* Add the Susy gem to your *.gemfile* and bundle install:

    # Compass specific gems.
    gem 'compass-rails'
    gem 'oily_png'
    gem 'susy'

*Step 3:* Import Susy into your project (uncomment):

*app/assets/stylesheets/application.scss*

    /* BASIC STRUCTURE
      ============================================================================ */
    @import "susy";
    @import "desktop/layout";

Don't forget to restart your server, and wallah! You have a powerful responsive grid system ready for implementation in your project.

Implementation
--------------

To implement Susy into your application follow these steps:

*Step 1*: Define the [basic settings][] for your Susy grid in *application.scss*:

    /* DEFINITIONS
      ============================================================================ */
    @import "define";

    /*  Susy Grid
      -----------------------

    $total-columns:     12
    $column-width:      4em
    $gutter-width:      1em
    $grid-padding:      $gutter-width

This tells Susy what the basic characteristics of the grid system are. In this case it will span 12 columns; each column has a width of 4em with a gutter and grid padding of 1em.

To calculate the total width of your grid, including its padding, use the following formula:

($total-columns x $column-width) + (($total-columns - 1) x $gutter-width) + ($grid-padding x 2)

(12 x 4em) + ((12 - 1) x 1em) + (1em x 2) = 61em

*Step 2*: Create an [outer grid-containing element][.container] in *application.html.haml* called *.container*:

    %body
      .container
        = chromeframe
        %header{:role => "banner"}
          = render :partial => 'shared/logo'
          = render :partial => 'shared/navigation'
        #main{:role => "main"}
          = yield
        = render :partial => 'shared/footer'
      = scripts

*Step 3*: Add the corresponding CSS to *_layout.sass*:

    .container
      +container

*+container* is a Susy mixin that applies the definitions you defined in Step 1 to the outer grid containing element you created in Step 2.

*Step 4*: Remove the following styles from the body tag since we are now replacing these properties with Susy:

      margin: 0 auto
      width: 960px

And that's it! Refresh your browser. You may see a very slight shift in the content, but otherwise everything should look the same, accept that Susy is now in control oof your grid system. In the Media Queries section of this chapter we will use Susy quite a bit, but first let's quickly learn how it works.

Susy in Action
--------------

Using Susy is pretty straightforward. Essentially it is a mixin scheme that applies a specified amount of columns to an element, based on the total columns available. In our implementation we specified 12 columns:

    $total-columns:     12

In the previous Flexible Grids section, in our example we used percentages to define grid element widths:

    .left-side, .right-side
      width: 50%

With Susy instead of using percentages directly, we define grid element widths through the Susy *+span-columns()* mixin:

    .left-side
      +span-columns(6, 12)

    .right-side
      +span-columns(6 omega, 12)

What ddoes this do? Since we set the total number of columns in our Susy grid to 12, for the two elements we are targeting we need only set the total number of columns each element will span of the available 12 columns in the grid, i.e. *+span-columns(6, 12)* (half of the available columns).

The "omega" in *.right-side* denotes that the element will be the last column in the grid and therefore will not have a gutter (right margin). With this information Susy calculates your percentages for us (or em's or px's if you would like) and produces the following CSS:

    .container:after {
      clear: both;
      content: "";
      display: table;
    }

    .container {
      margin-left: auto;
      margin-right: auto;
      max-width: 59em;
      padding-left: 1em;
      padding-right: 1em;
    }

    .left-side {
      display: inline;
      float: left;
      margin-right: 1.69492%;
      width: 49.1525%;
    }

    .right-side {
      display: inline;
      float: right;
      margin-right: 0;
      width: 49.1525%;
    }

And there it is in a nutshell! To really learn how to use Susy – it really packs a lot more punch than what I've demonstrated – the best reference can be found at the [source][]. The following tutorials also demonstrate Susy in action:

- [Responsive Grids With Susy][Susy Grids]
- [Off-canvas layout with Susy][Off-canvas]

NOTE: You may have noticed the "*max-with: 59em*" property in *.container*. The reason this is generated by Susy is to constrain the maximum width in the largest of screens, while maintaining flexibility within this limit. Doing so ensures that pages do not completely span the widths of very large screens and thereby reduce readability. This setting, and many more, can be overridden in Susy quite easily.

Susy Breakpoints
----------------

One of the great features of Susy is that breakpoints are baked right in. We could use the breakpoints we created in the [last chapter][Chapter 6], but why not take advantage of the mathematical capabilities of Susy and also be consistent with our grid system at the same time? Sounds like a good plan, and here's how we will use Susy breakpoints in our project.

### Set Up

**Step 1**: Redefine our Susy flexible grid in *application.scss* as follows:

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break5:            5;
    $break6:            6;
    $break7:            7;
    $break8:            8;
    $break9:            9;
    $break10:           10;
    $break11:           11;
    $break12:           12;

We're starting from a total column size of 4 instead of 12 since we are approaching development from a mobile first perspective. Then I add breakpoints for 5 to 12 column layouts using variables. I define an additional eight breakpoints on top of the base grid size because I want to test which breakpoints and corresponding layouts are best suited for the devices I'm targeting.

**Step 2**: In *_layout.sass* call the Susy at-breakpoint mixin for each breakpoint defined above as follows:

    .container
      +container($total-columns, $break5, $break6, $break7, $break8, $break9, $break10, $break11, $break12)
      +susy-grid-background

      +at-breakpoint($break5)
        +susy-grid-background
        background-color: red

      +at-breakpoint($break6)
        +susy-grid-background
        background-color: blue

      +at-breakpoint($break7)
        +susy-grid-background
        background-color: green

      +at-breakpoint($break8)
        +susy-grid-background
        background-color: yellow

      +at-breakpoint($break9)
        +susy-grid-background
        background-color: aqua

      +at-breakpoint($break10)
        +susy-grid-background
        background-color: brown

      +at-breakpoint($break11)
        +susy-grid-background
        background-color: violet

      +at-breakpoint($break12)
        +susy-grid-background
        background-color: white

NOTE: To help me identify the breakpoint being utilized when testing devices I also included a colorcode for each breakpoint and the Susy susy-grid-background mixin - which outlines each column with a background.

If you're curious, the above code produces the following @media rules:

    @media (min-width: 24em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 29em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 34em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 39em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 44em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 49em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 54em) {
      .container {
        *omitted*
      }
    }
    @media (min-width: 59em) {
      .container {
        *omitted*
      }

As you can see it is very similar to what we created manually except Susy calculates all the breakpoints for us based on the total columns for each breakpoint we defined and the following formula:

($total-columns x $column-width) + (($total-columns - 1) x $gutter-width)

(12 x 4em) + ((12 - 1) x 1em) = 59em

Since we're using a base font size of 16px, if you multiply the em's value by 16 you will get the equivalent breakpoints in pixels:

-  2 columns:  9em x 16px = 144px
-  3 columns: 14em x 16px = 224px
-  4 columns: 19em x 16px = 304px
-  5 columns: 24em x 16px = 384px
-  6 columns: 29em x 16px = 464px
-  7 columns: 34em x 16px = 544px
-  8 columns: 39em x 16px = 624px
-  9 columns: 44em x 16px = 704px
- 10 columns: 49em x 16px = 784px
- 11 columns: 54em x 16px = 864px
- 12 columns: 59em x 16px = 944px

**Step 3**: Test your breakpoints. After reviewing the grid on several different devices I settle on the following:

- 4 columns, 19em x 16px = 304px (Samsung, iPhone)
- 6 columns, 29em x 16px = 464px (Small Tablet)
- 9 columns, 44em x 16px = 704px (iPad)
- 12 columns, 59em x 16px = 944px (Desktop)

**Step 4**: Remove the unneeded breakpoints from *application.scss* which in my case leaves the following definitions:

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break6:            6;
    $break9:            9;
    $break12:           12;

**Step 5**: In *_layout.sass* remove the unneeded breakpoints plus the color-coded backgrounds:

    .container
      +container($total-columns, $break6, $break9, $break12)
      +susy-grid-background

      +at-breakpoint($break6)
        +susy-grid-background

      +at-breakpoint($break9)
        +susy-grid-background

      +at-breakpoint($break12)
        +susy-grid-background

And that's it! Now when you need to apply a particular style to a specific screen size use these breakpoints.

### Using Susy Breakpoints

Let's revisit the *.left-side* and *.right-side* div's example, but this time using our newly defined Susy breakpoints. As mobile first developers we'll start with our base 4 column layout, and move our way to the 12 column layout.

Since our four column base setting is designed for smaller screen sizes, we might want to stack the .left-side and .right-side div's (rather than have them appear cramped side-by-side):

    .left-side
      +span-columns(4 omega, 4)

    .right-side
      +span-columns(4 omega, 4)

What did we do? Here we tell Susy to span *.left-side* and *.right-side* across 4 of the available 4 columns. Since they are floated elements, doing so stacks *.left-side* and *.right-side* one on top of the other.

For the remaining three breakpoints we will apply grid widths that will result in a 50-50 side-by-side placement.

    .left-side
      +span-columns(4 omega, 4)

      +at-breakpoint($break6)
        +span-columns(3, $break6)

      +at-breakpoint($break9)
        +span-columns(4, $break9)

      +at-breakpoint($break12)
        +span-columns(6, $break12)

    .right-side
      +span-columns(4 omega, 4)

      +at-breakpoint($break6)
        +span-columns(3 omega, $break6)

      +at-breakpoint($break9)
        +span-columns(5 omega, $break9)

      +at-breakpoint($break12)
        +span-columns(6 omega, $break12)

Here we tell Susy to float the elements side-by-side, equally, except in the case of the 9 column layout. In that case one side is slightly bigger than the other. We could override this if we wanted to.

For illustration purposes let's color *.left-side* and *.right-side* red and blue, but only for our two largest screen sizes (all other breakpoint code committed):

    .left-side
      +at-breakpoint($break9)
        +span-columns(4, $break9)
        background-color: red

    .right-side
      +at-breakpoint($break9)
        +span-columns(5 omega, $break9)
        background-color: blue

In this case we only need to apply the background color to the 9 column breakpoint. It will trickle down to the 12 column layout so long as nothing at that breakpoint overrides the setting.

To learn more on how Susy breakpoints work, in addition to the Susy's own [reference][source], the following discussion hits the nail right on the head when it comes to understanding how to use Susy breakpoints:

- [Susy and Media Queries (guide for Muppets)][Muppets]

[Chapter 6]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp6-responsive-web-design.md

[Susy]:                 http://susy.oddbird.net/
[Compass]:              http://compass-style.org/
[basic settings]:       http://susy.oddbird.net/guides/reference/#ref-basic-settings
[.container]:           http://susy.oddbird.net/guides/reference/#ref-basic-mixins
[source]:               http://susy.oddbird.net/guides/getting-started/
[Susy Grids]:           http://net.tutsplus.com/tutorials/html-css-techniques/responsive-grids-with-susy/
[Off-canvas]:           http://oddbird.net/2012/11/27/susy-off-canvas/
[Muppets]:              https://groups.google.com/d/topic/compass-users/oXHAtZE4euI/discussion
