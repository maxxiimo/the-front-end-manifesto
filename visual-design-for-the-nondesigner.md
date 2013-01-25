Visual Design for the Nondesigner
=================================

The [last chapter][] was about Information Architecture, so design really goes beyond it's scope, however, [design is part of storytelling][Story Design] so let's see if we can in the very least point you in the right direction in visual design.

Up until now, we basically have a pretty blank wireframe: function before form. We need to add some spice to it.

> Firstly, think about what your pages do, not what they look like. Let your design flow from the services which they will provide to your users, rather than from some overarching idea of what you want pages to look like. Let form follow function, rather than trying to take a particular design and make it "work".

\- [A Dao of Web Design][Dao] by John Allsopp

Just by looking at your site your users should be able to understand what they're looking at. Your website must communicate it's story. To illustrate how simple this can be take a look at this 2007 website concept:

- http://noonebelongsheremorethanyou.com/00025

Jason Santa Maria pointed out this site in a presentation he gave in 2008. What I like about it is that it demonstrates the simplicity of storytelling: the entire site is written on kitchen appliances! ...and at the same time engages the user and ultimately delivers a message to entice action.

In the case of "View Thought" part of the story is:

"We are a great website **design** [emphasis supplied], development and user experience shop...we pay special attention to what your users will see."

If this is part of our story we better deliver some great graphic design on top of our information architecture, layout, and content that will help communicate it! To do so we will use a combination of fonts, color, images, and anything else I can think of to help View Thought tell it's story, and in such a way that users just get it. The combination of typefaces (fonts), color, branding, and images are the cornerstones of a sites look and feel. Let's explore each.

Typography
----------

After I have finished all of my information architecture stuff, the first visual design component I like to tackle is [typography][].

> 95% of the information on the web is written language. It is only logical to say that a web designer should get good training in the main discipline of shaping written information, in other words: Typography.

[Web Design Is 95% Typography][95% typography]

Before we dive into this, if you really want to learn about typography, the most highly acclaimed resource out there is (I through the second one in there for good measure):

- [The Elements of Typographic Style Applied to the Web][Typographic Style]
- [Thinking with Type][Think Type]

In this chapter I'm NOT going to cover a major component of typography, and that is grid systems. We introduced grid systems in the [Mobile on Rails][] chapter of this book, and include a [Grid Systems][] roundup in the appendices.

So let's get started. In my opinion the lowest hanging fruit in typography are base font characteristics: family, size, color and line height. If you have implemented the base style sheets from chapter 2, [Foundation Styles][], you have several font faces available to you out of the box and defined and organized in [_define.sass][], a sass file reserved for defining global stylesheet variables:

    /*  Fonts
      -----------------------

    // stacks...

    // http://unitinteractive.com/blog/2008/06/26/better-css-font-stacks/

    $arial:             Arial, "Helvetica Neue", Helvetica, sans-serif
    $verdana:           Verdana, Geneva, Tahoma, sans-serif
    $geneva:            Geneva, "Lucida Sans", "Lucida Grande", "Lucida Sans Unicode", Verdana, sans-serif
    $georgia:           Georgia, Palatino, "Palatino Linotype", Times, "Times New Roman", serif

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

    // base definitions...

    $base-font-family:  $arial       !default
    $base-font-size:    100%         !default
    $base-font-color:   #444         !default
    $base-line-height:  1.4          !default

    $base-font-header:  $georgia     !default
    $base-color-header: #222         !default

In Sass you can set up variables. Our definitions above begin with variables set to different font stacks. Variables can be set to other variables, and in our stylesheets defined font stacks are set to the $base-font-family variable which in turn is reference by our \<body> tags font-family property. Unless defined differently in child elements, this stack will now propagate throughout the entire application by virtue of the CSS we have written and the concept of CSS inheritance.

### Font Family

So let's pick a base font family for View Thought. For your project, to help you get the job done without having to earn a PhD in typeface, I created a quick reference "[Font Stacks Roundup][Appendix 7]" located in the appendix of this book. Here you will find recommendations for:

1.  Font stacks that you can copy and use in your project.

2.  Web safe fonts, i.e. fonts that are most common on most versions of Windows, Mac, and Linux.

    You can copy these and feel confident using them as your overall default font stack, or as a fallback font stack for a more interesting typeface.

3.  Fonts that go well together, say one font for your headers, and another contrasting font for your body.

I like to go straight for the section titled "combinations". Here designers with typographic knowledge and experience well beyond my own have paired fonts, describe their personality or feel, and/or provide samples for you to review and choose from.

> You might have already heard this; successful pairing relies on concord, or contrast, but not conflict. That is to say your selected fonts can work well together by sharing certain qualities, or by being completely different from one another. However, font pairs can conflict in a number of ways – being too similar being just one.

\- [A Beginner’s Guide to Pairing Fonts][Beginners Guide]

I have left a few font stacks and Google Web Fonts pairing ideas for you in our starter styles:

- [_define.sass][]
- [_head.html.haml][]

#### Font Stacks

The reason we use font stacks in the first place, i.e. a listing of several different fonts, is to make sure similar substitute fonts are available for devices that do not carry the font family you wish to use.

    Arial, "Helvetica Neue", Helvetica, sans-serif

If your device does not have the first font in the stack available, your browser will look for the second one and so forth until the very last one: which is typically generic and the most broadly available across different operating systems. The fonts in the stack are all similar enough that they can be interchanged with minimal differences between fonts used: at least that is the goal.

#### Font Services

Once I have chosen my pairing I use a font service to deliver them (without licensing headaches and through their CDN). Some services are subscription based and others are free. I have listed a few in the "[Font Services and Tools][Appendix 8]" appendix.

I use [Typekit][]. Fortunately for us, Typekit provides an excellent [series of articles][articles] on implementing Typekit, so [I'll][] [spare][] [you][] [the][] [details][].

Typekit is a paid service, [Google Web Fonts][] on the other hand is a free service:

[A Beginner’s Guide to Using Google Web Fonts][Beginners Guide]

### Trial and Error

Here are some screenshots of different font ideas for View Thought:

![][fonts]

As you can see, choosing fonts is a practice in trial and error. These articles might help frame the context of your decision making process:

- [Make a Statement with Type][Type Statement]
- [6 Questions You Should Ask Yourself When Choosing Fonts][6 Questions]
- [A Brief Primer on Typeface Selection][Brief Primer]
- [Mobile Design Typography is Vitally Important ... and Challenging][Mobile typography]

### Size

Choosing font size is actually not as straightforward and easy as one would expect. At the very basic level, you will choose between a measurement type such as px vs. ems vs. % vs. rem, and from a more complex perspective you might want to define a modular scale based on ratios derived from harmonic intervals or the golden ratio. Yowza!

So why so complex? Well essentially your choice will significantly impact the harmony and feel of your design; and how your site will look across different browsers, devices, and user settings. Your choice might also be the basis from which your entire site is responsive to.

Quite frankly to me it seemed like a whole heck of a lot of thinking and research that I would love to spare you from, so I'm just going to give you a very opinionated basis to start from. At the same time I will also provide you with the source of my thinking in "[A Brief History of Web Font Sizes][Appendix 9]" found in the appendices.

In Chapter 2 we implemented [Normalize.css][]. If you look at the [stylesheet][] you will notice that we reset our base font size to 100%:

    /*
    * 1. Corrects text resizing oddly in IE 6/7 when body `font-size` is set using `em` units.
    * 2. Prevents iOS text size adjust after orientation change, without disabling user zoom.
    */

    html {
        font-size: 100%; /* 1 */
        -webkit-text-size-adjust: 100%; /* 2 */
        -ms-text-size-adjust: 100%; /* 2 */
    }

Typically browsers default to a font size of 16px. We're going to accept this default font size for our project, so setting a font size of 100% through normalize is fine and dandy. Through the body tag we provide a way in which we may affect font sizes globally:

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

NOTE: It's important to keep in mind that ends are relative to the parent, and not the browser or \<body> font size.

 In Chapter 3 we learned about the benefits of [using em's][] in our grid system, and as it relates to our content. Using em's then goes hand-in-hand with our grid system.

For more details take a look at:

- [Ideal line length for content][Ideal Line Length]
- [CSS Font-Size: em vs. px vs. pt vs. percent][CSS Font-Size]
- [How we learned to leave default font-size alone and embrace the em][Embracing em's]

### Readability

Font choice, size, line length (measure), line height (leading), color all come together and contribute to your websites [readability][]. We've covered font choice and size, now let's look at the rest.

#### Measure

For line length let's plan to use any of the following ranges throughout our application:

> ...anywhere from 45–75 characters is considered acceptable.

\- [Readability][readability] by Billy Whited

> A general good rule of thumb is 2-3 alphabets in length, or 52-78 characters (including spaces).

\- [Five simple steps to better typography][Better Typography] by Mark Boulton

#### Leading

For line height

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

[last chapter]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[Story Design]:         http://24ways.org/2011/design-the-invisible/
[Dao]:                  http://www.alistapart.com/articles/dao
[typography]:           http://blog.8thlight.com/billy-whited/2011/07/26/what-is-typography.html
[95% typography]:       http://informationarchitects.net/blog/the-web-is-all-about-typography-period/
[Typographic Style]:    http://webtypography.net/
[Think Type]:           http://www.thinkingwithtype.com/
[Mobile on Rails]:      https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md
[Grid Systems]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-3.md#grid-systems
[Foundation Styles]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[Appendix 7]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-7.md#font-stacks-roundup
[Beginners Guide]:      http://webdesign.tutsplus.com/articles/typography-articles/a-beginners-guide-to-pairing-fonts/
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
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
[Type Statement]:       http://tympanus.net/codrops/2012/09/26/make-a-statement-with-type/
[6 Questions]:          http://tympanus.net/codrops/2011/12/01/6-questions-you-should-ask-yourself-when-choosing-fonts/
[Brief Primer]:         http://blog.8thlight.com/billy-whited/2011/08/25/a-brief-primer-on-typeface-selection.html
[Mobile Typography]:    http://tympanus.net/codrops/2012/11/12/mobile-design-typography-is-vitally-important-and-challenging/
[Appendix 9]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-9.md#a-brief-history-of-web-font-sizes
[Normalize.css]:        https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md#resets
[stylesheet]:           https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v102.scss
[using em's]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md#ems-and-media-queries
[CSS Font-Size]:        http://kyleschaeffer.com/user-experience/css-font-size-em-vs-px-vs-pt-vs/
[Ideal Line Length]:    http://www.maxdesign.com.au/articles/em/
[Embracing em's]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/
[readability]:          http://blog.8thlight.com/billy-whited/2011/08/23/readability.html
[Better Typography]:    http://www.markboulton.co.uk/journal/five-simple-steps-to-better-typography
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

[fonts]:                http://www.chrismaxwell.com/manifesto/fonts/fonts.gif
