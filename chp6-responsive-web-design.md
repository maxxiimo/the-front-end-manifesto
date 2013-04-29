Responsive Web Design
=====================

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 A List Apart article, "[Responsive Web Design][RWD]", and in his [book][RWD Book] he goes on to explain:

> So what does it take to create a responsive design? Speaking purely in terms of front-end layout, it takes three core ingredients:
>
> 1. A flexible, grid-based layout,
> 2. Flexible images and media, and
> 3. Media queries, a module from the CSS3 specification.

\- Ethan Marcotte, [Responsive Web Design][RWD Book], p.9

Let's take a look at these three components one by one starting with flexible grids. Before we do I want to first recommend the following resources to keep in your back pocket:

- [This Is Responsive][]
- [Responsive Design][]

1. Flexible Grids
-----------------

So the first component of Responsive Web Design is the "flexible, grid-based layout." What this means is a layout whose [grid][] dimensions change proportionately as a containing element, such as the screen size or viewport, changes. For example, if a pages major containing element width were 960 pixels relative to a typical desktop screen, maybe as the screen real estate decreased on a tablet it would make sense to decrease the width to 768 pixels. In other words, proportionally respond to the context in which the page is drawn.

This can be accomplished through the use of relative measurements in declaring grid element dimensions, margins, and/or padding. Ethan Marcotte recommends using percentages as the relative measurement, and in his book gives the following formula to determine these percentages:

Target ÷ Context = Result

...where target is the element in a layout you wish to apply the relevant measurement to, and context is the containing element in which the target responds to. For example, if the main container in your webpage, call it .container, has a width of 960 pixels, and within .container there are two equally sized containers called .left-side and .right-side:

    %body
      .container
        .left-side
        .right-side

...what would there relative measurement widths be?

The context is .container and since it contains two equally sized grid elements we can easily calculate in our heads that since they must be equal, each will have a width of 480 pixels (half of 960 pixels), but rather than use "width: 480px" in our CSS for both elements, we use "width: 50%". Mathematically, using the formula, this is calculated as follows: 480 ÷ 960 = .5 or 50%.

In our CSS we then write:

    .container
      width: 960px

    .left-side, .right-side
      width: 50%

Now if you were to change the size of .container, .left-side and .right-side would proportionally resize themselves to the new container size. Expand this example out to all grid elements including converting the 960px in .container to a percentage, and you have a responsive grid that will resize itself depending upon the context it renders on.

### Using Susy

As you can imagine there's quite a lot of math involved, so rather than calculate all the different percentage for your flexible grid, you can use a grid system that does this for you and save time. There is a pretty comprehensive list of [grid systems][Appendix 2] in the Appendices, but my preference is to use [Susy][] since it is a plug-in of Compass, which we are already using, and more importantly it is authored by [Eric Meyer][] whom I have a great deal of confidence in.

#### Installation

Before we begin I'm going to assume that you have removed or disabled our previous work with user agent sniffing. If so proceed. Installation is pretty straightforward:

*Step 1:* Add the following to */config/compass.rb*:

    require "susy"

*Step 2:* Add the Susy gem to your *.gemfile* and bundle install:

    # Compass specific gems.
    gem 'compass-rails'
    gem 'oily_png'
    gem 'susy'

*Step 3:* Import Susy into your project (uncomment):

app/assets/stylesheets/application.scss

    /* BASIC STRUCTURE
      ============================================================================ */
    @import "susy";
    @import "desktop/layout";

Don't forget to restart your server, and wallah! You have a powerful responsive grid system ready for implementation in your project.

#### Implementation

Within our application layout we will implement our Susy responsive grid as follows:

*Step 1*: Define the [basic settings][] of our grid in *application.scss*:

    /* DEFINITIONS
      ============================================================================ */
    @import "define";

    /*  Susy Grid
      -----------------------

    $total-columns:     12
    $column-width:      4em
    $gutter-width:      1em
    $grid-padding:      $gutter-width

This tells Susy what the basic characteristics of your flexible grid are. In this case the grid spans 12 columns across, each column has a width of 4em with a gutter and grid padding of 1em.

To calculate the total width of your grid including its padding use the following formula:

($total-columns x $column-width) + (($total-columns - 1) x $gutter-width) + ($grid-padding x 2)

(12 x 4em) + ((12 - 1) x 1em) + (1em x 2) = 61em

*Step 2*: Create an [outer grid-containing element][.container] in *application.html.haml* called .container:

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

+container is a Susy mixin that applies the definitions you defined in Step 1 to the outer grid containing element you created in Step 2.

NOTE: We remove the following styles from the body tag since we are now replacing these properties with Susy:

      margin: 0 auto
      width: 960px

#### Susy in Action

Using Susy is also pretty straightforward. Essentially it is a mixin scheme that applies a specified amount of columns to an element, based on the total columns available. If you recall in the previous Flexible Grids section, in our example we used percentages to define our widths:

    .left-side, .right-side
      width: 50%

With Susy instead of using percentages directly, we allow Susy to do the calculations by defining our widths through the Susy +span-columns() mixin:

    .left-side
      +span-columns(6, 12)

    .right-side
      +span-columns(6 omega, 12)

What did we do? Since we set the total number of columns in our Susy grid to 12:

    $total-columns:     12

...for the two elements we are targeting we need only set the total number of columns each element will span of the available 12 columns, i.e. +span-columns(6, 12); in our case half of the available columns for each element. The "omega" in .right-side denotes that it will be the last column in the grid and therefore will not have a gutter (right margin). With this information Susy calculates your percentages and produces the following CSS:

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

And there it is in a nutshell! To really learn how to use Susy – it really packs a lot more punch than what I've shown – the best reference can be found at the [source][]. The following tutorials also demonstrate Susy in action:

- [Responsive Grids With Susy][Susy Grids]
- [Off-canvas layout with Susy][Off-canvas]

NOTE: You may have noticed the "max-with: 59em" property in .container. The reason this is here is to constrain the maximum width in the largest of screens, while maintaining flexibility within this limit. Doing so ensures that pages do not completely span the widths of very large screens and thereby reduce readability. This setting can be overridden in Susy.

2. Flexible Media
-----------------

Now that we have a flexible grid, it's time to look at Ethan's second ingredient in RWD; flexible media. Why flexible media? Imagine loading a 600 pixel wide image into a 320px wide screen. It just doesn't make any sense.









3. Media Queries
----------------

Now that we have a Susy flexible grid, it's time to look at Ethan's second ingredient in RWD; media queries. Our goal is to respond to different screen sizes with content that makes sense for the device being used by our users. For example, maybe in smaller devices it makes sense to use a smaller font size, or a single column layout rather than a three column layout. Media queries will allow us to do this. To understand them and how they will help us, let's take a quick look at their history.

### Media Types

Media dependent stylesheets were first specified in the HTML4 and CSS2 W3C recommendations, and were designed to allow developers to target different devices through [media types][]: all, braille, embossed, handheld, print, projection, screen, speech, tty, tv. The idea was that through these media types, devices the belonged to a specific type could be targeted using @media or @import rules, or the HTML \<link> element, and served styles that applied to them and not other types. For example:

    %link{:href => "screen.css", :media => "screen", :rel => "stylesheet", :type => "text/css"}
    %link{:href => "print.css", :media => "print", :rel => "stylesheet", :type => "text/css"}

In this example screen.css would be served only to devices that were of the "screen" type, and print.css was served to devices of the "print" type.

The problem with this specification in practice for mobile was inconsistent implementation across mobile browsers, plus the list of media types did not accommodate the wide range of device types, especially in regards to different screen sizes. And that's essentially where media queries come in and save the day.

#### Media Queries to the Rescue

With inconsistent browser implementation and so many screen sizes and new devices coming to market, developers found that using media types alone to serve up styles for specific devices was impractical. On June 19, 2012, although in practice well before this, an official W3C recommendation was released that greatly expanded the capabilities of media types through media queries:

> A media query consists of a media type and zero or more expressions that check for the conditions of particular media features. Among the media features that can be used in media queries are ‘width’, ‘height’, and ‘color’. By using media queries, presentations can be tailored to a specific range of output devices without changing the content itself.

\- [Media Queries - W3C Recommendation 19 June 2012][Media Queries]

Unlike media types, media queries, do not solely rely on just a handful of predefined types. Media queries are much more flexible in that they allow developers to test a media type with a logical expression that evaluates to true or false. For example:

    @media (max-width: 480px) { color: red }

In this case, the media type "All" (implied by shorthand syntax) is matched against a devices user agent. If it evaluates to trueBeen the device is then tested for a maximum width of 480px. If it passes the second test the specified styles, the color red, is applied. If false it is not, and the device continues to use the default font color. A smart phone in portrait and landscape mode would pass this test, a desktop computer would not.

In addition to max-width, media queries allow you to test for a broader range of conditions including minimum widths, heights, screen orientation, [and more][]. Perfect for serving up device sensitive styles and content to a wide range of devices.

### Target Devices

Now that we have a basic understanding of media queries, the first step you will need to take before writing your own is determine what screen sizes you plan to target, i.e. what devices are your users using? The best source of this information comes from your weblogs. The following references will also help you understand what's out there and what's being used:

- [StatCounter Global Stats][Stats]
- [Tired of Hunting][]
- [2012 Device Map][]
- [A Simple Device Diagram for Responsive Design Planning][Device Diagram]

In general, here are the most common devices and dimensions:

- 320px (iPhone portrait, default)
- 480px (iPhone landscape)
- 768px (iPad portrait)
- 1024px (iPad landscape)
- 1140+ (Desktops)

So what should you use? In the ResponsiveDesign.is website under [Defining Breakpoints][] the section begins...

> Breakpoints are the point a which your sites content will respond to provide the user with the best possible layout to consume the information.
>
> When you first begin to work with Responsive Design you will define your breakpoints at the exact device widths that you are looking to target. Most often these are the smart phone (usually the iPhone at 320px and 480px), the tablet (usually the iPad at 768px and 1024px) and finally anything above 1024px.
>
> WRONG!
>
> I hope I didn't hurt your feelings but seriously, you're approaching this in the wrong way.

Ha! Something to keep in mind. I like this thinking. We should start with content and see how it looks on different screen sizes, then define our breakpoints.

On the other hand I think it's good to start with something and redefine as content dictates. I like the examples the author gives:

- [media queries for common device breakpoints][breakpoints]

Why don't we grab a few and begin.

### Breakpoints

Based on [StatCounter Global Stats][Stats] for North America over a three month period, it looks like there are five sizes we will need to address. Rather than use device names let's use generic names like: xs (extra small), s (small), m (medium), l (large), and xl (extra large). FYI - The breakpoints we define here will serve as a starting point, we can always change numbers or add/remove sizes (xxs, xxl, etc.) when user needs dictate that we should.

Here is the mapping I'm thinking of:

![][@media Definitions]

Having defined these sizes, and to drill a point home, I want to quote Happy Cog founder Jeffrey Zeldman:

> The most popular size is every size. If you're not thinking in a mobile-first, content-first way, if you're not planning an adaptive or responsive redesign, if you still think we have a standard canvas that ‘everybody’ uses, and if you can't feel the hot breath of mobile singeing the hairs on the back of your neck, you don't deserve to be a designer, or a consultant, or whatever these people think they are.

\- [Browser screen resolution stats rile devs][Happy Cog]

So what do our brand-new breakpoints look like?

    @mixin breakpoint($point)
      @if $point == xxs
        @media (max-width: 130px)
          @content

      @else if $point == xs
        @media (min-width: 240px)
          @content

      @else if $point == s
        @media (min-width: 320px)
          @content

      @else if $point == m
        @media (min-width: 768px)
          @content

      @else if $point == l
        @media (min-width: 1200px)
          @content

      @else if $point == xl
        @media (min-width: 1400px)
          @content

      @else if $point == retina
        @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi)
          @content

How do you use them? First we'll place them in a sass partial called [_media_queries.sass][], and then import them into our application.scss file:

    /* MIXINS
      ============================================================================ */
    @import "compass";
    @import "media_queries";
    @import "mixins"

Then if you want to specify a particular style for an element, lets say a different font color for super small screens for .some-class, you might write something like this:

    .some-class
      color: blue
      @include breakpoint(xxs)
        color: red

Now for any device with a minimum device screen size less than 130px (as defined by the xxs breakpoint), the font color will be red, and blue for everything else. Pretty straightforward.

There's a whole heck of a lot more you can do with media queries. Here are some good references for you if you're interested in learning more:

- [Media queries][]
- [Responsive Web Design in Sass: Using Media Queries in Sass 3.2][Sass Media Queries]
- [Retina Display Media Query][Retina Media Queries]

### Em's and Media Queries

You might have noticed that our responsive grid uses em's in it's definitions, and our media queries are using pixels. In fact all over the web in various media query articles you'll see the use of pixels, but this in fact is not the best practice. Em's-based media queries are actually a better idea and here's why.

Let's say a user – when viewing your project on their desktop – increases the base font size of their browser by hitting CTRL + several times (maybe they have trouble seeing at the default font size). Imagine that the content they are reading is split into three columns, which makes sense on a desktop, and for smaller screen sizes changes to a single column based on breakpoints. When the user zooms in,, the pixel-based breakpoints will have no affect on the layout since the pixel widths remain the same, and that three column layout that used to fit harmoniously into a desktop screen no longer does.

The bottom line, it might not look so good. If those same breakpoints had been defined with em's, the layout would have responded to the base font size increase. In other words, a three column layout would have changed to a single column layout even though the screen size remained the same, which might make better sense than serving the desktop version when zoomed in.

That's a lot to digest, and as usual I'm going to point you to some references that will help you understand the concept better:

- [The EMs have it: Proportional Media Queries FTW!][EMs have it]
- [How we learned to leave default font-size alone and embrace the em][Embrace the em]

NOTE: You can convert our pixel-based breakpoints to em's by dividing each breakpoint by 16: assumption being that the default screen size is 16px and therefore 1em = 16px.

### Susy Breakpoints

One of the great features of Susy is that breakpoints are baked right in. We could use the breakpoints we created above, but why not take advantage of the mathematical capabilities of Susy and also be consistent with our grid system at the same time? Sounds like a good idea, and here's how we will use Susy breakpoints in our project.

First, let's redefine our Susy flexible grid as follows:

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

We're starting from a total column size of 4 instead of 12 since we are approaching development from a mobile first perspective. Then I add breakpoints from 5 to 12 column layouts. I do this because I want to test which breakpoints and corresponding grid layouts are best for the devices I'm targeting. To help me identify the breakpoint being utilized I set up and colorcode my breakpoints as follows:

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

This produces the following @media rules:

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

As you can see it is very similar to what we created manually except Susy calculates all the breakpoints based on the grid we defined and the following formula:

($total-columns x $column-width) + (($total-columns - 1) x $gutter-width)

(12 x 4em) + ((12 - 1) x 1em) = 59em

...and remember that since we're using a base font size of 16px, if you multiply the em's value by that number you will get the equivalent breakpoints in pixels:

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

After reviewing the grid on several different devices I settle on the following breakpoints:

- 4 columns, 19em x 16px = 304px (Samsung, iPhone)
- 6 columns, 29em x 16px = 464px (Small Tablet)
- 9 columns, 44em x 16px = 704px (iPad)
- 12 columns, 59em x 16px = 944px (Desktop)

I then remove the unneeded breakpoints which leaves the following Susy definition:

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break6:            6;
    $break9:            9;
    $break12:           12;

...and in our styles:

    .container
      +container($total-columns, $break6, $break9, $break12)
      +susy-grid-background

      +at-breakpoint($break6)
        +susy-grid-background

      +at-breakpoint($break9)
        +susy-grid-background

      +at-breakpoint($break12)
        +susy-grid-background

Now when you need to apply a particular style to a specific screen size use these breakpoints.

Here is a practical example using the Flexible Grids section example we've been working with. Since our four column base setting is designed for smaller screen sizes, we might want to stack the .left-side and .right-side div's (rather than have them appear cramped side-by-side), but for the remaining three breakpoints we will apply grid widths that will result in a 50-50 side-by-side placement. For illustration purposes let's color .left-side and .right-side red and blue, but only for our two largest screen sizes: ipad and desktops, i.e. $break9 and $break12.

    .left-side
      +span-columns(4 omega, 4)

      +at-breakpoint($break6)
        +span-columns(3, $break6)

      +at-breakpoint($break9)
        +span-columns(4, $break9)
        background-color: red

      +at-breakpoint($break12)
        +span-columns(6, $break12)

    .right-side
      +span-columns(4 omega, 4)

      +at-breakpoint($break6)
        +span-columns(3 omega, $break6)

      +at-breakpoint($break9)
        +span-columns(5 omega, $break9)
        background-color: blue

      +at-breakpoint($break12)
        +span-columns(6 omega, $break12)

What did we do? For the 4 column case we told Susy to span .left-side and .right-side across 4 of the available 4 columns.

    +span-columns(4 omega, 4)

Since they are floated elements, doing so stacks .left-side and .right-side one on top of the other. For the remaining cases we told Susy to float the elements side-by-side equally, except in the case of the 9 column layout. In that case one side is slightly bigger than the other. We can override this if we want to. Finally starting at the 9 column breakpoint, we apply our background color which also trickles down to the 12 column layout.

If you're not too sure how this is all working, in addition to the Susy's own [reference][source] (and the articles I recommend above), the following discussion hits the nail right on the head when it comes to understanding how to use Susy breakpoints:

- [Susy and Media Queries (guide for Muppets)][Muppets]

[Appendix 2]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-2

[RWD]:                  http://www.alistapart.com/articles/responsive-web-design/
[RWD Book]:             http://www.abookapart.com/products/responsive-web-design
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html
[Responsive Design]:    http://alpha.responsivedesign.is/

[grid]:                 http://www.subtraction.com/pics/0703/grids_are_good.pdf
[Susy]:                 http://susy.oddbird.net/
[Eric Meyer]:           http://meyerweb.com/
[basic settings]:       http://susy.oddbird.net/guides/reference/#ref-basic-settings
[.container]:           http://susy.oddbird.net/guides/reference/#ref-basic-mixins
[source]:               http://susy.oddbird.net/guides/getting-started/
[Susy Grids]:           http://net.tutsplus.com/tutorials/html-css-techniques/responsive-grids-with-susy/
[Off-canvas]:           http://oddbird.net/2012/11/27/susy-off-canvas/

[media types]:          http://www.w3.org/TR/CSS21/media.html#media-types
[Media Queries]:        http://www.w3.org/TR/2012/REC-css3-mediaqueries-20120619/
[and more]:             http://www.w3.org/TR/css3-mediaqueries/#media0
[Stats]:                http://gs.statcounter.com/
[Tired of Hunting]:     http://www.websitedimensions.com/
[2012 Device Map]:      http://viljamis.com/blog/2012/responsive-workflow/device-map-2012.pdf
[Device Diagram]:       http://www.metaltoad.com/blog/simple-device-diagram-responsive-design-planning
[Defining Breakpoints]: http://alpha.responsivedesign.is/strategy/page-layout/defining-breakpoints
[breakpoints]:          http://alpha.responsivedesign.is/develop/media-queries/media-queries-for-common-device-breakpoints
[Happy Cog]:            http://www.netmagazine.com/news/browser-screen-resolution-stats-rile-devs-121897
[_media_queries.sass]:  https://github.com/maxxiimo/base-css/blob/master/_media_queries.sass
[Media queries]:        http://alpha.responsivedesign.is/develop/media-queries
[Sass Media Queries]:   http://thesassway.com/intermediate/responsive-web-design-in-sass-using-media-queries-in-sass-32
[Retina Media Queries]: http://css-tricks.com/snippets/css/retina-display-media-query/
[EMs have it]:          http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/
[Embrace the em]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/
[Muppets]:              https://groups.google.com/d/topic/compass-users/oXHAtZE4euI/discussion

[@media Definitions]:   http://chrismaxwell.com/manifesto/media-queries.gif
