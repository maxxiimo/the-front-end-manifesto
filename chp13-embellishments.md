Embellishments
==============


The Power of CSS
----------------

Adobe Photoshop is a graphic designers design tool. CSS and your browser are a front-end developers design tools. With CSS you can do almost anything for just a few short years ago  belong squarely in the realm of Photoshop design work.

Navigation
----------
<br>
<br>
![][Navigation 1]
<br>
<br>

<br>
<br>
![][Navigation 2]
<br>
<br>

Design Details
--------------

It's the little things that sometimes can make a big difference. Take for example quotes. We could always use regular quote characters: `&#147;` and `&#148;`, or the equivalent HTML entities: `&ldquo;` and `&rdquo;`, but That's a little bit too plain Jane for me. I have an idea on what I want, those giant quotes I see on some sites, but before I head down that path, I'm going to first check my [inspiration resources][Appendix 5].  Whenever designing it's a good idea to check your inspirational resources see how others might have implemented your idea, or possibly find something better suited for your projects content or use case. I did a quick search on [Pattern Tap][]:
<br>
<br>
![][Quote examples]
<br>
<br>
<br>
There are some good ideas there, including my giant curly quotes. I'm going to stick with that idea. The technique I use to accomplish this is pretty straightforward. I reviewed a few how-to articles to see how others implement giant curly quotes:

- [Swooshy Curly Quotes Without Images][Swooshy]
- [Create CSS Curly Quotes Without Images][Curly Quotes]
- [Modern Block Quote Styles][Block Quotes]

For View Thought I will add an icon font quote to my passage and use the techniques in the [24 Ways][Swooshy] article to style it so that it stands out. I included a few different types of quote characters in [my font library][Font Library] to experiment with.

NOTE: Make sure you complete the Chapter 10 icon font [set up steps][Icon Fonts].

To begin, add the following icon font `%span` within the `%blockquote` you would like to include the quote character in:

    %blockquote
      %span{"aria-hidden" => "true", "data-icon" => "&#x275d;".html_safe, :class => 'giant-quote'}
      A website should give its visitors immediate value, the moment they land on your...
    %p Chris Maxwell, founder of ViewThought

Icon fonts are regular characters, and will behave like regular characters. I gave mine a class of `giant-quote`, and will style the character through that class:

    .giant-quote
      display: block
      float: left
      line-height: 1.2
      padding-right: .443em
      // 1 + .274
      font-size: 1.274em

And that's it. I experimented a little and from my experimental set I like the second one from the left best:

![][Quotes]


Example Design Workflow
-----------------------

In this example we have our basic content, somewhat refined since we first architected it in [Chapter 9][]:
<br>
<br>
<br>
![][Design 1]
<br>
<br>
It's code is pretty straightforward:

    %section#process
      .container
        .process
          %h2 Our Process
          %p We bring together great design and great code...
        .discovery
          %h3 1. Discovery
          %p Through discovery we get to know you, your company...
        .development
          %h3 2. Development
          %p We believe in an iterative approach, where all...
        .repeat
          %h3 3. Repeat
          %p The discovery process never ends, but rather...
        .hire-button
          %button Want to Hire Us?

CSS:

    /* Process
      -----------------------

    #process
      padding: $padding-4 0
      background-color: $white

      +at-breakpoint($break6)
        padding: $padding-6 0

      +at-breakpoint($break9)
        padding: $padding-9 0

      +at-breakpoint($break12)
        padding: $padding-12 0

NOTE: Since every panel in the design will use the same amount of padding depending on its breakpoint, I've moved the padding into a variable located at `_define.sass`. This way I can change the setting site-wide in one location.

### Apply Styles That Already Exist

To begin the design process I will grab some of the design code already in place from our previous work; icon fonts and Sassy button styling:

    %section#process
      .container
        .process
          %h2 Our Process
          %p We bring together great design and great code...
        .discovery
          %span{"aria-hidden" => "true", "data-icon" => "&#x2691;".html_safe}
          %h3 1. Discovery
          %p Through discovery we get to know you, your company...
        .development
          %span{"aria-hidden" => "true", "data-icon" => "&#x2692;".html_safe}
          %h3 2. Development
          %p We believe in an iterative approach, where all...
        .repeat
          %span{"aria-hidden" => "true", "data-icon" => "&#x27f3;".html_safe}
          %h3 3. Repeat
          %p The discovery process never ends, but rather...
        .hire-button
          %button Want to Hire Us?

CSS:

    .hire-button
      text-align: center
      button
        +sassy-button

The result:
<br>
<br>
<br>
![][Design 2]
<br>
<br>

### Arrange Components Responsively

With a little help from my inspirational sites, I have an idea in my head about how I would like to organize this section. With this in mind my next step is to use Susy to arrange each element along the pattern I'm imagining. In doing so I also need to account for responsiveness. Here is a small section of the CSS that accomplishes this for the three process steps in this section:

    .discovery
      +at-breakpoint($break9)
        +span-columns(4, $break9)
        +prefix(.5)
        margin-right: 0

      +at-breakpoint($break12)
        +span-columns(5, $break12)
        +prefix(1, $break12)

    .development
      +at-breakpoint($break9)
        +span-columns(4, $break9)
        +prefix(.5)

      +at-breakpoint($break12)
        +span-columns(5, $break12)
        padding-left:  0

    .repeat
      +at-breakpoint($break9)
        +span-columns(4, $break9)
        +squish(2.5, 2.5)
        margin-top: 1.875em

      +at-breakpoint($break12)
        +span-columns(5, $break12)
        +squish(3.5, 3.5)

Result:
<br>
<br>
<br>
![][Design 3]
<br>
<br>
### Experiment

It's coming together, and the key to my design will be how the icons interplay with the text. I would really like them to stand out and help organize and direct the visual flow. To do this I increase their size:
<br>
<br>
<br>
![][Design 4]
<br>
<br>
Wow, that really pops out. The great thing about icon fonts is that they're very easy to resize, and they won't lose their sharpness.

Standalone, the icon fonts look pretty good, but I'm also thinking about framing them in a circle, kind of like a portal hole. I saw something like this in a couple of my inspirational sites; team member portraits were framed by circles. I think this might be a good look here and can be easily accomplished with CSS:

    .circle
      %span{"aria-hidden" => "true", "data-icon" => "&#x2691;".html_safe}

    @mixin circle-border($size: 100px, $border: 7px, $color: white)
      display: block
      width: $size
      height: $size
      text-align: center
      border: $border solid $color
      +box-shadow(0 0 5px rgba(0, 0, 0, 0.1))
      +border-radius($size)

    .circle
      margin: 0 auto
      +circle-border($size: (3.034em * 2), $color: $lime)
      span
        line-height: (3.034em * .63)
        font-size: 3.034em

I also think the larger fonts for the opening header and paragraph would give the section a better hierarchy. Finally, using `@mixin panel-shadow`, I'll add a thin line above the header to provide a visual cue separating this content from the content directly before it.

The result:
<br>
<br>
<br>
![][Design 6]
<br>
<br>
That makes a really nice difference, but something about the centering of each paragraph is off to me and I'm not quite sure what it is. I've experimented with centering the headers, center aligning the paragraphs, left aligning everything, but I'm just not finding the right balance. I'm also thinking that I could save some vertical space, and after some reshuffling, here is the result:
<br>
<br>
<br>
![][Design 7]
<br>
<br>

The What and How Approach to Design
-----------------------------------

There is quite a bit you can do with CSS, the question is what and how? Let's take another example from our View Thought project and answer this question and at the same time explore what I'm going to call the "what and how approach to design."

Start with coded raw content:

    %section#core-values
      .container
        .core-values
          %h2 Core Values
          %ol
            %li
              %span Build technology solutions that enhance the value proposition...
            %li
              %span Integrate beauty, design and optimal user experience in application...
            %li
              %span Address device constraints and opportunities while delivering...

It's a simple ordered list that unstyled looks like this:
<br>
<br>
![][Values 1]
<br>
<br>
Obviously, we need to add some style. The good thing is we now have a frame of reference; an ordered list. This answers the "what" part of our question. Ordered lists have been styled a thousand times over, so I guarantee you that there will be a lot of tutorials out there that will answer the "how" part of our question, and there is:

- [CSS Design: Taming Lists][Taming Lists]
- [CSS Swag: Multi-Column Lists][Multicolumn]
- [Hover on “Everything But”][Everything But]
- [Styling ordered list numbers][Styling OL]
- [Numbering In Style][]
- [CSS3 ordered list styles][CSS3 OL]

TIP: It's good practice to curate a bookmark list of CSS how to's. Every time I find an article that I think I may use someday or want to reference, I bookmark it under a category the defines it and similar articles. I always rename the bookmark with the articles date; beginning with the year and followed by the month and day (13-0131). This way I can decide what is more relevant since standards change (old articles have pearls of wisdom too though). Here is an example related to the how to links above:

![][Lists]

After reviewing my reference articles I come up with an idea. I like how some of the tutorials use an ordered lists number as a design element. Using this concept with a color from our color palette, and adding a `box-shadow` I style my list:
<br>
<br>
<br>
![][Values 2]
<br>
<br>
Nice, I like how it's looking. In fact I might just be done, but since our starter CSS includes a pretty cool set of box shadow mixins, I'm going to apply them to our list items to see what's available and how they might look:
<br>
<br>
![][Values 3]
<br>
<br>
<br>
I'm liking it even more, particularly the last one, and what I find amazing is that all of this has been accomplished with CSS only, quickly. With a little bit more CSS I can even make it look like the corners are turned up:
<br>
<br>
![][Values 4]
<br>
<br>
That some powerful stuff, and I accomplish this by asking the question:

What and how?

By defining "what" we were going to style it was easy to find "how" we were going to do it. Without the teachings and examples of the front end developer community, I probably would not have come up with this on my own, at least not so quickly. As front-end developers we learn from one another, take advantage of this in your design process and asked the question what am I going to design, then search online for how or review your bookmarks.

With the new CSS styles in place I decided to flow my list item boxes horizontally rather than vertically to save space. The result:
<br>
<br>
<br>
![][Values 5]
<br>
<br>
Pretty nice, and with the horizontal flow the content from the previous section fits into the viewport.

Here are the styles that accomplished this look:

    /* Core Values
      -----------------------

    #core-values
      position: relative
      padding: $padding-4 0
      background-color: $white
      z-index: -2

      +at-breakpoint($break6)
        padding-top: 0
        padding-bottom: $padding-6

      +at-breakpoint($break9)
        padding-bottom: $padding-9

      +at-breakpoint($break12)
        padding-bottom: $padding-12

    .core-values
      position: relative
      h2
        text-align: center
      li
        position: relative
        margin-bottom: 1.618em
        padding: 1em 1em 1em 3.034em
        font-size: 1em
        counter-increment: step
        list-style: none
        +box-shadow(0 0 10px rgba(0, 0, 0, 0.2))
        +shadow-3
        &:nth-child(3)
          margin-bottom: 0
        span:before
          content: counter(step, upper-roman)
          position: absolute
          top: 0
          left: 0
          width: 1.875em
          line-height: 1.875em
          text-align: center
          color: $white
          background-color: $orange
          // background-color: rgba(242, 101, 19, .7)
          +border-top-left-radius(4px)

      +at-breakpoint($break6)
        li
          // 1 + .169
          font-size: 1.169em

      +at-breakpoint($break9)
        +span-columns(9 omega, $break9)
        h2
          margin-top: 2.618em
          margin-bottom: 1.618em
        ol
          text-align: center
        li
          display: inline-block
          width: 7.942em
          margin: 0 .618em 0 0
          text-align: left
          vertical-align: top
          &:nth-child(3)
            margin-right: 0
        &:before
          +squish(.5, .5)
          +panel-shadow

      +at-breakpoint($break12)
        +span-columns(12 omega, $break12)
        li
          margin-right: 1em
          width: 11.089em
          // 1 + .236
          font-size: 1.236em

NOTE: The `+shadow-3` mixin is included in the [starter styles][].


[Chapter 9]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp9-information-architecting.md#information-architecting
[Icon Fonts]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#creating-your-own-set
[Appendix 5]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-5

[Pattern Tap]:          http://patterntap.com/
[Swooshy]:              http://24ways.org/2005/swooshy-curly-quotes-without-images/
[Curly Quotes]:         http://www.nealgrosskopf.com/tech/thread.php?pid=21
[Block Quotes]:         http://tympanus.net/codrops/2012/07/25/modern-block-quote-styles/
[Font Library]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#icon-fonts-to-play-with
[starter styles]:       https://github.com/maxxiimo/base-css/blob/master/app/assets/stylesheets/_mixins.sass

[Taming Lists]:         http://alistapart.com/article/taminglists
[Multicolumn]:          http://alistapart.com/article/multicolumnlists
[Everything But]:       http://css-tricks.com/hover-on-everything-but/
[Styling OL]:           http://www.456bereastreet.com/archive/201105/styling_ordered_list_numbers/
[Numbering In Style]:   http://css-tricks.com/numbering-in-style/
[CSS3 OL]:              http://www.red-team-design.com/css3-ordered-list-styles

[Navigation 1]:         http://www.chrismaxwell.com/manifesto/chp-13/navigation-1.gif
[Navigation 2]:         http://www.chrismaxwell.com/manifesto/chp-13/navigation-2.gif
[Quote Examples]:       http://www.chrismaxwell.com/manifesto/chp-13/quote-examples.gif
[Quotes]:               http://www.chrismaxwell.com/manifesto/chp-13/quotes.jpg
[Design 1]:             http://www.chrismaxwell.com/manifesto/chp-13/design-1.png
[Design 2]:             http://www.chrismaxwell.com/manifesto/chp-13/design-2.png
[Design 3]:             http://www.chrismaxwell.com/manifesto/chp-13/design-3.png
[Design 4]:             http://www.chrismaxwell.com/manifesto/chp-13/design-4.png
[Design 6]:             http://www.chrismaxwell.com/manifesto/chp-13/design-6.png
[Design 7]:             http://www.chrismaxwell.com/manifesto/chp-13/design-7.png
[Lists]:                http://www.chrismaxwell.com/manifesto/chp-13/bookmarks.gif
[Values 1]:             http://www.chrismaxwell.com/manifesto/chp-13/core-values-1a.gif
[Values 2]:             http://www.chrismaxwell.com/manifesto/chp-13/core-values-mac-1.png
[Values 3]:             http://www.chrismaxwell.com/manifesto/chp-13/core-values-3.gif
[Values 4]:             http://www.chrismaxwell.com/manifesto/chp-13/core-values-4.gif
[Values 5]:             http://www.chrismaxwell.com/manifesto/chp-13/core-values-mac-2.png
