Susy Breakpoints
================

One of the great features of Susy is that breakpoints are baked right in. We could use the breakpoints we created in the [last chapter][Chapter 6], but why not take advantage of the mathematical capabilities of Susy and also be consistent with our grid system at the same time? Sounds like a good plan, and here's how we will use Susy breakpoints in our project.

Set Up
------

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

Using Susy Breakpoints
----------------------

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

[Muppets]:              https://groups.google.com/d/topic/compass-users/oXHAtZE4euI/discussion
