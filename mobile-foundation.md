Mobile Foundation
-----------------

In Chapter 1 we learned about [foundation markup][], and in Chapter 2, [foundation styles][], but what about mobile? What about iPads? What about mobile browsers!! In the old days all you really had to worry about "cross anything" were browser issues. On the fringe back then there was talk about desktop screen sizes, but it could be overlooked since the differences were not so great, and the "fix" came relatively quickly (and became second nature) as monitors became less expensive and the industry settled on standard design widths and/or employed liquid layouts.

Nowadays you cannot overlook screen size. Devices will continue to drop in price which means a greater set of divergent screen sizes in people's hands, and the fix is a tad bit more difficult to say the least. With out a doubt your end-users are going to look at your work on a smart phone or some kind of tablet. In fact I think this is pretty much [common knowledge][], so let's end that discussion and just deal with it proactively by laying down a mobile foundation.

In this chapter we are going to explore the different ways in which we can serve content to our end-users tailored to the device they're using, and in this process we will develop our applications own mobile foundation.

### Mobile First

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing desktop application and turned it into a mobile app (pre-smartphone era). The result was a precise definition of the applications basic information architecture, no more no less. Several of my colleagues pointed this out and used the mobile application to better architect the greater desktop application.

As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense to me for information architecting alone, and given the large and increasing number of mobile users out there, it is an approach that you as a front end developer should consider using when building an application. In the very least, DO NOT leave mobile design as an afterthought.

In [Chapter 4][] we will tackle this paradigm shift head-on as we architect our application. As a general rule mobile is now a factor, so it makes sense to include preparing for it in our foundation work blueprint.

### Plan of Attack

With Ruby on Rails there are three ways we can tackle mobile browsers:

1.  Detecting user agents to serve mobile specific markup and styles.

2.  Detecting screen sizes via media queries to serve up responsive styles (that also can hide markup via display: none).

3.  A hybrid of 1 and 2.

I'm undecided about which method I prefer insofar as 1 and 2 go. My gut tells me to separate concerns, but I like responsive styles and lots of minds are working towards improving them. Here are some thoughts on the matter:

- Keep them separate and you can serve lighter, device specific stylesheets. This translates to less complexity and better performance.
- As applications grow and user needs change, it might become necessary to separate mobile out completely. If you start out separate this transition might be easier.
- Keep styles together, and no one will be left out, i.e. you won't forget to work on one while working on the other, that is if you're the forgetful sort.
- Designing for a mobile device, a tablet device, and a desktop could be time-consuming, response styles can accommodate all three.
- With responsive design, change the code once and it trickles down to all devices.

Right now "responsive" based on media queries is hugely popular and developers are circling the wagons around the preferred method for dealing with mobile browsers. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" does a great job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. There is one quote there that the author uses that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.
\- [Brian Fling][]

Whatever you decide, keep in mind that there are a spectrum of needs users and businesses may have, and responsive may in fact be the silver bullet for some sites on that spectrum. For example my personal website most certainly won't need mobile specific geolocation capabilities, and the changes required between screens are minor. In this case why not use media queries and keep things together?

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer… under-the-hood it would have been all wrong.
\[Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore the three plans of attack.

### User Agent Sniffing

Back at Fidelity mobile was a complete separate concern from desktops, it had to be. I worked there slightly before smart phones emerged, and back then smallscreen devices/carriers behind what was referred to as a "walled garden" oftentimes did not allow CSS, or JavaScript, or HTML tables, or some other kind of limitation. Back then there were so many different types of devices, rules, screen sizes, and none of them were smart. To complicate matters at Fidelity it was our objective to cover 99.999% [possibly exaggerated by me] of all small screen devices out there. Why? Imagine a billionaire customer from Bahrain trying to look at his or her Fidelity portfolio on some obscure cell phone and nothing showing up! [Rationale also made up by me, but not the underlying object. Consistent coverage.]

To accomplish ubiquity we developed a super dumbed down HTML 1.0 interface that would work on 90% of all small screen devices, remember pre-smart phone, and for the remaining devices serve up alternative markup that would display content correctly and consistent with the company's brand/look and feel. How do we know when to serve up the correct markup? By analyzing the devices HTTP_ACCEPT header and HTTP_USER_AGENT header. Over time with all the customers that Fidelity had, the company developed an extensive database of devices their customers used which included the device's screen size, operating system, carrier, and other pertinent information. Armed with this information they could tailor out markup depending on the request and information it contained: user agent sniffing.

Fast-forward to today, with the advent of smart devices and their proliferation we need to think like Fidelity thought back then: our applications work correctly for the majority of all situations they face. One huge difference between then and now is the mobile browser and its ubiquity across different devices. Consequently, as front end developers we can concentrate on real estate more so than on walled gardens and cross device issues. Like my days at Fidelity, we can effectively use the devices user agent to determine what markup and styles to serve.

#### Mobile Solutions Roundup

To get started, if you're not sure where to begin or as a review, take a look at this round up of mobile solutions:

1.  Ryan Bates screencast "[Mobile Devices][]".

2.  The tutorial "[How to Build a Mobile Rails 3.1 App][How to Build]" demonstrates how to use the [mobylette][] and [jquery_mobile_rails][] gems. The mobylette gem handles requests and allows your controller to respond with a :mobile format, while the jquery-mobile-rails gem adds [jQuery Mobile][] files to your asset pipeline: which helps make everything look great and work like a native mobile app.

3.  Much like mobylette, [mobile-fu][] detects mobile requests and allows your application to respond with a :mobile format. Here's a brief how to:

    [Mobilize Your Rails Application with Mobile Fu][Mobilize Rails]

4.  There is a rack-based detection solution called [mobvious][]:

    > Mobvious detects whether your app / website is being accessed by a phone, or by a tablet, or by a personal computer. You can then use this information throughout your app. (E.g. fork your front-end code with regard to device type. There is a [plugin][mobvious-rails] for Ruby on Rails that helps you with this.)

5.  The [mobvious-rails][] gem allows you to:

    > Access detected device type easily from controllers and views.<br>
    > Execute code for given device types only. Both in controllers and views.<br>
    > Do the above stuff also in your CoffeeScript.

6.  [Agent_orange][agent_orange] looks interesting. Although stable, it has its issues per the maintainers readme.

7.  > [UserAgent][] is a Ruby library that parses and compares HTTP User Agents.

9.  [Browser][] is a gem that allows you to test for the browser being used including mobile browsers, and includes ActionController integration.

10. In the tutorial "[Mobile Devices and Rails: Maintaining your Sanity][Maintain Sanity]" the author proposes placing mobile templates in a separate directory, then when requests come in from a mobile subdomain, like m.domain.com, these templates are served. If the templates are not available, the requester is served regular view templates; bring you up from having to create two templates for every action. Users can switch between the two templates, and user agent detection is employed.

11. If you're looking to beef up your detection capabilities, [Handset Detection][] is a service you can try (includes free and paid plans).

12. Here is a list of "[Mobile Browser ID (User-Agent) Strings][Mobile Strings]" you could incorporate into your project if you wanted to get granular.

### Responsive Web Design

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][Responsive]". 

[This Is Responsive][]

Yada yada yada, coming soon... ;)

[foundation markup]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
[foundation styles]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[common knowledge]:     http://www.themobileplaybook.com/en-us/#/cover
[Mobile First]:         http://www.abookapart.com/products/mobile-first
[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[Media Queries]:        http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
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
[Mobile Strings]:       http://www.zytrax.com/tech/web/mobile_ids.html

[Responsive]:           http://www.alistapart.com/articles/responsive-web-design/
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html

