Embellishments
==============



Example Workflow
----------------

In this example we have our basic content, somewhat refined since we first architected ViewThought in [Chapter 9][]:
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

To begin the design process I will grab some of the design code already in place, icon fonts and Sassy button styling:

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
That was easy, and I have an idea in my head about how I would like to organize this section. Using Susy I arrange each of the information components along the pattern I'm imagining, In doing so I also need to account for responsiveness. For brevity, here is a small section of the CSS that accomplishes this for the three steps:

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
It's coming together, and the key to my design will be how the icons interplay with the text. I would really like them to stand out and help organize and direct the visual flow. To do this I will increase their size:
<br>
<br>
<br>
![][Design 4]
<br>
<br>
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
<br>
<br>
<br>
![][Design 5]
<br>
<br>
That makes a really nice difference, but something about the century is off to me and I'm not quite sure what it is. I've experimented with centering the headers, the paragraphs, left aligning everything, but I'm just not finding that right balance. This is a great reason to never design in isolation. Get feedback!

[Chapter 9]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp9-information-architecting.md#information-architecting

[Design 1]:             http://www.chrismaxwell.com/manifesto/chp-13/design-1.png
[Design 2]:             http://www.chrismaxwell.com/manifesto/chp-13/design-2.png
[Design 3]:             http://www.chrismaxwell.com/manifesto/chp-13/design-3.png
[Design 4]:             http://www.chrismaxwell.com/manifesto/chp-13/design-4.png
[Design 5]:             http://www.chrismaxwell.com/manifesto/chp-13/design-5.png
