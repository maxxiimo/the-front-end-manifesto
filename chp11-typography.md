Typography
==========

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

Finally, choose a typeface and give it a test drive. Here are some different ideas for View Thought found in our starter styles, the logo style came from Typekit:
<br>
<br>
<br>
![][Fonts]
<br>
<br>
As you can see, choosing fonts is a practice in trial and error. To help you frame the context of your decision making process take a look at the section entitled "[Choosing Typeface Articles][Appendix 10]" in Appendix 10.

For View Thought I wasn't too crazy about any of the default combinations and ended up choosing three fonts from Typekit:
<br>
<br>
<br>
![][Final Three]
<br>
<br>
- [Quatro Sans][] for the logo. We're building things at View Thought and this font captures that feeling.

  > We are pleased to introduce you to Quatro Sans. An undeniably modern typeface with construction principles that attempt to find the balance between machine and hand.

- [Rooney Web][] for the body text. I wanted to use a serif font and Rooney seemed to embody the right combination of serious and fun that I was looking for.

  > Rooney feels serious yet its rounded shapes and soft curves make for an overall impression of warmth and smoothness.

- [CamingoDos Web][] for our headers and navigation. Oftentimes choosing fonts from the same foundry produces the best combinations. I wanted to use a sans-serif and Rooney Web's bbrother Rooney Sans Web was nice, but CamingoDos felt right.

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

### Line Height (Leading)

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

Obviously, color is a significant factor in your design and not just in readability.

And that's it! Here is what our site looks like with are new icon fonts, typefaces and applied modular scale:

![][Multidevice]

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md#foundation-styles
[Chapter 7]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-susy.md#susy
[Appendix 8]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-8
[Appendix 8 Combos]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#combinations
[Appendix 9]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-9
[Appendix 10]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-10
[Appendix 12]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-12

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

[Resets]:               https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp4-stylesheet-review.md#stylesheet-review#resets
[implementation]:       https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v102.scss

[Ideal Line Length]:    http://www.maxdesign.com.au/articles/em/
[CSS Font-Size]:        http://kyleschaeffer.com/user-experience/css-font-size-em-vs-px-vs-pt-vs/
[Embracing em's]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/

[readability]:          http://blog.8thlight.com/billy-whited/2011/08/23/readability.html
[Count]:                http://www.gbsheli.com/2009/05/count-improved-wc-bookmarklet.html
[Optimal]:              http://baymard.com/blog/line-length-readability
[Better Typography]:    http://www.markboulton.co.uk/journal/five-simple-steps-to-better-typography
[Meaningful Typography]: http://alistapart.com/article/more-meaningful-typography
[somewhere]:            http://www.kaikkonendesign.fi/typography/section/11

[Fonts]:                http://www.chrismaxwell.com/manifesto/chp-10/fonts.gif
[Final Three]:          http://www.chrismaxwell.com/manifesto/chp-10/final-three.gif
[Icon Fonts 1]:         http://www.chrismaxwell.com/manifesto/chp-10/icon-font-nav.gif
[Icon Fonts 2]:         http://www.chrismaxwell.com/manifesto/chp-10/icon-font-social.gif
[Multidevice]:          http://www.chrismaxwell.com/manifesto/chp-10/multidevice.png
