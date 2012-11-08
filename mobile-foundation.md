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
\[Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore the three plans of attack.

### 1. Responsive Web Design

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][Responsive]".

[This Is Responsive][]

Yada yada yada, coming soon... ;)

### 2. User Agent Sniffing

Back at Fidelity pre-smart phone, mobile was a complete separate concern from desktops. I worked there slightly before smart phones emerged, and back then smallscreen devices operated behind what was referred to as a carriers "walled garden" which oftentimes did not allow CSS, or JavaScript, or HTML tables, or all three. Back then there were so many different types of devices, rules, screen sizes, and mobile browsers (or none at all).

To complicate matters at Fidelity it was our objective to cover 99.999% [possibly exaggerated by me] of all small screen devices out there. Why? Imagine a billionaire customer from Bahrain trying to look at his or her Fidelity portfolio on some obscure cell phone and nothing showing up! [Rationale also made up by me, but not the underlying object. Consistent coverage.]

To accomplish ubiquity we developed a super dumbed down HTML 1.0 interface that would work on 90% of all small screen devices, remember pre-smart phone, and for the remaining devices served up alternative markup that would display content correctly and consistent with the company's brand and look and feel. We were able to successfully do this by analyzing the devices HTTP_ACCEPT header and HTTP_USER_AGENT header, i.e. user agent sniffing. Over time with all the customers that Fidelity had, the company developed an extensive database of devices their customers used which included the device's screen size, operating system, carrier, and other pertinent information. Armed with this information Fidelity could tailor out markup depending on the request and information it contained.

Fast-forward to today, with the advent of smart devices and their proliferation, we also need to make sure our applications work correctly and consistently across a multitude of different devices and screen sizes. Like my days at Fidelity, we can effectively use devices user agents to identify browsers, screen resolutions, type of device, and based on this determine what markup and styles to serve.

#### Mobile Solutions Roundup

To get started, if you're not sure where to begin or as a review, take a look at this round up of mobile solutions:

1.  Ryan Bates screencast "[Mobile Devices][]".

2.  The tutorial "[How to Build a Mobile Rails 3.1 App][How to Build]" demonstrates how to use the [mobylette][] and [jquery_mobile_rails][] gems. The mobylette gem handles requests and allows your controller to respond with a :mobile format, while the jquery-mobile-rails gem adds [jQuery Mobile][] files to your asset pipeline: which helps make everything look great and work like a native mobile app.

3.  Much like mobylette, [mobile-fu][] detects mobile requests and allows your application to respond with a :mobile format. Here's a brief how to:

    [Mobilize Your Rails Application with Mobile Fu][Mobilize Rails]

4.  There is a rack-based detection solution called [mobvious][]:

    > Mobvious detects whether your app / website is being accessed by a phone, or by a tablet, or by a personal computer. You can then use this information throughout your app. (E.g. fork your front-end code with regard to device type. There is a [plugin][mobvious-rails] for Ruby on Rails that helps you with this.)

    The [mobvious-rails][] gem allows you to:

    > Access detected device type easily from controllers and views.<br>
    > Execute code for given device types only. Both in controllers and views.<br>
    > Do the above stuff also in your CoffeeScript.

5.  [Agent_orange][agent_orange] looks interesting. Although stable, it has its issues per the maintainers readme.

6.  [UserAgent][] is a Ruby library that parses and compares HTTP User Agents.

7.  [Browser][] is a gem that allows you to test for the browser being used including mobile browsers, and includes ActionController integration.

8.  In the tutorial "[Mobile Devices and Rails: Maintaining your Sanity][Maintain Sanity]" the author proposes placing mobile templates in a separate directory, then when requests come in from a mobile subdomain, like m.domain.com, these templates are served. If the templates are not available, the requester is served regular view templates; freeing you up from having to create two templates for every action. Users can switch between the two templates, and user agent detection is employed.

9.  If you're looking to beef up your detection capabilities, the following services are available (includes free and paid plans).
    - [Handset Detection][]
    - [Akamai][]
    - [DeviceAtlas][]
    - [scientiamobile][]

10. You can also tap into the [WURFL][] database.

11. Here is a list of "[Mobile Browser ID (User-Agent) Strings][Mobile Strings]" you could incorporate into your project if you wanted to get granular.

#### Our Solution

We're going to use...

### 3. A Hybrid Approach



### Mobile on Rails

When I asked [LaunchWare][] founder Dan Pickett what he thought was the best approach for mobile, his answer was so succinct and backed with experience that I'm just going to quote it in its entirety here:

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
[Responsive]:           http://www.alistapart.com/articles/responsive-web-design/
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile
[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices
[mobylette]:            https://github.com/tscolari/mobylette
[jquery_mobile_rails]:  https://github.com/tscolari/jquery-mobile-rails
[How to Build]:         https://dev.tscolari.me/2011/09/15/how-to-build-a-mobile-rails-3-dot-1-app/
[mobile-fu]:            https://github.com/brendanlim/mobile-fu
[Mobilize Rails]:       http://www.intridea.com/blog/2008/7/21/mobilize-your-rails-application-with-mobile-fu#
[jQuery Mobile]:        http://jquerymobile.com/demos/1.2.0/
[mobvious]:             https://github.com/jistr/mobvious
[mobvious-rails]:       https://github.com/jistr/mobvious-rails
[agent_orange]:         https://github.com/kevinelliott/agent_orange
[UserAgent]:            https://github.com/josh/useragent
[Browser]:              https://github.com/fnando/browser
[Maintain Sanity]:      http://erniemiller.org/2011/01/05/mobile-devices-and-rails-maintaining-your-sanity/
[Handset Detection]:    http://code.google.com/p/mobile-device-detection-ruby-on-rails/
[Akamai]:               http://www.akamai.com/html/solutions/mobile_detection_redirect.html
[DeviceAtlas]:          https://deviceatlas.com/
[scientiamobile]:       http://www.scientiamobile.com/
[WURFL]:                http://wurfl.sourceforge.net/
[Mobile Strings]:       http://www.zytrax.com/tech/web/mobile_ids.html
[Ajax-Include]:         http://filamentgroup.com/lab/ajax_includes_modular_content/
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/
