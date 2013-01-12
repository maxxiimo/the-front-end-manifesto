Visual Design
-------------

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

### Typeface

After I have finished all of my information architecture stuff, the first component I like to tackle in visual design is defining the font family I will use, the base font size, color and line height. Before we dive into this, if you really want to learn about typeface the absolute best resources out there are:

- [][]

Before we begin to define our fonts for View Thought let's look at what we have available to us out-of-the-box in our foundation styles. Our fonts are organized in [_define.sass][]:

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

It starts with variables set to different common font stacks. Choose one of the variables to set as your base font family. Whatever you choose will then permeate throughout the entire application by virtue of the CSS we have written and the concept of CSS inheritance.

The reason we use stacks in the first place, i.e. a listing of several different fonts, is so that if your machine does not have the first font available, your browser will look for the second one and so forth until the very last one: which is the most broadly available. Overall the fonts in the stack are all similar enough that they can be interchanged with minimal differences between fonts used between different machines such as a Microsoft desktop versus a Macintosh experience.

#### Font Family

To help you get the job done without having to earn a PhD in typeface, I created a quick reference "[Font Stacks Roundup][Appendix 7]" in the appendix of this book. Here you will find recommendations for web safe fonts, i.e. fonts that come preinstalled in most systems that you can copy and feel confident using as either your overall default font stack, or as a fallback font stack for a more interesting typeface. The roundup also includes fonts that go well together, say one font for your headers, and another contrasting font for your body.


[Build better CSS font stacks][Font Stacks]
[CSS Web Safe Font Combinations][Web Safe]
[Mobile Design Typography is Vitally Important ... and Challenging][Mobile typography]

#### Size and Color



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


#### Images and Icon Sprites


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
