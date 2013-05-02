Device Detection
================

At Fidelity Investments, where I worked in 2007 - helping develop their then new mobile offering, we faced many challenges developing for the mobile landscape that existed back then:

1.  Bandwidth, latency, and CPU issues were significantly worse than what we experience today.
2.  Screen sizes were much more varied, and smaller than today.
3.  Carrier "walled gardens" oftentimes did not allow CSS, or JavaScript, or HTML tables, or any combination of the three.
4.  Proxy servers might strip your site of images, flash (hugely popular back then), multimedia, or enforce throughput limitations.
5.  Only a basic set of media types were available and they were implemented inconsistently across browsers.
6.  Compatibility testing was extremely difficult due to the highly fragmented device market.
7.  The browser market was also highly fragmented.
8.  Browsers were relatively unsophisticated and OS or device bound
9.  Browsers rendered and/or supported languages inconsistently.
10. There were competing protocols (WAP vs. HTTP) and markup languages (Wireless Markup Language - WML, XHTML Mobile Profile / XHTML Basic, HTML) which meant parsing issues and greater complexity.

Under these challenges, our goal was to cover 99.999% of all web-enabled mobile phones that our customers used. To accomplish this we developed a super dumbed down HTML 1.0 template that would render correctly on 90% of customer devices, and for the remaining edge cases serve an alternative template. We were able to do this by analyzing device HTTP_ACCEPT and HTTP_USER_AGENT headers, i.e. user agent sniffing.

> The User-Agent request-header field contains information about the user agent originating the request. This is for statistical purposes, the tracing of protocol violations, and automated recognition of user agents for the sake of tailoring responses to avoid particular user agent limitations.

\- [Hypertext Transfer Protocol -- HTTP/1.1, Section 14.43 User-Agent][User-Agent]

Over time Fidelity developed an extensive database of devices their customers used which included information about the devices screen size, OS, browser, protocol support, and more. Armed with this information Fidelity could then serve markup depending on the device request and the information it contained.

Fast-forward to today and you can still effectively use device user agents and third-party databases to serve device appropriate markup and styles to your users. In fact in Rails this is not difficult. Take a look at the [Mobile Solutions Roundup][Appendix 3] in the Appendices to get an idea of what you can do in Rails.

Mobvious
--------

For our device detection implementation we will use a gem called [Mobvious][]. It is a rack-based solution, easy to set up, and highly configurable. It is also versatile in how you can detect mobile requests:

1.  User-Agent sniffing
2.  URL pattern matching
3.  Remembering a user's manual choice

In other words it gives us more options.

Before you begin to set up Mobvious clone this books [base-mobile][] files:

    git clone git@github.com:maxxiimo/base-mobile.git

### Set Up

**Step 1:** Copy all the [base-mobile][] files from the default folder and place them into their corresponding directories, i.e. *stylesheets/mobile* files go in *stylesheets/mobile* in your application. You should be able to cleanly merge the files in one sweep into your project. When you are finished, the following files will have been added to your repository:

![][new-files]

**Step 2:** Add the following to your application.rb file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

\- [Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work]

**Step 3:** Add the following gems to your *Gemfile* and then bundle install:

    gem 'mobvious'
    gem 'mobvious-rails'

**Step 4:** Add the following to *application.rb*:

    # Tell your app to use Mobvious::Manager as Rack middleware.
    config.middleware.use Mobvious::Manager

**Step 5:** Add the following includes:

    application_controller.rb:
    include Mobvious::Rails::Controller

    application_helper.rb:
    include Mobvious::Rails::Helper

**Step 6:** Create an initializer file *config/initializers/mobvious.rb* and configure it as follows:

    Mobvious.configure do |config|
      config.strategies = [ Mobvious::Strategies::MobileESP.new(:mobile_desktop) ]
    end

Don't forget to restart your application, and wallah! You have a detection strategy that will return a variable of *:mobile* or *:desktop* depending on the device type of the request. What you do with that information is entirely up to you. In the next section we will start you off on the right foot.

NOTE: Tablet devices as configured here will return :desktop as well, although you can change this.

To test that Mobvious is working you can add the following helper method in *application_helper.rb*:

    def device_test
      # Drop in pages_controller#home: @device = request.env['mobvious.device_type']
      # Drop in pages/home.html.haml: = device_test
      no_device = "What!? That's nil bro."
      if @device.nil?
        no_device
      else
        "#{@device}"
      end
    end

NOTE: For an even simpler solution checkout [Mobylette][Appendix 4] in the Appendices.

### Mime Types

Now that we have Mobvious set up, here is how we will use it.

To begin we will add a bit of [Ryan Bates mobile solution][Ryan Bates] to our Mobvious implementation. Part of his solution creates a new mime type, *:mobile*, and uses a *before_filter* to test if an incoming request is mobile. If true, the *before_filter* sets the mime type to *:mobile* and only files named with the *.mobile.haml* extension are served.

To do this in our application in conjunction with Mobvious, we add the following *before_filter* and private method *prepare_for_mobile* to *application_controller.rb*:

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

We then register the *:mobile* mime type in *config/initializers/mime_types.rb*:

    Mime::Type.register_alias "text/html", :mobile

Don't forget to restart your server, and with that, requests from mobile devices detected by Mobvious will be served *.html.mobile views*. Only one is included in our base mobile files, but I'm beginning to get concerned that as we move along development, we will find that we have way too many files in our *app/views* folder – some ending with *.html.haml* others with *.mobile.haml*.

NOTE: If you use Firefox try [User Agent Switcher][] to test on your desktop.

### Reorganization

To better organize and reduce clutter in our views, let's store our mobile views in a separate folder than our regular views.

**Step 1**: Create a new *app/views/mobile* folder and move all mobile views there.

**Step 2**: We tell Rails that our mobile views are now located in this directory by adding the following *prepend_view_path* to our *prepare_for_mobile* method:

    *application_controller.rb*:

    def prepare_for_mobile
      if request.env['mobvious.device_type'] == :mobile
        request.format = :mobile
        prepend_view_path "app/views/mobile"
      end
    end

Now, in addition to our mime type, we have designated a specific view path as the location to find our mobile views, but with  this new folder structure in place there really no longer is a need for a mobile mime type.

More importantly, with a common mime type we can now use the same views for both desktop and mobile devices through Rails [template inheritance][] – your application will default to regular views when mobile views are not available. This is especially useful when making an existing app mobile friendly; a little bit at a time.

**Step 3**: To complete the mobile views reorganization, delete the mime type we defined from the previous section (it can be found in *mime_types.rb*), and remove the *request.format = :mobile* line from the *prepare_for_mobile method*.

**Step 4**: Finally, don't forget to rename your mobile views extensions from *mobile.haml* back to *.html.haml*.

Restart your server and you're done!

NOTE: If you prefer to organize your mobile views outside of the regular *app/views* path, for example in *app/views_mobile*, swap the *prepend_view_path* with:

    prepend_view_path Rails.root + 'app' + 'views_mobile'

A Hybrid Approach
-----------------

User agent sniffing might not be the silver bullet we seek to deliver different device optimized versions of a website. Things are happening in mobile so fast that it might be difficult to keep up with the speed of change with user agent sniffing and device databases, plus some devices might not register as *:mobile* and slip through the cracks and receive the desktop version of the website.

> That’s not to say that mobile websites are inherently flawed, or that there aren’t valid business cases for creating them. But I do think fragmenting our content across different "device-optimized" experiences is a losing proposition, or at least an unsustainable one. As the past few years have shown us, we simply can’t compete with the pace of technology.

\- Ethan Marcotte, [Responsive Web Design][RWD Book], p.96

On the other hand, a purely responsive web design may deliver too much bloat for smaller devices with lower connection speeds, higher latency, and smaller CPUs. The idea of context sensitivity also comes into play. Perhaps your user needs are different on mobile than they are on a desktop because of the context in which they are viewing and using your application. On top of that, smaller devices require a lot more tweaks between device capabilities (from dumb phones to smart phones), and require developers to contend with a greater amount of screen size increments.

All of these factors might be good reason to keep code organized separately, not just in a separate stylesheet, or in hidden and conditionally loaded elements, but as a separate system entirely. A hybrid approach can meet these challenges.

### How It Works

If we take a hybrid approach, we might do so by providing responsive web design for larger screens and tablets, and a separate responsive web design for small screen devices that register as mobile via our user agent detection scheme. The smaller devices then would not receive any of the bloat that may be associated with the desktop and tablet versions of our website. We could also use the information available in user agent strings for even greater levels of adaptation and tweaking.

For small screen devices that slip through the cracks, our desktop version of the site then would provide a more general small screen responsive design backup for those devices.

Will this be too much work? That remains to be discovered, I personally don't think so, but if you choose to use a hybrid approach here is how we would do it:

1. Leave the Mobvious solution in place.

2. Leave the Susy-based responsive web design implementation from [Chapter 7][] as is.

3. Create a second Susy-based Responsive Web Design specifically for small devices.

### File Structure

To create a second Susy-based responsive web design specifically for small devices we are literally going to take all of the techniques we learned in [Chapter 7][], and repeat them for mobile. First let's understand where this second RWD implementation will belong by reviewing our current file structure:

![][file-structure]

With a few arrows let me explain:

![][file-structure-w-lines]

**(1)** There are two main stylesheets:

- **mobile.scss** which organizes and pulls together all the partials under the *mobile* folder.
- **application.scss** which organizes and pulls together all the partials under the *desktop* folder.

**mobile.scss** is called through the mobile version of **application.html.haml** (*mobile/layouts/application.html.haml*) and served only when Mobvious detects that the device is a mobile device.

**application.scss** is served in all other cases.

**(2)** Partials common to both **mobile.scss** and **application.scss**.

**(3)** All mobile related views are organized under the *mobile* folder. Desktop views are organized under the default Rails file structure.

**(4)** When Mobvious detects that a request is coming from a mobile device, Rails will serve mobile views from the *mobile* folder. When those views are not available in the *mobile* folder, through template inheritance, Rails will look for the view with the same name in the regular default location. For example, the *_logo.html.haml* partial is common to both website versions, so there is no reason repeat it.

This means that we can create a second implementation of RWD under the *mobile.scss* stylesheet branch. Doing so will not affect our first implementation.

### Susy-based Mobile RWD

Now that we have reviewed where everything belongs, let's set up the mobile version of our website.

First, import Susy into app/assets/stylesheets/mobile.scss:

    /* BASIC STRUCTURE
      ============================================================================ */
    @import "susy";
    @import "mobile/layout";

In our previous implementation of Susy breakpoints we defined the following in application.scss:

    // Susy Grid

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break6:            6;
    $break9:            9;
    $break12:           12;

To start our mobile implementation we will do the same in mobile.scss, but focus only on the first two breakpoints as follows:

    // Susy Grid

    $total-columns:     4;
    $column-width:      4em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

    $break6:            6;

Finally, create the outer grid-containing element in app/views/mobile/layouts/application.html.haml:

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

...and add the corresponding CSS to app/assets/stylesheets/mobile/_layout.sass:

    .container
      +container

That's it! How will this work?

It all starts with the question, "is the request coming from a mobile device?"

If true, mobile.scss along with of the mobile version of application.html.haml will be served.

NOTE: mobile.scss is coded to optimally handle devices with column widths of < 6 columns (464px), and application.html.haml is coded with mobile in mind only. Compare the _head.html.haml files for both and you will see that they are significantly different from one another. One draws from regular [HTML5 Boilerplate][] and the other from [Mobile Boilerplate][].

If false, application.scss along with of the mobile version of application.html.haml will be served.

NOTE: application.scss is designed to take advantage of the greater capabilities of devices with > 9 columns (704px) screen widths.

If a false positive squeaks by, application.scss is coded to handle the < 6 columns cases as well (although > 9 columns assets and elements might be received by the smaller device and therefore the experience is not optimized).

I personally really like this approach. To see how I have organized this in a live application, feel free to clone or poke around https://github.com/maxxiimo/viewthought.

Using JavaScript
----------------

### Media Query Polyfills

Media queries are a cornerstone of responsive web design, however, as a front end developer you need to be aware that many older versions of browsers do not support media queries. To overcome these deficiencies in older browsers there are a couple JavaScript-based solutions that will bridge this gap:

- [css3-mediaqueries-js][]

  > ...a JavaScript library to make IE 5+, Firefox 1+ and Safari 2 transparently parse, test and apply CSS3 Media Queries. Firefox 3.5+, Opera 7+, Safari 3+ and Chrome already offer native support.

- [Respond.js][]

  > A fast & lightweight polyfill for min/max-width CSS3 Media Queries (for IE 6-8, and more)

- [Mediatizr][]

  > This library adds media queries support to browsers that don't support it (like Internet Explorer 5.5-8).

The key for these JavaScript-based fixes is that JavaScript must be available or enabled, but unfortunately this is not always the case. Fortunately for our end-users, we approached development from a mobile first perspective. If media queries or JavaScript are not available, breakpoints will not take affect, and our users will be served our four column layout, which is not a bad fallback since the site will still look great and be readable: Another perk of the mobile first approach!

> Employ progressive enhancements and graceful degradation.

\- [Manifesto][]

### Conditional Loading

The idea behind conditional loading is to use JavaScript to test if there is enough screen real estate to display certain pieces of content, say for example a sidebar or a large image. If there is enough room then load the content, if not, don't.

A great idea, but beyond the scope of this chapter and the section it belongs to: Setting up a Foundation. To help you explore this idea though, here is a list of articles iin publication order that will more than set you on the right path:

- *12/18/10* [Speed Up Your Site with Delayed Content][24 Ways Speed]
- *02/12/11* [Conditional Loading for Responsive Designs][24 Ways Loading]
- *12/02/11* [Clean conditional loading][Clean Loading]
- *12/02/11* [Conditional Loading for Responsive Designs][Conditional Loading]
- *03/28/12* [An Ajax-Include Pattern for Modular Content][Ajax-Include Pattern]
- *04/24/12* [Conditionally loading content][Conditional Content]
- *09/04/12* [Enquire.js – Media Query Callbacks in JavaScript][Callbacks]

JavaScript Libraries:

- [enquire.js][]

  > enquire.js is a lightweight, pure javascript library (with no dependencies) for programmatically responding to media queries.

- [Adapt.js - Adaptive CSS ][Adapt.js]

  > Adapt.js is a lightweight (848 bytes minified) JavaScript file that determines which CSS file to load before the browser renders a page. If the browser tilts or resizes, Adapt.js simply checks its width, and serves only the CSS that is needed, when it is needed.

### Zepto

One of the major issues with mobile browsing is CPU and bandwidth limitations. Zepto is a JavaScript library developed for speed, or it could be said to reduce the type of bloat found in libraries such as jQuery:

> Zepto is a minimalist JavaScript library for modern browsers with a largely jQuery-compatible API. If you use jQuery, you already know how to use Zepto.

\- [Github Zepto][]

To learn more visit:

- [Zepto.js][]
- [The Essentials of Zepto.js][Zepto]

[Chapter 7]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-susy.md
[Appendix 3]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-3
[Appendix 4]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-4
[base-mobile]:          https://github.com/maxxiimo/base-mobile

[User-Agent]:           http://tools.ietf.org/html/rfc2616#section-14.43

[Mobvious]:             https://github.com/jistr/mobvious
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[Ryan Bates]:           http://railscasts.com/episodes/199-mobile-devices
[User Agent Switcher]:  http://chrispederick.com/work/user-agent-switcher/
[template inheritance]: http://railscasts.com/episodes/269-template-inheritance

[RWD Book]:             http://www.abookapart.com/products/responsive-web-design
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[Mobile Boilerplate]:   http://html5boilerplate.com/html5boilerplate.com/dist/mobile/

[css3-mediaqueries-js]: http://code.google.com/p/css3-mediaqueries-js/
[Respond.js]:           https://github.com/scottjehl/Respond
[Mediatizr]:            https://github.com/pyrsmk/mediatizr

[24 Ways Speed]:        http://24ways.org/2010/speed-up-your-site-with-delayed-content/
[24 Ways Loading]:      http://24ways.org/2011/conditional-loading-for-responsive-designs/
[Clean Loading]:        http://adactio.com/journal/5042/
[Conditional Loading]:  http://adactio.com/articles/5043/
[Ajax-Include Pattern]: http://filamentgroup.com/lab/ajax_includes_modular_content/
[Conditional Content]:  http://adactio.com/journal/5414/
[Callbacks]:            http://css-tricks.com/enquire-js-media-query-callbacks-in-javascript/
[enquire.js]:           http://wicky.nillia.ms/enquire.js/
[Adapt.js]:             http://adapt.960.gs/

[Github Zepto]:         https://github.com/madrobby/zepto
[Zepto.js]:             http://zeptojs.com/
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/

[new-files]:            http://chrismaxwell.com/manifesto/chp-8/new-files.gif
[file-structure]:       http://chrismaxwell.com/manifesto/chp-8/file-structure.gif
[file-structure-w-lines]: http://chrismaxwell.com/manifesto/chp-8/file-structure-w-lines.gif
