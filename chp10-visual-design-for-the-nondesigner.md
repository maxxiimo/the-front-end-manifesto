Visual Design for the Nondesigner
=================================

In the [last chapter][Chapter 9] our focus was Information Architecture, and in that chapter I emphasized storytelling while purposefully deemphasizing design. Here is why:

> Firstly, think about what your pages do, not what they look like. Let your design flow from the services which they will provide to your users, rather than from some overarching idea of what you want pages to look like. Let form follow function, rather than trying to take a particular design and make it "work".

\- [A Dao of Web Design][Dao] by John Allsopp

By starting with information architecture before design we put functionality and content first, as it should be, and now it's time to design. Like blocks of information in the previous chapter, [design is part of storytelling][Story Design], and must communicate the websites story.

The combination of:

- branding
- harmony
- icons
- images
- typography ([Chapter 11][])
- color ([Chapter 12][])
- embellishments ([Chapter 13][])

...are the largest contributors to a sites look and feel. In this chapter we explore the first four items on the list, but first let me make an observation relevant to your role as a front end engineer and design.

Paradigm Shift
--------------

Over the last several years I've noticed a paradigm shift in the role that front end engineers play in the design process. Back in the day for really great design you absolutely needed a Graphic Designer. Unless you could work Adobe Photoshop or Adobe Illustrator like there was no tomorrow, Graphic Designers were the ones who produced rounded corners, cool fonts, gradients, translucent images, buttons, icons, icon sprites, etc.. In addition to required design elements, Graphic Designers created visual mockups of a website that non-coding stakeholders could "touch and feel", i.e. actually see and understand.

Discussion and changes could then be made around these mockups before any engineering costs were incurred; it was more efficient and cost-effective to do it this way. As a result decision-makers would gravitate towards brainstorming on usability, architecting, and the design aspects of a project at the graphic design phase in the development process: that began and oftentimes ended before front end engineers were really involved.

Back then that kind of made sense, it was a simpler world, one design could almost fit all, and things happening in the browser were not as super interactive as they are today. Consequently, front end developers found the bulk of their contribution to a project in implementing completed mockups: They understood what kind of code the backend team needed and how they would use it, and they had the skills necessary to turn graphic design into pixel perfect – the standard of excellence back then – cross browser friendly code.

Fast-forward to today and everything has changed:

- HTML5 and CSS3 have made it possible – preferable – to produce design elements directly in the browser as code rather than images.
- It is increasingly more efficient to produce dynamic and responsive prototypes with the benefits of CSS3, rather than static mockups.
- Much of what is happening on the front end cannot be easily replicated in a static mockup.
- Prototyping by nature is more representative of how a webpage will ultimately look and behave across different devices.
- Users can instantly access and interact with a prototype, not with a mockup.
- One size no longer fits all. Technologies and devices are rapidly changing.
- Understanding the resulting capabilities and/or limitations of browsers and devices in a constantly evolving landscape is not a luxury but a necessity, and an area of expertise more often than not found with front end engineers.

As a result of these changes; usability, architecting and design decisions are beginning to convalesce around the point in which front end code is written, prototyping, as opposed to around graphic design mockups. Design elements feed into prototyping, and are necessary, but today, the absence of front end developers in the design process is no longer an option.

The end result of the paradigm shift for the design and development process is a more rapid, iterative, interactive, and [agile design process][].

The takeaway in relation to this chapter is that as front end engineers you need to understand that your role is changing. With the abilities of CSS3, think of yourself as a coder and an artist. You are the handshake between design and backend engineering and can work in either realm. With this new role, in addition to coding prowess, understanding the elements of good design, the art, is essential to the success of projects you will participate in.

This and the next three chapters are written to help developers along this path, but before exploring this art let me leave you with one final thought: never undervalue the hard earned design talents of graphic designers. Beautiful design is not easy.

Branding
--------

If ever there were an area in your design that could really use the help of a graphic designer, it's branding. A companies identity can radiate from it's [brand][], and brands can become so well-known that they become [memes][].

A company's logo is more often than not the cornerstone of a company's brand, and as you probably guessed, prominent on a webpage.

- [Beautiful and Simple Logos for your Delight][Inspiring Logos]

9 times out of 10 the companies you work for already have a logo, but in the 10th case, like developing a logo for View Thought, you will need to create something.

If you find yourself in this situation, like I am right now, the approach I recommend is to keep it really simple. Take for example the following [companies][Fresh Tilled Soil] brand/logo:
<br>
<br>
![][Fresh]
<br>
<br>
<br>
It's just stylized text, and I like it. If I do this for View Thought all that's really left for me to do is find the right typeface for my logo.

In the next chapter we're going to thoroughly explore typography, and jumping ahead, based on the teachings of that Chapter 11 I chose the following typeface for View Thoughts logo:

- [Quatro Sans][]

  > We are pleased to introduce you to Quatro Sans. An undeniably modern typeface with construction principles that attempt to find the balance between machine and hand.

I chose this typeface because we're building things at View Thought, and to me this font captures that feeling. My inspiration for this logo came from an [article][] I read. With that typeface in hand, and using the techniques in the article, I created the following simple logo:

![][Logo]

Nice!

Modular Scales
--------------

With a logo out of the way, the next major design element I recommend you tackle before doing anything else is create a modular scale.

***What is it?***

A modular scale is a scale based on ratios derived from harmonic intervals or the proportions of the [golden ratio][].

In layman's terms this means that the measurements of the scale are related to one another in an artistic/design awesome way, and when you use numbers from the scale for line length, column widths, line heights, and pretty much anything in your website that requires a measurement, you pass on this design awesomeness (versus picking random unrelated numbers). In the very least, you are making a design informed decision!

***What does a modular scale look like?***

Here is the modular scale I will use for all measurements moving forward:

- [View Thought's Modular Scale][scale]

***How do you create one?***

To create this I used a [Modular Scale][] tool. The tool requests three variables. Here is what I input into it to generate my scale:

- Our base font size of 16 pixels
- Our logo font size of 30 pixels
- The Golden ratio – I decided to go with a classic base ratio

Modular skills is a subject worth researching. I think it makes a huge difference in your design, as a whole harmonious creation. If you're interested in learning more, take a look at the following resources:

- [Tim Brown - More Perfect Typography][Perfect Typography] (Go to minute 15:00, great talk.)
- Articles 10, 11, and 12 in Appendix 11, [A Brief History of Web Font Sizes][Appendix 11]

***Now what I do with my scale?***

Once created, use only the numbers defined in the scale for measurements throughout your application, like font sizes, margins, paddings, column widths, etc.. After creating mine I went through the application and converted every single number to a number in the scale. Every single number!

Having said that, before applying your scale to your project its important to keep this in mind:

> Modular scales are a tool, they’re not magic. They’re not going to work for every measurement, and that’s okay. Math is no substitute for an experienced designer’s eye, but it can provide both hints and constraints for decision making. Consider the scale’s numbers educated suggestions. Round them if you like (22.162 becomes 22). Combine them (3.56 + 16 = 19.56). Or as we saw me do here, break from the scale entirely.

\- [More Meaningful Typography][Meaningful Typography] by Tim Brown

NOTE: In the [_define.sass][] partial it's a good idea to comment on the source of your scale:

    /*  Modular Scale
      -----------------------

    // http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0

    // 16px  @ 1:1.618 - base font size
    // 30px  @ 1:1.618 - logo font size

Icons
-----

Icons give a website a really nice touch, and they pack a lot of design punch. You've heard the expression, "a picture says 1000 words." Icons instantly explain a great deal, and usually within a 16 pixel by 16 pixel area.

Developers used to use images for icons, but each image would require a trip out to the server which could slow down a pages rendering, especially for mobile. Then someone got smart and figured out that putting all the icons on a single image called an "image sprite" would save a website from all those trips to the server. A front end developer could then move that sprite around a tiny imaginary viewport using CSS and reveal only one of the icons through that space.

### Icon Fonts

Icon sprites are a great idea, but then something better came along, especially for mobile: icon fonts.

Regular letter fonts are glyphs. A glyph is a shape. A letters glyph is shaped in such a way that we see and interpret the glyph as a letter. Icon fonts use glyphs in the same way, but to create icon imagery. Just like a letter font, icon fonts can be easily rendered on a webpage, and their size can be increased and decreased without affecting their weight, unlike an image: The larger the image, the more it weighs. In fact, anything you can do with a font, you can do with an icon font.

For View Thought we're going to create the following icon fonts:

- Navigation

  ![][Icon Fonts 1]

- Social

  ![][Icon Fonts 2]

What follows are the steps you should take to create your own fonts, but first here are a few references that may interest you, or in the very least are good to have handy:

- [How to make your own icon webfont][DIY Icon Fonts]
- [HTML for Icon Font Usage][Icon Font HTML]
- [The Big List of Flat Icons & Icon Fonts][Big List]
- [Icomoon][]
- [We Love Icon Fonts][Love]
- [Getting Font-Face to work with the Asset Pipeline][Pipeline]
- [Testing @font-face Support on Mobile and Tablet][Icon Font Support]

### Creating Your Own Set

**Step 1**: Visit http://icomoon.io/app/ and select icons you wish to use. You can add more icon sets.

TIP: Load all the icon sets and search by keywords to compare across different sets, e.g. "social" for social icons.

**Step 2**: Review and configure your selected fonts.

NOTE: I generally keep the defaults but change the Preferences -> Font Name to "icon-fonts". Depending on the project needs you can change the encoding to: PUA (Private Use Area), Symbols, or Latin characters. My preference is for symbols. For my navigation font set, if for any reason the icons are not available, symbols will yield the following:

![][Symbols]

**Step 3**: Download your fonts. Copy the zipped folder `fonts` into your `app/asset/images` folder. Save the original in `vendor/source`.

**Step 4**: Create the HTML that will handle your new fonts, for example:

    %a{:href => "/", :title => 'Home'}
      %span{"aria-hidden" => "true", "data-icon" => "&#x2616;".html_safe}
      %span.screen-reader-text Home

Notice the Unicode value in the `data-icon` attribute? To find your Unicode values go back to your original download and open `index.html` in your browser. Also notice the `.html_safe ` method? This will ensure that the string is inserted unaltered into the output.

**Step 5**: Pull your fonts into your project through `_define.sass` through the following:

    // icon fonts...

    @font-face
      font-family: 'icon-fonts'
      font-weight: normal
      font-style: normal
      src: font-url('icon-fonts.eot')
      src: font-url('icon-fonts.eot?#iefix') format("embedded-opentype"), font-url('icon-fonts.svg#icon-fonts') format("svg"), font-url('icon-fonts.woff') format("woff"), font-url('icon-fonts.ttf') format("truetype")

**Step 6**: Create the styles necessary to use your new font. Add the following styles mixin to `_mixin.sass`:

    /*  Icon Fonts
      -----------------------

    @mixin data-icon
      font-family: 'icon-fonts'
      content: attr(data-icon)
      speak: none
      font-weight: normal
      line-height: 1
      -webkit-font-smoothing: antialiased

Already defined in `_misc.sass`:

    .screen-reader-text
      position: absolute
      top: -9999px
      left: -9999px

Call your new mixin were needed as follows:

    [data-icon]:before
      +data-icon

For example if needed in your footer:

    footer
      [data-icon]:before
        +data-icon

### Icon Fonts To Play With

After completing the creation steps I now have the following fonts to play with:

![][Collection]

This is a nice collection to work with and these icons will definitely add a needed design touch to View Thought. When I finalize on the design, I'll remove the icons I didn't use to save bandwidth. You can do this by regenerating your font library following the steps above.

### Icon Sprites

If you haven't guessed already, like regular fonts, icon fonts are not multicolor, and do not provide the full design possibilities found in image-based icons:

![][Icon Sample]

When using icons, it's best to save them in a single sprite. You can do this manually or you can let [Compass][Compass Sprites] do all the sprite creation work for you.

NOTE: Ryan Bates provides an excellent tutorial on this called [Compass & CSS Sprites][Sprites].

If you do decide to create icon sprites manually, and I'm not sure exactly why you would (hint, hint), when you lay out your icons it's better on the implementation side of things to have them line up horizontally (as opposed to vertically):

![][Icon Slider]

Right align your icons and place each icons top edge on an equidistant grid line whose coordinate is a multiple of 5 pixels. For example, the horizontal grid line coordinates for 4 icons that are 16px x 16px might be:

0 (first image)<br>
20px<br>
40px<br>
60px

Using multiples of five makes it easier to find the Y coordinate in the CSS positioning property later on. The CSS positioning XY values for the above are:

0, 0<br>
0, -20px<br>
0, -40px<br>
0, -60px

Experience has also shown me that having extra pixels of blankness between icons can be beneficial. For example, if icons are 32px x 32px, >40 pixel gridlines would be good:

![][Icon Grid]

Save your icon sprites as .gif's and .png's. .jpg's are really reserved for photos and not efficient for things like this, plus they do not preserve alpha transparencies which become an issue if backgrounds change in the future (kind of following in a roundabout way the old adage; "measure twice, cut once.").

Images
------

Just like with icons, images pack a lot of design punch. People are also much more responsive to pictures, especially of faces. In eye tracking studies I have participated in, users gravitated  heaviest on people's faces.


[20 Examples of Effective Image Usage in Web Design][Effective Image Use]
[21 Inspiring Examples of Big Images in Web Design][Big Images]
[19 Inspiring Examples of Text Over Images in Web Design][Text Over Images]


[jQuery Anystretch][]
[Backstretch][]
[Vegas Background jQuery Plugin][Vegas]

![][Silhouette]

Buttons
-------

A good-looking button adds a lot of pizzazz to a website, and can scream; "click me!" It's a look and feel element that I know will be needed in almost any project I'm a part of. Basically, if it has a form it has a button. Knowing this I like to get the mechanics of my buttons of the way from the get-go, not necessarily the button style, but how I will create the buttons.

There are two great compass plug-in resources available for creating good-looking cross browser buttons:

- [Sassy Buttons][]
- [Fancy Buttons][]

### Button Set Up

 I have no particular preference between the two, so whichever you choose to use, this is how to install either:

**Step 1**: Add the gem 'fancy-buttons' or gem 'sassy-buttons' to the assets group of your gemfile:

    group :assets do
      gem 'sass-rails', '3.2.5'
      gem 'coffee-rails', '3.2.2'
      gem 'uglifier', '1.2.3'

      # Compass specific gems.
      gem 'compass-rails'
      gem 'oily_png'
      gem 'susy'
      gem 'fancy-buttons'
      gem 'sassy-buttons'
    end

**Step 2**: Import it, preferably from application.css.scss per the CSS Organization chapter:

    /* FORMS
      ============================================================================ */
    @import "fancy-buttons";
    @import "sassy-buttons";
    @import "desktop/forms";

IMPORTANT: Make sure your import appears before wherever you include the button mixin, otherwise you will get an error. In my case the mixin was found in "forms", and I made the mistake of placing my import below @import "forms". I was scratching my head for an hour before I realized the stupid mistake!

**Step 3**: `bundle install`

**Step 4**: Install your button plug-ins assets:

    bundle exec compass install fancy-buttons

    or

    bundle exec compass install sassy-buttons

**Step 5**: Include the most basic mixin and expand from there:

    button
      +fancy-button or
      +sassy-button

    alternatively (syntax)...

    button
      @include fancy-button or
      @include +sassy-button

I used sassy buttons for View Thought, and here is what they look like:

![][Button 1]
![][Button 2]

Other Resources
---------------

[6 jQuery Plugins for Scrolling Effects][6 Plugins]


[CSS Triangle][]
[The Shapes of CSS][CSS Shapes]
[Triangle With Shadow][]


The devil is in the details. It's the little things, the details, that make a design come to life. What kind of things? Maybe a gradient between panels, or a simple border. The best way to find design detail inspiration is by visiting websites you like or are renowned for good design. Look at the underlying code and learn the techniques used to implement the design detail. Once you understand the technique, you can apply it to your own creation in a new and unique way.

One thing I like to do is browse websites that have inspired me, and when I see an element that I like I snap a screenshot of it and name the file the domain name I snapped it from. Later on I can review all of my snapshots and decide if I'm interested in applying a similar technique to my design.

[20 Single Page Web Designs to Inspire You][Single Page]

- Reverse engineer pieces of things you already like.

http://patterntap.com/?sort_by=created&type=23047&style=All&platform=All&page=1
http://patterntap.com/pattern/quote-sumail

What follows are some ideas and resources to help you create your site's look and feel:

- Use a framework. We listed several frameworks you can use in the [Frameworks][Appendix 1] section of the Appendices.


- Hire a graphic designer. With your layout organized via our wireframe work in the last chapter, half of the designers work is done. Now he or she needs to pull it all together with a stellar look and feel. When hiring a designer, make sure you let them know that the layout you have in place is not set in stone, this way your designer can add their experience to the project.

  Here are some resources for finding graphic designers:

  - XXX

[PSD Freebies][]

- Get a freebie and port it over to your application.

  - [Premium Pixels][]

- Buy a template. Templates are significantly less expensive than hiring a graphic designer. As a front end coder implementing them into your layout should be a breeze. Here are some template resources:

  - [Premium Web UI Kits][Designmodo]
  - [ThemeTrust][]

http://www.squarespace.com/templates/

- Read a tutorial.

http://css-tricks.com/triangle-with-shadow/

  - [How to Nail the Coveted Flat Design Look (9 Actionable Tips)][Flat Design]
  - [Jazz up a Static Webpage with Subtle Parallax][Jazzy Parallax]
  - [Web 2.0 Tutorials Round-Up][Web 2.0]

[Chapter 9]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp9-information-architecting.md#information-architecting
[Chapter 10]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#visual-design-for-the-nondesigner
[Chapter 11]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp11-typography.md#typography
[Chapter 12]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp12-the-color-palette.md#the-color-palette
[Chapter 13]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp13-embellishments.md#embellishments
[Appendix 1]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-1
[Appendix 11]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-11

[Dao]:                  http://www.alistapart.com/articles/dao
[Story Design]:         http://24ways.org/2011/design-the-invisible/

[agile design process]: http://webdesignledger.com/tips/applying-agile-principles-to-design

[brand]:                http://en.wikipedia.org/wiki/Brand
[memes]:                http://en.wikipedia.org/wiki/Meme
[Fresh Tilled Soil]:    http://www.freshtilledsoil.com
[Quatro Sans]:          http://cargocollective.com/pstype/Quatro-Sans
[article]:              http://blog.typekit.com/2011/03/24/type-study-choosing-fallback-fonts/
[Inspiring Logos]:      http://webdesignledger.com/inspiration/beautiful-and-simple-logos-for-your-delight

[golden ratio]:         http://en.wikipedia.org/wiki/Golden_ratio
[scale]:                http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0
[Modular Scale]:        http://modularscale.com/
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/app/assets/stylesheets/_define.sass
[Perfect Typography]:   http://vimeo.com/17079380
[Sassy Modular Scale]:  https://github.com/Team-Sass/modular-scale
[Meaningful Typography]: http://alistapart.com/article/more-meaningful-typography

[DIY Icon Fonts]:       http://www.webdesignerdepot.com/2012/01/how-to-make-your-own-icon-webfont/
[Icon Font HTML]:       http://css-tricks.com/html-for-icon-font-usage/
[Icomoon]:              http://icomoon.io
[Love]:                 http://weloveiconfonts.com/
[Big List]:             http://css-tricks.com/flat-icons-icon-fonts/
[Pipeline]:             http://myrailslearnings.wordpress.com/2012/05/01/getting-font-face-to-work-with-the-asset-pipeline/
[Icon Font Support]:    http://blog.kaelig.fr/post/33373448491/testing-font-face-support-on-mobile-and-tablet
[Sprites]:              http://railscasts.com/episodes/334-compass-css-sprites
[Compass Sprites]:      http://compass-style.org/help/tutorials/spriting/

[Effective Image Use]:  http://webdesignledger.com/inspiration/20-examples-of-effective-image-usage-in-web-design
[Big Images]:           http://webdesignledger.com/inspiration/21-inspiring-examples-of-big-images-in-web-design
[Text Over Images]:     http://webdesignledger.com/inspiration/19-inspiring-examples-of-text-over-images-in-web-design
[jQuery Anystretch]:    https://github.com/danmillar/jquery-anystretch
[Backstretch]:          http://srobbin.com/jquery-plugins/backstretch/
[Vegas]:                http://vegas.jaysalvat.com/

[Sassy Buttons]:        http://jaredhardy.com/sassy-buttons/
[Fancy Buttons]:        http://brandonmathis.com/projects/fancy-buttons/
[6 Plugins]:            http://webdesignledger.com/tools/6-jquery-plugins-for-scrolling-effects
[CSS Triangle]:         http://css-tricks.com/snippets/css/css-triangle/
[CSS Shapes]:           http://css-tricks.com/examples/ShapesOfCSS/
[Triangle With Shadow]: http://css-tricks.com/triangle-with-shadow/

[Single Page]:          http://webdesignledger.com/inspiration/20-single-page-designs-to-inspire-you
[PSD Freebies]:         http://www.bestpsdfreebies.com/
[Premium Pixels]:       http://www.premiumpixels.com/
[Designmodo]:           http://designmodo.com/shop/
[ThemeTrust]:           http://themetrust.com/themes
[Flat Design]:          http://psd.fanextra.com/articles/flat-design-trend/
[Jazzy Parallax]:       http://webdesign.tutsplus.com/tutorials/htmlcss-tutorials/jazz-up-a-static-webpage-with-subtle-parallax/
[Web 2.0]:              http://www.smashingmagazine.com/2007/03/10/web-20-tutorials-round-up/

[Fresh]:                http://www.chrismaxwell.com/manifesto/chp-10/fresh-tilled-soil.gif
[Logo]:                 http://www.chrismaxwell.com/manifesto/chp-10/viewthought-logo.gif
[Icon Fonts 1]:         http://www.chrismaxwell.com/manifesto/chp-10/icon-font-nav.gif
[Icon Fonts 2]:         http://www.chrismaxwell.com/manifesto/chp-10/icon-font-social.gif
[Symbols]:              http://www.chrismaxwell.com/manifesto/chp-10/symbols.gif
[Collection]:           http://www.chrismaxwell.com/manifesto/chp-10/collection.gif
[Icon Sample]:          http://www.chrismaxwell.com/manifesto/chp-10/30-toolbar-icons.jpg
[Icon Slider]:          http://www.chrismaxwell.com/manifesto/chp-10/icon-slider.png
[Icon Grid]:            http://www.chrismaxwell.com/manifesto/chp-10/icon-grid.gif
[Silhouette]:           http://www.chrismaxwell.com/manifesto/chp-10/silhouette-files-icons.gif
[Button 1]:             http://www.chrismaxwell.com/manifesto/chp-10/button-3.gif
[Button 2]:             http://www.chrismaxwell.com/manifesto/chp-10/button-4.gif
