Responsive Web Design
=====================

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article, "[Responsive Web Design][RWD]", and in his [book][RWD Book] he defines the core components of responsive web design as follows:

> So what does it take to create a responsive design? Speaking purely in terms of front-end layout, it takes three core ingredients:
>
> 1. A flexible, grid-based layout,
> 2. Flexible images and media, and
> 3. Media queries, a module from the CSS3 specification.

\- Ethan Marcotte, [Responsive Web Design][RWD Book], p.9

Let's take a look at these three components one by one starting with flexible grids. Before we do I want to first recommend the following resources to keep in your back pocket:

- [This Is Responsive][]
- [Responsive Design][]

Flexible Grids
--------------

In layman's terms Ethan's "flexible, grid-based layout" means a webpage that proportionally fits itself into any screen it is viewed in.

<br>
![][Devices]
<br>
<br>

In other words a layout [grid][] with dimensions that resize relative to the screen size or viewport it renders in; a flexible grid.

#### Illustration

If a pages major containing element like the `<body>` tag or containing `<div>` were given a width of 1024 pixels, as the screen real estate decreased – let's say when viewed on a tablet – it wouldn't make sense to continue to draw the element at a size greater than the screen real estate available right?

The problem with this would be that content like text (that looked great on a desktop) might suddenly get cut off in unpredictable places when viewed on a tablet. Users would have to scroll left and right to read it, line after line. Yikes! What a pain that would be.

It would make better sense to decrease the width of the element to 768 pixels when viewed through a tablet, and by less when viewed on a smaller device like a smartphone.

#### Relative Measurements

So how do you find the right width for each and every element where it matters? (And does it really make sense to use a static number like 768 pixels? Not really. There's got to be a better way! Some kind of number that can change as screen sizes change...hmmmm.)

The answer is you use relative measurements when declaring the dimensions of things like grid elements, margins, and/or padding – and with that those elements become variable.

Pretty cool, huh? But what is a freaken' relative measurement!? In a word: percentages. At least that's the one Ethan Marcotte recommends using. He uses the following formula to find them:

*Target ÷ Context = Result*

...where target is the element in a layout you wish to apply the relevant measurement to, and context is the containing element the target responds to.

### Use Case "Practice Problem"

Let's put this into practice. Let's say the container in your webpage, call it `.container`, has a width of 960 pixels and within `.container` there are two equally sized containers called `.left-side` and `.right-side`:

    %body
      .container
        .left-side
        .right-side

...what would there relative measurement widths be?

#### Answer:

In this case, using the formula jargon, the context is `.container` and since it contains two equally sized grid elements we can easily surmise that since they are equal, each will have a width of 480 pixels (half of 960 pixels).

Rather than use `width: 480px` in our CSS for both elements, which would be counterproductive in a device with a 320 pixel wide viewport, we use `width: 50%, and wallah! problem solved across different devices.

Mathematically using the formula this is calculated as follows:

*480 ÷ 960 = .5 or 50%*

In our CSS we then write:

    .container
      width: 960px

    .left-side, .right-side
      width: 50%

Now if you were to change the size of `.container`, both `.left-side` and `.right-side` would proportionally resize themselves to the new container size because they use a relative measurement.

Expand this example out to all grid elements including converting the 960 pixels in *.container* to a percentage, and you have a responsive grid that will resize itself depending upon the context it renders on.

#### Forget the Math!

As you can imagine there's quite a lot of math involved, so rather than calculate all the different percentage for your flexible grid you can use a grid system that does this for you. There is a pretty comprehensive list of [grid systems][Appendix 2] in the Appendices, but my preference is to use [Susy][] since it is a Compass plug-in, which we are already using, and it's extremely flexible and powerful for grid purposes. We will implement Susy into our application in [Chapter 7][].

Media Queries
-------------

The goal of Responsive Web Design is to respond to different screen sizes with content that makes sense for the device being used. For example, maybe in smaller devices it makes sense to use a smaller font size, or a single column layout rather than a three column layout. Media queries will allow us to do this. To understand them, and how they will help our application become responsive, let's take a quick look at their history.

### Media Types

Media dependent stylesheets were first specified in the HTML4 and CSS2 W3C recommendations, and they were designed to allow developers to target different devices through [media types][]: all, braille, embossed, handheld, print, projection, screen, speech, tty, tv. The idea was that through these media types, devices that belonged to a specific type could be targeted using *@media* or *@import* rules, or the HTML *\<link>* element, and served styles that applied to them and not other types. For example:

    %link{:href => "screen.css", :media => "screen", :rel => "stylesheet", :type => "text/css"}
    %link{:href => "print.css", :media => "print", :rel => "stylesheet", :type => "text/css"}

In this example *screen.css* would be served only to devices that were of the "screen" media type, and *print.css* was served to devices of the "print" media type.

Sounds good right? The problem, however was that in practice its implementation was inconsistent across mobile browsers, plus the list of media types did not accommodate the wide range of device types in the market, especially in regards to different screen sizes. And that's essentially where media queries come in to save the day.

#### Media Queries to the Rescue

With inconsistent browser implementation and so many screen sizes and new devices coming to market, developers found that using media types alone to serve up styles for specific devices was impractical. On June 19, 2012, although in practice well before this, an official W3C recommendation was released that greatly expanded the capabilities of media types:

> A media query consists of a media type and zero or more expressions that check for the conditions of particular media features. Among the media features that can be used in media queries are ‘width’, ‘height’, and ‘color’. By using media queries, presentations can be tailored to a specific range of output devices without changing the content itself.

\- [Media Queries - W3C Recommendation 19 June 2012][W3C Media Queries]

Unlike media types, media queries, do not rely only on a handful of predefined types. Media queries are much more flexible and allow developers to test a media type with a logical expression that evaluates to true or false. For example:

    @media (max-width: 480px) { color: red }

In this case, the media type "All" (implied by shorthand syntax) is matched against a devices user agent. If it evaluates to true the device is then tested for a maximum width of 480 pixels. If it passes the second test, the specified style, a red font color, is applied. If false, it is not, and the device continues to use the default font color. A smart phone in portrait and landscape mode would pass this test, a desktop computer would not.

This second dimension of conditional testing opens a whole window of opportunity to serve up device sensitive styles based on logical conditions. Conditions that in addition to `max-width`, include tests for minimum widths, heights, screen orientation, [and more][].

With great power comes great responsibility. Just kidding, but how awesome is that? Now you can create ranges in which certain styles and content will apply, and ranges where it will not. The point at which the conditional logic switch is flipped on or off is referred to as a "breakpoint".

> Breakpoints are the point a which your sites content will respond to provide the user with the best possible layout to consume the information.

\- [Defining Breakpoints][]

### Target Devices and Breakpoints

For our application we're going to base our breakpoints on screen size, which begs the question; what screen sizes do we target, i.e. what devices are my users using? The best source of this information comes from your weblogs. [Appendix 3][] will give you a good sense of what devices are out there in the wild and their corresponding screen sizes.

In general, here are the most common screen sizes:

- 320px (iPhone portrait, default)
- 480px (iPhone landscape)
- 768px (iPad portrait)
- 1024px (iPad landscape)
- 1140+ (Desktops)

So which should you target? Read the following:

> When you first begin to work with Responsive Design you will define your breakpoints at the exact device widths that you are looking to target. Most often these are the smart phone (usually the iPhone at 320px and 480px), the tablet (usually the iPad at 768px and 1024px) and finally anything above 1024px.
>
> WRONG!
>
> I hope I didn't hurt your feelings but seriously, you're approaching this in the wrong way.

\- [Defining Breakpoints][]

#### The Right Way

The take away is don't generalize, start with content and see how it looks on different screen sizes, then define your breakpoints. But despite this take away, I don't think it's such a bad idea to start with some common devices you expect your users will visit your site with, base your breakpoints off of these dimensions, and redefine as content dictates. Here are some common device dimensions:

- [media queries for common device breakpoints][breakpoints]

Too general for you? I feel the same. Try starting with [StatCounter Global Stats][Stats] to figure out what devices people are really using today. The following table is based on statistics for North America over a three month period; it looks like there are five devices we should address:

![][@media Definitions]

Having defined our target devices, and to drill a point home, I want to quote Happy Cog founder Jeffrey Zeldman:

> The most popular size is every size. If you're not thinking in a mobile-first, content-first way, if you're not planning an adaptive or responsive redesign, if you still think we have a standard canvas that ‘everybody’ uses, and if you can't feel the hot breath of mobile singeing the hairs on the back of your neck, you don't deserve to be a designer, or a consultant, or whatever these people think they are.

\- [Browser screen resolution stats rile devs][Happy Cog]

#### Breakpoint Mixin

Our [starter CSS][] includes a breakpoint mixin called [\_media\_queries.sass][_media_queries.sass] that looks something like this:

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

What we've done here is applied our researched media definitions, and used variables to designate devices – to easily make changes in one location. We use generic variables starting with `xxs` (extra extra small) to `xl` (extra large) to avoid marrying a specific device name to oyur code base, things change.

To activate this mixin uncomment `@import "media_queries";` in `application.css.scss`:

    /* MIXINS
      ============================================================================ */
    @import "compass";
    // @import "susy";
    @import "media_queries";
    @import "mixins";

Then, if you want to specify a particular style for an element based on screen size, you can write something like this:

    .some-class
      color: blue
      @include breakpoint(xl)
        color: red

In this style any device with a screen size less than 1400 pixels (as defined by the `xl` breakpoint) will use a blue font color, and red for everything that is 1400 pixels or greater.

To learn more check out the following:

- [CSS Media Queries][]
- [Media queries][]
- [Responsive Web Design in Sass: Using Media Queries in Sass 3.2][Sass Media Queries]
- [Retina Display Media Query][Retina Media Queries]
- [Conditional Media Query Mixins][Conditional Media Query]

### Em's and Media Queries

You might have noticed that our responsive grid uses em's in it's definitions, and our media query example above uses pixels (the actual file does not). In fact, all over the web in various media query articles you'll see the use of pixels, but this is not the best practice. Em's-based media queries are actually a better idea and here's why:

Let's say a user – when viewing your project on their desktop – increases the base font size of their browser by hitting CTRL + several times (maybe they have trouble seeing at the default font size).

Imagine that the content they are reading is split into three columns, which makes sense on a desktop, and for smaller screen sizes changes to a single column based on pixel-based breakpoints. When the user zooms in, the pixel-based breakpoints have no affect on the layout since the pixel widths of the webpage remain the same, but that three column layout that used to fit so harmoniously is now difficult to read.

If those same breakpoints had been defined with em's, the layout would have responded to the base font size increase. In other words, a three column layout would have changed to a single column layout even though the screen size remained the same, which might make better sense for readability than serving a three column desktop version when zoomed in.

That's a lot to digest, and as usual I'm going to point you to some references that will help you better understand the concept:

- [The EMs have it: Proportional Media Queries FTW!][EMs have it]
- [How we learned to leave default font-size alone and embrace the em][Embrace the em]

NOTE: You can convert pixels to em's by dividing the pixels by 16: assumption being that the default screen size is 16 pixels and therefore 1em = 16px.

Flexible Media
--------------

Now that we have a flexible grid system and understand media queries, it's time to look at the final ingredient in RWD: Flexible Media. Why flexible media? Imagine loading a 600 pixel wide image into a 320 pixel wide screen. What would happen?

Here's a practical example; using breakpoints the following image looks fine on a desktop:
<br>
<br>
![][Image 1]

Here it is on an iPad:
<br>
<br>
![][Image 2]

I added a dotted red border to both containing boxes to illustrate what happens when an image is rendered within a smaller containing element: It bleeds through its borders.


### Overflow and Maximum Widths

One solution to this problem is to use:

    overflow: hidden

The result:
<br>
<br>
![][Image 3]

Although this solution prevents the bleeding image issue, it's not the silver bullet we're looking for. As you can see part of the image is clipped. We need the image to shrink relative to its containing element. Fortunately, there is a simple CSS technique that will accomplish this. Add the following style:

    img, embed, object, video
      max-width: 100%

And just like that, in all modern browsers, your image will proportionally shrink to fit in its containing element (and with this technique you've also covered several other media types).

The end result:
<br>
<br>
![][Image 4]

Of course to be completely responsive we should address font sizes and the space between the image and the text for this breakpoint.

NOTE: IE 6 does not support max-width, you will need to use `width: 100%` and follow the directions [in this article][article].

### CSS Background Property

But still, this isn't the silver bullet I'm looking for. One thing you need to consider is that in a smart phone, although the image will resize to its container, it's still larger than necessary and will consume bandwidth. In mobile bandwidth comes at a premium so wherever we can save on bandwidth we improve the user experience.

One possible solution is to serve a completely different lighter image for smaller screens using the CSS background property:

    .images-container
      background: image-url("icons/devices-100px.png") 0 0 no-repeat

      @include breakpoint(m)
        background: image-url("icons/devices-200px.png") 0 0 no-repeat

      @include breakpoint(l)
      background: image-url("icons/devices-350px.png") 0 0 no-repeat

The beauty of this method comes in the bandwidth savings, but the drawback is the need to create multiple images. I personally don't mind doing this.

[Chapter 7]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-susy.md#susy
[Appendix 2]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-2
[starter CSS]:          https://github.com/maxxiimo/base-css

[RWD]:                  http://www.alistapart.com/articles/responsive-web-design/
[RWD Book]:             http://www.abookapart.com/products/responsive-web-design
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html
[Responsive Design]:    http://alpha.responsivedesign.is/

[grid]:                 http://www.subtraction.com/pics/0703/grids_are_good.pdf
[Susy]:                 http://susy.oddbird.net/

[media types]:          http://www.w3.org/TR/CSS21/media.html#media-types
[W3C Media Queries]:    http://www.w3.org/TR/2012/REC-css3-mediaqueries-20120619/
[and more]:             http://www.w3.org/TR/css3-mediaqueries/#media0

[Defining Breakpoints]: http://alpha.responsivedesign.is/strategy/page-layout/defining-breakpoints
[breakpoints]:          http://alpha.responsivedesign.is/develop/media-queries/media-queries-for-common-device-breakpoints
[Stats]:                http://gs.statcounter.com/

[Happy Cog]:            http://www.netmagazine.com/news/browser-screen-resolution-stats-rile-devs-121897
[_media_queries.sass]:  https://github.com/maxxiimo/base-css/blob/master/app/assets/stylesheets/_media_queries.sass
[CSS Media Queries]:    http://cssmediaqueries.com/
[Media queries]:        http://responsivedesign.is/guidelines/media-queries
[Sass Media Queries]:   http://thesassway.com/intermediate/responsive-web-design-in-sass-using-media-queries-in-sass-32
[Retina Media Queries]: http://css-tricks.com/snippets/css/retina-display-media-query/
[Conditional Media Query]: http://css-tricks.com/conditional-media-query-mixins/
[EMs have it]:          http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/
[Embrace the em]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/

[article]:              http://unstoppablerobotninja.com/entry/fluid-images

[Devices]:              http://chrismaxwell.com/manifesto/chp-6/devices.png
[@media Definitions]:   http://chrismaxwell.com/manifesto/chp-6/media-queries.gif
[Image 1]:              http://chrismaxwell.com/manifesto/chp-6/images-1.gif
[Image 2]:              http://chrismaxwell.com/manifesto/chp-6/images-2.gif
[Image 3]:              http://chrismaxwell.com/manifesto/chp-6/images-3.gif
[Image 4]:              http://chrismaxwell.com/manifesto/chp-6/images-4.gif
