Mobile on Rails
===============

In Chapter 1 we learned about [foundation markup][], and in Chapter 2, [foundation styles][], but what about mobile? What about smartphones and tablets? What about mobile browsers!! In the old days all you really had to worry about "cross anything" were browser issues. There was talk about desktop screen sizes, but it could be overlooked since the differences were not so great or prevalent, and the "fix" came relatively quickly: the industry settled on standard design widths and/or employed liquid layouts.

Fast-forward to today and as a front end engineer you cannot overlook screen size, and the fix is a tad bit more difficult than it was back then to say the least.

> Mobile browsing is rapidly consuming the Internet. The smartphone and tablet lifestyle is replacing laptops and desktop computers as the primary way we go online.

\- [Mobile Browsing: It Will Get Better and Worse][Better and Worse] by Chris Kelly of New Relic

With out a doubt your end-users are going to look at your work on a smartphone or some kind of tablet. In fact I think this is pretty much [common knowledge][] now, so let's end that discussion and just deal with it proactively by laying down a mobile foundation.

In this chapter we are going to explore the different ways in which we can serve content tailored to the different devices our users are using, and in this process we will develop our own mobile foundation, or best practices.

Mobile First
------------

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing desktop application and turned it into a mobile app (pre-smartphone era). The result was a precise definition of the applications basic information architecture, no more no less. Several of my colleagues pointed this out and used the mobile application to better architect the greater desktop application.

As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense to me for information architecting alone, and given the large and increasing number of mobile users out there, it is an approach that you as a front end developer should consider using when building an application. In the very least, DO NOT leave mobile design as an afterthought.

In [Chapter 4][] we will tackle this paradigm shift head-on as we architect our application. As a general rule,, mobile is now a factor, so it makes sense to include preparing for it at the get-go of the project.

Plan of Attack
--------------

At the end of this chapter Dan Pickett the founder of [LaunchWare][] describes several different methods to tackle mobile on Ruby on Rails, but for this chapter we will need to choose one approach to build our mobile foundation. Perhaps in the next book "Mobile on Rails" we can dive in even further. For now, here are three possibilities we will explore:

1.  Detecting screen sizes via media queries to serve up responsive styles.

2.  Detecting user agents to serve mobile specific markup and styles.

3.  A hybrid of 1 and 2.

Personally I like to separate concerns but include responsive design within this separation since there is no one size fits all in mobile, so I tend to use option three. I'm not alone in this thinking:

> Now, oftentimes, people think about device detection as a "one or the other" sort of thing. Either you’re doing responsive design or you’re using device detection to route people to separate templates, and that you would choose one of those two options; you wouldn’t build something that uses both. But we’ve actually combined responsive design with server-side detection quite a bit.

\- [Jason Grigsby – Mobile-First Responsive Design][Jason Grigsby]

I don't think an all or nothing approach really makes sense as a rule of thumb. Let the situation dictate the solution. Here are some thoughts on option 1 versus option 2:

- Keep them separate and you can serve lighter, device specific stylesheet, JavaScript and images. This translates to less complexity and better performance.
- As applications grow and user needs change, it might become necessary to separate mobile out completely. If you start out separate this transition might be easier.
- Keep styles together, and you won't forget to work on one while working on the other.
- Designing for a mobile device, a tablet device, and a desktop could be time-consuming, responsive design can accommodate all three.
- With responsive design, change the code once and it trickles down to all devices.

Right now responsive web design is hugely popular. The article [Reasons for Responsive Design][Responsive Reasons] give you some good reasons why you should consider using it. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" gives an opposite perspective and does a good job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. There is one quote in particular that the author uses that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.

\- [Brian Fling][]

On the other hand, Jiří Stránský -- the author of the Mobvious gem we implement later in this chapter -- commented to me:

> I think responsive web design is going to be preferred over server-based solutions for the vast majority of use cases in the future, for two main reasons:
>
> 1. Boundaries within device types will blend. It used to be PCs and phones, now it's tablets, TVs, e-book readers and more. It's hard to detect them server-side and for some of them, even if you know what device it is, you're still not sure what category they should belong to :) Hence the term "phablets" :)
>
> 2. Bandwidth is less of an issue, year by year. It will be best to send the whole thing to the client, then detect client's precise capabilities and render what you want, how you want.

This prediction certainly makes an awful lot of sense.

Whatever approach you decide, keep in mind that there are a spectrum of user and business needs, and responsive may in fact be the silver bullet for some sites on that spectrum. For example my personal website is pretty simple so maybe detecting user agents to serve something specific to mobile browsers is not the best use of my time. In this case why not use Responsive Web Design and keep things together? On the other hand more complex applications may need to serve up specific markup and styles, take for example Basecamp mobile:

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer... under-the-hood it would have been all wrong.

\- [Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore the three plans of attack.

I. User Agent Sniffing
----------------------

When I worked at Fidelity Investments, pre-smart phone era, mobile was a complete separate concern from desktops. Smallscreen devices operated behind what was referred to as a carriers "walled garden" which oftentimes did not allow CSS, or JavaScript, or HTML tables, or all three. Then, like now, there were so many different types of devices, carrier rules, screen sizes, and mobile browsers (or none at all), and Fidelity wanted to cover 99.999% [possibly exaggerated by me] of all small screen devices out there. Why? Imagine a billionaire customer from Bahrain trying to look at his or her Fidelity portfolio on some obscure cell phone and nothing showing up! [Rationale also made up by me, but not the underlying object. Consistent coverage.]

To accomplish ubiquity we developed a super dumbed down HTML 1.0 interface that would work on 90% of all small screen devices, remember pre-smart phone, and for the remaining devices served up alternative markup that would display content correctly and consistent with the company's brand and look and feel. We were able to successfully do this by analyzing the devices HTTP_ACCEPT header and HTTP_USER_AGENT header, i.e. user agent sniffing. Over time with all the customers that Fidelity had, the company developed an extensive database of devices that their customers used which included the device's screen size, operating system, carrier, and other pertinent information. Armed with this information Fidelity could serve tailored markup depending on the request and information it contained.

Fast-forward to today, with the advent of smart devices and their proliferation, we also need to make sure our applications work correctly and consistently across a multitude of different devices and screen sizes. Like my days at Fidelity, we can effectively use devices user agents to identify browsers, screen resolutions, type of device, and based on this information determine what markup and styles to serve.

### Quickest Solution

There are a number of different solutions you can use to deliver mobile based on User Agent Sniffing. Take a look at the [Mobile Solutions Roundup][Mobile Roundup] in the Appendix to get an idea of what's out there. To deliver our mobile views we will use the quickest and simplest solution: Tiago Scolari's [mobylette][] gem with [jQuery Mobile][] for our user interface. Here are the steps you will follow to implement this solution:

*Step 1:* Copy all the [base-mobile][] files from the simple solution folder and place them into their corresponding directories, i.e. stylesheets/mobile files go in stylesheets/mobile in your application.

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

### Advanced Solution

For our advanced solution we we use a gem called [Mobvious][]. It is a rack-based solution and easy to set up, and is highly configurable and versatile in on how you detect mobile requests:

1.  User-Agent sniffing
2.  URL pattern matching
3.  Remembering a user's manual choice

#### Set Up

Here are the steps we will use to configure Mobvious for our needs:

*Step 1:* Copy all the [base-mobile][] files from the advanced solution folder and place them into their corresponding directories, i.e. stylesheets/mobile files go in stylesheets/mobile in your application.

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

Now in addition to our mime type, we have designated a specific view path as the location to house our mobile views. Go ahead and create the new app/views/mobile folder and move all mobile views there. I've already set up this folder structure [here][mobile views].

NOTE: One folder ends in [mobile] and the other in [html]. The difference between the two are in the files mime types: .mobile.haml vs. .html.haml.

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

Don't forget to restart your server, and wallah! You have a pretty powerful responsive grid system. To learn how to use it, the best reference can be found at the [source][]. The following tutorials also demonstrate Susy in action:

- [Responsive Grids With Susy][Susy Grids]
- [Off-canvas layout with Susy][Off-canvas]

#### Implementing Susy

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

app/assets/stylesheets/mobile/_layout.sass

    .container
      +container

app/assets/stylesheets/desktop/_layout.sass and

    body
      font-size: $base-font-size
      line-height: $base-line-height
      background-color: $bg-bo

    .container
      +container

NOTE: We removed...

      margin: 0 auto
      width: 960px

...from the desktop version body tag since we are now replacing these properties with Susy.






### @media

Now that we have a flexible grid, it's time to look at Ethan's second ingredient in RWD; media queries. To understand media queries let's take a little look at the history behind them.

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

So what dimensions should we use? Here are some references for this:

- [StatCounter Global Stats][Stats]
- [Tired of Hunting][]

After reviewing these references we will settle on: 320, 480, 768, 1024, and 1400px. Lets break this down to understand why. In the ResponsiveDesign.is website under [Defining Breakpoints][] the section begins...

> Breakpoints are the point a which your sites content will respond to provide the user with the best possible layout to consume the information.
>
> When you first begin to work with Responsive Design you will define your breakpoints at the exact device widths that you are looking to target. Most often these are the smart phone (usually the iPhone at 320px and 480px), the tablet (usually the iPad at 768px and 1024px) and finally anything above 1024px.
>
> WRONG!
>
> I hope I didn't hurt your feelings but seriously, you're approaching this in the wrong way.

Ha ha! Something to keep in mind. I like this thinking. We should start with content and see how it looks on different screen sizes, then define our breakpoints.

On the other hand I think it's good to start with something and redefine as content dictates. I like the examples the author gives:

- [media queries for common device breakpoints][breakpoints]

Why don't we grab a few and begin.

#### @media Rules

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

### Flexible Media

Now that we have a flexible grid and em-based media queries, it's time to look at Ethan's second ingredient in RWD; flexible media. Why flexible media? Imagine loading a 600 pixel wide image into a 320px wide screen. It just doesn't make any sense.





### Conditional Loading




III. A Hybrid Approach
----------------------

> That’s not to say that mobile websites are inherently flawed, or that there aren’t valid business cases for creating them. But I do think fragmenting our content across different "device-optimized" experiences is a losing proposition, or at least an unsustainable one. As the past few years have shown us, we simply can’t compete with the pace of technology.

- Ethan Marcotte, [Responsive Web Design][RWD Book], p.96



An Ajax Include Pattern
-----------------------

[An Ajax-Include Pattern for Modular Content][Ajax-Include]

Using JavaScript
----------------

Feature Detection


[The Essentials of Zepto.js][Zepto]


What We've Done
---------------

We've covered three approaches to mobile development in this chapter, and have incorporated these approaches into our foundation code base. So many different approaches begs the question, which one do I use? Well, that depends. It depends on the project and needs. When I asked [LaunchWare][] founder Dan Pickett what he thought was the best approach for mobile, his answer was so succinct (and backed with experience) that I'm just going to quote it in its entirety here:

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

[foundation markup]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
[foundation styles]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[Better and Worse]:     http://insights.wired.com/profiles/blogs/mobile-browsing-will-get-both-better-and-worse#axzz2IFWc81o0
[common knowledge]:     http://www.themobileplaybook.com/en-us/#/introduction
[Mobile First]:         http://www.abookapart.com/products/mobile-first
[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[LaunchWare]:           http://launchware.com/
[Jason Grigsby]:        http://www.uie.com/brainsparks/2012/10/12/jason-grigsby-mobile-first-responsive-design/
[Responsive Reasons]:   http://www.mixd.co.uk/blog/technical/reasons-for-responsive-design/
[Media Queries]:        http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
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
[mobile views]:         https://github.com/maxxiimo/base-mobile/tree/master/reorganization
[RWD]:                  http://www.alistapart.com/articles/responsive-web-design/
[RWD Book]:             http://www.abookapart.com/products/responsive-web-design
[Responsive Design]:    http://alpha.responsivedesign.is/
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html
[Grid Systems]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-3.md#grid-systems
[Susy]:                 http://susy.oddbird.net/
[Chapter 5]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/visual-design-for-the-nondesigner.md
[source]:               http://susy.oddbird.net/guides/getting-started/
[Susy Grids]:           http://net.tutsplus.com/tutorials/html-css-techniques/responsive-grids-with-susy/
[Off-canvas]:           http://oddbird.net/2012/11/27/susy-off-canvas/
[basic settings]:       http://susy.oddbird.net/guides/reference/#ref-basic-settings
[.container]:           http://susy.oddbird.net/guides/reference/#ref-basic-mixins
[media types]:          http://www.w3.org/TR/CSS21/media.html
[Media Queries]:        http://www.w3.org/TR/css3-mediaqueries/#media0
[Stats]:                http://gs.statcounter.com/
[Tired of Hunting]:     http://www.websitedimensions.com/
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
[Ajax-Include]:         http://filamentgroup.com/lab/ajax_includes_modular_content/
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/

[@media Definitions]:   http://chrismaxwell.com/manifesto/media-queries.gif
