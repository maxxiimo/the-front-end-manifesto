Embellishments
==============



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
### Experimenting

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

The Power of CSS
----------------

Adobe Photoshop is a graphic designers design tool. CSS and your browser are your design tools. There is quite a bit you can do with CSS, the question is what can you do, or how do you find out what you can do, and how do you do it?

Let's take another example from our View Thought project. Again we start with raw content:

<br>
<br>
<br>
![][Competencies 1]
<br>
<br>
<br>
<br>
<br>
![][Competencies 2]
<br>
<br>
<br>
<br>
<br>
![][Competencies 3]
<br>
<br>



[Chapter 9]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp9-information-architecting.md#information-architecting
[Icon Fonts]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#creating-your-own-set
[Appendix 5]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-5

[Pattern Tap]:          http://patterntap.com/
[Swooshy]:              http://24ways.org/2005/swooshy-curly-quotes-without-images/
[Curly Quotes]:         http://www.nealgrosskopf.com/tech/thread.php?pid=21
[Block Quotes]:         http://tympanus.net/codrops/2012/07/25/modern-block-quote-styles/
[Font Library]:         https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#icon-fonts-to-play-with

[Quote Examples]:       http://www.chrismaxwell.com/manifesto/chp-13/quote-examples.gif
[Quotes]:               http://www.chrismaxwell.com/manifesto/chp-13/quotes.jpg
[Design 1]:             http://www.chrismaxwell.com/manifesto/chp-13/design-1.png
[Design 2]:             http://www.chrismaxwell.com/manifesto/chp-13/design-2.png
[Design 3]:             http://www.chrismaxwell.com/manifesto/chp-13/design-3.png
[Design 4]:             http://www.chrismaxwell.com/manifesto/chp-13/design-4.png
[Design 6]:             http://www.chrismaxwell.com/manifesto/chp-13/design-6.png
[Design 7]:             http://www.chrismaxwell.com/manifesto/chp-13/design-7.png
[Competencies 1]:       http://www.chrismaxwell.com/manifesto/chp-13/core-competencies-1.gif
[Competencies 2]:       http://www.chrismaxwell.com/manifesto/chp-13/core-competencies-2.gif
[Competencies 3]:       http://www.chrismaxwell.com/manifesto/chp-13/core-competencies-3.gif
