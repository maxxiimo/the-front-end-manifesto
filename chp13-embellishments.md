Embellishments
==============



Example Workflow
----------------

In this example we have our basic content for what will become the process panel in our design, somewhat refined since we first architected ViewThought in [Chapter 9][]:

![][Design 1]

It's code is pretty straightforward:

    %section#process
      .container
        .process
          %h2 Our Process
          %p We bring together great design and great code to make mobile and Web applications work and look amazing across any device no matter how big or small.
        .discovery
          %h3 1. Discovery
          %p Through discovery we get to know you, your company, project, market, target audience, goals, key business requirements, and so forth. We come to an understanding, a plan, and an agreement. From discovery we get to work!
        .development
          %h3 2. Development
          %p We believe in an iterative approach, where all stakeholders are involved in producing your project&ndash;from start to finish and in a manner that makes sense. We like to deploy often and frequently, iteratively, and with the goal of reaching perfection.
        .repeat
          %h3 3. Repeat
          %p The discovery process never ends, but rather continuously feeds into the development of your application. We value feedback.
        .hire-button
          %button Want to Hire Us?

...With some basic padding to give it some separation:

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

NOTE: Since every panel will use the same amount of padding depending on its breakpoint, I've moved the padding amount into a variable located at `_define.sass`. This way I can change the setting site wide in one location.

The first embellishments I will add will be icon fonts and Sassy button styling:

![][Design 2]

That was easy:

    %section#process
      .container
        .process
          %h2 Our Process
          %p We bring together great design and great code to make mobile and Web applications work and look amazing across any device no matter how big or small.
        .discovery
          %span{"aria-hidden" => "true", "data-icon" => "&#x2691;".html_safe}
          %h3 1. Discovery
          %p Through discovery we get to know you, your company, project, market, target audience, goals, key business requirements, and so forth. We come to an understanding, a plan, and an agreement. From discovery we get to work!
        .development
          %span{"aria-hidden" => "true", "data-icon" => "&#x2692;".html_safe}
          %h3 2. Development
          %p We believe in an iterative approach, where all stakeholders are involved in producing your project&ndash;from start to finish and in a manner that makes sense. We like to deploy often and frequently, iteratively, and with the goal of reaching perfection.
        .repeat
          %span{"aria-hidden" => "true", "data-icon" => "&#x27f3;".html_safe}
          %h3 3. Repeat
          %p The discovery process never ends, but rather continuously feeds into the development of your application. We value feedback.
        .hire-button
          %button Want to Hire Us?

...And I added this style:

    .hire-button
      text-align: center
      button
        +sassy-button

I have an idea in my head about how I would like to convey ViewThought's process. Using Susy I arrange each of the information components along the pattern I'm imagining:

![][Design 3]

In doing so I also need to account for responsiveness. Here is the CSS that accomplishes all of this:

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
        padding-bottom: $padding-12 0

    .process
      +at-breakpoint($break6)
        h2
          text-align: center

      +at-breakpoint($break9)
        +span-columns(8, $break9)
        +squish(.5, .5)
        margin-bottom: 1.875em

      +at-breakpoint($break12)
        +span-columns(10, $break12)
        +squish(1, 1)

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

    .hire-button
      text-align: center
      button
        +sassy-button
        margin-top: 1.618em
        font-size: 1.159em

      +at-breakpoint($break6)
        button
          margin-top: 1.875em
          // 1 + .274
          font-size: 1.274em

      +at-breakpoint($break9)
        button
          // 1 + .443
          font-size: 1.443em

      +at-breakpoint($break12)
        button
          font-size: 1.618em

The key to my design will be how the icons interplay with the text. I would really like them to stand out and help direct the visual flow. To do this I will increase their size:

![][Design 4]

Wow, that really pops out. The great thing about icon fonts is that they're very easy to resize, and they won't lose their sharpness.

Standalone the icon fonts look pretty good, but I'm also thinking about framing them in a circle, kind of like a portal hole. I saw something like this in a couple of my inspirational sites; team member portraits were framed by circles. I think this might be a good look here and can be easily accomplished with CSS:

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

The result:

![][Design 5]

That makes a really nice difference, but something about the century is off to me and I'm not quite sure what it is. I've experimented with centering the headers, the paragraphs, left aligning everything, but I'm just not finding that right balance. This is a great reason to never design in isolation. Get feedback!

[Chapter 7]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-susy.md#susy

[Design 1]:             http://www.chrismaxwell.com/manifesto/chp-13/design-1.gif
[Design 2]:             http://www.chrismaxwell.com/manifesto/chp-13/design-2.gif
[Design 3]:             http://www.chrismaxwell.com/manifesto/chp-13/design-3.gif
[Design 4]:             http://www.chrismaxwell.com/manifesto/chp-13/design-4.gif
[Design 5]:             http://www.chrismaxwell.com/manifesto/chp-13/design-5.gif
