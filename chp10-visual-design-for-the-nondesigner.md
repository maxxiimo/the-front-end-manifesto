Visual Design for the Nondesigner
=================================

In the [last chapter][Chapter 9] our focus was Information Architecture, and in that chapter I emphasized storytelling while purposefully deemphasizing design. Here is why:

> Firstly, think about what your pages do, not what they look like. Let your design flow from the services which they will provide to your users, rather than from some overarching idea of what you want pages to look like. Let form follow function, rather than trying to take a particular design and make it "work".

\- [A Dao of Web Design][Dao] by John Allsopp

[Design is part of storytelling][Story Design] and like blocks of information in the previous chapter, the visual design must also communicate the websites story, and do so in such a way that the user just gets it.

The combination of typography, color, branding, images, and icons will help communicate a storyline, and are a major contributor to a sites look and feel. We will explore each of these elements in this chapter, but first let me make an observation relevant to your role as a front end engineer and design.

Paradigm Shift
--------------

Over the last several years I've noticed a paradigm shift in the role that front end engineers play in the design process. Back in the day for really great design you absolutely needed a Graphic Designer; unless you could work Adobe Photoshop or Adobe Illustrator like there was no tomorrow. Graphic Designers were the ones who produced rounded corners, cool fonts, gradients, translucent images, buttons, icons, icon sprites, etc.. In addition to required design elements, Graphic Designers created visual mockups of a website that non-coding stakeholders could "touch and feel", i.e. actually see and understand.

Discussion and changes could be made around these mockups before any engineering costs were incurred, consequently, it was more efficient to mock up a website before coding. As a result decision-makers would gravitate towards brainstorming on usability, architecting, and design aspects of a project at the graphic design phase in the development process: that began and oftentimes ended before front end engineers were really involved.

Back then that kind of made sense, it was a simpler world, one design could almost fit all, and most things that happened in the browser could be replicated in a mockup, and so front end developers found the bulk of their contribution to a project in implementing completed mockups. They understood what kind of code the backend team needed and how they would use it, and they had the skills necessary to turn graphic design into pixel perfect – the standard of excellence back then – cross browser friendly code.

NOTE: Chapter 11, [Slicing and Dicing Mockups][Chapter 11], will dive into the mechanics of doing exactly that.

Fast-forward to today and everything has changed:

- HTML5 and CSS3 have made it possible – preferable – to produce design elements directly in the browser.
- It is increasingly more efficient to produce dynamic and responsive prototypes with the benefits of CSS3, rather than static mockups.
- Much of what is happening on the front end cannot be easily replicated in a static mockup.
- Prototyping by nature is more representative of how a webpage will ultimately look and behave across different devices.
- Prototyping allows for a more rapid, iterative, interactive, and agile design process.
- One size no longer fits all. Technologies and devices are rapidly changing. Understanding the resulting capabilities and/or limitations of browsers and devices used by end-users in a constantly evolving landscape is a necessity, not a luxury, and an area of expertise belonging to front end engineers.

As a result of these changes; usability, architecting and design decisions are beginning to convalesce around the point in which front end code is written, prototyping, as opposed to around graphic design mockups. In the very least, the absence of front end developers in the design process is no longer an option.

The takeaway in relation to this chapter is that as front end engineers we need to understand that our roles are changing. Don't for a moment think that creative license on the front end belongs only to designers. It does not, in fact with the abilities of CSS3, much of the design work can now occur in the browser straight from our IDE's. Think of yourself as artists of a new age; you are the handshake between design and backend engineering and can work in either realm. With this new role, in addition to coding prowess, understanding the elements of a good design, the art, is essential to the success of projects you will participate in.

This chapter is written to help developers along this path. With that lets get started, but first let me leave you with one final thought: never undervalue the hard earned design talents of graphic designers.

Branding
--------



Typography
----------

> 95% of the information on the web is written language. It is only logical to say that a web designer should get good training in the main discipline of shaping written information, in other words: Typography.

\- [Web Design Is 95% Typography][95% typography]

The first visual design component I like to tackle is [typography][]. The lowest hanging fruit in typography are typefaces:

- Font Family
- Font Size
- Readability

Using the base styles from [Chapter 3][] these typographic elements are predefined and available to you to experiment with through the [_define.sass][] sass partial:

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

    $pt-serif:          "PT Serif", serif

    $droid-serif:       "Droid Serif", Georgia, Times, serif
    $droid-sans:        "Droid Sans", Helvetica, Arial, sans-serif

    // base definitions...

    $base-font-family:  $droid-sans       !default
    $base-font-size:    100%              !default
    $base-line-height:  1.4               !default

    $base-font-header:  $droid-serif      !default
    $base-font-nav:     $droid-serif      !default

    // non-google web fonts alternativ:
    // $base-font-header:  $arial         !default
    // $base-font-header:  $georgia       !default
    // $base-font-nav:     $georgia       !default

This partial is reserved for defining global stylesheet variables, and begins with variables set to different font stacks. In Sass, variables can also be set to other variables and so variables like `$base-font-family`, the key to our application fonts, references one of the different predefined font stack like `$droid-sans`. `$base-font-family` in turn is referenced by the `<body>` tags `font-family` property and will propagate throughout the entire application by virtue of CSS inheritance. You can experiment with the predefined fonts included in [_define.sass][] by changing the variables that the base definitions point to.

Over the next several sections we will explore the basic building blocks of typography and how it is implemented in our application. As a side note, if you really want to learn more, the most highly acclaimed resource out there is:

- [The Elements of Typographic Style Applied to the Web][Typographic Style]

Font Family
-----------

When choosing a font family for a project you can try some of the fonts predefined in [_define.sass][] or try something else. To help you select an alternative I created a quick reference "[Font Stacks Roundup][Appendix 8]" located in the Appendices of this book.

When choosing a font family for a project try following these steps:

### Step 1: Define Adjectives

> Write down a general description of the qualities of the message you are trying to convey, and then look for typefaces that embody those qualities.

\- Tim Brown quoting Jason Santa Maria in [More Perfect Typography][Perfect Typography]

...According to Tim Brown, the Type Manager for Adobe Typekit, he always begins a project this way. He starts with body text, "which gives tone for a piece," then moves on to markers like headers, "that give it personality and character."

The article, "[A Brief Primer on Typeface Selection][Brief Primer]," echoes the same idea:

> Read your content to determine the mood it conveys. Describe this mood using a list of adjectives. Find typefaces that you feel are accurately described by these adjectives. Essentially, you want to ensure that your typeface conveys the appropriate feeling.

What adjectives describe View Thought? To start, let's revisit the storyline:

> We are a great website design, development and user experience shop. We have tons of experience, have worked with a bunch of different clients who are all happy with our work, and we really care about what we do. We specialize in Ruby on Rails, and we pay special attention to what your users will see. You should hire us! ...or give us a call and learn more.

That is the message, and here are some adjectives that help communicate the mood and qualities of the message:

1.  Clean
2.  Reliable
3.  Artistic
4.  Appealing
5.  Youthful
6.  Competent
7.  Knowledgeable
8.  Trustworthy
9.  Cutting Edge
10. Innovative
11. Fun
12. Steadfast
13. Friendly

NOTE: I recommend listening to Jason Santa Maria's presentation "[On Web Typography][]". He gives excellent advice on picking typefaces (starting at minute 31:45). You can find this advice transcribed in [Appendix 10][Appendix 10].

### Step 2: Use a Font Service

Using a font service to browse available fonts and deliver those fonts is a good idea. Font services eliminate the licensing headaches one might encounter with creative works, and also provides a CDN to efficiently serve fonts from. Some services are subscription based and others are free. I have listed a few in the "[Font Services and Tools][Appendix 9]" appendix.

My preferred service is [Typekit][]. They provides an excellent [series of articles][articles] on implementing Typekit: [[I'll][]] [[spare][]] [[you][]] [[the][]] [[details][]].

Typekit is a paid service, [Google Web Fonts][] on the other hand is a free service:

- [A Beginner’s Guide to Using Google Web Fonts][Beginners Guide]

### Step 3: Pair Typefaces

> You might have already heard this; successful pairing relies on concord, or contrast, but not conflict. That is to say your selected fonts can work well together by sharing certain qualities, or by being completely different from one another. However, font pairs can conflict in a number of ways – being too similar being just one.

\- [A Beginner’s Guide to Pairing Fonts][Beginners Guide]

When selecting font families I recommend reviewing the [Combinations][Appendix 8 Combos] section of Appendix 8. Here designers with substantial typographic knowledge and experience have paired fonts, described their personalities or feel, and provide samples to review and choose from.

A few Google Web Fonts pairing ideas derived from articles in Appendix 8 can be found in the starter styles:

- [_define.sass][]
- [_head.html.haml][]

### Step 4: Choose a Typeface

Finally, choose a typeface and give it a test drive. Here are some screenshots of different font ideas for View Thought:
<br>
<br>
<br>
![][Fonts]
<br>
<br>
As you can see, choosing fonts is a practice in trial and error. To help you frame the context of your decision making process take a look at the section entitled "[Choosing Typeface Articles][Appendix 10]" in Appendix 10.

For View Thought I chose three fonts from Typekit:

- [Quatro Sans][] for the logo. We're building things at View Thought in this font captures that feeling.

  > We are pleased to introduce you to Quatro Sans. An undeniably modern typeface with construction principles that attempt to find the balance between machine and hand.

- [Rooney Web][] for the body text. I wanted to use a serif font and Rooney seemed to embody the right combination of serious and fun that I was looking for.

  > Rooney feels serious yet its rounded shapes and soft curves make for an overall impression of warmth and smoothness.

- [CamingoDos Web][] for our headers and navigation. Oftentimes choosing fonts from the same foundry produces the best combinations. I wanted to use a sans-serif and Rooney Sans Web was nice, but CamingoDos felt right.

  > CamingoDos Web is tailored for use on websites. The fonts are manually hinted for optimal on-screen reading, providing a good performance across different operating systems and browsers.

### Step 5: Define Fallbacks (Font Stacks)

Finally, once you choose your fonts it's good practice to also define fallback fonts. Together your chosen font and its fallbacks are a "font stack". For example:

    "rooney-web", Georgia, Palatino, "Palatino Linotype", Times, "Times New Roman", serif

The desired font is rooney-web, but if it is not available on the system the website is served to, the browser will try to use the next font in the stack, and so forth until the very last font: which is a [generic font][] and the most broadly available across different operating systems. All the fonts in the stack are similar enough that they can be interchanged with minimal differences between fonts used (at least that is the goal).

A good source for font stacks can be found in the appendices:

- [Font Stack Roundup][]

For a list of preinstalled fonts checkkout:

- [Complete Guide to Pre-Installed Fonts in Linux, Mac, and Windows][Complete Guide]

Font Size
---------

Now that we have selected a font family, we need to set a base font size. Choosing font size is actually an important decision. Your choice will become the measurement from which the entire site is responsive to.

First, choose a unit of measurement: `px` vs. `em` vs. `%` vs. `pt` vs `rem`.

In our starter code we use `%` to establish a baseline, and `em` to set font sizes for elements throughout the project.

NOTE: If you're interested in the research for this basis to start from take a look at "[A Brief History of Web Font Sizes][Appendix 11]" in the appendices.

### Base Font Size

In Chapter 3 we [implemented Normalize.css][Resets]. In [Normalize][implementation] the base font size is set to 100%:

    /*
    * 1. Corrects text resizing oddly in IE 6/7 when body `font-size` is set using
    * `em` units.
    * 2. Prevents iOS text size adjust after orientation change, without disabling
    * user zoom.
    */

    html {
        font-size: 100%; /* 1 */
        -webkit-text-size-adjust: 100%; /* 2 */
        -ms-text-size-adjust: 100%; /* 2 */
    }

As a rule of thumb, browsers typically default to a font size of 16 pixels. We're going to accept this default font size, and will not override Normalize, however, through the `<body>` tag we can:

app\assets\stylesheets\desktop\_layout.sass

    body
      margin: 0 auto
      width: 960px
      font-size: $base-font-size
      line-height: $base-line-height
      background-color: $bg-body

app\assets\stylesheets\_define.sass

    $base-font-size:    100%         !default

### Using Em's

To affect font size for individual elements use em's. Em's are a scalable unit relative to the parent font size. In other words, if the parents font size changes, the children's font sizes will also change, proportionally.

With our settings:

1em = default browser font size = typically 16px

Here's a practical example. If you would like to double an elements size compared to the base font, let's say for a header, set its `font-size` property to `2em` (2 x 16px = 32px).

NOTE: It's important to keep in mind that em's are relative to the parent, and not the browser or `<body>` font size.

For more details on using em's take a look at:

- [Ideal line length for content][Ideal Line Length]
- [CSS Font-Size: em vs. px vs. pt vs. percent][CSS Font-Size]
- [How we learned to leave default font-size alone and embrace the em][Embracing em's]

Modular Scales
--------------

A modular scale is a scale based on ratios derived from harmonic intervals or the [golden ratio][]. In layman's terms this means that the measurements of the scale are related to one another in an artistic/design awesome way, and when you use numbers from the scale for line length, column widths, line heights, and pretty much anything in your website that requires a measurement, you pass on this design awesomeness (versus picking random unrelated numbers), or in the very least you are making a design informed decision!

What does a modular skill look like? Here is an example:

- [View Thought's Modular Scale][scale]

For View Thought I used a [Modular Scale][] tool, and input the following:

- Our base font size of 16 pixels
- Our logo font size of 30 pixels
- The Golden ratio

Once created, in the [_define.sass][] partial take note of the source of your scale as follows:

    /*  Modular Scale
      -----------------------

    // http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0

    // 16px  @ 1:1.618 - base font size
    // 30px  @ 1:1.618 - logo font size

There are some great references out there that will do a much better job of explaining the what's and how's of modular scales in case you're interested:

- [Tim Brown - More Perfect Typography][Perfect Typography] (Go to minute 15:00, great talk.)
- Articles 10, 11, and 12 in Appendix 11, [A Brief History of Web Font Sizes][Appendix 11]

For the more adventurous take a look at [Sassy Modular Scale][].

Now that we have a scale we will use it throughout our design, but before applying it its important to keep this in mind:

> Modular scales are a tool, they’re not magic. They’re not going to work for every measurement, and that’s okay. Math is no substitute for an experienced designer’s eye, but it can provide both hints and constraints for decision making. Consider the scale’s numbers educated suggestions. Round them if you like (22.162 becomes 22). Combine them (3.56 + 16 = 19.56). Or as we saw me do here, break from the scale entirely.

\- [More Meaningful Typography][Meaningful Typography] by Tim Brown

Readability
-----------

Font family and size, line length and height (measure and leading), and font color and contrast are the main components of [readability][]. We've covered font family and size, now let's look at the rest.

### Line Length (Measure)

> Having the right amount of characters on each line is key to the readability of your text. It shouldn’t merely be your design that dictates the width of your text, it should also be a matter of legibility.

\- [Readability: the Optimal Line Length][Optimal] by Christian Holst

Good point! So what is the optimal character range for legibility? Christian Holst suggests 50 to 75 characters per line. Others recommend:

- > ...anywhere from 45–75 characters is considered acceptable.

  \- [Readability][readability] by Billy Whited

- > A general good rule of thumb is 2-3 alphabets in length, or 52-78 characters (including spaces).

  \- [Five simple steps to better typography][Better Typography] by Mark Boulton

For View Thought we will use 45 to 75 characters per line, and now need to figure out the minimum and maximum number of columns that our text should flow on since we are using [Susy][Chapter 7]. There are two ways to do this, the easy way and the hard way.

Which reminds me, before we move forward we should apply our new modular scale to our Susy columns:

    $total-columns:     4;
    $column-width:      4.236em;
    $gutter-width:      1em;
    $grid-padding:      $gutter-width;

#### The Easy Way

The easy way is basic trial and error: count the characters flowing across sections of your content. If the line length falls outside the characters per line range you have chosen, change the number of columns for that section until the line length falls within your range. Simple as that.

Fortunately, there's a tool that will make counting characters super easy:

- [Count - an improved WC bookmarklet][Count]

#### The Hard Way

And now for the hard way, figuring out exactly what 45 to 75 characters means in em's and susy columns. To do so follow these steps:

**Step 1**: Take a sample and find the cutoff points.

For View Thought I'll take a sample of text directly off of our wireframe:

> Nothing beats the involvement of a well-seasoned, front-end developer that understands the semantics of what you're trying to pull off.

There are 116 characters in that sample, so what I need to do is find its 45 to 75 character cutoff points (excluding spaces). You can count characters manually, with a word processor, or use the count bookmarklet.

~45 characters:

Nothing beats the involvement of a well-seasoned,

~75 characters:

Nothing beats the involvement of a well-seasoned, front-end developer that understands

**Step 2**: Translate the cutoff points to widths in em's.

With the fonts and font size I have chosen and implemented, for this particular piece of text my measure should not cause the text to wrap before the "," after seasoned, or span longer than "understands":

Nothing beats the involvement of a well-seasoned, **&#124; 45 &#124;** front-end developer that understands **&#124; 75 &#124;** the semantics of what you're trying to pull off.

Knowing this about our sample we can translate this information into measurable units by manually increasing and decreasing the sample texts containing elements width until we reach the cutoff points. I use Firebug to easily increase and decrease the width of my containing element and come up with the following two ranges: `28em` and `42em` – my minimum and maximum line lengths.

**Step 3**: Find the new widths in your scale.

Since neither measure is in my scale, I find the closest numbers: `29.03em` and `46.971em`

Need them to be even closer? You can add and subtract up to two numbers from the same scale, just comment your math:

    // 29.03-1
    28.03em

    // 46.971 - 4.909
    42.062em

Finally, translate these to the Minimum and maximum number of columns in our Susy grid. Keep in mind that a single column measures `4.236em` with a `1em` right margin on all columns except the last column. So in effect each call them you define is `5.236em` wide. Doing some simple math we figure out our column ranges:

28 / 5.236 = 5.348
42 / 5.236 = 8.021

Ther optimal number of columns for text in our design should never be less than 5 columns or more than 8 columns.

**Step 4**: Apply to your design.

Moving forward in my design I now have constraints I can keep an eye on when sizing columns in my layout. To ensure that I don't forget these constraint I add the following commented out note to [_define.sass][]:

    // line widths...

    // Minimum
    // 28em
    // 29.03-1 = 28.03em
    // 5 columns
    // 28 / 5.236 = 5.348

    // Maximum
    // 42em
    // 46.971 - 4.909 = 42.062em
    // 8 columns
    // 42 / 5.236 = 8.021

### Line Heigt (Leading)

For line height there are a couple key things to keep in mind. You will need more line height when:

1. Your lines are longer – otherwise your readers might get lost
2. When you use a darker font color – so that you do not to overwhelm the rest of the site

For our site we're going to pick a number from our scale. After some trial and error, 1.618 seems to be the best line height:

    $base-line-height:  1.618         !default

The next natural step down in our scale is 1.159, which seems to be too much of a step down, so using another figure in our scale I calculate alternatives in case I need one, and include them in [_define.sass][]:

    $base-line-height:  1.618         !default

    // 1.618 - 0.105 = 1.513
    // 1.618 - 0.236 = 1.382
    // 1.618 - 0.382 = 1.236

### Color and Contrast

I read [somewhere][] that to make your text appear softer and still maintain a good contrast you shouldn't use pure black for your font color. Use something slightly lighter. The idea makes a lot of sense to me so we use the following defaults in our starter styles:

    $base-font-color:   #444         !default
    $base-header-color: #222         !default

Obviously, color is a significant factor in your design and not just in readability. Before we move on to the color palette, were going to take a quick detour to icons with an emphasis in icon fonts.

Icons
-----

Icons pack a lot of design punch. You've heard the expression, "a picture says 1000 words." Icons instantly explain a great deal, and usually within a 16 pixel by 16 pixel area. Back in the old days we used to use images for icons, but each image would require a trip out to the server which can slow down a pages rendering. Then someone got smart and figured out that putting all the icons on a single image called an "image sprite" would save a website from all those trips to the server.  A front end coder could then move that sprite around a tiny imaginary viewport using CSS and reveal only one of the icons through that space.

### Icon Fonts

Icon sprites was a great idea, and then came along icon fonts, and took over the world. Fonts or glyphs. A glyph is a shape. A letters glyph is shaped in such a way that we see and interpret it as a letter. Icon fonts use glyphs to create icon imagery, but just like a font, they can be easily rendered on a webpage. Their size can be increased and decreased without affecting their weight, unlike an image. The larger the image, the more it weighs. In fact anything you can do with a font, you can do with an icon font.

We're going to get right into implementing icon fonts, but before we begin, here are a few references that may interest you, or in the very least are good to have handy:

- [How to make your own icon webfont][DIY Icon Fonts]
- [HTML for Icon Font Usage][Icon Font HTML]
- [The Big List of Flat Icons & Icon Fonts][Big List]
- [Icomoon][]
- [We Love Icon Fonts][Love]
- [Getting Font-Face to work with the Asset Pipeline][Pipeline]
- [Testing @font-face Support on Mobile and Tablet][Icon Font Support]

#### Implementing Icon Fonts

**Step 1**: Visit http://icomoon.io/app/ and select icons you wish to use. You can add more icon sets.

NOTE: I generally load all the icon sets and search by keywords to compare across different sets, e.g. "social" for social icons.

**Step 2**: Review and configure your selected fonts.

NOTE: I generally keep the defaults but change the Preferences -> Font Name to "icon-fonts". You can also change the encoding – depending on the project – to PUA (Private Use Area), Symbols or Latin characters.

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

Call your new mixin were needed as follows:

    [data-icon]:before
      +data-icon

For example if needed in your footer:

    footer
      [data-icon]:before
        +data-icon

### Icon Sprites



The Color Palette
-----------------

> There are many contributing factors that go into making a good visual design, but one of the simplest ways to do this is through the use of colour. The colour palette used in a design can have such a profound effect on a visual design that it almost feels like you’re cheating. It’s easy to add more and more subtle shades of colour to add a sense of sophistication and complexity to a design, but it dilutes the overall visual impact. When I design, I almost have a rule that only allows me to use a very limited colour palette.

\- Mike Kus, "[Nine Things I've Learned][9 Things]"

So how do we begin to develop our own color palette? First, some background (for your reference). The following articles do an excellent job of defining the fundamentals of color theory, and the basic steps and components in building a color scheme:

- [Build a Color Scheme: The Fundamentals][Color Fundamentals]
- [Basic color schemes - Introduction to Color Theory][Color Theory]
- [Color Matters - Basic Color Theory][Color Matters]

The basic steps and components include:

1.  Selecting a base color while taking into account the effect colors have on our perceptions and feelings.
2.  Choosing color harmonies from the color wheel, i.e. what colors will work well together.
3.  Selecting the right tones, shades and tints for each color in the color scheme.

...But practically speaking, how do you begin?

### Step 1: Pick a Color

The first step in creating a color palette is to choose a base color. If you already have a logo to work with, the colors in the logo are good place to start from. Since I don't have a logo yet I'm going to borrow from a [technique][Adjectives] we used in the Font Family section of this chapter. Here is the list of adjectives used to choose a typeface:

1.  Clean
2.  Reliable
3.  Artistic
4.  Appealing
5.  Youthful
6.  Competent
7.  Knowledgeable
8.  Trustworthy
9.  Cutting Edge
10. Innovative
11. Fun
12. Steadfast
13. Friendly

Are there any colors that may help convey this? Reviewing the color descriptions in the following references:

- [The Meanings of Colors][] (MoC)
- [Build a Color Scheme: The Fundamentals][Color Fundamentals] (BaCS)
- [Color in Motion][] (CiM)

...I do come up with a few:

- **White** - This makes a lot of sense to me since we start our adjectives list with the word "Clean".

  > A white color scheme can represent cleanliness, purity, perfection and space...If you are looking for a clean design with plenty of negative space, play around with white more. - BaCS

- **Red** - As an overall base color I'm not sold on it for my purposes, but I do have some callout buttons so will keep this color in mind if it fits in my color wheel choice.

  > A red color scheme is bold, fiery, aggressive and screams for your attention...Red is a really powerful marketing color that can be used to grab the user’s attention and get them to click on an ad or register for a product. - BaCS

  > Red is the color of extremes. It’s the color of passionate love, seduction, violence, danger, anger, and adventure...Red captures attention. It is one of the most visible colors, second only to yellow... - MoC

  > Dynamic, vital, romantic, commanding, alert, rebellious, complementary, joyful, visible, hot, and fun. - CiM

- **Orange** - This might be the one. Aside from the fact that the parent company of View Thought uses it, it's feel seems to touch on a lot of the adjectives I have listed, plus it could be an alternative to red for callouts.

  > An orange color scheme speaks happiness...Orange is a very friendly color, a warm color that is inviting and can be another very effective color for call-to-actions. - BaCS

  > Orange is vibrant. It’s hot, healthy, fruity and engaging – but it can be abrasive and crass. It’s a polarizing color. People either love it or detest it. - MoC

  > Helpful, burning, cozy, abundant, warning, flavorful, festive, active, excited, communicative, and inspiring. - CiM

- **Green** - I'm liking this one insofar as it touches on trust and stability.

  > A green color scheme is peaceful and natural and is usually associated with growth, harmony, peace, strength and stability....it portrays a feeling of safety and trust... - BaCS

  > Green is no longer just a color. It's now the symbol of ecology and a verb. - MoC

  > Patient, natural, adventurous, relaxed, athletic, unfortunate, lucky, balanced, safe, and sharing. - CiM

- **Blue** - Well if this isn't the cats meow.

  > Blue means stability and depth and is a great color for creating a calm clean environment. Blue symbolizes confidence, faith, hope, wisdom, knowledge and trust. - BaCS

  > Blue is the favorite color of all people...Most blues convey a sense of trust, loyalty, cleanliness, and understanding. On the other hand, blue evolved as symbol of depression in American culture...Blue is the most commonly used color in corporate identity. - MoC

  > Technical, deep, free, educated, protective, lonely, peaceful, cold, clean, authoritative, and formal. - CiM

- **Yellow** - Creative is good, so is young, but coward... not liking that.

  > Creative, young, visible, right, cheerful, lightweight, curious, coward, playful, nutritious, ill, and expanding. - CiM

- **Purple** - Not quite the look I'm looking for.

  > Intelligent, artistic, aloof, luxurious, loyal, vain, fantastic, melancholic, feminine, fragrant, and solemn. - CiM

So based on this preliminary research, white, orange and blue are looking like very strong candidates for View Thought's color palette.

Once you have an idea about the colors you want to use, find their hex values. I like to use the tool [0to255][]. It gives you a lot of options in terms of shades. [216 Web Safe Colors][Web Safe] Possible candidate hex values for View Thought are:

- White: #ffffff
- Orange: #eb7e28

  ![][Orange]

  Or perhaps the parent companies shhade of orange: #f69233

- Blue: #4b99f9

  ![][Blue]

Let's bring these colors over to the color wheel.

### Step 2: Use the Color Wheel

> The human brain will reject under-stimulating information. At the other extreme is a visual experience that is so overdone, so chaotic that the viewer can't stand to look at it. The human brain rejects what it can not organize, what it can not understand. The visual task requires that we present a logical structure. Color harmony delivers visual interest and a sense of order.

\- [Color Matters - Basic Color Theory][Color Matters]

The color wheel is the basis from which our color choices will flow. It will help us find color harmonies based on color theory. It's important to get to know this tool.
<br>
<br>
<br>
![][Color Wheel]

Fortunately for us, there are a number of online color wheels we can use. There is a list of them in the [Color Wheels][] section of Appendix 12, but before we use one familiarize yourself with the different ways you can derive colors on the color wheel:

- [Analogous][]
- [Complementary][]
- [Triadic][]
- [Split-Complementary][]
- [Rectangle (Tetradic)][]
- [Square][]
- Monochromatic

I like to play around with a couple different color wheels:

- [Adobe Kuler][]

  ![][Kuler]

- [Color Wizard][]

  ![][Wizard]

With these tools you have a lot of color harmonies to play with.

### Step 3: Look at Alternatives

It's a good idea not to rely solely on the color wheel.

#### Find different shades of a color...

For example, there's a tool I like to use for finding different shades of a color:

- [Color Palette Creator][Palette Creator]

  ![][Shades]

#### Generated a color palette from an image...

I've also been considering using a hero image on our homepage. A color palette that matches that hero image might not be a bad idea. There are a [number of tools][] that will create a color palette based off of an image:

- [Color Palette Generator][]

  ![][Generator]

- [Pictaculous][]

  ![][Pictaculous Image]

#### Browse a color palette sharing service...

Finally, look at [color palettes created by the design community][Palettes]. You never know what you will find or be inspired by. Here are some of the palettes I have added to a "My Favorites" list in my favorite palette sharing service:

- [Adobe Kuler][Kuler]

  ![][Favorites]

I'm strongly considering the following palettes:

- https://kuler.adobe.com/Copy-of-Flat-UI-color-theme-2585872/

  ![][Palette 1]

- https://kuler.adobe.com/Black-%26-Orange-color-theme-2251290/

  ![][Palette 2]

- https://kuler.adobe.com/Nakamoto-color-theme-2532500/

  ![][Palette 3]

The last palette is a good example of finding inspiration from community palettes. Green was not at the top of my list, although I liked it.

### Step 4: Apply

> With colors you can set a mood, attract attention, or make a statement. You can use color to energize, or to cool down. By selecting the right color scheme, you can create an ambiance of elegance, warmth or tranquility, or you can convey an image of playful youthfulness. Color can be your most powerful design element if you learn to use it effectively.

\- [Basic color schemes - Introduction to Color Theory][Color Theory]


Appendix 5, [Inspirational Sites][]


Images
------



Other Resources
---------------

What follows are some ideas and resources to help you create your site's look and feel:

- Use a framework. We listed several frameworks you can use in the [Frameworks][Appendix 1] section of the Appendices.

- Reverse engineer pieces of things you already like.

- Find a plug-in.

- Hire a graphic designer. With your layout set via our wireframe work half of the designers work is done. Now he or she needs to pull it all together with a stellar look and feel. When hiring a designer, make sure you let them know that the layout you have in place is not set in stone. This way your designer can add their experience to the project. Here are some resources for finding graphic designers:

  - XXX

- Get a freebie and port it over to your application.

  - [Premium Pixels][]

- Buy a template. Templates are significantly less expensive than hiring a graphic designer. As a front end coder implementing them into your layout should be a breeze. Here are some template resources:

  - XXX

- Read a tutorial.

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md#foundation-styles
[Chapter 7]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-susy.md#susy
[Chapter 9]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp9-information-architecting.md#information-architecting
[Chapter 11]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp11-slicing-and-dicing-mockups.md#slicing-and-dicing-mockups
[Appendix 1]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-1
[Inspirational Sites]:  https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-5
[Appendix 8]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-8
[Appendix 8 Combos]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#combinations
[Appendix 9]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-9
[Appendix 10]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-10
[Appendix 11]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-11
[Appendix 12]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-12
[Color Wheels]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#color-wheels
[number of tools]:      https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#image-based-color-generators
[Palettes]:             https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#palettes

[Dao]:                  http://www.alistapart.com/articles/dao
[Story Design]:         http://24ways.org/2011/design-the-invisible/

[typography]:           http://blog.8thlight.com/billy-whited/2011/07/26/what-is-typography.html
[95% typography]:       http://informationarchitects.net/blog/the-web-is-all-about-typography-period/
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/app/assets/stylesheets/_define.sass
[Typographic Style]:    http://webtypography.net/

[Perfect Typography]:   http://vimeo.com/17079380
[Brief Primer]:         http://blog.8thlight.com/billy-whited/2011/08/25/a-brief-primer-on-typeface-selection.html
[On Web Typography]:    http://vimeo.com/34178417

[Typekit]:              https://typekit.com/
[articles]:             http://blog.typekit.com/category/font-events/
[I'll]:                 https://github.com/maxxiimo/viewthought/blob/master/app/views/layouts/_head.html.haml
[spare]:                https://github.com/maxxiimo/viewthought/blob/master/app/assets/javascripts/application.js
[you]:                  https://github.com/maxxiimo/viewthought/blob/master/app/assets/javascripts/site.js
[the]:                  https://github.com/maxxiimo/viewthought/blob/master/app/assets/stylesheets/_define.sass
[details]:              https://github.com/maxxiimo/viewthought/blob/master/app/assets/stylesheets/desktop/_typography.sass
[Google Web Fonts]:     http://www.google.com/webfonts#
[Beginners Guide]:      http://designshack.net/articles/css/a-beginners-guide-to-using-google-web-fonts/

[Beginners Guide]:      http://webdesign.tutsplus.com/articles/typography-articles/a-beginners-guide-to-pairing-fonts/
[_head.html.haml]:      https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_head.html.haml

[Quatro Sans]:          http://cargocollective.com/pstype/Quatro-Sans
[Rooney Web]:           http://www.janfromm.de/typefaces/rooney/overview/
[CamingoDos Web]:       http://www.janfromm.de/typefaces/camingodos/overview/

[generic font]:         http://www.w3.org/TR/CSS2/fonts.html#generic-font-families
[Font Stack Roundup]:   https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#font-stack-roundup
[Complete Guide]:       http://www.apaddedcell.com/web-fonts

[Resets]:        https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp4-stylesheet-review.md#stylesheet-review#resets
[implementation]:       https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v102.scss

[Ideal Line Length]:    http://www.maxdesign.com.au/articles/em/
[CSS Font-Size]:        http://kyleschaeffer.com/user-experience/css-font-size-em-vs-px-vs-pt-vs/
[Embracing em's]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/

[golden ratio]:         http://en.wikipedia.org/wiki/Golden_ratio
[Modular Scale]:        http://modularscale.com/
[scale]:                http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0
[Sassy Modular Scale]:  https://github.com/Team-Sass/modular-scale

[readability]:          http://blog.8thlight.com/billy-whited/2011/08/23/readability.html
[Count]:                http://www.gbsheli.com/2009/05/count-improved-wc-bookmarklet.html
[Optimal]:              http://baymard.com/blog/line-length-readability
[Better Typography]:    http://www.markboulton.co.uk/journal/five-simple-steps-to-better-typography
[Meaningful Typography]: http://alistapart.com/article/more-meaningful-typography
[somewhere]:            http://www.kaikkonendesign.fi/typography/section/11

[DIY Icon Fonts]:       http://www.webdesignerdepot.com/2012/01/how-to-make-your-own-icon-webfont/
[Icon Font HTML]:       http://css-tricks.com/html-for-icon-font-usage/
[Icomoon]:              http://icomoon.io
[Love]:                 http://weloveiconfonts.com/
[Big List]:             http://css-tricks.com/flat-icons-icon-fonts/
[Pipeline]:             http://myrailslearnings.wordpress.com/2012/05/01/getting-font-face-to-work-with-the-asset-pipeline/
[Icon Font Support]:    http://blog.kaelig.fr/post/33373448491/testing-font-face-support-on-mobile-and-tablet

[9 Things]:             http://24ways.org/2011/nine-things-ive-learned/
[Color Fundamentals]:   http://tympanus.net/codrops/2012/09/17/build-a-color-scheme-the-fundamentals/
[Color Theory]:         http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm
[Color Matters]:        http://colormatters.com/color-and-design/basic-color-theory

[The Meanings of Colors]: http://colormatters.com/color-symbolism/the-meanings-of-colors
[Adjectives]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#visual-design-for-the-nondesigner#step-1-define-adjectives
[Color in Motion]:      http://www.mariaclaudiacortes.com/colors/Colors.html
[0to255]:               http://0to255.com/
[Web Safe]:             http://websafecolors.info/

[Analogous]:            http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm#analogous
[Complementary]:        http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm#complementary
[Triadic]:              http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm#triadic
[Split-Complementary]:  http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm#split-complementary
[Rectangle (Tetradic)]: http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm#rectangle
[Square]:               http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm#square
[Adobe Kuler]:          https://kuler.adobe.com/#
[Color Calculator]:     http://www.sessions.edu/color-calculator
[Color Wizard]:         http://www.colorsontheweb.com/colorwizard.asp
[Palette Creator]:      http://slayeroffice.com/tools/color_palette/
[Color Palette Generator]: http://jrm.cc/color-palette-generator/
[Pictaculous]:          http://pictaculous.com/
[Kuler]:                https://kuler.adobe.com/explore/

[Premium Pixels]:       http://www.premiumpixels.com/

[Fonts]:                http://www.chrismaxwell.com/manifesto/chp-10/fonts.gif
[Color Wheel]:          http://www.chrismaxwell.com/manifesto/chp-10/pocket-color-wheel.jpg
[Orange]:               http://www.chrismaxwell.com/manifesto/chp-10/orange.gif
[Blue]:                 http://www.chrismaxwell.com/manifesto/chp-10/blue.gif
[Kuler]:                http://www.chrismaxwell.com/manifesto/chp-10/kuler.gif
[Wizard]:               http://www.chrismaxwell.com/manifesto/chp-10/color-wizard.gif
[Shades]:               http://www.chrismaxwell.com/manifesto/chp-10/shades.gif
[Generator]:            http://www.chrismaxwell.com/manifesto/chp-10/generator.gif
[Pictaculous Image]:    http://www.chrismaxwell.com/manifesto/chp-10/pictaculous.gif
[Favorites]:            http://www.chrismaxwell.com/manifesto/chp-10/palettes.gif
[Palette 1]:            http://www.chrismaxwell.com/manifesto/chp-10/palette-1.gif
[Palette 2]:            http://www.chrismaxwell.com/manifesto/chp-10/palette-2.gif
[Palette 3]:            http://www.chrismaxwell.com/manifesto/chp-10/palette-3.gif
