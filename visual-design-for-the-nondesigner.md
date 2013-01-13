Visual Design for the Nondesigner
---------------------------------

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

### Typography

After I have finished all of my information architecture stuff, the first visual design component I like to tackle is my base typography.

> 95% of the information on the web is written language. It is only logical to say that a web designer should get good training in the main discipline of shaping written information, in other words: Typography.

[Web Design Is 95% Typography][95% typography]

Before we dive into this, if you really want to learn about typography, the absolute best resources out there are:

- [The Elements of Typographic Style Applied to the Web][Typographic Style]
- [Thinking with Type][Think Type]

In this chapter I'm not going to cover a major component of typography, and that is grid systems. We introduced grid systems in the [Mobile on Rails][] chapter of this book, and include a [Grid Systems][] roundup in the appendices.

So let's get started. In my opinion the lowest hanging fruit in typography are base font characteristics: family, size, color and line height. If you have implemented the base style sheets from chapter 2, [Foundation Styles][], you have several font faces available to you out of the box, and base font characteristics have been predefined in global variables. All of this is organized in [_define.sass][], a sass file reserved for defining global stylesheet variables:

    /*  Fonts
      -----------------------

    // stacks...

    $arial:             Arial, "Helvetica Neue", Helvetica, sans-serif
    $georgia:           Georgia, Palatino, "Palatino Linotype", Times, "Times New Roman", serif
    $verdana:           Verdana, Geneva, Tahoma, sans-serif
    $geneva:            Geneva, "Lucida Sans", "Lucida Grande", "Lucida Sans Unicode", Verdana, sans-serif
    $arvo:              Arvo, Georgia, Times, serif

    // base definitions...

    $base-font-family:  $arial  !default
    $base-font-size:    1em     !default
    $base-font-color:   #333    !default
    $base-line-height:  1.4     !default

In Sass you can set up variables. As you can see above, our definitions begin with variables set to different font stacks. These variables can then be assigned to the $base-font-family variable. What ever variable you sign to $base-font-family will then permeate throughout the entire application by virtue of the CSS we have written and the concept of CSS inheritance. In our case we set the font family of our <body> tag to $base-font-family. All child elements will then inherit this font family, unless defined otherwise.

#### A note on Font Stacks

The reason we use font stacks in the first place, i.e. a listing of several different fonts, is to make sure similar substitute fonts are available for devices that do not carry the font family you wish to use. If your device does not have the first font in the stack available, your browser will look for the second one and so forth until the very last one: which is the most broadly available. The fonts in the stack are all similar enough that they can be interchanged with minimal differences between fonts used: at least that is the goal.

#### Font Family

So let's pick a base font family for View Thought. For your project, to help you get the job done without having to earn a PhD in typeface, I created a quick reference "[Font Stacks Roundup][Appendix 7]" located in the appendix of this book. Here you will find recommendations for:

1. Web safe fonts, i.e. fonts that come preinstalled in most systems that you can copy and feel confident using as either your overall default font stack, or as a fallback font stack for a more interesting typeface.
2. Fonts that go well together, say one font for your headers, and another contrasting font for your body.
3.


[Build better CSS font stacks][Font Stacks]
[CSS Web Safe Font Combinations][Web Safe]
[Mobile Design Typography is Vitally Important ... and Challenging][Mobile typography]

#### Size



#### Color



#### Line Height



### Color

> There are many contributing factors that go into making a good visual design, but one of the simplest ways to do this is through the use of colour. The colour palette used in a design can have such a profound effect on a visual design that it almost feels like you’re cheating. It’s easy to add more and more subtle shades of colour to add a sense of sophistication and complexity to a design, but it dilutes the overall visual impact. When I design, I almost have a rule that only allows me to use a very limited colour palette.

- Mike Kus, "[Nine Things I've Learned][9 Things]"


### Branding

### Images

### Icons

#### Icon Fonts



[The Big List of Flat Icons & Icon Fonts][Big List]

[HTML for Icon Font Usage][Icon Font HTML]

[Getting Font-Face to work with the Asset Pipeline][Pipeline]

[How to make your own icon webfont][DIY Icon Fonts]

[Testing @font-face Support on Mobile and Tablet][Icon Font Support]

#### Icon Sprites



### Images


### Other Resources

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

[last chapter]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/information-architecting.md
[Story Design]:         http://24ways.org/2011/design-the-invisible/
[Dao]:                  http://www.alistapart.com/articles/dao
[95% typography]:       http://informationarchitects.net/blog/the-web-is-all-about-typography-period/
[Typographic Style]:    http://webtypography.net/
[Think Type]:           http://www.thinkingwithtype.com/
[Mobile on Rails]:      https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-on-rails.md
[Grid Systems]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-3.md#grid-systems
[Foundation Styles]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/_define.sass
[Appendix 7]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-7.md#font-stacks-roundup
[Font Stacks]:          http://www.codestyle.org/css/font-family/BuildBetterCSSFontStacks.shtml
[Web Safe]:             http://www.w3schools.com/cssref/css_websafe_fonts.asp
[Mobile Typography]:    http://tympanus.net/codrops/2012/11/12/mobile-design-typography-is-vitally-important-and-challenging/
[9 Things]:             http://24ways.org/2011/nine-things-ive-learned/
[Responsive Navigation]: http://bradfrostweb.com/blog/web/responsive-nav-patterns/
[Big List]:             http://css-tricks.com/flat-icons-icon-fonts/
[Icon Font HTML]:       http://css-tricks.com/html-for-icon-font-usage/
[Pipeline]:             http://myrailslearnings.wordpress.com/2012/05/01/getting-font-face-to-work-with-the-asset-pipeline/
[DIY Icon Fonts]:       http://www.webdesignerdepot.com/2012/01/how-to-make-your-own-icon-webfont/
[Icon Font Support]:    http://blog.kaelig.fr/post/33373448491/testing-font-face-support-on-mobile-and-tablet
[Frameworks]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-5.md#frameworks
[Premium Pixels]:       http://www.premiumpixels.com/
