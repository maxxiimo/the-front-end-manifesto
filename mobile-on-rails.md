Mobile on Rails
===============

In Chapter 1 we learned about [foundation markup][Chapter 1], and in Chapter 2, [foundation styles][Chapter 2], but we never addressed mobile. What about smartphones and tablets? What about mobile browsers!! In the old days it never really was an issue for most developers. All you really had to worry about "cross anything" were browser issues. Desktop screen sizes were debated then, but it could be overlooked since the differences were not so great or prevalent, and the "fix" came relatively quickly: the industry settled on standard design widths and/or employed liquid layouts.

Fast-forward to today and as a front end engineer you cannot help but think about screen size, and the fix is a bit more difficult than it was back then to say the least!

> Mobile browsing is rapidly consuming the Internet. The smartphone and tablet lifestyle is replacing laptops and desktop computers as the primary way we go online.

\- [Mobile Browsing: It Will Get Better and Worse][Better and Worse] by Chris Kelly of New Relic

The fact of the matter is, your end-users are going to consume your work on smartphones or some kind of tablet. I think this is pretty much [common knowledge][] now, so let's deal with it proactively by laying down a mobile foundation. In this chapter we are going to explore the different ways in which we can serve content tailored to the different devices our users are using, and in this process develop our own mobile foundation's best practices.

Mobile First
------------

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit in Boston, we took an existing desktop application and turned it into a mobile app (pre-smartphone era). The result was a precise definition of the applications basic information architecture, no more no less. Several of my colleagues pointed this out to me, and used the mobile application to better architect the greater desktop application.

As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense to me for information architecting alone, but given the large and increasing number of mobile users out there, it is an approach that you as a front end developer should consider adopting when building any application. In the very least, DO NOT leave mobile design as an afterthought.

Throughout the rest of this book I will take the Mobile First approach.

Plan of Attack
--------------

When I asked [LaunchWare][] founder Dan Pickett what he thought was the best approach for mobile, his answer was so succinct (and backed with experience) that it deserves quoting in its entirety:

> We've generally found, UI/UX wise, though that the paradigm is so different that it generally requires a different set of controllers and views.
>
> So I see three or four different levels:
>
> - A responsive design for content oriented / non-workflow based sites (pure HTML/CSS/JS solution)
> - A set of different mobile vs. traditional web views sharing the same controllers (use only when the workflow experience is the same on both paradigms, but still have request specs exercising both mediums)
> - A set of different controllers and views optimized for each experience, with appropriate request specs for each paradigm. (we've suggested this approach in most apps - shared business logic, different views and controllers)
> - A separate, mobile web application that talks to the main application client side via a service oriented architecture (this is usually the last progression before going native, and we only go this route if the mobile app is vastly different from the web application)
>
> The later three allow for a phonegap or a similar solution so that the app can be listed in the app stores and can take advantage of some of the native functions of the device.

I think I would enjoy writing a book called "Mobile on Rails" after exploring the avenues he presents, but for this chapter (of this book) let's narrow down our plan of attack to the following:

1.  Detect user agents to serve mobile versions of our website.

2.  Detect screen size via media queries to serve up responsive web design.

3.  A hybrid of 1 and 2.

Personally I like to separate concerns and tend to use option three, but include responsive design within this separation since there is no one size fits all in mobile. I'm not alone in this thinking:

> Now, oftentimes, people think about device detection as a "one or the other" sort of thing. Either you’re doing responsive design or you’re using device detection to route people to separate templates, and that you would choose one of those two options; you wouldn’t build something that uses both. But we’ve actually combined responsive design with server-side detection quite a bit.

\- [Jason Grigsby – Mobile-First Responsive Design][Jason Grigsby] Podcast by Sean Carmichael

Like Jason Grigsby, I don't think an all or nothing approach really makes sense as a rule of thumb. Let the situation dictate the solution. Here are some thoughts on option 1 versus option 2:

- Keep them separate and you can serve lighter, device specific stylesheets, JavaScript and images. This translates to less complexity and better performance.
- As applications grow and user needs change, it might become necessary to separate mobile out completely. If you start out separate this transition might be easier.
- Many argue that if you keep styles together, you won't forget to work on one while working on the other.
- Designing for a mobile, tablet and desktop versionProcess of your website can be time-consuming, responsive design can accommodate all three.
- You may mis-categorize or entirely miss mobile devices using user agent strings and device databases.

The article [Reasons for Responsive Design][Responsive Reasons] give you some good reasons why you should consider using it. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Fools Gold]" gives an opposite perspective and does a good job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. There is one quote in particular that the author uses that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.

\- [Mobile Design and Development ][Brian Fling] by Brian Fling

On the other hand, Jiří Stránský -- the author of the Mobvious gem we implement later in this chapter -- commented to me:

> I think responsive web design is going to be preferred over server-based solutions for the vast majority of use cases in the future, for two main reasons:
>
> 1. Boundaries within device types will blend. It used to be PCs and phones, now it's tablets, TVs, e-book readers and more. It's hard to detect them server-side and for some of them, even if you know what device it is, you're still not sure what category they should belong to :) Hence the term "phablets" :)
>
> 2. Bandwidth is less of an issue, year by year. It will be best to send the whole thing to the client, then detect client's precise capabilities and render what you want, how you want.

Whatever approach you decide, keep in mind that there are a spectrum of user and business needs. Responsive may in fact be the silver bullet for some sites on that spectrum, and for others not. For example my personal website is pretty simple so maybe detecting user agents to serve a mobile version of the site is not the best use of my time. In this case why not use Responsive Web Design and keep things together? But more complex applications may need to serve up specific markup and styles, take for example Basecamp mobile:

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer... under-the-hood it would have been all wrong.

\- [Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore all three plans of attack.

I. User Agent Sniffing
----------------------

When web-enabled mobile phones first appeared, front end engineers we were faced with many challenges:

- Mobile browsers were relatively unsophisticated and operating system/device bound, the browser market was highly fragmented, and browsers rendered and/or supported languages inconsistently.
- Parsing issues due to different protocol (WAP versus HTTP) markup languages: Wireless Markup Language (WML), XHTML Mobile Profile / XHTML Basic, HTML
- Bandwidth, latency, and CPU issues were significantly worse than what we experience today.
- Screen sizes were much more varied or unstandardized, and smaller than today.
- Carrier "walled gardens" oftentimes did not allow CSS, or JavaScript, or HTML tables, or any combination of the three.
- Proxy servers might strip your site of images, flash (hugely popular back then), multimedia, or enforce throughput limitations.
- Only a basic set of media types were available and they were implemented inconsistently across browsers.
- A highly fragmented device market made compatibility testing extremely difficult.

At Fidelity, under these challenges, we wanted to cover 99.999% of all web-enabled mobile phones out there [possibly exaggerated by me]. To accomplish this we developed a super dumbed down HTML 1.0 interface that would work on 90% of all devices, and for the edge cases we served an alternative markup. We did so by analyzing the devices HTTP_ACCEPT header and HTTP_USER_AGENT header, i.e. user agent sniffing. Over time with all the customers that Fidelity had, the company developed an extensive database of devices that their customers used which included the device's screen size, operating system, and other pertinent information. Armed with this information Fidelity could then serve tailored markup for edge cases depending on the request and the information it contained.

Fast-forward to today, and you can still effectively use device user agents and third-party databases to identify browsers, screen resolutions, type of device, and based on this information determine what markup and styles to serve.

There are a number of different solutions you can use to deliver mobile versions of your application using user agent sniffing. Take a look at the [Mobile Solutions Roundup][Mobile Roundup] in the Appendix to get an idea of what's out there.

### Mobylette

To deliver our mobile views lets experiment with one of the quickest and simplest solutions: Tiago Scolari's [mobylette][] gem with [jQuery Mobile][] for our user interface. Here are the steps you will follow to implement this solution:

*Step 1:* Copy all the [base-mobile][] files from the mobylette folder and place them into their corresponding directories, i.e. stylesheets/mobile files go in stylesheets/mobile in your application.

*Step 2:* Add the following to your application.rb file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

([Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work])

*Step 3:* Add the following gem to your Gemfile and then bundle install:

    gem 'mobylette'

*Step 4:* Add the following line to application_controller.rb:

    include Mobylette::RespondToMobileRequests
    mobylette_config do |config|
      config[:skip_xhr_requests] = false
    end

*Step 5:* Add the following to your config/environments/production.rb:

    # Precompile additional assets (application.js, application.css, and all non-JS/CSS are already added)
    config.assets.precompile += %w( modernizr-2.6.2.min.js, jquery.mobile-1.2.0.css )

And that's it! I like to use [User Agent Switcher][] to test on my browser. Give it a try.

There certainly does seem to be a lot of repetition in our code, two files for almost everything. So you know, if a .mobile.haml file is not available, Mobylette will default to a regular .html.haml file. I personally like splitting concerns, but I also understand that this may not be the best approach for many projects. One of the key arguments for Responsive Web Design is the elimination of duplication. We will investigate this option thoroughly, but before then let's try a more advanced agent sniffing solution.

### Mobvious

For an alternative to Mobylette we we use a gem called [Mobvious][]. It is a rack-based solution and easy to set up, and highly configurable and versatile in on how you detect mobile requests:

1.  User-Agent sniffing
2.  URL pattern matching
3.  Remembering a user's manual choice

#### Set Up

Here are the steps we will use to configure Mobvious for our needs:

*Step 1:* Copy all the [base-mobile][] files from the mobvious folder and place them into their corresponding directories, i.e. stylesheets/mobile files go in stylesheets/mobile in your application.

*Step 2:* Add the following to your application.rb file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

([Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work])

*Step 3:* Add the following gems to your Gemfile and then bundle install:

    gem 'mobvious'
    gem 'mobvious-rails'

*Step 4:* Add the following into application.rb:

    # Tell your app to use Mobvious::Manager as Rack middleware.
    config.middleware.use Mobvious::Manager

*Step 5:* Add the following includes into application_controller.rb and application_helper.rb:

    include Mobvious::Rails::Controller

    include Mobvious::Rails::Helper

*Step 6:* Create a initializer file (config/initializers/mobvious.rb) and configure it as follows:

    Mobvious.configure do |config|
      config.strategies = [ Mobvious::Strategies::MobileESP.new(:mobile_desktop) ]
    end

Don't forget to restart your application, and wallah! You have a detection strategy that will detect user agents and return a variable of :mobile or :desktop depending on the device type of the request. Tablets as configured here will returns :desktop.

To test that it is working you can use:

    def device_test
        # Drop in controller: @device = request.env['mobvious.device_type']
        no_device = "What!? That's nil bro."
        if @device.nil?
          no_device
        else
          "#{@device}"
        end
    end

#### Usage

Now that we have it set up, here is how we will use it. From our [Mobile Solutions Roundup][Mobile Roundup] we combine a bit of [Ryan Bates][] mobile solution with Mobvious. Part of Ryan Bates solution creates a new mime type (:mobile), and uses a before_filter to test if the request is a mobile request. If true, the mime type is set to :mobile. As such, only files named with a ".mobile.haml" extension will be served.

To do this in our application we add the following to application_controller.rb:

    class ApplicationController < ActionController::Base
      protect_from_forgery
      include Mobvious::Rails::Controller
      before_filter :prepare_for_mobile


      private

      def prepare_for_mobile
        if request.env['mobvious.device_type'] == :mobile
          request.format = :mobile
        end
      end
    end

...and the following to /config/initializers/mime_types.rb:

    Mime::Type.register_alias "text/html", :mobile

Just like in the simple solution, requests from different devices will be served up the correct markup and styles for the device, based on the new mime type.

#### Reorganize

Our solution is working well, but I'm feeling like there are too many files in each app/views folder – some ending with ".html.haml" others with ".mobile.haml". To better organize we can create a special folder just for our mobile views by adding the following to the prepare_for_mobile method in application_controller.rb:

    def prepare_for_mobile
      if request.env['mobvious.device_type'] == :mobile
        request.format = :mobile
        **prepend_view_path "app/views/mobile"**
      end
    end

Now in addition to our mime type, we have designated a specific view path as the location to organize our mobile views. Go ahead and create the new app/views/mobile folder and move all mobile views there.

With this new folder structure there really is no need for different mime types. With a common mime type you can use the same partials for both desktop and mobile devices, and through Rails template inheritance your application will default to regular views when mobile views in the new folder are not available; which is especially useful when making an existing app mobile friendly a little bit at a time.

Remove:

- the mime type we defined in mime_types.rb
- request.format = :mobile in application_controller.rb in the preparer_for_mobile method

NOTE: More often than not the same content will be used in both the mobile and regular versions of your site. With template inheritance you can refactor content into partials, and have both the regular and mobile versions use the same partials. This can get messy though so be careful. It may be overkill.

If you prefer to organize your mobile views outside of the regular app/views path, for example in app/views_mobile, swap the prepend_view_path with:

         prepend_view_path Rails.root + 'app' + 'views_mobile'

II. Responsive Web Design
-------------------------

User agent stiffing is awesome, but what about in projects where it's overkill? Is there something else we can do? The answer is yes, and it's called Responsive Web Design. Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][RWD]". In his corresponding book he explains:

> So what does it take to create a responsive design? Speaking purely in terms of front-end layout, it takes three core ingredients:
>
> 1. A flexible, grid-based layout,
> 2. Flexible images and media, and
> 3. Media queries, a module from the CSS3 specification.

\- Ethan Marcotte, [Responsive Web Design][RWD Book], p.9

If you're interested in learning more definitely read the book, it's pretty good, and also checkout:

- [This Is Responsive][]
- [Responsive Design][]

Let's take a look at these three components one by one starting with flexible grids.

### Flexible Grids

"A flexible, grid-based layout" is a layout that proportionally responds via CSS to the context in which the page is drawn. In other words the grids dimensions are flexible and change proportionately as a screen size changes. It does so through the use of percentages or em's in declaring a containers dimensions, margins, and/or padding.

Ethan recommends using percentages which are determined by taking the target width and dividing it by the context in which that width proportionally responds to.

Target ÷ Context = Result

For example, if the main container in your webpage, call it .container, has a width of 960 pixels, and within .container there are two equally sized containers called .left-side and .right-side:

    %body
      .container
        .left-side
        .right-side

...what would there widths be?

Well obviously half of 960 pixels: 480 pixels, and declaring percentages for this equally obvious: 50%. Mathematically, using the formula, this is calculated as follows: 480 ÷ 960 = .5 or 50%.

    .container
      width: 960px

    .left-side
      width: 50%

    .right-side
      width: 50%

Now if you were to change the size of .container, .left-side and .right-side would proportionally resize themselves to the new container size. Expand this example out to all containers and you have a responsive grid that will resize itself depending upon the screen size it is drawn into.

### Using Susy

Rather than calculate all the different percentage ratios within a layout, I prefer to use a grid system and save some time. You will find a pretty comprehensive list of [Grid Systems][]in the appendix, but my preference is to use [Susy][] since we are already using Compass, and it is authored by Eric Meyer whom I have a great deal of confidence in. On top of that it is based on em's which is my metric of choice, more on this below and in [Chapter 5][].

#### Installation

Installation is pretty straightforward:

*Step 1:* Add the following to /config/compass.rb:

    require "susy"

*Step 2:* Add the Susy gem to your .gemfile and bundle install:

    # Compass specific gems.
    gem 'compass-rails'
    gem 'oily_png'
    **gem 'susy'**

*Step 3:* Import Susy into your project:

app/assets/stylesheets/mobile.scss

    /* BASIC STRUCTURE
      ============================================================================ */
    **@import "susy";**
    @import "mobile/layout";

app/assets/stylesheets/application.scss

    /* BASIC STRUCTURE
      ============================================================================ */
    @import "susy";
    @import "desktop/layout";
    // @import "grids";

Don't forget to restart your server, and wallah! You have a pretty powerful responsive grid system ready for implementation in your project.

#### Implementation

Within our application layout we will implement our Susy responsive grid as follows:

*Step 1*: Define the [basic settings][] of our grid:

app/assets/stylesheets/mobile.scss

    /* DEFINITIONS
      ============================================================================ */
    @import "define";

    /*  Susy Grid
      -----------------------

    $total-columns:     5
    $column-width:      4em
    $gutter-width:      1em
    $grid-padding:      $gutter-width

app/assets/stylesheets/application.scss

    /* DEFINITIONS
      ============================================================================ */
    @import "define";

    /*  Susy Grid
      -----------------------

    $total-columns:     12
    $column-width:      4em
    $gutter-width:      1em
    $grid-padding:      $gutter-width

NOTE: We do not add these definitions directly into our define partial because the variables will differ between desktop and mobile versions of our application.

*Step 2*: Create an [outer grid-containing element][.container] in our application.html.haml (for both desktop and mobile) by creating a \<body> tag child \<div> called .container:

app/views/mobile/layouts/application.html.haml

    %body
      **.container**
        %header{:role => "banner"}
          = render :partial => 'shared/navigation'
          .header
            = render :partial => 'shared/logo'
        #main{:role => "main"}
          = yield
        = render :partial => 'shared/footer'
      = scripts

app/views/layouts/application.html.haml

    %body
      **.container**
        = chromeframe
        %header{:role => "banner"}
          = render :partial => 'shared/logo'
          = render :partial => 'shared/navigation'
        #main{:role => "main"}
          = yield
        = render :partial => 'shared/footer'
      = scripts

*Step 3*: Add the corresponding CSS:

app/assets/stylesheets/desktop/_layout.sass and app/assets/stylesheets/mobile/_layout.sass

    .container
      +container

NOTE: We removed...

      margin: 0 auto
      width: 960px

...from the desktop version body tag since we are now replacing these properties with Susy.

#### Use

In our previous flexible grid example:

    %body
      .container
        .left-side
        .right-side

...we used percentages to define our flexible widths:

    .container
      width: 960px

    .left-side
      width: 50%

    .right-side
      width: 50%

With Susy .container does not need to be set since it was defined in step three of our implementation, and for the two remaining layout elements we would use Susy as follows:

    .left-side
      +span-columns(6, 12)

    .right-side
      +span-columns(6 omega, 12)

What did we do? Earlier on we set the total number of columns in our Susy grid to 12:

    $total-columns:     12

For the two elements we layout we then set the total number of columns the element will span through the +span-columns() mixin. In our case half of the available columns for each element. The "omega" in the .right-side element denotes that this element will Contain the last column in the grid and therefore will not have a right margin.

To learn how to use Susy, the best reference can be found at the [source][]. The following tutorials also demonstrate Susy in action:

- [Responsive Grids With Susy][Susy Grids]
- [Off-canvas layout with Susy][Off-canvas]

### @media

Now that we have a Susy flexible grid, it's time to look at Ethan's second ingredient in RWD; media queries. To understand them let's take a little look at their history.

#### Media Types

Media dependent stylesheets were first specified in the HTML4 and CSS2 W3C recommendations and were designed to allow developers to target specific device types. The recognized [media types][] were: all, braille, embossed, handheld, print, projection, screen, speech, tty, tv (CSS2).

Media types could be targeted via @media or @import rules, or in the HTML \<link> element. For example:

    %link{:href => "screen.css", :media => "screen", :rel => "stylesheet", :type => "text/css"}
    %link{:href => "print.css", :media => "print", :rel => "stylesheet", :type => "text/css"}

The problem with this specification though was inconsistent implementation across mobile browsers, plus the list of media types did not accommodate the wide range of screen sizes. Could you imagine how useless it would be today? And that's where media queries came in and saved the day.

#### Media Queries

With so many screen sizes and new devices popping up left and right, using media type alone to serve up styles for specific devices would be impractical. Media queries, on the other hand, do not solely rely on just a handful of predefined types. Media queries are much more flexible in that they allow you to test a media type with a logical expression that evaluates to true or false. For example:

    @media (max-width: 480px) { color: red }

In this case, the media type All (implied by shorthand syntax) is matched against the devices user agent. If they match the device is then tested for a maximum width of 480px, e.g. a smart phone in portrait and landscape mode would pass this test, a desktop computer would not. If the statement is true the specified styles, the color red, are applied. If false they are not, and the device continues to use the default font color.

Unlike the old specification, media queries allow you to move beyond a finite set of media types, and test for a broader range of conditions including minimum and maximum widths, heights, screen orientation, [and more][Media Queries]. Perfect for serving up device sensitive styles and content to a wide range of screen sizes and device capabilities.

### Target Devices

Before we write our own media queries we need to determine what screen sizes we plan to target. I'm going to make the assumption that our audience uses desktop computers/laptops, tablet devices, and smart phones, but not televisions or anything else for that matter to browse the web. I'm making this assumption to give us something to work with, but you should check your Web logs!

So what dimensions should we use? Here are some references to help you decide:

- [StatCounter Global Stats][Stats]
- [Tired of Hunting][]
- [2012 Device Map][]
- [A Simple Device Diagram for Responsive Design Planning][Device Diagram]

Here are some common device dimensions:

- 320px (iPhone portrait, default)
- 480px (iPhone landscape)
- 768px (iPad portrait)
- 1024px (iPad landscape)
- 1140+ (Desktops)

So what should we use? In the ResponsiveDesign.is website under [Defining Breakpoints][] the section begins...

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

Based on [StatCounter Global Stats][Stats] for North America over the last three months, it looks like there are five sizes we should define. Rather than use device names let's use generic names like: xs (extra small), s (small), m (medium), l (large), and xl (extra large). FYI - The breakpoints we define here will serve as a starting point, we can always change numbers or add/remove sizes (xxs, xxl, etc.) when user needs dictate that we should.

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

How do you use them? First we'll place them in a sass partial called [_media_queries_px.sass][px media querries], and then import them into our application.scss file (this will be included by default in your base styles):

    /* MIXINS
      ============================================================================ */
    @import "compass";
    @import "media_queries_px";
    @import "mixins"

Then if you want to specify a particular style for whatever, lets say a different font color for super small screens, you might write something like this:

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

You might have noticed that our responsive grid uses em's, and our media queries are using px's. In fact all over the web in various media query articles you'll see the use of px's, but this in fact is not the best practice. Em's-based media queries are actually a better idea and here's why:

Let's say your user – when viewing your project on their desktop – increases the base font size of their browser by hitting CTRL + several times (maybe they're a baby boomer and have trouble seeing at the default font size). Imagine that the content they are reading is contained in a \<div> using px's to define width, well when the user increases the base font size nothing will happen with its containing div, the width will remain the same, and those lines of text they are reading will be squeezed into the same \<div> – that smaller lines of text once harmoniously fit into.

The bottom line, it might not look so good. If that same \<div>'s width had been defined with em's, it's width would have increased proportionally with the base font size increase. In other words, the amount of text per line would not dramatically alter the contents readability.

If we use em's for our breakpoints, the trigger for the breakpoint would also take into account the base font size since it is based on em's, and even though the actual screen size has not changed, serving a layout on their desktop designed for smaller devices might make better sense when a larger base font is used.

That's a lot to digest, and as usual I'm going to point you to some references that will help you understand the concept better:

- [The EMs have it: Proportional Media Queries FTW!][EMs have it]
- [How we learned to leave default font-size alone and embrace the em][Embrace the em]

I've gone ahead and [converted the above breakpoints][converted breakpoints] to em's for you by dividing each breakpoint by 16: assumption being that the default screen size is 16px and therefore 1em = 16px. They are already part of your base styles if you are following along with the book.

### Susy Breakpoints

One of the great features of Susy is that breakpoints are baked right in. We could use the breakpoints we created above, but why not take advantage of the mathematical capabilities of Susy and also be consistent with our grid system at the same time.

Here's how we will use Susy breakpoints in our project. First, let's define our Susy flexible grid as follows:

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


We're starting from a total column size of 4 instead of 12 since we are approaching development from a mobile first perspective. Then I add breakpoints from 5 to 12 columns. I do this because I want to test which breakpoints are best for the devices I'm targeting. To identify the breakpoint being utilized I set up my styles as follows:

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

As you can see it is very similar to what we created manually except Susy calculates all the breakpoints based on the grid set up and following formula:

($total-columns x $column-width) + (($total-columns - 1) x $gutter-width)
(12 x 4em) + ((12 - 1) x 1em) = 59em

...and remember that since we're using a base font size of 16px, if you multiply the em's value by that number you will get the equivalent in px:

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

- Samsung, iPhone: 4 columns, 19em x 16px = 304px
- Small Tablet: 6 columns, 29em x 16px = 464px
- iPad: 9 columns, 44em x 16px = 704px
- Desktop: 12 columns, 59em x 16px = 944px

...which leaves the following Susy definitions:

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

Now when you need to apply a particular style that is dependent on specific screen sizes use these breakpoints. In our example from before:

    %body
      .container
        .left-side
        .right-side

    .left-side
      +span-columns(6, 12)

    .right-side
      +span-columns(6 omega, 12)

With the new breakpoints set up we can add styles that will only take affect when the viewport reaches the defined breakpoint.

Here is a practical example. Our four column base setting is designed for smaller screen sizes so we might want to stack the .left-side and .right-side div's (rather than have them appear cramped side-by-side), but for the remaining three breakpoints we will apply grid widths that will result in a 50-50 side-by-side placement. For illustration purposes let's color .left-side and .right-side red and blue, but only for our two largest screen sizes: ipad and desktops, i.e. $break9 and $break12.

    .left-side
      +span-columns(4 omega, 4)

      +at-breakpoint($break6)
        +span-columns(6, $break6)

      +at-breakpoint($break9)
        +span-columns(9, $break9)
        background-color: red

      +at-breakpoint($break12)
        +span-columns(12, $break12)

    .right-side
      +span-columns(4 omega, 4)

      +at-breakpoint($break6)
        +span-columns(6 omega, $break6)

      +at-breakpoint($break9)
        +span-columns(9 omega, $break9)
        background-color: blue

      +at-breakpoint($break12)
        +span-columns(12 omega, $break12)

If you're not too sure how this is all working, in addition to the Susy's own [reference][source] (and the articles I recommend above), the following discussion hits the nail right on the head when it comes to understanding how to use Susy breakpoints:

[Susy and Media Queries (guide for Muppets)][Muppets]

### Flexible Media

Now that we have a flexible grid and em-based media queries, it's time to look at Ethan's second ingredient in RWD; flexible media. Why flexible media? Imagine loading a 600 pixel wide image into a 320px wide screen. It just doesn't make any sense.





### Conditional Loading




III. A Hybrid Approach
----------------------

> That’s not to say that mobile websites are inherently flawed, or that there aren’t valid business cases for creating them. But I do think fragmenting our content across different "device-optimized" experiences is a losing proposition, or at least an unsustainable one. As the past few years have shown us, we simply can’t compete with the pace of technology.

\- Ethan Marcotte, [Responsive Web Design][RWD Book], p.96

...But what about a hybrid approach? What Ethan says here is true, things are happening so fast it could be difficult to keep up with the speed of change using User Agent Sniffing to deliver a mobile version of a website – some devices might not register as mobile and receive the desktop version of the website.

On the other hand, a purely responsive web design may deliver too much bloat for smaller devices with lower connection speeds, higher latency, and smaller CPUs. On top of that, smaller devices may require a lot more tweaks between device capabilities (from dumb phones to smart phones), and require developers to contend with a greater amount of screen size increments found with smaller devices. All of these factors might be good reason to keep code organized separately, not just in a separate stylesheet or hidden and conditionally loaded elements, but as a separate system entirely.

If we took this hybrid approach, we might do so by providing responsive web design specifically for small screen devices that register as mobile via our user agent detection scheme. These devices would not receive any of the bloat that may be associated to desktop and tablet versions of our website. We could also use the information available in user agent strings for even greater levels adaptation and tweaking.

For non-mobile we can use a different responsive web design that provides a small screen responsive design backup for those devices the slip through the cracks.

Will this be too much work? That remains to be discovered, but if we should choose to use this type of approach here is how we would do it:

1. Leave the User Agent Sniffing solution in place.

2. Leave the Susy-based Responsive Web Design in place as is.

3. Create a second Susy-based Responsive Web Design specifically for small devices.

### File Structure

To create a second Susy-based responsive web design specifically for small devices we are literally going to take all of the techniques we learned in the previous section, and repeat them for mobile. First let's understand where everything will belonged by revisiting the lay of the land, i.e. our file organization:

![][file-structure]

What you see is our project as it is organized up until now. To understand how this relates with a hybrid approach allow me to draw a couple arrows and explain:

![][file-structure-w-lines]

**(1)** There are two main stylesheets:

- **mobile.scss** which organizes and pulls together all the partials under the mobile folder
- **application.scss** which organizes and pulls together all the partials under the desktop folder

**mobile.scss** is called through the mobile version of **application.html.haml** – served only when Mobvious detects that the device is a mobile device.

**application.scss** is served in all other cases.

**(2)** Partials common to both **mobile.scss** and **application.scss**.

**(3)** All mobile related views are organized under the "mobile" folder.

**(4)** When Mobvious detects that a request is coming from a mobile device, Rails will serve mobile views from the mobile folder. When those views are not available in the mobile folder, through template inheritance, Rails will look for the view with the same name in its regular default location.

EXAMPLE: In our file structure under the views/mobile/shared folder, _footer.html.haml is the only file with a display difference between the mobile and desktop versions of our site, therefore it is the only file we need to add the mobile shared folder. We can use the same logo, navigation, and social links files found in the views/shared folder between both versions of our site.

So what does this mean? It means that our second set of Susy-based mobile responsive web design has a clear home to live in, and will be served only when our user agent detection scheme has determined that a device is mobile.

### Susy-based Mobile RWD

In our previous implementation of Susy breakpoints we defined the following:

    application.scss

    // Susy Grid

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break6:            6;
    $break9:            9;
    $break12:           12;

To start our mobile implementation we will focus on only the first two break points as follows:

    mobile.scss

    // Susy Grid

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break6:            6;

How will this work?

It all starts with the question, "is the requests coming from a mobile device?"

If true mobile.scss will be served. mobile.scss is coded to optimally handle devices with column widths of < 6 columns (464px).

If false application.scss will be served. application.scss is designed to take advantage of the greater capabilities of devices with > 9 columns (704px) screen widths.

If a false false squeaks by, application.scss is coded to handle the < 6 columns cases as well – although > 9 columns assets and elements might be received by the smaller device and therefore the experience is not optimized.

And there lies the crux of using a hybrid approach, optimizing for smaller screen sizes.

An Ajax Include Pattern
-----------------------

[An Ajax-Include Pattern for Modular Content][Ajax-Include]

Using JavaScript
----------------

Feature Detection


[The Essentials of Zepto.js][Zepto]


What We've Done
---------------

We began this chapter by briefly describing the state of mobile today and yesterday, how important it is, and in light of this, adopted the [Mobile First][] design and development strategy. We then laid out our plan of attack, the different means by which we might develop a mobile foundation to build from.

Our plan of attack divided this chapter into three major sections for each prospective method:

I. User Agent Sniffing<br>
II. Responsive Web Design<br>
III. A Hybrid Approach

We covered each method in detail and incorporated our work into our foundation code base, but with so many different approaches begs the question, which one do I use? Well, that depends. It depends on the project and needs.

What is important is that you now have options for a mobile foundation that can handle a variety of needs, depending on which one you choose to employ.

The goal of Section I of this book has been to set up a foundation for any application we build. The three major pillars of this validation are: our [foundation markup][Chapter 1], [foundation styles][Chapter 2], and with this chapter of our mobile foundation.

We have a solid base to build on, and are ready to move onto Section II of this book beginning with Chapter 4, "[Information Architecting][Chapter 4]".


[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[Better and Worse]:     http://insights.wired.com/profiles/blogs/mobile-browsing-will-get-both-better-and-worse#axzz2IFWc81o0
[common knowledge]:     http://www.themobileplaybook.com/en-us/#/introduction
[Mobile First]:         http://www.abookapart.com/products/mobile-first
[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[LaunchWare]:           http://launchware.com/
[Jason Grigsby]:        http://www.uie.com/brainsparks/2012/10/12/jason-grigsby-mobile-first-responsive-design/
[Responsive Reasons]:   http://www.mixd.co.uk/blog/technical/reasons-for-responsive-design/
[Fools Gold]:           http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile
[Mobile Roundup]:       https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-4.md#mobile-solutions-roundup
[mobylette]:            https://github.com/tscolari/mobylette
[jQuery Mobile]:        http://jquerymobile.com/
[base-mobile]:          https://github.com/maxxiimo/base-mobile
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[User Agent Switcher]:  http://chrispederick.com/work/user-agent-switcher/
[Mobvious]:             https://github.com/jistr/mobvious
[Ryan Bates]:           http://railscasts.com/episodes/199-mobile-devices
[Maintain Sanity]:      http://erniemiller.org/2011/01/05/mobile-devices-and-rails-maintaining-your-sanity/
[RWD]:                  http://www.alistapart.com/articles/responsive-web-design/
[RWD Book]:             http://www.abookapart.com/products/responsive-web-design
[Responsive Design]:    http://alpha.responsivedesign.is/
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html
[Grid Systems]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-3.md#grid-systems
[Susy]:                 http://susy.oddbird.net/
[Chapter 5]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/visual-design-for-the-nondesigner.md
[source]:               http://susy.oddbird.net/guides/getting-started/
[basic settings]:       http://susy.oddbird.net/guides/reference/#ref-basic-settings
[.container]:           http://susy.oddbird.net/guides/reference/#ref-basic-mixins
[Susy Grids]:           http://net.tutsplus.com/tutorials/html-css-techniques/responsive-grids-with-susy/
[Off-canvas]:           http://oddbird.net/2012/11/27/susy-off-canvas/
[media types]:          http://www.w3.org/TR/CSS21/media.html
[Media Queries]:        http://www.w3.org/TR/css3-mediaqueries/#media0
[Stats]:                http://gs.statcounter.com/
[Tired of Hunting]:     http://www.websitedimensions.com/
[2012 Device Map]:      http://viljamis.com/blog/2012/responsive-workflow/device-map-2012.pdf
[Device Diagram]:       http://www.metaltoad.com/blog/simple-device-diagram-responsive-design-planning
[Defining Breakpoints]: http://alpha.responsivedesign.is/strategy/page-layout/defining-breakpoints
[breakpoints]:          http://alpha.responsivedesign.is/develop/media-queries/media-queries-for-common-device-breakpoints
[Happy Cog]:            http://www.netmagazine.com/news/browser-screen-resolution-stats-rile-devs-121897
[px media querries]:    https://github.com/maxxiimo/base-css/blob/master/_media_queries_px.sass
[Media queries]:        http://alpha.responsivedesign.is/develop/media-queries
[Sass Media Queries]:   http://thesassway.com/intermediate/responsive-web-design-in-sass-using-media-queries-in-sass-32
[Retina Media Queries]: http://css-tricks.com/snippets/css/retina-display-media-query/
[EMs have it]:                     http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/
[Embrace the em]:     http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/
[converted breakpoints]: https://github.com/maxxiimo/base-css/blob/master/_media_queries.sass
[Muppets]:                     https://groups.google.com/d/topic/compass-users/oXHAtZE4euI/discussion
[Ajax-Include]:         http://filamentgroup.com/lab/ajax_includes_modular_content/
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/

[@media Definitions]:   http://chrismaxwell.com/manifesto/media-queries.gif
[file-structure]:       http://chrismaxwell.com/manifesto/file-structure.gif
[file-structure-w-lines]: http://chrismaxwell.com/manifesto/file-structure-w-lines.gif
