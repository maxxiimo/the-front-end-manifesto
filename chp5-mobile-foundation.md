Mobile Foundation
=================

In Chapter 1 we set up our [foundation markup][Chapter 1], and in Chapter 3 our [foundation styles][Chapter 3], but we never addressed mobile in our foundation code. What about smartphones and tablets? What about mobile browsers!! In the old days mobile was never really a concern for most developers. All you really had to worry about "cross anything" were browser issues. Desktop screen sizes were debated then, but they could be overlooked; the differences were not so great or prevalent, and the "fix" came relatively quickly as the industry settled on standard design widths and/or employed liquid layouts.

Fast-forward to today and as a Front End Engineer you cannot help but think about screen size, and the fix is a bit more difficult than it was back then to say the least!

> Mobile browsing is rapidly consuming the Internet. The smartphone and tablet lifestyle is replacing laptops and desktop computers as the primary way we go online.

\- [Mobile Browsing: It Will Get Better and Worse][Better and Worse] by Chris Kelly of New Relic

The fact of the matter is end-users are going to consume your work on smartphones or some kind of tablet. I think this is pretty much [common knowledge][] now, so let's deal with it proactively by laying down a mobile foundation. In this chapter we are going to explore the different ways in which we can serve content tailored to the different devices our users are using, and in this process develop our own mobile foundation's best practices. Practices that we will explore in:

- [Chapter 6 - Responsive Web Design][Chapter 6]
- [Chapter 7 - Device Detection][Chapter 7]

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

I think I would enjoy writing a book called "Mobile on Rails" after exploring the avenues he presents, but for this section (of this book) let's narrow down our plan of attack to the following:

1. Detect screen size via media queries to serve up responsive web design.

2. Detect user agents to serve mobile versions of our website.

3. A hybrid of 1 and 2.

### Best Choice

Personally I tend to use option three. I like to separate concerns, but include responsive design within this separation since there is no one size fits all in mobile. I'm not alone in this thinking:

> Now, oftentimes, people think about device detection as a "one or the other" sort of thing. Either you’re doing responsive design or you’re using device detection to route people to separate templates, and that you would choose one of those two options; you wouldn’t build something that uses both. But we’ve actually combined responsive design with server-side detection quite a bit.

\- [Jason Grigsby – Mobile-First Responsive Design][Jason Grigsby] Podcast by Sean Carmichael

Like Jason Grigsby, I don't think an all or nothing approach really makes sense as a rule of thumb. Let the situation dictate the solution.

### Holy Wars

Tabs or spaces? CamelCase, underscores or hyphens? Vim or Emacs? And the list goes on in programming. In my mobile research it seems a new holy war is brewing around responsive web design and here are the two camps:

- [Reasons for Responsive Design][Responsive Reasons] - Some good reasons why you should consider using it.
- [CSS MediaQuery for Mobile is Fool’s Gold][Fools Gold] - Illustrates why media queries might not be the silver bullet for serving up mobile styles and content.

My personal number one argument against using solely Responsive Web Design:

- Keep them separate and you can serve lighter, device specific stylesheets, JavaScript and images. This translates to less complexity and better performance.

My personal number one reason to conclude Responsive Web Design:

- You may mis-categorize or entirely miss mobile devices using user agent strings and device databases.

Jiří Stránský, the author of the Mobvious gem commented to me:

> I think responsive web design is going to be preferred over server-based solutions for the vast majority of use cases in the future, for two main reasons:
>
> 1. Boundaries within device types will blend. It used to be PCs and phones, now it's tablets, TVs, e-book readers and more. It's hard to detect them server-side and for some of them, even if you know what device it is, you're still not sure what category they should belong to :) Hence the term "phablets" :)
>
> 2. Bandwidth is less of an issue, year by year. It will be best to send the whole thing to the client, then detect client's precise capabilities and render what you want, how you want.

Whatever approach you decide, keep in mind that there are a spectrum of user and business needs. Responsive may in fact be the silver bullet for some sites on that spectrum, and for others not. For example my personal website is pretty simple so maybe detecting user agents to serve a mobile version of the site is not the best use of my time. In this case why not use Responsive Web Design and keep things together? But more complex applications may need to serve up specific markup and styles, take for example Basecamp mobile:

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer... under-the-hood it would have been all wrong.

\- [Behind the speed: Basecamp mobile][Basecamp Mobile]

Between [Chapter 6][] and [Chapter 7][] we will explore all three plans of attack. Before we move on, I will leave you with one quote that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.

\- [Mobile Design and Development ][Brian Fling] by Brian Fling


[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/the-manifesto.md
[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md
[Chapter 6]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp6-responsive-web-design.md
[Chapter 7]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-device-detection.md

[Better and Worse]:     http://insights.wired.com/profiles/blogs/mobile-browsing-will-get-both-better-and-worse#axzz2IFWc81o0
[common knowledge]:     http://www.themobileplaybook.com/en-us/#/introduction

[LukeW]:                http://www.lukew.com/ff/entry.asp?933
[Mobile First]:         http://www.abookapart.com/products/mobile-first

[LaunchWare]:           http://launchware.com/
[Jason Grigsby]:        http://www.uie.com/brainsparks/2012/10/12/jason-grigsby-mobile-first-responsive-design/
[Responsive Reasons]:   http://www.mixd.co.uk/blog/technical/reasons-for-responsive-design/
[Fools Gold]:           http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
