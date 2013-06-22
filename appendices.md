Appendices
----------

1.  [Frameworks][Appendix 1]
    :: An overview of some popular frameworks: Twitter Bootstrap, Blueprint, YUI, Foundation 3, Skeleton.

2.  [Grid Systems][Appendix 2]
    :: A roundup of the different grid systems available: 320 and Up, Responsive Grid System, etc..

3.  [Mobile Solutions Roundup][Appendix 3]
    :: Different ways to detect mobile devices and deliver mobile versions of your application.

4.  [Mobylette and jQuery Mobile][Appendix 4]
    :: A quick and simple solution for delivering mobile views.

5.  [Inspirational Sites][Appendix 5]
    :: Resources to help inspire design and UI patterns for desktop, mobile and responsive websites.

6.  [Placeholder Services][Appendix 6]
    :: A roundup of Lorem Ipsum and image placeholder services.

7.  [Feedback Services and Device Testing][Appendix 7]
    :: A roundup of UX feedback services, and articles on device testing.

8.  [Font Stack Roundup][Appendix 8]
    :: Different font stack combinations, fallbacks, surveys and code.

9.  [Font Services and Tools][Appendix 9]
    :: A jackpot listing of font services and tools to help you deliver a great typographic experience.

10. [Choosing Typefaces][Appendix 10]
    :: Choosing typeface articles and grear advice from Jason Santa Maria on choosing typefaces.

11. [A Brief History of Web Font Sizes][Appendix 11]
    :: Different articles from my archives over the last 12 years regarding web font sizes.

12. [Color Tools, Wheels, Generators, Palettes and Collections][Appendix 12]
    :: A roundup of different color tools, color wheels, image to color palette generators, community color palettes, and color collections.



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
Appendix 4
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
    config.assets.precompile += %w( modernizr-2.6.2.min.js, jquery.mobile-1.2.0.css )

And that's it!

One thing that you may have noticed is that there certainly does seem to be a lot of repetition in our code, two files for almost everything. One of the key arguments for Responsive Web Design is the elimination of duplication.



<br><hr /><br>
Appendix 5
----------

### Inspirational Sites

In addition to reviewing competitor sites or similar services to help generate ideas, the following sites may also inspire or provide you with best practices/design patterns:

#### Desktop

1.  [Awwwards][]

    > Awwwards are the awards that recognize and promote the talent and effort of the best developers, designers and web agencies in the world.

2.  [Pattern Tap][]

    > ...It's a living classroom, where designers learn what is working well on the Web and why.

3.  [UI Patterns][]

    > User Interface Design patterns are recurring solutions that solve common design problems. Design patterns are standard reference points for the experienced user interface designer.

4.  [siteInspire][]

    > siteInspire is showcase and CSS gallery featuring the best web design today.

5.  [Codrops][]

    > Codrops is a web design and development blog that publishes articles and tutorials about the latest web trends, techniques and new possibilities.

    Here are a few Codrops examples:
    - [Stop, Look, Click: Attention-Grabbing Elements in Web Design][Codrops 1]
    - [Make a Statement with Type][Codrops 2]
    - [Creative Background Styles and Trends in Web Design][Codrops 3]
    - [Dashboard Design Elements for the Win][Codrops 4]

6.  [Favourite Website Awards (FWA)][FWA]

    >  FWA stands for Favourite Website Awards, an industry recognised internet award program and inspirational portal, established in May 2000.

#### Mobile

The following links deal specifically with mobile:

1.  [Inspired UI][]

    > Find your inspiration

2.  [Pattern Tap Mobile][]

3.  [AppSites][]

    > App Sites is a showcase of beautiful iPhone, iPad & Mac app websites.

4.  [Mobile Patterns][]

5.  [Mobile Awesomeness][]

    > Big-time awesome for the small screen.

6.  [Mobile Design Pattern Gallery][Mobile Gallery]

    > UI Patterns for iOS, Android and More

7.  [Media Queries][]

    > A collection of inspirational websites using media queries and responsive web design.

8.  [FWA Mobile][]

    > FWA is the most visited website award program in the history of the internet, with over 140 million site visits as of July 2011 (and multiple billion hits to our servers).

9.  [WAPReview Directory][WapReview]

    > Welcome to the WapReview Directory, a comprehensive catalog of the mobile web, featuring reviews and ratings of 2254 mobile web sites.

10. [Mobile in Higher Ed][Higher Ed]

    > The following is a non-exhaustive listing of higher ed mobile web sites. Hopefully it’s useful to you as you evaluate features and ideas for your own mobile site.

11. [WTF Mobile Web][WTF]

    > We need better reasons. Real examples. Proof that what we are all doing is not working anymore. That’s what this website is about. Examples convince. Seeing trends makes us smarter. The problem isn’t insurmountable if it’s known. So let’s get to know the problem.

#### Responsive

Because responsive will play a big part in your design the following two links may help you think through your navigation:

1. [70 Stunning Responsive Sites for Your Inspiration][70 Sites]

2. [Responsive Navigation Patterns][Responsive Nav]

3. [Complex Navigation Patterns for Responsive Design][Complex Navigation]



<br><hr /><br>
Appendix 6
----------

### Placeholder Services

Here are some Rails Gems for creating Lorem Ipsum placeholders:

- [The Ruby Toolbox - Lorem Ipsum][Toolbox 1]

There are a lot of Lorem Ipsum generator services out there (some of them are kind of funny):

1. [html-ipsum][]
2. [lipsum][]
3. [Fillerama][]
4. [Samuel L. Ipsum][]
5. [Hipster Ipsum][]
6. [Gangsta Lorem Ipsum][]
7. [Cupcake Ipsum][]
8. [Bacon Ipsum][]
9. [T'lipsum][]

Image placeholders in different sizes and styles are also plentiful. The second link will give you a pretty comprehensive list to choose from, followed by two that are not included in the list that I list separately for thoroughness:

1. [The Ruby Toolbox - Image Placeholders][Toolbox 2]
2. [List of Dummy Image Generators][Image Generators]
3. [Functional Placeholder Images][Cambelt]
4. [Holder.js][]



<br><hr /><br>
Appendix 7
----------

### Feedback Services and Device Testing

A roundup of feedback services and device testing articles.

#### Feedback Services

1.  [Verify][]

    > Verify is the fastest way to collect and analyze user feedback on screens or mockups.

2.  [Concept Feedback][]

    > Get Website Feedback and Increase Conversion Rates
    > Expert analysis, detailed recommendations and solutions you can implement today.

3.  [IntuitHQ][]

    > Get useful, actionable results, improve usability in no time, and create a site your users will love.

4.  [Loop11][]

    > Loop11 is a remote usability testing tool that enables you to test the user-experience of any website and identify navigational and usability issues. Get the hard facts about your website quickly and cost effectively!

5.  [Silverback][]

    > Guerrilla usability testing software for designers and developers

6.  [UserTesting.com][]

    > Usability Testing Has Never Been Easier
    > The fastest, cheapest way to find out why users leave your website.

7.  Steve Krug wrote a second book on usability testing, and gives a basic demo of it on YouTube:
    - [Rocket Surgery Made Easy by Steve Krug: Usability Demo][Rocket Surgery]

#### Device Testing

1.  *112/14/10* - [Smartphone Browser Landscape][DT1]

    > In this article, I’ll give you an overview of the mobile web market, as well as phone platforms and their browsers, so that you can decide which mobile devices to test on. Then, we’ll look at how to set up a mobile test bed.

2.  *01/04/12* - [Test on Real Mobile Devices without Breaking the Bank][DT2]

    > Mobile is the future of the web, so it’s time to start investing in some mobile devices. Testing on actual devices is now an absolutely essential part of web design.

3.  *02/07/12* - [Strategies for choosing test devices][DT3]

    > It’s been great to see a conversation developing around how to acquire test devices and how to do so on a budget. But once you have a budget in place, how should you spend it?

4.  *03/28/12* - [Testing for Dummies][DT4]

    > We thought we’d share some information on our testing process.

5.  *06/26/12* - [How to Build a Device Lab [Part 1]][DT5]

    > Recently, we were lucky enough to be given the opportunity to build a device lab for our department. Stephanie Rieger (@stephanierieger) covers the many reasons why organizations need to get their hands on real devices for testing.

6.  *09/11/12* - [Testing Websites in Game Console Browsers][DT6]

    > More than one in eight internet users in the UK, US, and France—and nearly one in four American teens—uses a game console to get online, according to studies from 2010 and 2011.

7.  *09/24/12* - [Establishing An Open Device Lab][DT7]

    > Managing a personal device lab can be quite hard with an ever expanding number of devices. It’s not only expensive, but also bad for our environment.

8.  *11/01/12* - [Building the Happy Cog Test Lab][DT8]

    > hen first planning our test lab, I surveyed my own collection of devices and then asked around our Austin office for people who had some older phones sitting at home in a closet or junk drawer.

9.  [LabUp!][DT9]

    > LabUp! is here to help people around the world in establishing nonprofit Open Device Labs which helps others access a large number of mobile devices for testing, leading to an ultimate improvement of the mobile web &amp; app experience both for developers and consumers.



<br><hr /><br>
Appendix 8
----------

Here you will find recommendations for:

1.  Font stacks that you can copy and use in your project.

2.  Web safe fonts, i.e. fonts that are most common on most versions of Windows, Mac, and Linux.

    You can copy these and feel confident using them as your overall default font stack, or as a fallback font stack for a more interesting typeface.

3.  Typefaces that go well together, say one font for your headers and another contrasting font for your body.

4.  Mobile fonts.

5.  Font classifications and definitions.

### Font Stack Roundup

1.  *06/26/08* - [Better CSS Font Stacks][Better Stacks]

    > One aspect of designing for the web that almost immediately offends designers is the lack of fonts that are considered safe to use.

2.  *08/15/08* - [Web fonts can be nice (honest)][Honest]

    > ...but it strikes me that we are still not using the few fonts we can play with to their full potential. So today Ladies and Gents, I present the case for these, somewhat under-used gems...

3.  *01/08/09* - [8 Definitive Web Font Stacks Article][Definitive]

    > The font stacks listed here are grouped together by the universal font that forms the base of that stack. A designer can therefore decide on a typographical look for their site, grab the appropriate font stack, and tweak it to suit their needs.

4.  *09/22/09* - [Guide to CSS Font Stacks: Techniques and Resources][Techniques]

    > CSS Font stacks are one of those things that elude a lot of designers. Many stick to the basic stacks Dreamweaver auto-recommends or go even more basic by just specifying a single web-safe font.

5.  *03/19/12* - [Complete Guide to Pre-Installed Fonts in Linux, Mac, and Windows][Complete Guide]

    > Web fonts are gaining in popularity now, but they can still be a bit of a challenge to use. Copyright issues often require the use of a third-party font service, which can be risky and expensive.The good news is that all major operating systems come with a variety of fonts that you can use to create your font stacks.

6.  *04/21/12* - [Font Stacks][]

7.  *06/18/12* - [The 10 Best Script and Handwritten Google Web Fonts][Google Scripts]

    > A good script is hard to find. I’m extremely picky when it comes to this particular area of typefaces and tend to hate most of what I see. With this post, you can skip the work of sorting through the crap and cut straight to the awesome scripts that are readable, attractive and perfect for your site.

8.  [TYPECHART][]

    > Browse web type, grab CSS. TYPECHART lets you flip through, preview and compare web typography while retrieving the CSS.

9.  [Revised Font Stack][]

    > Serious efforts are being made to get more typeface choices on the web to enhance web typography. Still, most of us prefer web-safe fonts like: Verdana, Georgia, Times New Roman and Arial. Though choices are limited, yet the number can be increased by exploring other pre-installed fonts.

#### Web Safe

1.  *2010?* - [16 Gorgeous Web Safe Fonts To Use With CSS][Gorgeous]

    > I have gathered together a nice resource list of stunning web safe fonts that you can use with CSS stylesheets.

2.  *12/12/10* - [Web Safe Fonts Cheat Sheet v.3][Cheat Sheet]

    > This is the third major overhaul of the Web Safe Fonts Cheat Sheet, which now includes examples of fonts suitable for the CSS @font-face property, along with revised CSS font stacks, font installation breakdowns by operating system, and some of the new Google Font API fonts.

3.  [Common fonts to all versions of Windows &amp; Mac equivalents][Common Fonts]

    > Here you can find the list with the standard set of fonts common to all versions of Windows and their Mac substitutes, referred sometimes as "browser safe fonts".

4.  [CSS Font Stack][]

    > A complete collection of web safe CSS font stacks

5.  [Combined font survey results][Font Survey]

    > Is that font Web safe? Code Style font survey results show the most common fonts on Windows, Mac and Linux computers to help you build a Web safe font stack.

6.  [CSS Web Safe Font Combinations][Web Safe]

    > The font-family property should hold several font names as a "fallback" system, to ensure maximum compatibility between browsers/operating systems. If the browser does not support the first font, it tries the next font.

#### Combinations

1.  *09/18/09* - [19 top fonts in 19 top combinations][19 Combinations]

    > I recently compiled a list of the 19 most popular fonts according to usage by graphic designers from all over the web. I could have had 100, but I got it down to under 50, and from there whittled it down to just the 19 best fonts.

2.  *03/10* - [Four Techniques for Combining Fonts][Four Techniques]

    > Is there a way to know what fonts will work together? Building a palette is an intuitive process, but expanding a typographic duet to three, four, or even five voices can be daunting.

3.  *10/23/11* - [10 Great Google Font Combinations You Can Copy][Google Fonts]

    > Today we’re going to use the Google Font API as a playground for mixing fonts and finding ideal pairings. You’ll be able to skim through and instantly grab out selections that you think are appropriate for your projects.

4.  *11/12/11* - [25 Fresh Examples of Beautiful Typeface Combinations in Web Design][25 Combinations]

    > From print to web layouts, typography is the center piece of a good design and today we gathered a few examples of beautiful typeface combinations in web design to inspire you.

5.  *03/20/12* - [10 More Great Google Font Combinations You Can Copy][More Google Fonts]

    > ...it’s becomingly increasingly difficult to sift through the library to find the best selections. We’ve got your back though and are serving up another great collection of Google Web Font combinations ripe for the stealing.

6.  *11/26/12* - [A Beginner’s Guide to Pairing Fonts][Beginners Guide]

    > Pairing fonts can be a challenge. Selecting two or more fonts which work well is one thing – selecting two which work together to achieve your typographic aims may have you reaching for the aspirin. Let’s see if we can alleviate any headaches. This guide will help you get started with font pairing for the web.

7.  [Combining Typefaces][]

    > Combining typefaces is challenging and fun, but it takes practice. Successful combinations are partly a matter of good taste, which can be tough to develop.

8.  [Typeface Combinations][]

    > Although the idea of typeface combining revolves around contrast, the best serif and sans serif combinations have similar characteristics.

#### Mobile

1.  [5 Tips for Excellent Mobile Typography][5 Tips]

    > Mobile typefaces have a lot in common with Goldilocks and the Three Bears. Everything needs to be just right. To look best on a small screen and be readable at a smaller size, the best font has the following 5 qualities...

2.  [Mobile Design Typography is Vitally Important ... and Challenging][Mobile typography]

    > One of the emerging challenges for web designers is creating web typography that works in the mobile environment as well. But it can be difficult, and there are many things to consider. The keys are to focus on readability, contrast, space and responsiveness.

3.  [iOS Fonts][]

    > A Place for Happy Typography (includes links to Android and Windows Phone 7 default typography.)

#### Font Classifications and Definitions

1.  *03/02/11* - [The Next Big Thing in Online Type][Online Type]

    > Beginning in 2006, Microsoft says it will ship with its operating system and other software products six brand new typefaces created especially for extended on-screen reading.

2.  [Typefaces, like most things, are made up of constituent parts.][Constituent Parts]

    > Typefaces, like most things, are made up of constituent parts. It is the characteristics of these parts that gives typefaces their character.

3.  [Font Factory][]

    > Fonts fall into logical categories, e.g. Serif or Script etc. But within a category, there are many subtitles, so we have assigned each font a specific sub-category that best describes the unique elements of a font. Each of the primary categories below have further categories to explore.

4.  [Type Classifications][Type Class]

    > Adobe typefaces are organized in the Type Classification pop-up menu according to a simplified version of the internationally recognized system adopted by the Association Typographique Internationale (ATypI).

5.  [Typeface Classifications][Classifications]

    > Serif and Sans Serif. A serif is a small projection that finishes the end of a stroke of a letter. Sans is an early French term based on a Latin word that means without.

6.  [What are the different categories for fonts?][Different Categories]

    > You can browse fonts in the following categories...



<br><hr /><br>
Appendix 9
----------

### Font Services and Tools

The font services below are listed in alphabetical order, some are free and others subscription-based, but together they represent what I consider be the best font services out there.

The tools I've listed, if needed, will help you deliver a superior typographic experience for your end-users.

#### Services

1. [Font Squirrel][]

   > Free fonts have met their match. We know how hard it is to find quality freeware that is licensed for commercial work. We've done the hard work, hand-selecting these typefaces and presenting them in an easy-to-use format.

2. [Fontdeck][]

   > Maintain your distinct brand online without resorting to time-consuming hacks. Use real text with professional typefaces optimised for the web.

3. [Fontspring][]

   > Font Licensing Doesn’t Have To Suck - Fontspring is a unique font license distributor. Our goal is to make buying fonts easy.

4. [Google Web Fonts][]

   > Google Web Fonts makes it quick and easy for everyone to use web fonts, including professional designers and developers. We believe that everyone should be able to bring quality typography to their web pages and applications.

5. [Typekit][]

   > This will change the way you design websites. Add a line of code to your pages and choose from hundreds of web fonts. Simple, bulletproof, standards compliant, accessible, and totally legal.

6. [WebINK][]

   > The WebINK service lets you put pro-quality fonts on your website. And we deliver these fonts to every visitor's browser in an instant.

### Tools

1.  [Lettering.JS][]

    > A jQuery plugin for radical web typography - Web type is exploding all over the web but CSS currently doesn't offer complete down-to-the-letter control. So we created a jQuery plugin to give you that control.

2.  [FitText.js][]

    > A jQuery plugin for inflating web type - FitText makes font-sizes flexible. Use this plugin on your fluid or responsive layout to achieve scalable headlines that fill the width of a parent element.

3.  [Ffffallback][]

    > Web fonts are here, sparking an exciting new era in web design. Ffffallback makes it easy to find the perfect fallback fonts, so that your designs degrade gracefully.

4.  [Font Stack Builder][]

    > Use the Code Style font stack builder to create robust CSS font-family declarations. The font stack builder shows the probability that your preferred fonts are displayed on Windows, Mac and Linux Web browsers.

5.  [Modular Scale][]

6.  [Relative \<font-size> calculator][Calculator]

7.  [Soma FontFriend][FontFriend]

    > Font­Friend is a book­marklet for typo­graph­i­cally obsessed web design­ers. It enables rapid check­ing of fonts and font styles directly in the browser with­out edit­ing code and refresh­ing pages...

8.  [Typetester][]

    > The Typetester is an online application for comparison of the fonts for the screen.

9.  [Web Font Specimen][]

    > Real web type in real web context. Web Font Specimen is a handy, free resource web designers and type designers can use to see how typefaces will look on the web.

####  Em's

1.  [Em Calculator][]

    > Em Calculator is a small JavaScript tool which helps making scalable and accessible CSS design. It converts size in pixels to relative em units, which are based on a text size.

2.  [Page width in ems][]

3.  [PXtoEM.com][]

    > PX to EM conversion made simple.



<br><hr /><br>
Appendix 10
-----------

### Choosing Typefaces

The following is designed to help you choose your typefaces. Here are some articles, and an excellent transcript from a presentation by Jason Santa Maria.

#### Choosing Typeface Articles

1.  *12/14/10* - [“What Font Should I Use?”: Five Principles for Choosing and Using Typefaces][Five Principles]

2.  *08/25/11* - [A Brief Primer on Typeface Selection][Brief Primer]

3.  *12/01/11* - [6 Questions You Should Ask Yourself When Choosing Fonts][6 Questions]

4.  *09/26/12* - [Make a Statement with Type][Type Statement]

Mobile

5.  *10/02/11* - [5 Tips for Excellent Mobile Typography][5 Tips]

6.  *11/12/12* - [Mobile Design Typography is Vitally Important ... and Challenging][Mobile typography]

#### Jason Santa Maria On Web Typography

Jason Santa Maria, in a presentation at [Build 2011][] called [On Web Typography][] spoke about picking typefaces. I've transcribed it here in part and slightly paraphrased:

1.  Questions to ask yourself: What are you using it for? How will it be used? Under what conditions? From the slide "considerations":

    > **Dimensions**
    > Are there requirements for how much text must fit in a given region?

    > **Special Features** - Do you require special features your typefaces
    > What features do you require? Multiple weights, lining &amp; old-style figures, small caps, etc?

    > **Prolonged Reading** -
    > Is this a book or a long format periodical?

    > **Internationalization** -
    > Does a given font support all the special characters of the language to be used?


2.  Readability and distinctness in characters matters. Will the typeface cause the reader to become confused, or tired of reading it?

3.  Avoid readymades. Fonts with design baked in.

4.  Develop your own personal palette. Find typefaces that you like, that you gravitate to, and keep using them. Get to know a typeface.

5.  Get to know the history of a typeface. When was it designed? Why was it designed? This should complement not contradict your text/subject.

6.  Find typefaces that embody a mental association: terms you want to associate with the design.

7.  Pair fonts that are designed together, they will work well together. The serif for the body text, the sans serif for the supplementary stuff like page numbers and captions.

8.  Use alternatives for commonly used typefaces get the same type of feel without being the same as everyone else. For example Helvetica. You can use an alternative rather than the frequently used Helvetica itself: FF Dagny, Proxima Nova, Museo Sans, Prehematica Slabserif.

9.  Try it out! Test out your ideas. See how it looks. See how it reads. See how it feels. In long-form text, in short-form text. Small columns, wide columns. Big text, small text. Doing this gives you a very real impression on how other people are going to see it.

NOTE: This work is [copyrighted][].



<br><hr /><br>
Appendix 11
-----------

### A Brief History of Web Font Sizes

Over the years I've referred to different articles when determining font size for projects I'm working on. Here they are in chronological order. A few are not so relevant today and some of them are exceptional! I'll let you be the judge of that, and have included them here as a reference.

1.  *05/11/01* - [CSS Design: Size Matters][BH1]

2.  *12/31/02* - [Text Sizing][BH2]

3.  *04/04/09* - [Power To The People: Relative Font Sizes][BH3]

4.  *05/18/04* - [How to size text using ems][BH4]

5.  *12/08/05* - [Don’t compose without a scale][BH5]

6.  *04/09/07* - [Setting Type on the Web to a Baseline Grid][BH6]

7.  *11/20/07* - [How to Size Text in CSS][BH7]

8.  *09/30/08* - [CSS Font-Size: em vs. px vs. pt vs. percent][BH8]

9.  *05/01/11* - [Font sizing with rem][BH9]

10. *05/03/11* - [More Meaningful Typography][BH10]

11. *10/28/11* - [R(a|ela)tional Design][BH11]

12. *12/09/11* - [Composing the New Canon: Music, Harmony, Proportion][BH12]

13. *07/18/12* - [How we learned to leave default font-size alone and embrace the em][BH13]

14. *07/19/12* - [On ems and rems][BH14]

15. *11/08/12* - [Why Ems?][BH15]



<br><hr /><br>
Appendix 12
-----------

### Color Tools

1.  [0to255][]

    > 0to255 is a simple tool that helps web designers find variations of any color.

2.  [Color Blender][]

    > Pick a color value format, input two valid CSS color values in the format you chose, and pick the number of midpoints you'd like to see. The palette will show the colors you input as well as the requested number of midpoint colors, and the values of those colors.

3.  [ColorBlender][]

    > To get started, choose a preferred color using the color picker below, and a 6-color matching palette (a "blend") will be automatically calculated.

4.  [ColorExplorer][]

    > Simply put, ColorExplorer is an online toolbox for working with color palettes.

5.  [Color Schemer][]

  > Online Color Scheme Generator

6.  [Colorspire][]

  > Create Color Schemes, Test Color Combinations

7.  [ColorTo.me][]

    > Create an image, share a pallet.

8.  [Contrast-A][]

    > Contrast-A checks color combinations for sufficient contrast and displays the results according to WCAG 2.0 (Luminance Ratio) as well as the results according to older accessibility guidelines, WCAG 1.0 (Difference in Brightness and Color).

9.  [Grab Website Colors - Color Scheme Extraction Tool][Grab Colors]

    > The website color extraction tool is used to grab colors from a website.

10. [Infohound Color Schemer][Infohound]

    > This color schemer is a simple tool to help you experiment with various color schemes for your next web or print project.

11. [Mother-effing hsl][]

#### Color Wheels

1.  [Adobe Kuler][]

    > Adobe Kuler is a web-hosted application for generating color themes that can inspire any project. No matter what you're creating, with Kuler you can experiment quickly with color variations and browse thousands of themes from the Kuler community.

2.  [Color Scheme Designer][]

3.  [Color Calculator][]

    > Use the free Color Calculator to explore creative color options for your design project. Simply pick your base color(s), choose a color harmony, tweak/explore as needed, and see results.

4.  [Color Wizard][]

    > The color wizard lets you submit your own base color, and it automatically returns matching colors for the one you selected.

5.  [Sphere: Color Theory Visualizer][Sphere]

#### Image Based Color Generators

1.  [color hunter][]

    > create and find color palettes made from images

2.  [Color Palette FX][]

    > Color Palette FX is a color tool for print and web design that creates color palettes from photos.

3.  [Color Palette Generator][]

    > Generate a color palette based on an image.

4.  [Genopal][]

    > Create harmonious colour schemes with Genopal

5.  [Image to Colors Palette Generator][Image to Colors]

    > Welcome to CSS Drive's Image to Colors Palette Generator! Upload an image to generate a color palette based on the image's primary colors. Useful for quickly grabbing a particular color within an image for inspiration.

6. [Pictaculous][]

    > Ever wonder what colors to use with an image? Upload your image – get a color palette!

#### Palettes

1.  [COLRD][]

    > ColRD: Create and share color inspiration with the world.

2.  [ColoRotate][]

    > Colors come to life in 3D! Browse color palettes, or create your own. Adjusts, mix and blend to your hearts content.

3.  [COLOURlovers][]

    > Share Your Color Ideas & Inspiration. COLOURlovers is a creative community where people from around the world create and share colors, palettes and patterns, discuss the latest trends and explore colorful articles... All in the spirit of love.

4.  [colr.org][]

    > Play with colors and color schemes!

5.  [Kuler][]

    > Adobe Kuler is a web-hosted application for generating color themes that can inspire any project. No matter what you're creating, with Kuler you can experiment quickly with color variations and browse thousands of themes from the Kuler community.

#### Collections

1.  [BrandColors][]

    > A collection of major brand color codes curated by Galen Gidman.

2.  [Fifty Shades of Grey: A Review][Gray Shades]

3.  [216 Web Safe Colors][Web Safe]



[Appendix 1]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-1
[Appendix 2]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-2
[Appendix 3]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-3
[Appendix 4]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-4
[Appendix 5]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-5
[Appendix 6]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-6
[Appendix 7]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-7
[Appendix 8]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-8
[Appendix 9]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-9
[Appendix 10]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-10
[Appendix 11]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-11
[Appendix 12]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-12



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

[Awwwards]:             http://www.awwwards.com/
[Pattern Tap]:          http://patterntap.com/
[UI Patterns]:          http://ui-patterns.com/
[siteInspire]:          http://siteinspire.com/showcase
[Codrops]:              http://tympanus.net/codrops/
[Codrops 1]:            http://tympanus.net/codrops/2012/09/28/stop-look-click-attention-grabbing-elements-in-web-design/
[Codrops 2]:            http://tympanus.net/codrops/2012/09/26/make-a-statement-with-type/
[Codrops 3]:            http://tympanus.net/codrops/2012/08/17/creative-background-styles-and-trends-in-web-design/
[Codrops 4]:            http://tympanus.net/codrops/2012/09/20/dashboard-design-elements-for-the-win/
[FWA]:                  http://www.thefwa.com/
[Inspired UI]:          http://inspired-ui.com/
[Pattern Tap Mobile]:   http://patterntap.com/?sort_by=created&platform[]=7
[AppSites]:             http://appsites.com/
[Mobile Patterns]:      http://www.mobile-patterns.com/
[Mobile Awesomeness]:   http://www.mobileawesomeness.com/
[Mobile Gallery]:       http://mobiledesignpatterngallery.com/mobile-patterns.php
[Media Queries]:        http://mediaqueri.es/
[FWA Mobile]:           http://m.thefwa.com/mobile_type/mobile_website/
[WAPReview]:            http://wapreview.com/?id=0
[Higher Ed]:            http://www.dmolsen.com/mobile-in-higher-ed/higher-ed-mobile-sites/
[WTF]:                  http://wtfmobileweb.com/
[70 Sites]:             http://www.mobify.com/blog/70-stunning-responsive-sites-for-your-inspiration/
[Responsive Nav]:       http://bradfrostweb.com/blog/web/responsive-nav-patterns/
[Complex Navigation]:   http://bradfrostweb.com/blog/web/complex-navigation-patterns-for-responsive-design/



[Toolbox 1]:            https://www.ruby-toolbox.com/search?utf8=%E2%9C%93&q=lorem+ipsum
[html-ipsum]:           http://html-ipsum.com/
[lipsum]:               http://www.lipsum.com/
[Fillerama]:            http://chrisvalleskey.com/fillerama/
[Samuel L. Ipsum]:      http://slipsum.com/
[Hipster Ipsum]:        http://hipsteripsum.me/
[Gangsta Lorem Ipsum]:  http://lorizzle.nl/
[Cupcake Ipsum]:        http://cupcakeipsum.com/
[Bacon Ipsum]:          http://baconipsum.com/
[T'lipsum]:             http://tlipsum.appspot.com/

[Toolbox 2]:            https://www.ruby-toolbox.com/search?utf8=%E2%9C%93&q=image+placeholders
[Image Generators]:     http://www.russellheimlich.com/blog/list-of-dummy-image-generators/
[Cambelt]:              http://cambelt.co/
[Holder.js]:            http://imsky.github.com/holder/



[Verify]:               http://verifyapp.com/
[Concept Feedback]:     http://www.conceptfeedback.com/
[IntuitHQ]:             http://www.intuitionhq.com/
[Loop11]:               http://www.loop11.com/
[Silverback]:           http://silverbackapp.com/
[UserTesting.com]:      http://www.usertesting.com/
[Rocket Surgery]:       http://www.youtube.com/watch?v=QckIzHC99Xc&feature=player_embedded

[DT1]:                  http://alistapart.com/article/smartphone-browser-landscape
[DT2]:                  http://bradfrostweb.com/blog/mobile/test-on-real-mobile-devices-without-breaking-the-bank/
[DT3]:                  http://stephanierieger.com/strategies-for-choosing-test-devices/
[DT4]:                  http://mobiletestingfordummies.tumblr.com/post/20056227958/testing
[DT5]:                  http://www.dmolsen.com/mobile-in-higher-ed/2012/06/26/how-to-build-a-device-lab-part-1/
[DT6]:                  http://alistapart.com/article/testing-websites-in-game-console-browsers
[DT7]:                  http://mobile.smashingmagazine.com/2012/09/24/establishing-an-open-device-lab/
[DT8]:                  http://cognition.happycog.com/article/building-the-happy-cog-test-lab
[DT9]:                  http://lab-up.org/



[Better Stacks]:        http://unitinteractive.com/blog/2008/06/26/better-css-font-stacks/
[Honest]:               http://aversionfour.petercolesdc.com/web-fonts-nice-honest/
[Definitive]:           http://www.sitepoint.com/eight-definitive-font-stacks/
[Techniques]:           http://coding.smashingmagazine.com/2009/09/22/complete-guide-to-css-font-stacks/
[Complete Guide]:       http://www.apaddedcell.com/web-fonts
[Font Stacks]:          http://css-tricks.com/snippets/css/font-stacks/
[Google Scripts]:       http://designshack.net/articles/css/the-10-best-script-and-handwritten-google-web-fonts/
[TYPECHART]:            http://www.typechart.com/
[Revised Font Stack]:   http://www.awayback.com/revised-font-stack/

[Gorgeous]:             http://www.webdesigndev.com/web-development/16-gorgeous-web-safe-fonts-to-use-with-css
[Cheat Sheet]:          http://www.mightymeta.co.uk/web-safe-fonts-cheat-sheet-v-3-with-font-face-fonts-and-os-breakdown/
[Common Fonts]:         http://www.ampsoft.net/webdesign-l/WindowsMacFonts.html
[CSS Font Stack]:       http://cssfontstack.com/
[Font Survey]:          http://www.codestyle.org/css/font-family/sampler-CombinedResults.shtml
[Web Safe]:             http://www.w3schools.com/cssref/css_websafe_fonts.asp

[19 Combinations]:      http://bonfx.com/19-top-fonts-in-19-top-combinations/
[Four Techniques]:      http://www.typography.com/email/2010_03/index_tw.htm
[Google Fonts]:         http://designshack.net/articles/css/10-great-google-font-combinations-you-can-copy/
[More Google Fonts]:    http://designshack.net/articles/typography/10-more-great-google-font-combinations-you-can-copy/
[Beginners Guide]:      http://webdesign.tutsplus.com/articles/typography-articles/a-beginners-guide-to-pairing-fonts/
[25 Combinations]:      http://tympanus.net/codrops/2011/11/12/25-fresh-examples-of-beautiful-typeface-combinations-in-web-design/
[Combining Typefaces]:  http://www.fivesimplesteps.com/products/combining-typefaces
[Typeface Combinations]: http://www.peatah.org/combinations2.html

[5 Tips]:               http://wixmobile.com/5-tips-for-excellent-mobile-typography
[Mobile Typography]:    http://tympanus.net/codrops/2012/11/12/mobile-design-typography-is-vitally-important-and-challenging/
[iOS Fonts]:            http://iosfonts.com/

[Online Type]:          http://www.poynter.org/how-tos/newsgathering-storytelling/visual-voice/32588/the-next-big-thing-in-online-type/
[Constituent Parts]:    http://designingfortheweb.co.uk/book/part3/part3_chapter12.php
[Font Factory]:         http://www.fontfactory.com/categories.php
[Type Class]:           http://www.adobe.com/type/browser/classifications.html
[Classifications]:      http://www.peatah.org/classifications.html
[Different Categories]: http://www.myfonts.com/Article8122.html



[Font Squirrel]:        http://www.fontsquirrel.com/
[Fontdeck]:             http://fontdeck.com/
[Fontspring]:           http://www.fontspring.com/
[Google Web Fonts]:     http://www.google.com/webfonts#
[Typekit]:              https://typekit.com/
[WebINK]:               http://www.webink.com/

[Lettering.JS]:         http://letteringjs.com/
[FitText.js]:           http://fittextjs.com/
[Em Calculator]:        http://riddle.pl/emcalc/
[Ffffallback]:          http://ffffallback.com/
[Font Stack Builder]:   http://www.codestyle.org/servlets/FontStack
[Modular Scale]:        http://modularscale.com/
[FontFriend]:           http://somadesign.ca/projects/fontfriend/
[Typetester]:           http://www.typetester.org/
[Web Font Specimen]:    http://webfontspecimen.com/

[Calculator]:           http://tools.the-echoplex.net/font-size/
[Page width in ems]:    http://www.themaninblue.com/experiment/emWidths/
[PXtoEM.com]:           http://pxtoem.com/



[Five Principles]:      http://www.smashingmagazine.com/2010/12/14/what-font-should-i-use-five-principles-for-choosing-and-using-typefaces/
[Brief Primer]:         http://blog.8thlight.com/billy-whited/2011/08/25/a-brief-primer-on-typeface-selection.html
[Type Statement]:       http://tympanus.net/codrops/2012/09/26/make-a-statement-with-type/
[6 Questions]:          http://tympanus.net/codrops/2011/12/01/6-questions-you-should-ask-yourself-when-choosing-fonts/

[5 Tips]:               http://wixmobile.com/5-tips-for-excellent-mobile-typography
[Mobile Typography]:    http://tympanus.net/codrops/2012/11/12/mobile-design-typography-is-vitally-important-and-challenging/

[Build 2011]:           http://2011.buildconf.com/
[On Web Typography]:    http://vimeo.com/34178417
[copyrighted]:          http://creativecommons.org/licenses/by-nc/3.0/



[BH1]:                  http://www.alistapart.com/articles/sizematters
[BH2]:                  http://www.thenoodleincident.com/tutorials/box_lesson/font/index.html
[BH3]:                  http://www.alistapart.com/articles/relafont
[BH4]:                  http://clagnut.com/blog/348/
[BH5]:                  http://webtypography.net/Harmony_and_Counterpoint/Size/3.1.1/
[BH6]:                  http://www.alistapart.com/articles/settingtypeontheweb
[BH7]:                  http://www.alistapart.com/articles/howtosizetextincss/
[BH8]:                  http://kyleschaeffer.com/user-experience/css-font-size-em-vs-px-vs-pt-vs/
[BH9]:                  http://snook.ca/archives/html_and_css/font-size-with-rem
[BH10]:                 http://www.alistapart.com/articles/more-meaningful-typography/
[BH11]:                 http://blog.8thlight.com/billy-whited/2011/10/28/r-a-ela-tional-design.html
[BH12]:                 http://24ways.org/2011/composing-the-new-canon/
[BH13]:                 http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/
[BH14]:                 http://filamentgroup.com/lab/on_ems_and_rems/
[BH15]:                 http://css-tricks.com/why-ems/



[0to255]:               http://0to255.com/
[Color Blender]:        http://meyerweb.com/eric/tools/color-blend/
[ColorBlender]:         http://www.colorblender.com/
[ColorExplorer]:        http://colorexplorer.com/
[Color Schemer]:        http://www.colorschemer.com/online.html
[Colorspire]:           http://www.colorspire.com/
[ColorTo.me]:           http://colorto.me/
[Contrast-A]:           http://www.dasplankton.de/ContrastA/
[Grab Colors]:          http://www.colorcombos.com/grabcolors.html
[Infohound]:            http://infohound.net/colour/
[Mother-effing hsl]:    http://mothereffinghsl.com/

[Adobe Kuler]:          https://kuler.adobe.com/#
[Color Scheme Designer]: http://www.colorschemedesigner.com/
[Color Calculator]:     http://www.sessions.edu/color-calculator
[Color Wizard]:         http://www.colorsontheweb.com/colorwizard.asp
[Sphere]:               http://mudcu.be/sphere/

[color hunter]:         http://www.colorhunter.com/
[Color Palette FX]:     http://www.palettefx.com/
[Color Palette Generator]: http://jrm.cc/color-palette-generator/
[Genopal]:              http://www.genopal.com/
[Image to Colors]:      http://www.cssdrive.com/imagepalette/
[Pictaculous]:          http://pictaculous.com/

[COLRD]:                http://colrd.com/
[ColoRotate]:           http://web.colorotate.org/
[COLOURlovers]:         http://www.colourlovers.com/
[colr.org]:             http://www.colr.org/
[Kuler]:                https://kuler.adobe.com/explore/

[BrandColors]:          http://brandcolors.net/
[Gray Shades]:          http://visualidiot.com/articles/fifty-shades
[Web Safe]:             http://websafecolors.info/
