Appendices
----------

1.  [Frameworks][Appendix 1]
    :: An overview of some popular frameworks: Twitter Bootstrap, Blueprint, YUI, Foundation 3, Skeleton.

2.  [Grid Systems][Appendix 2]
    :: A roundup of the different grid systems available: 320 and Up, Responsive Grid System, etc..

3.  [Mobile Screen Sizes][Appendix 3]
    :: A roundup of mobile screen size matrices/tables.

4.  [Mobile Solutions Roundup][Appendix 4]
    :: Different ways to detect mobile devices and deliver mobile versions of your application.

5.  [Mobylette and jQuery Mobile][Appendix 5]
    :: A quick and simple solution for delivering mobile views.



<br><hr /><br>
Appendix 1
----------

### Frameworks

In so far as responsive frameworks go, the following article gives you a nice comparison:

- [Responsive CSS Framework Comparison][Framework Comparison]

Here is a brief framework roundup worth taking a look at for your project.

#### Twitter Bootstrap

I like [Twitter Bootstrap][]. It's a great place to learn about best practices for any application or framework, and you can get some amazing designs in absolutely no time. It's well-documented, but here's the problem: it's built on [Less][], and use it and your site will look pretty much like everyone else's. Of course you can override styles, but I'm just sayin'.

> Sleek, intuitive, and powerful front-end framework for faster and easier web development.

Getting it to work with Rails is not impossible, hardly, but if you go this path there are some choices to consider:

- [Twitter Bootstrap, Less, and Sass: Understanding Your Options for Rails 3.1][Options]

#### Blueprint

[Blueprint][], in my opinion, is the granddaddy of all frameworks. I used to use Blueprint all of the time, and Compass makes it readily available. It's tried-and-true, and a good choice, but I rarely use it these days. I'm not too crazy about it's look and feel. It does seem to be more of a minimalist framework - which is not a bad thing.

> Blueprint is a CSS framework, which aims to cut down on your development time. It gives you a solid foundation to build your project on top of, with an easy-to-use grid, sensible typography, useful plugins, and even a stylesheet for printing.

#### YUI

 I've used YUI and personally I'm not too crazy about its grid system which is a pretty major component to any framework - so I generally stay away.

> YUI is a free, open source JavaScript and CSS library for building richly interactive web applications.
\- [YUI website][]

#### Foundation 3

I haven't used Foundation, but I'm interested.

> The most advanced responsive front-end framework in the world.
\- [Zurb website][]

#### Skeleton

I also haven't use Skeleton, but soon enough.

> A Beautiful Boilerplate for Responsive, Mobile-Friendly Development
\- [Skeleton website][]



<br><hr /><br>
Appendix 2
----------

### Grid Systems

You just can't believe how many grid system there are out there so here is a roundup for you to choose from (in alphabetical order):

1.  [320 and Up][]

    > ‘320 and Up’ is a lightweight, easy to use and content first responsive web design boilerplate.

2.  [34Grid][]

    > 34Grid is a Responsive Grid System based on "equally distributed columns" layout basis. In contrast to other great grid systems (@see bottom of page), 34Grid provides equally distributed columns for each row. (and also column complements for inequal distributions)

3.  [960 Grid System][]

    > The 960 Grid System is an effort to streamline web development workflow by providing commonly used dimensions, based on a width of 960 pixels. There are two variants: 12 and 16 columns, which can be used separately or in tandem.

4.  [Columnal][]

    > The Columnal CSS grid system is a “remix” of a couple others with some custom code thrown in. The elastic grid system is borrowed from cssgrid.net, while some code inspiration (and the idea for subcolumns) are taken from 960.gs.

5.  [Frameless][]

    > Dig responsive design? Hate fluid grids? Try a Frameless grid.

6.  [Golden Grid System ][]

    > A folding grid for responsive design.

7.  [Fluid Baseline Grid System][]

    > The FBG system was built with typographic standards in mind and combines principals of fluid-column layouts, baseline grids and mobile-first responsive design into a resolution independent and device agnostic framework.

8.  [Responsive GS][]

    > Fluid grid CSS framework for fast, intuitive development of responsive websites. Available in 12, 16 and 24 columns with media queries for all standard devices, clearfix, and optional reset.

9.  [Responsive Grid System][]

    > The Responsive Grid System isn't a framework. It's not a boilerplate either. It's a quick, easy & flexible way to create a responsive web site.

10. [rwdgrid][]

    > rwdgrid is just another Grid system based on popular 960grid , which is responsive and ranges from mobile, tablet, laptops and wide screen displays.

11. [SimpleGrid][]

    > Responsive. Infinite nesting. One class per element. Simple.

12. [1140 CSS Grid][]

    > The 1140 grid fits perfectly into a 1280 monitor. On smaller monitors it becomes fluid and adapts to the width of the browser.

13. [Gridiculous][]

    > Gridiculous was created after I tried out a bunch of different responsive grids and realized that none of them offered all of the features I required. First and foremost, I wanted to make sure that the grid would work from a large desktop monitor through to a tablet and all the way down to a mobile phone. That's why Gridiculous starts off at 1200px and works itself down to 320px.



<br><hr /><br>
Appendix 3
----------

### Mobile Screen Sizes

- [A Simple Device Diagram for Responsive Design Planning][Device Diagram]
- [2012 Device Map][]
- [dpilove][]
- [Mobile device screen width table][Width Table]
- [Mobile Matrices][]
- [Common Smartphone and Tablet values][mydevice.io]
- [screensiz.es][]
- [StatCounter Global Stats][Stats]
- [Tired of Hunting][]
- [Viewport Sizes][]



<br><hr /><br>
Appendix 4
----------

### Mobile Solutions Roundup

To get started, if you're not sure where to begin or as a review, take a look at this round up of mobile solutions:

1.  The tutorial "[How to Build a Mobile Rails 3.1 App][How to Build]" demonstrates -- although slightly dated from the gem -- how to use the authors [mobylette][] and [jquery_mobile_rails][] gems. Mobylette handles requests and allows your controller to respond with a :mobile format, while jquery-mobile-rails adds [jQuery Mobile][] files to your asset pipeline: which helps make everything look great and work like a native mobile app.

2.  Much like mobylette, [mobile-fu][] detects mobile requests and allows your application to respond with a :mobile format.

3.  There is a rack-based detection solution called [mobvious][]:

    > Mobvious detects whether your app / website is being accessed by a phone, or by a tablet, or by a personal computer. You can then use this information throughout your app. (E.g. fork your front-end code with regard to device type. There is a [plugin][mobvious-rails] for Ruby on Rails that helps you with this.)

    The [mobvious-rails][] gem allows you to:

    > Access detected device type easily from controllers and views.<br>
    > Execute code for given device types only. Both in controllers and views.<br>
    > Do the above stuff also in your CoffeeScript.

4.  Ryan Bates screencast "[Mobile Devices][]" will teach you how to roll your own user agent detector.

5.  In the tutorial "[Mobile Devices and Rails: Maintaining your Sanity][Maintain Sanity]" the author proposes placing mobile templates in a separate directory, then when requests come in from a mobile subdomain, like m.domain.com, these templates are served. If the templates are not available, the requester is served regular view templates; freeing you up from having to create two templates for every action. Users can switch between the two templates, and user agent detection is employed.

6.  If you're looking to beef up your detection capabilities, the following services are available (includes free and paid plans).
    - [Handset Detection][]
    - [Akamai][]
    - [DeviceAtlas][]
    - [scientiamobile][]

7.  You can also tap into the [WURFL][] database.

8.  Here is a list of "[Mobile Browser ID (User-Agent) Strings][Mobile Strings]" you could incorporate into your project if you wanted to get granular.



<br><hr /><br>
Appendix 5
----------

### Mobylette and jQuery Mobile

One of the quickest and simplest solutions to deliver mobile views is Tiago Scolari's [mobylette][] gem with [jQuery Mobile][jQuery Mobile Home] for our user interface. Here are the steps you will follow to implement this solution:

**Step 1:** Copy all the [base-mobile][] files from the default folder followed by the mobylette folder, and place them into their corresponding directories, i.e. *stylesheets/mobile* files go in *stylesheets/mobile* in your application.

**Step 2:** Add the following to your *application.rb* file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

\- [Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work]

**Step 3:** Add the following gem to your *Gemfile* and then bundle install:

    gem 'mobylette'

**Step 4:** Add the following to *application_controller.rb*:

    include Mobylette::RespondToMobileRequests
    mobylette_config do |config|
      config[:skip_xhr_requests] = false
    end

**Step 5:** Add the following to *config/environments/production.rb*:

    # Precompile additional assets (application.js, application.css, and all non-JS/CSS are already added)
    config.assets.precompile += %w( modernizr-2.7.1.min.js, jquery.mobile-1.2.0.css )

And that's it!

One thing that you may have noticed is that there certainly does seem to be a lot of repetition in our code, two files for almost everything. One of the key arguments for Responsive Web Design is the elimination of duplication.



[Appendix 1]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-1
[Appendix 2]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-2
[Appendix 3]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-3
[Appendix 4]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-4
[Appendix 5]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-5



[Framework Comparison]: http://responsive.vermilion.com/compare.php
[Twitter Bootstrap]:    http://twitter.github.com/bootstrap/
[Options]:              http://rubysource.com/twitter-bootstrap-less-and-sass-understanding-your-options-for-rails-3-1/
[Blueprint]:            http://www.blueprintcss.org/
[YUI website]:          http://yuilibrary.com/
[Zurb website]:         http://foundation.zurb.com/
[Skeleton website]:     http://www.getskeleton.com/



[320 and Up]:           http://stuffandnonsense.co.uk/projects/320andup/
[34Grid]:               http://34grid.com/
[960 Grid System]:      http://960.gs/
[Columnal]:             http://www.columnal.com/
[Frameless]:            http://framelessgrid.com/
[Golden Grid System ]:  http://goldengridsystem.com/
[Fluid Baseline Grid System]:http://fluidbaselinegrid.com/
[Responsive GS]:        http://responsive.gs/
[Responsive Grid System]:http://www.responsivegridsystem.com/
[rwdgrid]:              http://rwdgrid.com/
[SimpleGrid]:           http://simplegrid.info/
[1140 CSS Grid]:        http://cssgrid.net/
[Gridiculous]:          http://gridiculo.us/



[Device Diagram]:       http://www.metaltoad.com/blog/simple-device-diagram-responsive-design-planning
[2012 Device Map]:      http://viljamis.com/blog/2012/responsive-workflow/device-map-2012.pdf
[dpilove]:              http://dpi.lv/
[Width Table]:          http://iamachine.com/blog/mobile-device-screen-width-table
[Mobile Matrices]:      https://github.com/h5bp/mobile-boilerplate/wiki/Mobile-Matrices
[mydevice.io]:          http://mydevice.io/devices/
[screensiz.es]:         http://screensiz.es/phone
[Stats]:                http://gs.statcounter.com/
[Tired of Hunting]:     http://www.websitedimensions.com/
[Viewport Sizes]:       http://viewportsizes.com/



[mobylette]:            https://github.com/tscolari/mobylette
[jquery_mobile_rails]:  https://github.com/tscolari/jquery-mobile-rails
[How to Build]:         https://dev.tscolari.me/2011/09/15/how-to-build-a-mobile-rails-3-dot-1-app/
[mobile-fu]:            https://github.com/brendanlim/mobile-fu
[jQuery Mobile]:        http://jquerymobile.com/demos/1.2.0/
[mobvious]:             https://github.com/jistr/mobvious
[mobvious-rails]:       https://github.com/jistr/mobvious-rails
[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices
[Maintain Sanity]:      http://erniemiller.org/2011/01/05/mobile-devices-and-rails-maintaining-your-sanity/
[Handset Detection]:    http://code.google.com/p/mobile-device-detection-ruby-on-rails/
[Akamai]:               http://www.akamai.com/html/solutions/mobile_detection_redirect.html
[DeviceAtlas]:          https://deviceatlas.com/
[scientiamobile]:       http://www.scientiamobile.com/
[WURFL]:                http://wurfl.sourceforge.net/
[Mobile Strings]:       http://www.zytrax.com/tech/web/mobile_ids.html



[base-mobile]:          https://github.com/maxxiimo/base-mobile
[mobylette]:            https://github.com/tscolari/mobylette
[jQuery Mobile Home]:   http://jquerymobile.com/
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
