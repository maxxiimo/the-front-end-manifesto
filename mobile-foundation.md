Mobile Foundation
-----------------

In Chapter 1 we learned about [foundation markup][], and in Chapter 2, [foundation styles][], but what about mobile? What about iPads? What about mobile browsers!! In the old days all you really had to worry about "cross anything" were browser issues. On the fringe back then there was talk about desktop screen sizes, but it could be overlooked since the differences were not so great, and the "fix" came relatively quickly (and became second nature) as monitors became less expensive and the industry settled on standard design widths and/or employed liquid layouts.

Nowadays you cannot overlook screen size. Devices will continue to drop in price which means a greater set of divergent screen sizes in people's hands, and the fix is a tad bit more difficult to say the least. With out a doubt your end-users are going to look at your work on a smart phone or some kind of tablet. In fact I think this is pretty much [common knowledge][], so let's end that discussion and just deal with it proactively by laying down a mobile foundation.

In this chapter we are going to explore the different ways in which we can serve content to our end-users tailored to the device they're using, and in this process we will develop our applications own mobile foundation.

### Mobile First

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing desktop application and turned it into a mobile app (pre-smartphone era). The result was a precise definition of the applications basic information architecture, no more no less. Several of my colleagues pointed this out and used the mobile application to better architect the greater desktop application.

As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense to me for information architecting alone, and given the large and increasing number of mobile users out there, it is an approach that you as a front end developer should consider using when building an application. In the very least, DO NOT leave mobile design as an afterthought.

In [Chapter 4][] we will tackle this paradigm shift head-on as we architect our application. As a general rule mobile is now a factor, so it makes sense to include preparing for it in our foundation work.

### Plan of Attack

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

Right now responsive web design is hugely popular. The article [Reasons for Responsive Design][] give you some good reasons why you should consider using it. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" gives an opposite perspective and does a good job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. There is one quote in particular that the author uses that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.
\- [Brian Fling][]

Whatever approach you decide, keep in mind that there are a spectrum of user and business needs, and responsive may in fact be the silver bullet for some sites on that spectrum. For example my personal website is pretty simple so maybe detecting user agents to serve something specific to mobile browsers is not the best use of my time. In this case why not use media queries and keep things together? On the other hand more complex applications may need to serve up specific markup and styles, take for example Basecamp mobile:

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer... under-the-hood it would have been all wrong.
[Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore the three plans of attack.

### 1. User Agent Sniffing

Back at Fidelity pre-smart phone, mobile was a complete separate concern from desktops. I worked there slightly before smart phones emerged, and back then smallscreen devices operated behind what was referred to as a carriers "walled garden" which oftentimes did not allow CSS, or JavaScript, or HTML tables, or all three. Back then there were so many different types of devices, rules, screen sizes, and mobile browsers (or none at all).

To complicate matters at Fidelity it was our objective to cover 99.999% [possibly exaggerated by me] of all small screen devices out there. Why? Imagine a billionaire customer from Bahrain trying to look at his or her Fidelity portfolio on some obscure cell phone and nothing showing up! [Rationale also made up by me, but not the underlying object. Consistent coverage.]

To accomplish ubiquity we developed a super dumbed down HTML 1.0 interface that would work on 90% of all small screen devices, remember pre-smart phone, and for the remaining devices served up alternative markup that would display content correctly and consistent with the company's brand and look and feel. We were able to successfully do this by analyzing the devices HTTP_ACCEPT header and HTTP_USER_AGENT header, i.e. user agent sniffing. Over time with all the customers that Fidelity had, the company developed an extensive database of devices their customers used which included the device's screen size, operating system, carrier, and other pertinent information. Armed with this information Fidelity could tailor out markup depending on the request and information it contained.

Fast-forward to today, with the advent of smart devices and their proliferation, we also need to make sure our applications work correctly and consistently across a multitude of different devices and screen sizes. Like my days at Fidelity, we can effectively use devices user agents to identify browsers, screen resolutions, type of device, and based on this determine what markup and styles to serve.

#### Simplest Solution

There are a number of different solutions you can use to deliver a mobile solution based on User Agent Sniffing. Take a look at the [Mobile Solutions Roundup][Mobile Roundup] in the Appendix to get an idea of what's out there. To deliver our mobile views in what I consider the simplest way possible, we're going to use Tiago Scolari's [mobylette][] gem with [jQuery Mobile][] for our user interface. Here are the steps you will follow:

**Step 1:** Add the following gem to your Gemfile and then bundle install:

        gem 'mobylette'

**Step 2:** Add the following line to application_controller.rb:

    include Mobylette::RespondToMobileRequests
    mobylette_config do |config|
      config[:skip_xhr_requests] = false
    end

**Step 3:** Copy all the files located [here][base-mobile] and place them into their corresponding directories, i.e. stylesheets/mobile files go in stylesheets/mobile in your application.

**Step 4:** Add the following to your application.rb file:

    # Precompile *all* assets, except those that start with underscore per:
    # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
    config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

([Getting Compass to Work With Rails 3.1 (and 3.2)][Get Compass to Work])

**Step 5:** Add the following to your config/environments/production.rb:

    # Precompile additional assets (application.js, application.css, and all non-JS/CSS are already added)
    config.assets.precompile += %w( modernizr-2.6.2.min.js, jquery.mobile-1.2.0.css )

And that's it! I like to use [User Agent Switcher][] to test on my browser. Give it a try.

You're probably saying that there certainly does seem to be a lot of repetition in our code. So you know, if a .mobile.haml file is not available, Mobylette will default to a regular .html.haml file, but this kind of defeats the purpose of using it. I personally like splitting the two concerns, but this may not be the best approach for many projects. One of the key arguments for Responsive Web Design is the elimination of duplication.

#### Advanced Solution



### 2. Responsive Web Design

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][Responsive]".

[This Is Responsive][]

Yada yada yada, coming soon... ;)

#### Media Queries



#### Conditional Loading




### 3. A Hybrid Approach



### Mobile on Rails

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

### An Ajax Include Pattern

[An Ajax-Include Pattern for Modular Content][Ajax-Include]

### Using JavaScript

Feature Detection


[The Essentials of Zepto.js][Zepto]


[foundation markup]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
[foundation styles]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[common knowledge]:     http://www.themobileplaybook.com/en-us/#/cover
[Mobile First]:         http://www.abookapart.com/products/mobile-first
[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[LaunchWare]:           http://launchware.com/
[Jason Grigsby]:        http://www.uie.com/brainsparks/2012/10/12/jason-grigsby-mobile-first-responsive-design/
[Responsive Reasons]:   http://www.mixd.co.uk/blog/technical/reasons-for-responsive-design/
[Media Queries]:        http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile
[Responsive]:           http://www.alistapart.com/articles/responsive-web-design/
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html
[Mobile Roundup]:       https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix.md#mobile-solutions-roundup
[mobylette]:            https://github.com/tscolari/mobylette
[jQuery Mobile]:        http://jquerymobile.com/
[base-mobile]:          https://github.com/maxxiimo/base-mobile
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[User Agent Switcher]:  http://chrispederick.com/work/user-agent-switcher/
[Ajax-Include]:         http://filamentgroup.com/lab/ajax_includes_modular_content/
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/
