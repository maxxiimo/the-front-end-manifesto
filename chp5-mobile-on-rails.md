Mobile on Rails
===============

In Chapter 1 we learned about [foundation markup][Chapter 1], and in Chapter 3, [foundation styles][Chapter 3], but we never addressed mobile. What about smartphones and tablets? What about mobile browsers!! In the old days it never really was an issue for most developers. All you really had to worry about "cross anything" were browser issues. Desktop screen sizes were debated then, but it could be overlooked since the differences were not so great or prevalent, and the "fix" came relatively quickly: the industry settled on standard design widths and/or employed liquid layouts.

Fast-forward to today and as a front end engineer you cannot help but think about screen size, and the fix is a bit more difficult than it was back then to say the least!

> Mobile browsing is rapidly consuming the Internet. The smartphone and tablet lifestyle is replacing laptops and desktop computers as the primary way we go online.

\- [Mobile Browsing: It Will Get Better and Worse][Better and Worse] by Chris Kelly of New Relic

The fact of the matter is, your end-users are going to consume your work on smartphones or some kind of tablet. I think this is pretty much [common knowledge][] now, so let's deal with it proactively by laying down a mobile foundation. In this chapter we are going to explore the different ways in which we can serve content tailored to the different devices our users are using, and in this process develop our own mobile foundation's best practices.

Mobile First
------------

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit in Boston, we took an existing desktop application and turned it into a mobile app (pre-smartphone era). The result was a precise definition of the applications basic information architecture, no more no less. Several of my colleagues pointed this out to me, and used the mobile application to better architect the greater desktop application.

Luke Wroblewski in his 2009 article "[Mobile First][LukeW]" echoes this exact same sentiment:

> Mobile devices require software development teams to focus on only the most important data and actions in an application. There simply isn't room in a 320 by 480 pixel screen for extraneous, unnecessary elements. You have to prioritize.

As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense to me for information architecting alone, but given the large and increasing number of mobile users out there, it is an approach that you as a front end developer should consider adopting when building any application. In the very least, DO NOT leave mobile design as an afterthought.

Throughout the rest of this book I will take the Mobile First approach.

> Provide for the mobile experience as a forethought.

\- [Manifesto][]

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




What We've Done
---------------

We began this chapter by briefly describing the state of mobile today and yesterday, how important it is, and in light of this, adopted the [Mobile First][] design and development strategy. We then laid out our plan of attack, the different means by which we might develop a mobile foundation for our application.

Our plan of attack divided this chapter into three major sections for each prospective method:

I. User Agent Sniffing<br>
II. Responsive Web Design<br>
III. A Hybrid Approach

We covered each method in detail and incorporated our work into our foundation code base, but with so many different approaches begs the question, which one do I use? Well, that depends. It depends on the project and it's needs. What is important is that you now have options for a mobile foundation that can handle a variety of needs, depending on which one you choose to employ.

We ended the chapter with a quick overview of JavaScript and mobile: media query polyfills, conditional loading, and ending with a very brief reference to Zepto, a minimalist JavaScript library.

"Mobile on Rails" is the last chapter of "Section I - Setting up a Foundation". The three pillars of this foundation are our [foundation markup][Chapter 1], [foundation styles][Chapter 3], and with this chapter our mobile foundation.

We now have a solid base to build on, and are ready to move onto Section II of this book beginning with Chapter 8, "[Information Architecting][Chapter 8]".

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/the-manifesto.md
[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp2-markup-review.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md
[Chapter 8]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp8-information-architecting.md
[Appendix 2]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-2
[Appendix 3]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-3

[Better and Worse]:     http://insights.wired.com/profiles/blogs/mobile-browsing-will-get-both-better-and-worse#axzz2IFWc81o0
[common knowledge]:     http://www.themobileplaybook.com/en-us/#/introduction

[LukeW]:                http://www.lukew.com/ff/entry.asp?933
[Mobile First]:         http://www.abookapart.com/products/mobile-first

[LaunchWare]:           http://launchware.com/
[Jason Grigsby]:        http://www.uie.com/brainsparks/2012/10/12/jason-grigsby-mobile-first-responsive-design/
[Responsive Reasons]:   http://www.mixd.co.uk/blog/technical/reasons-for-responsive-design/
[Fools Gold]:           http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile

[User-Agent]:           http://tools.ietf.org/html/rfc2616#section-14.43

[mobylette]:            https://github.com/tscolari/mobylette
[jQuery Mobile]:        http://jquerymobile.com/
[base-mobile]:          https://github.com/maxxiimo/base-mobile
[Get Compass to Work]:  http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[User Agent Switcher]:  http://chrispederick.com/work/user-agent-switcher/

[Mobvious]:             https://github.com/jistr/mobvious
[Ryan Bates]:           http://railscasts.com/episodes/199-mobile-devices
[template inheritance]: http://railscasts.com/episodes/269-template-inheritance

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

[@media Definitions]:   http://chrismaxwell.com/manifesto/media-queries.gif
[file-structure]:       http://chrismaxwell.com/manifesto/file-structure.gif
[file-structure-w-lines]: http://chrismaxwell.com/manifesto/file-structure-w-lines.gif
