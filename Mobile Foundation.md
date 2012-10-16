Mobile Foundation
-----------------

Chapter 1 and 2 are great, really great in my opinion ;-), but what about mobile? What about iPads? What about mobile browsers!! In the old days all you really had to worry about "cross anything" were browser issues. I mean on the fringe back then there was talk about desktop screen sizes, but it could be overlooked. 

Nowadays you cannot overlook screen sizes. You better believe that people are going to look at your website on a mobile phone or some kind of tablet, especially an iPad. In fact I think this is pretty much [common knowledge][], so let's just deal with it. How? Let's explore in this chapter.

### Mobile First

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing application and turned it into a mobile app (pre-smartphones). The result was a precise definition of the applications basic information architecture, no more no less. As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense. I don't think anyone can afford to consider mobile design as an afterthought anymore.

Yes, we did layout are foundation markup and styles with the desktop in mind, and that is fine and as it should be, but as we move into the next chapter we actually start thinking about how to build an application, and we do so tackle it from the mobile first perspective.

By the end of this chapter we will have completed our foundation work underrated tackle any browser, device, or screen size.

### Plan of Attack

With Ruby on Rails there are three ways we can tackle mobile browsers:

1.  Detecting user agents to serve mobile specific markup and styles.

2.  Detecting screen sizes via media queries to serve up responsive styles (that also can hide markup via display: none).

3.  A hybrid of 1 and 2.

I'm undecided about which method I prefer insofar as 1 and 2 go. My gut tells me to separate concerns. Anyway, here are my thoughts on the subject:

- Keep them separate and you can serve lighter, device specific stylesheets. This translates to less complexity and better performance.
- As applications grow and user needs change, it might become necessary to separate mobile out completely. If you start out separate this transition might be easier.
- Keep styles together, and no one will be left out, i.e. you won't forget to work on one while working on the other, that is if you're the forgetful sort.
- Designing for a mobile device, a tablet device, and a desktop could be time-consuming, response styles can accommodate all three.
- With responsive design, change the code once and it trickles down to all devices.

Right now "responsive" based on media queries is the rage. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" does a great job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. There is one quote there that the author uses that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.
\- [Brian Fling][]

Whatever you decide, keep in mind that there are a spectrum of needs and responsive may in fact be the silver bullet for some sites on that spectrum. For example my personal website most certainly won't need mobile specific geolocation capabilities, and all on all, the changes required between screens is minor. In this case why not use media queries and keep things together?

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer… under-the-hood it would have been all wrong.
\[Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore both plans of attack.

### User Agent Sniffing

Back at Fidelity mobile was a complete separate concern from desktops, it had to be. I worked there slightly before smart phones emerged, and back then smallscreen devices oftentimes did not allow CSS, or existed behind a walled garden that did not allow JavaScript or HTML tables or some other kind of limitation. Back then there were so many different types of devices, rules, and screen sizes, and it was our objective to cover 99.999% [possibly exaggerated by me] of all small screen devices out there. Why? Imagine a billionaire customer from Bahrain trying to look at his or her Fidelity portfolio on some obscure cell phone and nothing showing up! [rationale also made up by me]

To accomplish ubiquity we developed a super dumbed down HTML 1.0 interface that would work on 90% of all small screen devices, remember pre-smart phone, and for the remaining devices serve up alternative markup that would display content correctly and consistent with the company's brand/look and feel.  How do we know when to serve up the correct markup? By analyzing the devices user agent (HTTP_ACCEPT header and HTTP_USER_AGENT header). Over time with all the customers that fidelity had, the company developed an exhaustive database of devices their customers used which included the device's screen size, operating system, and other pertinent information. With that information they could tailor out markup that would work on the majority of their clients smallscreen devices.

Fast-forward to today, with smart phones for the most part we now concentrate solely on screen size (and hooking into a device's native functionality as a non-native entity, but that's for another chapter). One huge difference between then and now is the mobile browser. With its maturity and ubiquity across these devices, as front end developers we can concentrate on real estate, and like my days at Fidelity, will use the user agent to determine what markup and styles to serve.

### Mobile Solutions Roundup

To get started, if you're not sure where to begin, take a look at this round up of mobile solutions:

1.  Ryan Bates screencast "[Mobile Devices][]".

2.  In the  tutorial "[How to Build a Mobile Rails 3.1 App][How to Build]" the author shows you how to use the [mobylette][] and [jquery_mobile_rails][] gems in your application. The mobylette gem handles requests and allows your controller to respond with a :mobile format, while the jquery-mobile-rails gem adds [jQuery Mobile][] files to your asset pipeline which helps make everything look great and work like a native mobile app.

3.  Much like mobylette, [mobile-fu][] detects mobile requests and allows you to respond with a :mobile format. Here's some more information on this gem:

    \- [Mobilize Your Rails Application with Mobile Fu][Mobilize Rails]

4.  There is a rack-based detection solution called [mobvious][]:

    > Mobvious detects whether your app / website is being accessed by a phone, or by a tablet, or by a personal computer. You can then use this information throughout your app. (E.g. fork your front-end code with regard to device type. There is a [plugin][mobvious-rails] for Ruby on Rails that helps you with this.)

5.  The [mobvious-rails][] gem allows you to "access detected device type easily from controllers and views."

6.  [Agent_orange][agent_orange] looks interesting. Although stable, it has its issues per the maintainers account.

7.  [UserAgent][] is a Ruby library that parses and compares HTTP User Agents.

9.  [Browser][] is a gem that allows you to test for the browser being used including mobile browsers, and includes ActionController integration.

10. In the tutorial "[Mobile Devices and Rails: Maintaining your Sanity][Maintain Sanity]" the author proposes placing mobile templates in a separate directory, then when requests come in from a mobile subdomain, like m.domain.com, these templates are served. If the templates are not available, the requester is served regular view templates; bring you up from having to create two templates for every action. Users can switch between the two templates, and user agent detection is employed.

11. If you're looking to beef up your detection capabilities, [Handset Detection][] is a service you can try (includes free and paid plans).

12. Here is a list of "[Mobile Browser ID (User-Agent) Strings][Mobile Strings]" you could incorporate into your project if you wanted to get granular.

### Responsive Web Design

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][Responsive]". 

[This Is Responsive][]



[common knowledge]:     http://www.themobileplaybook.com/en-us/#/cover
[Mobile First]:         http://www.abookapart.com/products/mobile-first
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

