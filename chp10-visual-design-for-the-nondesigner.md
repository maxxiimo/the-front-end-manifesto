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

Back then that kind of made sense, it was a simpler world, one design could almost fit all, and most things that happened in the browser could be replicated in a mockup, and so front end developers found the bulk of their contribution to a project in implementing completed mockups. They were in essence the handshake between graphic design and backend code. They understood what kind of code the backend team needed and how they would use it, and they had the skills necessary to turn graphic design into pixel perfect – the standard of excellence back then – cross browser friendly code.

NOTE: Chapter 11, [Slicing and Dicing Mockups][Chapter 11], will dive into the mechanics of doing exactly that.

Fast-forward to today and everything has changed:

- HTML5 and CSS3 have made it possible – preferable – to produce design elements directly in the browser.
- It is increasingly more efficient to produce dynamic and responsive prototypes with the benefits of CSS3, rather than static mockups.
- Much of what is happening on the front end cannot be easily replicated in a static mockup.
- Prototyping by nature is more representative of how a webpage will ultimately look and behave across different devices.
- Prototyping allows for a more rapid, iterative, interactive, and agile design process.
- One size no longer fits all. Technologies and devices are rapidly changing. Understanding the resulting capabilities and/or limitations of browsers and devices used by end-users in a constantly evolving landscape is a necessity, not a luxury, and an area of expertise belonging to front end engineers.

As a result of these changes; usability, architecting and design decisions are beginning to convalesce around the point in which front end code is written, prototyping, as opposed to around graphic design mockups. In the very least, the absence of front end developers in the design process is no longer an option.

The takeaway in relation to this chapter is that as front end engineers we need to understand that our roles are changing. In addition to coding prowess, understanding the elements of a good design, the art, is essential to the success of projects we participate in.

This chapter is written to help developers along this path. With that lets get started.

Typography
----------

> 95% of the information on the web is written language. It is only logical to say that a web designer should get good training in the main discipline of shaping written information, in other words: Typography.

\- [Web Design Is 95% Typography][95% typography]

The first visual design component I like to tackle is [typography][]. The lowest hanging fruit in typography are typefaces:

- Font Family
- Font Size
- Readability

Using the base styles from [Chapter 3][] these typographic elements are predefined and available to you to experiment with through the [_define.sass][] sass partial – reserved for defining global stylesheet variables:

    /* Fonts
      -----------------------

    // stacks...

    // http://unitinteractive.com/blog/2008/06/26/better-css-font-stacks/

    $arial: Arial, "Helvetica Neue", Helvetica, sans-serif
    $verdana: Verdana, Geneva, Tahoma, sans-serif
    $geneva: Geneva, "Lucida Sans", "Lucida Grande", "Lucida Sans Unicode", Verdana, sans-serif
    $georgia: Georgia, Palatino, "Palatino Linotype", Times, "Times New Roman", serif

    // google web fonts...

    // http://designshack.net/articles/css/10-great-google-font-combinations-you-can-copy/
    // http://designshack.net/articles/typography/10-more-great-google-font-combinations-you-can-copy/

    $cantata: "Cantata One", Georgia, serif
    $imprima: Imprima, Verdana, Helvetica, sans-serif

    $allerta: Allerta, Helvetica, Arial, sans-serif
    $crimson: Crimson Text, Georgia, Times, serif

    $arvo: Arvo, Georgia, Times, serif
    $pt-sans: "PT Sans", Helvetica, Arial, sans-serif

    $pt-serif: "PT Serif", serif

    $droid-serif: "Droid Serif", Georgia, Times, serif
    $droid-sans: "Droid Sans", Helvetica, Arial, sans-serif

    // base definitions...

    $base-font-family: $droid-sans !default
    $base-font-size: 100% !default
    $base-line-height: 1.4 !default

    $base-font-header: $droid-serif !default
    $base-font-nav: $droid-serif !default

    // non-google web fonts alternativ:
    // $base-font-header: $arial !default
    // $base-font-header: $georgia !default
    // $base-font-nav: $georgia !default

NOTE: Our font definitions begin with variables set to different font stacks. In Sass, variables can also be set to other variables. In our case the `$base-font-family` variable, the key to our application fonts, references one of the different predefined font stack variables and is in turn is referenced by our `<body>` tags `font-family` property and will propagate throughout the entire application by virtue of the CSS written and the concept of CSS inheritance. You can experiment with the predefined fonts by changing the variable that `$base-font-family` points to.

Font Family
-----------

Since we have predefined fonts, let's experiment and pick one for View Thought. You do not have to use what is predefined. To help you select an alternative I created a quick reference "[Font Stacks Roundup][Appendix 8]" located in the Appendices of this book. Here you will find recommendations for:

1.  Font stacks that you can copy and use in your project.

2.  Web safe fonts, i.e. fonts that are most common on most versions of Windows, Mac, and Linux.

    You can copy these and feel confident using them as your overall default font stack, or as a fallback font stack for a more interesting typeface.

3.  Typefaces that go well together, say one font for your headers and another contrasting font for your body.

When deciding on a font family for a project I follow the following steps:

### Step 1: Define Adjectives

> Write down a general description of the qualities of the message you are trying to convey, and then look for typefaces that embody those qualities.

\- [More Perfect Typography][Perfect Typography] (Tim Brown quoting Jason Santa Maria.)

According to Tim Brown, the Type Manager for Adobe Typekit, he always begins a project this way. He starts with body text, "which gives tone for a piece," then moves on to markers like headers, "that give it personality and character." Perfect places to apply Step 2's pairings.

The article, "[A Brief Primer on Typeface Selection][Brief Primer]" echoes the same idea:

> Read your content to determine the mood it conveys. Describe this mood using a list of adjectives. Find typefaces that you feel are accurately described by these adjectives. Essentially, you want to ensure that your typeface conveys the appropriate feeling.

What adjectives describe View Thought? To start, I revisited the storyline:

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

NOTE: Jason Santa Maria, a master on the subject, in a presentation called [On Web Typography][] gives excellent advice on picking typefaces starting at 31:45. You can find this advice transcribed in [Appendix 10][Appendix 10].

### Step 2: Use a Font Service

I like to use a font service to browse and deliver fonts. Using a fonts service eliminates the licensing headaches one might encounter using other people's works, and also provides a CDN to serve fonts from. Some services are subscription based and others are free. I have listed a few in the "[Font Services and Tools][Appendix 9]" appendix.

My preferred service is [Typekit][]. They provides an excellent [series of articles][articles] on implementing Typekit, so [/[I'll/]][I'll] [/[spare/]][spare] [/[you/]][you] [/[the/]][the] [/[details/]][details].

Typekit is a paid service, [Google Web Fonts][] on the other hand is a free service:

- [A Beginner’s Guide to Using Google Web Fonts][Beginners Guide]

### Step 3: Pairing Typefaces

> You might have already heard this; successful pairing relies on concord, or contrast, but not conflict. That is to say your selected fonts can work well together by sharing certain qualities, or by being completely different from one another. However, font pairs can conflict in a number of ways – being too similar being just one.

\- [A Beginner’s Guide to Pairing Fonts][Beginners Guide]

When selecting font families it's helpful for me to go straight to the Font Stacks Roundup's "[Combinations][Appendix 8 Combos]" section. Here designers with typographic knowledge and experience well beyond my own have paired fonts, describe their personality or feel, and more often than not provide samples for you to review and choose from.

There are a few Google Web Fonts pairing ideas in the starter styles to try:

- [_define.sass][]
- [_head.html.haml][]

### Step 4: Choose a Typeface

With Step 1 through 3 behind us, and the predefined fonts in our starter styles, the next step in the process is to actually choose something, and give it a test drive. Here are some screenshots of different font ideas for View Thought:

![][fonts]

As you can see, choosing fonts is a practice in trial and error. In Appendix 10 in the section entitled "[Choosing Typeface Articles][Appendix 10]," I list different articles that might help you frame the context of your decision making process.

### Step 5: Define Fallbacks (Font Stacks)

Finally, once you choose your fonts it's good practice to also define fallback fonts. Together your chosen font and its fallbacks are a font stack; a listing of several different fonts.

The reason we define a font stack is to make sure similar substitute fonts are available for devices that do not carry the font family you wish to use. For example:

    Arial, "Helvetica Neue", Helvetica, sans-serif

If your device does not have the first font in the stack, Arial, your browser will look for the second one and so forth until the very last one: which is a generic font and the most broadly available across different operating systems. All the fonts in the stack are similar enough that they can be interchanged with minimal differences between fonts used (at least that is the goal).

Font Size
---------

Now that we have selected a font family, we need to set a base font size. Choosing font size is actually an important decision. At the very basic level you will choose between a measurement types such as px's vs. em's vs. % vs. pt's vs rem's, and from a more complex perspective you need to consider that your choice might also be the measurement from which your entire site is responsive to, and in our case it is.

Quite frankly to me it seemed like a whole heck of a lot of thinking and research that I would love to spare you from, so I'm just going to give you a very opinionated basis to start from. At the same time I will also provide you with the source of my thinking in "[A Brief History of Web Font Sizes][Appendix 11]" found in the appendices.

In [Chapter 3][] we implemented [Normalize.css][]. If you look at our [implementation][] you will notice that we reset our base font size to 100%:

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

### Using Em's

Throughout our application moving forward if we would like to affect font size for let's say headers or a specific element, we will use em's. We use em's because there are a scalable unit relative to the parent font size. In our case, 1em = default browser font size = typically 16px. If we would like to double in size we use 2em = 32px.

NOTE: It's important to keep in mind that em's are relative to the parent, and not the browser or \<body> font size.

In Chapter 3 we learned about the benefits of [using em's][] in our media querries, and that using em's goes hand-in-hand with our Susy grid system.

For more details on using em's take a look at:

- [Ideal line length for content][Ideal Line Length]
- [CSS Font-Size: em vs. px vs. pt vs. percent][CSS Font-Size]
- [How we learned to leave default font-size alone and embrace the em][Embracing em's]

Modular Scales
--------------

A modular scale is a scale based on ratios derived from harmonic intervals or the golden ratio and key measure/s in your application (such as the base font size). Yowza! What? Well in layman's terms it's a bunch of measurements used for key measurements in your application, a scale, that are related to one another in some artistic/design awesome way; versus randomly picking numbers. You use numbers from the scale throughout your application for things like line length, column widths, line heights, etc., and by doing so your design will be better, or in the very least you are making a design informed decision!

So how is this modular scale created? Fortunately there are some great references out there that will do a much better job of explaining the what's and how's of modular scales:

- [Tim Brown - More Perfect Typography][Perfect Typography] (Go to minute 15:00, great talk.)
- Articles 10, 11, and 12 in Appendix 11, [A Brief History of Web Font Sizes][Appendix 11]
- The [Modular Scale][] tool

 Using the Modular Scale tool here is the scale we will use for View Thought:

- http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0

Our scale is based on the golden ratio and two important numbers, our base font size of 16px and our logo font size of 30px. In our [_define.sass][] partial we take note of this as follows:

    /*  Modular Scale
      -----------------------

    // http://modularscale.com/scale/?px1=16&px2=30&ra1=1.618&ra2=0

    // 16px  @ 1:1.618 - base font size
    // 30px  @ 1:1.618 - logo font size

Now that we have a scale, let's apply it. For the more adventurous take a look at:

[Sassy Modular Scale][]

Readability
-----------

Readability is the perfect place to begin applying our brand-new Modular Scale. Font choice, size, line length (measure), line height (leading), and font color and contrast are the main components of [readability][]. We've covered font choice and size, now let's look at the rest.

### Line Length (Measure)

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

### Line Heigt (Leading)

For line height there are a couple key things to keep in mind: You will need more line height when your lines are longer – otherwise your readers might get lost, and/or when you use a darker font color – so that you do not to overwhelm the rest of the site.

For our site we're going to pick a number from our scale. After some trial and error, 1.618 seems to be the best line height:

    $base-line-height:  1.618         !default

The next natural step down in our scale is 1.159, which seems to be too much of a step down, so using another figure in our scale I calculate an alternative in case I need it:

    // 1.618 - 0.105 = 1.513
    // 1.618 - 0.236 = 1.382
    // 1.618 - 0.382 = 1.236

### Color

I read [somewhere][] that to make your text appear softer and still maintain a good contrast you shouldn't use pure black for your font color but something slightly lighter. The idea made a lot of sense to me so we use the following defaults in our starter styles:

    $base-font-color:   #444         !default
    $base-header-color: #222         !default

Of course, black on white does not have to be the default color and contrast.

Color Palette
-------------

> There are many contributing factors that go into making a good visual design, but one of the simplest ways to do this is through the use of colour. The colour palette used in a design can have such a profound effect on a visual design that it almost feels like you’re cheating. It’s easy to add more and more subtle shades of colour to add a sense of sophistication and complexity to a design, but it dilutes the overall visual impact. When I design, I almost have a rule that only allows me to use a very limited colour palette.

\- Mike Kus, "[Nine Things I've Learned][9 Things]"

So how do we begin to develop our own color palette? The articles:

- [Build a Color Scheme: The Fundamentals][Color Fundamentals]
- [Basic color schemes - Introduction to Color Theory][Color Theory]
- [Color Matters - Basic Color Theory][Color Matters]

...do an excellent job of **defining** the fundamentals of color theory and the basic steps and components in building a color scheme:

1.  Selecting a base color while taking into account the effect colors have on our perceptions and feelings.
2.  Choosing color harmonies from the color wheel, i.e. what colors will work well together.
3.  Selecting the right tones, shades and tints for each color in the color scheme.

Read the article and you'll understand what these steps entail, but it still begs the question, practically speaking, how do I begin?

### Step 1: Base Color Selection

> With colors you can set a mood, attract attention, or make a statement. You can use color to energize, or to cool down. By selecting the right color scheme, you can create an ambiance of elegance, warmth or tranquility, or you can convey an image of playful youthfulness. Color can be your most powerful design element if you learn to use it effectively.

\- [Basic color schemes - Introduction to Color Theory][Color Theory]

Wow, that quote certainly says something. Obviously a color scheme is powerful so to start let's choose a base color, and to do so I'm going to borrow from the techniques we used in the "[Choosing Typefaces][]" section of this chapter. Here is the list of adjectives I came up with:

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

Are there any colors that may help convey this? Reviewing the color descriptions in the following references:

- [The Meanings of Colors][] (MoC)
- [Build a Color Scheme: The Fundamentals][Color Fundamentals] (BaCS)
- [What do colors mean?][Color Meaning]
- [Color in Motion][]

...I do come up with a few:

- **White** - This makes a lot of sense to me since we start our adjectives list with the word "Clean"

  > A white color scheme can represent cleanliness, purity, perfection and space...If you are looking for a clean design with plenty of negative space, play around with white more. - BaCS

- **Red** - As an overall base color I'm not sold on it for my purposes, but I do have some callout buttons so will keep this color in mind if it fits in my color wheel choice.

  > A red color scheme is bold, fiery, aggressive and screams for your attention...Red is a really powerful marketing color that can be used to grab the user’s attention and get them to click on an ad or register for a product. - BaCS

  > Red is the color of extremes. It’s the color of passionate love, seduction, violence, danger, anger, and adventure...Red captures attention. It is one of the most visible colors, second only to yellow... - MoC

- **Orange** - This might be the one. Aside from the fact that the parent company of View Thought uses it, it's feeling seems to touch on a lot of adjectives I have listed, plus it could be an alternative to read for our callouts.

  > An orange color scheme speaks happiness...Orange is a very friendly color, a warm color that is inviting and can be another very effective color for call-to-actions. - BaCS

  > Orange is vibrant. It’s hot, healthy, fruity and engaging – but it can be abrasive and crass. It’s a polarizing color. People either love it or detest it. - MoC

- **Green** - I'm liking this one insofar as it touches on trust and stability.

  > A green color scheme is peaceful and natural and is usually associated with growth, harmony, peace, strength and stability....it portrays a feeling of safety and trust... - BaCS

  > Green is no longer just a color. It's now the symbol of ecology and a verb. - MoC

- **Blue** - Well if this isn't the cats meow.

  > Blue means stability and depth and is a great color for creating a calm clean environment. Blue symbolizes confidence, faith, hope, wisdom, knowledge and trust. - BaCS

  > Blue is the favorite color of all people...Most blues convey a sense of trust, loyalty, cleanliness, and understanding. On the other hand, blue evolved as symbol of depression in American culture...Blue is the most commonly used color in corporate identity. - MoC

### Step 2: Color Wheel Experimentation

> The human brain will reject under-stimulating information. At the other extreme is a visual experience that is so overdone, so chaotic that the viewer can't stand to look at it. The human brain rejects what it can not organize, what it can not understand. The visual task requires that we present a logical structure. Color harmony delivers visual interest and a sense of order.

\- [Color Matters - Basic Color Theory][Color Matters]

If you read the three articles referenced in the introduction of this section, especially:

- [Basic color schemes - Introduction to Color Theory][Color Theory]

...

Colors on the color wheel can be:

- Analogous
- Complementary
- Monochromatic
- Triadic
- Split-Complementary
- Rectangle (Tetradic)
- Square





- Based on nature

### Step 3: Finishing Touches


### Step 4: Where to Apply



Branding
--------


Images
------


Icons
-----

### Icon Fonts

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

[The Big List of Flat Icons & Icon Fonts][Big List]

[HTML for Icon Font Usage][Icon Font HTML]

[Getting Font-Face to work with the Asset Pipeline][Pipeline]

[How to make your own icon webfont][DIY Icon Fonts]

[Testing @font-face Support on Mobile and Tablet][Icon Font Support]

[We Love Icon Fonts][Love]

#### @font-face


### Icon Sprites



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

What We've Done
---------------

Don't for a moment think that creative license belongs only to designers. It does not, in fact with the abilities of CSS3, much of the design work can now occur in the browser straight from our IDE's. Think of yourself as artists of a new age; you are the handshake between design and backend engineering and can work in either realm.

We started this chapter by covering typography. We discussed the basic building blocks of typography and how it is implemented in our application. As a side note, if you really want to learn more, the most highly acclaimed resource out there is:

- [The Elements of Typographic Style Applied to the Web][Typographic Style]

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md
[Chapter 9]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp9-information-architecting.md
[Chapter 11]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp11-slicing-and-dicing-mockups.md
[Appendix 1]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-1
[Appendix 8]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-8
[Appendix 8 Combos]:    https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#combinations
[Appendix 9]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-9
[Appendix 10]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-10
[Appendix 11]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-11
[Appendix 12]:          https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-12

[Dao]:                  http://www.alistapart.com/articles/dao
[Story Design]:         http://24ways.org/2011/design-the-invisible/

[typography]:           http://blog.8thlight.com/billy-whited/2011/07/26/what-is-typography.html
[95% typography]:       http://informationarchitects.net/blog/the-web-is-all-about-typography-period/
[_define.sass]:         https://github.com/maxxiimo/base-css/blob/master/app/assets/stylesheets/_define.sass

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

[Normalize.css]:        https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp2-foundation-styles.md#resets
[implementation]:       https://github.com/maxxiimo/base-resets/blob/master/_h5bp_normalize_v102.scss

[using em's]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-mobile-on-rails.md#ems-and-media-queries
[Ideal Line Length]:    http://www.maxdesign.com.au/articles/em/
[CSS Font-Size]:        http://kyleschaeffer.com/user-experience/css-font-size-em-vs-px-vs-pt-vs/
[Embracing em's]:       http://filamentgroup.com/lab/how_we_learned_to_leave_body_font_size_alone/

[Modular Scale]:        http://modularscale.com/
[Sassy Modular Scale]:  https://github.com/scottkellum/modular-scale

[readability]:          http://blog.8thlight.com/billy-whited/2011/08/23/readability.html
[Better Typography]:    http://www.markboulton.co.uk/journal/five-simple-steps-to-better-typography
[Meaningful Typography]: http://alistapart.com/article/more-meaningful-typography
[somewhere]:            http://www.kaikkonendesign.fi/typography/section/11

[9 Things]:             http://24ways.org/2011/nine-things-ive-learned/
[Color Fundamentals]:   http://tympanus.net/codrops/2012/09/17/build-a-color-scheme-the-fundamentals/
[Color Theory]:         http://www.tigercolor.com/color-lab/color-theory/color-theory-intro.htm
[Color Matters]:        http://colormatters.com/color-and-design/basic-color-theory

[The Meanings of Colors]: http://colormatters.com/color-symbolism/the-meanings-of-colors
[Choosing Typefaces]:   https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-visual-design-for-the-nondesigner.md#choosing-typefaces
[Color Meaning]:        http://lmgtfy.com/?q=What+do+colors+mean%3F
[Color in Motion]:      http://www.mariaclaudiacortes.com/colors/Colors.html

[Big List]:             http://css-tricks.com/flat-icons-icon-fonts/
[Icon Font HTML]:       http://css-tricks.com/html-for-icon-font-usage/
[Pipeline]:             http://myrailslearnings.wordpress.com/2012/05/01/getting-font-face-to-work-with-the-asset-pipeline/
[DIY Icon Fonts]:       http://www.webdesignerdepot.com/2012/01/how-to-make-your-own-icon-webfont/
[Icon Font Support]:    http://blog.kaelig.fr/post/33373448491/testing-font-face-support-on-mobile-and-tablet
[Love]:                 http://weloveiconfonts.com/

[Premium Pixels]:       http://www.premiumpixels.com/
[Typographic Style]:    http://webtypography.net/

[fonts]:                http://www.chrismaxwell.com/manifesto/chp-10/fonts.gif
