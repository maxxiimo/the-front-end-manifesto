Visual Design for the Nondesigner
=================================

In the [last chapter][Chapter 4] our focus was Information Architecture, and in that chapter we really emphasize storytelling. [Design is part of storytelling][Story Design] so let's see if we can in the very least point you in the right direction in visual design.

Up until now, we basically have a pretty blank wireframe: function before form. We need to add some spice to it:

> Firstly, think about what your pages do, not what they look like. Let your design flow from the services which they will provide to your users, rather than from some overarching idea of what you want pages to look like. Let form follow function, rather than trying to take a particular design and make it "work".

\- [A Dao of Web Design][Dao] by John Allsopp

We learned in Chapter 4 that by looking at your site your users should be able to understand what they're looking at. That your website must communicate it's story. In the case of "View Thought" part of the story is:

> We are a great website **design** [emphasis supplied], development and user experience shop...we pay special attention to what your users will see.

If this is part of our story we better deliver some great graphic design on top of our information architecture, layout, and content, that will help communicate our story! To do so we will use a combination of typography, color, branding, images, icons, and anything else I can think of to help View Thought tell it's story, and in such a way that the user just gets it. The combination of these elements are the cornerstones of a sites look and feel. Let's explore each.

Paradigm Shift
--------------

Before we do, I want to mention a paradigm shift I've been noticing in the front end world. It used to be for really great design you absolutely needed a graphic designer. Unless you could work Photoshop or Illustrator like it was no tomorrow, graphic designers were the ones who would give you rounded corners, images of cool header fonts or hero text, gradients for your backgrounds and headers, icons an icon sprites, and the like. Because of this oftentimes entire design process had already been completed by the time you got it.

Your job was then to provide a handshake between graphic design and backend code. You understood what kind of code the backend team needed and how they would use it, and you had skills to turn graphic design into front end code. In my own personal experience as a consultant brought into projects, more times than not design mockups had already been completed and I would then slice and dice these mockups and integrate them into the application as pixel perfect and cross browser friendly as possible (pixel perfect used to really matter!).

NOTE: Chapter 6, [Slicing and Dicing Mockups][Chapter 6], will dive into the mechanics of doing exactly that.

With the advent of HTML5 and the continuous improvement in W3C CSS3 specifications and implementation by browser vendors, a lot of these image based design elements can now be created through front end code. In other words "graphic design" cannot take place on your IDE and in the browser.

As a view coder I'm really excited about this! One of the things I used to not like about the old paradigm is that a lot of decisions about information architecture and design had already taken place by the time mockups reached my hands (keep in mind that I've been a consultant for most of my career, brought in to do exactly this). This left me with very little say in these areas because often times internal bureaucracies, review committees, whatever you want to call them, were difficult to reconvene for the iteration at hand, and these iterations once implemented became the law of the land so to speak.

A glaring problem with this old process was that often times those making decisions didn't understand the full capabilities or limitations of the medium used. Photoshop and mockups are inherently limited. More important than this though is that a really important resource in the process was not being fully utilized.

Fast-forward to today and this has all changed. Design and the design process can now include, if not occur, at the point of front end coding. In fact I think it should be this way. Doing so provides for very rapid prototyping, experimenting, and iterations in the actual medium/s. The turnaround in relation to this chapter is that in order to participate in the process,, as front-end coders today, we need to really understand design – more so than ever before.

With that lets get started...

Typography
----------

After I have finished all of my information architecture stuff, the first visual design component I like to tackle is [typography][].

> 95% of the information on the web is written language. It is only logical to say that a web designer should get good training in the main discipline of shaping written information, in other words: Typography.

\- [Web Design Is 95% Typography][95% typography]

So let's get started. In my opinion the lowest hanging fruit in typography are typefaces:

- Font Family
- Font Size
- Readability

If you have implemented the base style sheets from Chapter 2, [Foundation Styles][Chapter 2], these typographic elements are predefined and available to you out-of-the-box in [_define.sass][] – a sass partial reserved for defining global stylesheet variables:

    /*  Fonts
      -----------------------

    // stacks...

    // http://unitinteractive.com/blog/2008/06/26/better-css-font-stacks/

    $arial:             Arial, "Helvetica Neue", Helvetica, sans-serif
    $verdana:           Verdana, Geneva, Tahoma, sans-serif
    $geneva:            Geneva, "Lucida Sans", "Lucida Grande", "Lucida Sans Unicode", Verdana, sans-serif
    $georgia:           Georgia, Palatino, "Palatino Linotype", Times, "Times New Roman", serif

    // base definitions...

    $base-font-family:  $arial       !default
    $base-font-size:    100%         !default
    $base-font-color:   #444         !default
    $base-line-height:  1.4          !default

    $base-font-header:  $georgia     !default
    $base-color-header: #222         !default

I recommend setting up something like this if you are not using ours. From this partial we can effect typography throughout the site through Sass's ability to set up variables.

For example, our definitions above begin with variables set to different font stacks. Variables can also be set to other variables, and in our case to the $base-font-family variable, the key to our application fonts. This variable is referenced by our \<body> tags font-family property, and will propagate throughout the entire application by virtue of the CSS we have written and the concept of CSS inheritance.

### Font Family

Since we have already predefined font stack variables, let's pick one for View Thought. If you don't like what is predefined for your site, to help you select an alternative without having to earn a PhD in typeface, I created a quick reference "[Font Stacks Roundup][Appendix 7]" located in the appendix of this book. Here you will find recommendations for:

1.  Font stacks that you can copy and use in your project.

2.  Web safe fonts, i.e. fonts that are most common on most versions of Windows, Mac, and Linux.

    You can copy these and feel confident using them as your overall default font stack, or as a fallback font stack for a more interesting typeface.

3.  Typefaces that go well together, say one font for your headers, and another contrasting font for your body.

#### Pairing Typefaces

When selecting font families for my projects I like to go straight for the "[Font Stacks Roundup][Appendix 7]" section titled "Combinations". Here designers with typographic knowledge and experience well beyond my own have paired fonts, describe their personality or feel, and more often than not provide samples for you to review and choose from.

> You might have already heard this; successful pairing relies on concord, or contrast, but not conflict. That is to say your selected fonts can work well together by sharing certain qualities, or by being completely different from one another. However, font pairs can conflict in a number of ways – being too similar being just one.

\- [A Beginner’s Guide to Pairing Fonts][Beginners Guide]

I have left a few font stacks and Google Web Fonts pairing ideas for you in our starter styles:

- [_define.sass][]
- [_head.html.haml][]

    // google web fonts...

    // http://designshack.net/articles/css/10-great-google-font-combinations-you-can-copy/
    // http://designshack.net/articles/typography/10-more-great-google-font-combinations-you-can-copy/

    $cantata:           "Cantata One", Georgia, serif
    $imprima:           Imprima, Verdana, Helvetica, sans-serif

    $allerta:           Allerta, Helvetica, Arial, sans-serif
    $crimson:           Crimson Text, Georgia, Times, serif

    $arvo:              Arvo, Georgia, Times, serif
    $pt-sans:           "PT Sans", Helvetica, Arial, sans-serif

    $droid-serif:       "Droid Serif", Georgia, Times, serif
    $droid-sans:        "Droid Sans", Helvetica, Arial, sans-serif

#### Font Stacks

The reason we use font stacks in the first place, i.e. a listing of several different fonts, is to make sure similar substitute fonts are available for devices that do not carry the font family you wish to use. For example:

    Arial, "Helvetica Neue", Helvetica, sans-serif

If your device does not have the first font in the stack, Arial, your browser will look for the second one and so forth until the very last one: which is a generic font and the most broadly available across different operating systems. The fonts in the stack are all similar enough that they can be interchanged with minimal differences between fonts used: at least that is the goal.

#### Font Services

Once I have chosen my pairing I use a font service to deliver them (without licensing headaches and through their CDN). Some services are subscription based and others are free. I have listed a few in the "[Font Services and Tools][Appendix 8]" appendix.

I use [Typekit][]. Fortunately for us, Typekit provides an excellent [series of articles][articles] on implementing Typekit, so [I'll][] [spare][] [you][] [the][] [details][].

Typekit is a paid service, [Google Web Fonts][] on the other hand is a free service:

- [A Beginner’s Guide to Using Google Web Fonts][Beginners Guide]

#### Choosing Typefaces

Here are some screenshots of different font ideas for View Thought:

![][fonts]

As you can see, choosing fonts is a practice in trial and error. In Appendix 9 in the section entitled "[Choosing Typeface Articles][Choosing Typeface]," I list different articles that might help you frame the context of your decision making process.

I also think the following idea is worth noting by itself: In a presentation by Tim Brown, the Type Manager for Adobe Typekit, he quotes Jason Santa Maria as saying:

> Write down a general description of the qualities of the message you are trying to convey, and then look for typefaces that embody those qualities.

\- [More Perfect Typography][Perfect Typography]

...and states that now, this is how he always begins a project. He then goes on to describe that he starts with body text, which gives tone for a piece, then moves on to markers like headers, that give it personality and character. Food for thought.

Speaking of Jason Santa Maria, in another presentation called [On Web Typography][] he gives advice on picking typefaces. Besides being a master on the subject, his recommendations (starting at 31:45) are excellent. You can find them transcribed in [Appendix 9][].

### Font Size

Now that we have selected a font family, we need to set a base font size. Choosing font size is actually an important decision. At the very basic level you will choose between a measurement types such as px's vs. em's vs. % vs. pt's vs rem's, and from a more complex perspective you need to consider that your choice might also be the measurement from which your entire site is responsive to, and in our case it is.

Quite frankly to me it seemed like a whole heck of a lot of thinking and research that I would love to spare you from, so I'm just going to give you a very opinionated basis to start from. At the same time I will also provide you with the source of my thinking in "[A Brief History of Web Font Sizes][Appendix 10]" found in the appendices.

In Chapter 2 we implemented [Normalize.css][]. If you look at our [implementation][] you will notice that we reset our base font size to 100%:

    /*
    * 1. Corrects text resizing oddly in IE 6/7 when body `font-size` is set using `em` units.
    * 2. Prevents iOS text size adjust after orientation change, without disabling user zoom.
    */

    html {
        font-size: 100%; /* 1 */
        -webkit-text-size-adjust: 100%; /* 2 */
        -ms-text-size-adjust: 100%; /* 2 */
    }

As a rule of thumb, browsers typically default to a font size of 16px. We're going to accept this default font size for our project, so setting a font size of 100% through normalize is fine and dandy. Through the body tag we also provide a way in which we may affect font sizes globally:

app\assets\stylesheets\_define.sass

    $base-font-size:    100%         !default

app\assets\stylesheets\desktop\_layout.sass

    body
      margin: 0 auto
      width: 960px
      font-size: $base-font-size
      line-height: $base-line-height
      background-color: $bg-body

Again, we're going to use the browser's default setting. I include 100% here, but could also omit the reference completely.

#### Using Em's

Throughout our application moving forward if we would like to affect font size for let's say headers or a specific element, we will use em's. We use em's because there are a scalable unit relative to the parent font size. In our case, 1em = default browser font size = typically 16px. If we would like to double in size we use 2em = 32px.

NOTE: It's important to keep in mind that em's are relative to the parent, and not the browser or \<body> font size.

In Chapter 3 we learned about the benefits of [using em's][] in our media querries, and that using em's goes hand-in-hand with our Susy grid system.

For more details on using em's take a look at:

- [Ideal line length for content][Ideal Line Length]
- [CSS Font-Size: em vs. px vs. pt vs. percent][CSS Font-Size]
- [How we learned to leave default font-size alone and embrace the em][Embracing em's]

### Readability

Font choice, size, line length (measure), line height (leading), and font color and contrast all come together and contribute to your websites [readability][]. We've covered font choice and size, now let's look at the rest. Before we do we need to first understand what a modular scale is and define our own.

#### Modular Scales

A modular scale is a scale based on ratios derived from harmonic intervals or the golden ratio and key measure/s in your application (such as the base font size). Yowza! What? Well in layman's terms it's a bunch of measurements used for key measurements in your application, a scale, that are related to one another in some artistic/design awesome way; versus randomly picking numbers. You use numbers from the scale throughout your application for things like line length, column widths, line heights, etc., and by doing so your design will be better, or in the very least you are making a design informed decision!

So how is this modular scale created? Fortunately there are some great references out there that will do a much better job of explaining the what's and how's of modular scales:

- [Tim Brown - More Perfect Typography][Perfect Typography] (Go to minute 15:00, great talk.)
- Articles 10, 11, and 12 in Appendix 10, [A Brief History of Web Font Sizes][Appendix 10]
- The [Modular Scale][] tool

 Using the Modular Scale tool here is the scale we will use for View Thought:

- http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0

Our scale is based on the golden ratio and two important numbers, our base font size of 16px and our logo font size of 30px. In our [_define.sass][] partial we take note of this as follows:

    /*  Modular Scale
      -----------------------

    // http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0

    // 16px  @ 1:1.618 - base font size
    // 30px  @ 1:1.618 - logo font size

Now that we have a scale, let's apply it.

#### Line Length (Measure)

For line length the following character ranges seem to be the best ones to use:

> ...anywhere from 45–75 characters is considered acceptable.

\- [Readability][readability] by Billy Whited

> A general good rule of thumb is 2-3 alphabets in length, or 52-78 characters (including spaces).

\- [Five simple steps to better typography][Better Typography] by Mark Boulton

For View Thought I'll take a sample of text directly off of our wireframe:

> Nothing beats the involvement of a well-seasoned, front-end developer that understands the semantics of what you're trying to pull off.

There are 116 characters in that sample, so what I need to do is find the 45 to 75 character cutoff points (without spaces) in it. To do so I'll use a word processors word count capabilities.

~45 characters:

> Nothing beats the involvement of a well-seasoned,

~75 characters:

> Nothing beats the involvement of a well-seasoned, front-end developer that understands

With the fonts and font size I have chosen and implemented, for this particular piece of text my measure should not cause the text to span shorter than the "," after seasoned or longer than "understands". Well great, how does that help me with the rest of my content?

Knowing this about our sample we can translate this information into measurable units by marginally decreasing the texts containing elements width until we reach the cutoff points. I use Firebug to easily decrease the width of my containing element and come up with the following two measurements:

    28em
    42em

...my minimum and maximum line lengths. But neither measure is in my scale. No problem, find the closest numbers:

    29.03em
    46.971em

Need them to be even closer? You can add and subtract up to two numbers from the same scale, just comment your math:

    // 29.03-1
    28.03em

    // 46.971 - 4.909
    42.062em

> Modular scales are a tool, they’re not magic. They’re not going to work for every measurement, and that’s okay. Math is no substitute for an experienced designer’s eye, but it can provide both hints and constraints for decision making. Consider the scale’s numbers educated suggestions. Round them if you like (22.162 becomes 22). Combine them (3.56 + 16 = 19.56). Or as we saw me do here, break from the scale entirely.

\- [More Meaningful Typography][Meaningful Typography] by Tim Brown

Moving forward in my design I now have constraints I can keep an eye on when sizing columns in my layout.

#### Line Heigt (Leading)

For line height there are a couple key things to keep in mind: You will need more line height when your lines are longer – otherwise your readers might get lost, and/or when you use a darker font color – so that you do not to overwhelm the rest of the site.

For our site we're going to pick a number from our scale. After some trial and error, 1.618 seems to be the best line height:

    $base-line-height:  1.618         !default

The next natural step down in our scale is 1.159, which seems to be too much of a step down, so using another figure in our scale I calculate an alternative in case I need it:

    // 1.618 - 0.105 = 1.513
    // 1.618 - 0.236 = 1.382
    // 1.618 - 0.382 = 1.236

#### Color

I read [somewhere][] that to make your text appear softer and still maintain a good contrast you shouldn't use pure black for your font color but something slightly lighter. The idea made a lot of sense to me so we use the following defaults in our starter styles:

    $base-font-color:   #444         !default
    $base-header-color: #222         !default

Of course, black on white does not have to be the default color and contrast. Will learn more about color in the next section.

Color
-----

> There are many contributing factors that go into making a good visual design, but one of the simplest ways to do this is through the use of colour. The colour palette used in a design can have such a profound effect on a visual design that it almost feels like you’re cheating. It’s easy to add more and more subtle shades of colour to add a sense of sophistication and complexity to a design, but it dilutes the overall visual impact. When I design, I almost have a rule that only allows me to use a very limited colour palette.

\- Mike Kus, "[Nine Things I've Learned][9 Things]"


Branding
--------


Images
------


Icons
-----

### Icon Fonts



[The Big List of Flat Icons & Icon Fonts][Big List]

[HTML for Icon Font Usage][Icon Font HTML]

[Getting Font-Face to work with the Asset Pipeline][Pipeline]

[How to make your own icon webfont][DIY Icon Fonts]

[Testing @font-face Support on Mobile and Tablet][Icon Font Support]


#### @font-face


### Icon Sprites



Images
------


Other Resources
---------------

What follows are some ideas and resources to help you create your site's look and feel:

- Use a framework. We listed several frameworks you can use in the [Frameworks][] section of the Appendix.

- Reverse engineer pieces of things you already like.

- Find a plug-in.

- Hire a graphic designer. With your layout set via our wireframe work half of the designers work is done. Now he or she needs to pull it all together with a stellar look and feel. When hiring a designer, make sure you let them know that the layout you have in place is not set in stone. This way your designer can add their experience to the project. Here are some resources for finding graphic designers:

  - XXX

- Get a freebie and port it over to your application.

  - [Premium Pixels][]

- Buy a template. Templates are significantly less expensive than hiring a graphic designer. As a front end coder implementing them into your layout should be a breeze. Here are some template resources:

  - XXX

- Read a tutorial.

What We've Done
---------------

Don't for a moment think that creative license belongs only to designers. It does not, in fact with the abilities of CSS3, much of the design work can now occur in the browser straight from our IDE's. Think of yourself as artists of a new age; you are the handshake between design and backend engineering and can work in either realm.

We started this chapter by covering typography. We discussed the basic building blocks of typography and how it is implemented in our application. As a side note, if you really want to learn more, the most highly acclaimed resource out there is:

- [The Elements of Typographic Style Applied to the Web][Typographic Style]

[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[Story Design]:         http://24ways.org/2011/design-the-invisible/
[Dao]:                  http://www.alistapart.com/articles/dao
[Chapter 6]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/slicing-and-dicing-mockups.md
[typography]:           http://blog.8thlight.com/billy-whited/2011/07/26/what-is-typography.html
[95% typography]:       http://informationarchitects.net/blog/the-web-is-all-about-typography-period/
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md
[Appendix 7]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-7.md#font-stacks-roundup
[Beginners Guide]:      http://webdesign.tutsplus.com/articles/typography-articles/a-beginners-guide-to-pairing-fonts/
[_head.html.haml]:      https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_head.html.haml
[Appendix 8]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-8.md#font-services-and-tools
[Typekit]:              https://typekit.com/
[articles]:             http://blog.typekit.com/category/font-events/
[I'll]:                 https://github.com/maxxiimo/viewthought/blob/master/app/views/layouts/_head.html.haml
[spare]:                https://github.com/maxxiimo/viewthought/blob/master/app/assets/javascripts/application.js
[you]:                  https://github.com/maxxiimo/viewthought/blob/master/app/assets/javascripts/site.js
[the]:                  https://github.com/maxxiimo/viewthought/blob/master/app/assets/stylesheets/_define.sass
[details]:              https://github.com/maxxiimo/viewthought/blob/master/app/assets/stylesheets/desktop/_typography.sass
[Google Web Fonts]:     http://www.google.com/webfonts#
[Beginners Guide]:      http://designshack.net/articles/css/a-beginners-guide-to-using-google-web-fonts/
[Choosing Typeface]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-9.md#choosing-typeface-articles
[Perfect Typography]:   http://vimeo.com/17079380
[On Web Typography]:    http://vimeo.com/34178417
[Appendix 9]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-9.md#jason-santa-maria-on-web-typography
[Appendix 10]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-10.md#a-brief-history-of-web-font-sizes
[Normalize.css]:        https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md#resets
[implementation]:       https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v102.scss
[using em's]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md#ems-and-media-queries
[CSS Font-Size]:        http://kyleschaeffer.com/user-experience/css-font-size-em-vs-px-vs-pt-vs/
[Ideal Line Length]:    http://www.maxdesign.com.au/articles/em/
[Embracing em's]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/
[Modular Scale]:        http://modularscale.com/
[readability]:          http://blog.8thlight.com/billy-whited/2011/08/23/readability.html
[Better Typography]:    http://www.markboulton.co.uk/journal/five-simple-steps-to-better-typography
[Meaningful Typography]: http://alistapart.com/article/more-meaningful-typography
[somewhere]:            http://www.kaikkonendesign.fi/typography/section/11
[9 Things]:             http://24ways.org/2011/nine-things-ive-learned/
[Responsive Navigation]: http://bradfrostweb.com/blog/web/responsive-nav-patterns/
[Big List]:             http://css-tricks.com/flat-icons-icon-fonts/
[Icon Font HTML]:       http://css-tricks.com/html-for-icon-font-usage/
[Pipeline]:             http://myrailslearnings.wordpress.com/2012/05/01/getting-font-face-to-work-with-the-asset-pipeline/
[DIY Icon Fonts]:       http://www.webdesignerdepot.com/2012/01/how-to-make-your-own-icon-webfont/
[Icon Font Support]:    http://blog.kaelig.fr/post/33373448491/testing-font-face-support-on-mobile-and-tablet
[Frameworks]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-5.md#frameworks
[Premium Pixels]:       http://www.premiumpixels.com/
[Typographic Style]:    http://webtypography.net/

[fonts]:                http://www.chrismaxwell.com/manifesto/fonts/fonts.gif
