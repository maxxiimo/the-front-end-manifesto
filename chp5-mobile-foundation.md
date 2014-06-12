Mobile Foundation
=================

In Chapter 1 we set up our [foundation markup][Chapter 1], and in Chapter 3 our [foundation styles][Chapter 3], but we never addressed mobile in our foundation code. What about smartphones and tablets? What about mobile browsers!! In the old days mobile was never really a concern for most developers. All you really had to worry about "cross anything" were browser issues. Desktop screen sizes were debated back then, but they could be overlooked; the differences were not so great or prevalent, and the "fix" came relatively quickly as the industry settled on standard design widths and/or employed liquid layouts.

Fast-forward to today and you would be ill-advised to overlook mobile:

> Mobile browsing is rapidly consuming the Internet. The smartphone and tablet lifestyle is replacing laptops and desktop computers as the primary way we go online.

\- [Mobile Browsing: It Will Get Better and Worse][Better and Worse] by Chris Kelly of New Relic

The fact of the matter is your users are going to consume your website on smartphones or some kind of tablet. I think this is pretty much [common][] [knowledge][] now, so the question is what will your approach be for designing and developing for mobile?

In this chapter we are going to explore the different ways in which we can serve content tailored to the different devices our users are using, and in this process develop our own mobile foundation's best practices. Practices that we will explore in:

- [Chapter 6 - Responsive Web Design][Chapter 6]
- [Chapter 8 - Device Detection][Chapter 8]

Mobile First
------------

Years ago when I worked for Fidelity Investments' FEB Design unit in Boston, myself and a colleague were asked to convert an existing Fidelity desktop application to a mobile experience, pre-smartphone era. We began by re-architected the application for a smaller screen size experience; and the result was a precise definition of the applications basic information architecture, no more no less. Several of my colleagues pointed this out, and used the redesigned mobile application to better architect the larger desktop application.

Luke Wroblewski in his 2009 article "[Mobile First][LukeW]" writes:

> Mobile devices require software development teams to focus on only the most important data and actions in an application. There simply isn't room in a 320 by 480 pixel screen for extraneous, unnecessary elements. You have to prioritize.

The [Mobile First][] design paradigm makes sense to me for information architecting reasons alone, but given the large number of mobile users out there, it is an approach that you should really consider adopting when building any application, if you haven't done so already. In the very least, DO NOT leave mobile design as an afterthought.

![Silvrback blog image](https://silvrback.s3.amazonaws.com/uploads/3876b088-98e4-4158-9ea5-c2b82b04f20a/apple-icons-1_large.png)

Throughout the rest of this book I will take the Mobile First approach.

> Provide for the mobile experience as a forethought.

\- [Manifesto][]

Once architected though, how do you move forward with development?

Plan of Attack
--------------

When I asked [LaunchWare][] founder Dan Pickett what he thought was the best approach for developing for mobile his answer was so succinct (and backed with experience) that it deserves quoting in its entirety:

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

I think I would enjoy writing a book called "Mobile on Rails" after exploring the avenues he presents, but for this section (of this book) let's narrow down our plan of attack to the following:

1. Detect screen size via media queries to serve up responsive web design.

2. Detect user agents to serve mobile versions of our website.

3. A hybrid of 1 and 2.

### Best Choice

Personally I tend to use option three. I like to separate concerns, and include responsive design within this separation since there is no one size fits all in mobile:

> Now, oftentimes, people think about device detection as a "one or the other" sort of thing. Either you’re doing responsive design or you’re using device detection to route people to separate templates, and that you would choose one of those two options; you wouldn’t build something that uses both. But we’ve actually combined responsive design with server-side detection quite a bit.

\- [Jason Grigsby – Mobile-First Responsive Design][Jason Grigsby] Podcast by Sean Carmichael

An all or nothing approach really does not make sense as a rule of thumb. Let the situation dictate the solution.

### Holy Wars

Tabs or spaces? CamelCase, underscores or hyphens? Vim or Emacs? And the list goes on in programming. In my mobile research it seemed like a holy war was brewing around responsive web design and here are the two camps:

- [Reasons for Responsive Design][Responsive Reasons] - Some good reasons why you should consider using it.
- [CSS MediaQuery for Mobile is Fool’s Gold][Fools Gold] - Illustrates why media queries might not be the silver bullet for serving up mobile styles and content.

Personally, I like the idea of keeping mobile and desktop development separate. In my opinion doing so will translate into less complexity and better performance by serving lighter, device specific stylesheets, JavaScript and images.

On the other hand, by not using responsive web design you may mis-categorize or entirely miss mobile devices when relying solely on user agent strings and device databases.

Jiří Stránský, the author of the Mobvious gem commented to me:

> I think responsive web design is going to be preferred over server-based solutions for the vast majority of use cases in the future, for two main reasons:
>
> 1. Boundaries within device types will blend. It used to be PCs and phones, now it's tablets, TVs, e-book readers and more. It's hard to detect them server-side and for some of them, even if you know what device it is, you're still not sure what category they should belong to :) Hence the term "phablets" :)
>
> 2. Bandwidth is less of an issue, year by year. It will be best to send the whole thing to the client, then detect client's precise capabilities and render what you want, how you want.

Whatever approach you decide to take, keep in mind that there are a spectrum of user and business needs. Responsive may be the silver bullet for some sites on that spectrum, and for others not. For example my personal website is pretty simple so maybe detecting user agents to serve a mobile version of the site is not the best use of my time. In this case why not use Responsive Web Design and keep things together? More complex applications, however, may need to serve up specific markup and styles, take for example Basecamp mobile:

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer... under-the-hood it would have been all wrong.

\- [Behind the speed: Basecamp mobile][Basecamp Mobile]

Through [Chapter 6][] and [Chapter 8][] we will explore all three plans of attack, and depending on the situation, after finishing these chapters you will have a solution for whatever your projects needs are.

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.

\- [Mobile Design and Development ][Brian Fling] by Brian Fling

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md#foundation-markup
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md#foundation-styles
[Chapter 6]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp6-responsive-web-design.md#responsive-web-design
[Chapter 8]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp8-device-detection.md#device-detection

[Better and Worse]:     http://insights.wired.com/profiles/blogs/mobile-browsing-will-get-both-better-and-worse#axzz2IFWc81o0
[common]:               http://www.themobileplaybook.com/en-us/#/introduction
[knowledge]:            http://www.mobify.com/blog/13-stats-to-convince-your-boss-to-invest-in-mobile-in-2013/

[LukeW]:                http://www.lukew.com/ff/entry.asp?933
[Mobile First]:         http://www.abookapart.com/products/mobile-first

[LaunchWare]:           http://launchware.com/
[Jason Grigsby]:        http://www.uie.com/brainsparks/2012/10/12/jason-grigsby-mobile-first-responsive-design/
[Responsive Reasons]:   http://www.mixd.co.uk/blog/technical/reasons-for-responsive-design/
[Fools Gold]:           http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
