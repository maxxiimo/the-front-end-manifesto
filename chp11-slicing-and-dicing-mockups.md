Slicing and Dicing Mockups
==========================

Unlike in previous chapters, often times I find myself in situations where all of the information architecting has been thought out, the look and feel is in place, and the designer has put it all together in a mockup. In this chapter we're going to go through the exercise of slicing and dicing an example mockup to learn one approach to turning mockups into front end code. Here is the mockup we will use:

![][mockup]

To begin, use Adobe Photoshop to work with mockups. You will need it. Start off by taking a look at the mockup for a few minutes. Think of yourself as a sculptor looking at a marble block for the first time. You have a vision in your head and your getting ready to chisel. In other words just absorb it, understand it. Look at the major layout elements, i.e. the framework of the site, and begin to ask yourself some basic high-level questions like:

1.  How wide is it designed to be? 960px, 980px, 1040px?

2.  Is the width fluid or static?

3.  Can it be divided into major sections? A header, main body, footer?

4.  Where is the main navigation? Is there a utility navigation? Is the navigation tabs, links, what?

5.  Is the footer stuck on the bottom or flow with the main content?

6.  Does the designer use a [grid system][]? (FYI - Compass has a great [grid-background][] mixin for this.)

7.  Is the header the same width as the main body or does it expand the entire page?

8.  Are gradients used and where? Are gradients used in the header and outer sides of the main body?

9.  Are corners rounded? Double check them all.

10. Where's the logo? Is it standard or does it overlap and need special attention?

11. Anything interesting going on with the background?

These are just a few questions to get you to start to think about how you will implement, and at the highest or strategic level - what will hold these elements, and what will the base layout look like. Constructing the base HTML layout is the most important step in the process. Take your time, think about:

- Semantics.
- How sections will interrelate and in some cases interact.
- How will the base layout be affected by future changes.
- Try to imagine how you will compartmentalize things in such a way that your code is efficient, organized, and less likely to require repetition (as in DRY).

As the underlying structure comes together in your mind, your coding vision, you can then start to look at content within the body, the overall look and feel, images, colors and fonts, and you can begin to start to think about whether you will use CSS or JavaScript to create various effects.

The truth of a matter is that slicing mockups is pretty straightforward. There are only so many ways you can organize a page layout, and most components within a page layout are pretty standard: I mean you have paragraphs, and headers, and links, a way to get around through navigation, and so forth. On the other hand though a designer's artistic expression and the look and feel of the site are very subjective; mockup to mockup. Making a mockup come to life per the designers vision, consistently across devices and browsers, requires a certain amount of HTML/CSS art (based on trial and error and experience). There is no formula for doing it, just basic guidelines which I will layout here as steps, and use a demo project to illustrate.

### Step 1 - Set Major Widths

Start with the lowest hanging fruit; major widths. Pretty straightforward, but doing so early on will provide the structure you will work with and within moving forward.

What are major widths? This is the main body or area of any website. It's what holds everything together and frames your content. In our example our major widths can be found in two places:

1. The blue header which expands the entire width of the browser, but also has an inner width for its content (the inner width is aligned with the main bodies width).

2. The main body: the white tabbed area.

How you define these widths is up to you, but I highly recommend using a [grid system][]. My tool of choice for creating a grid system is [Susy][].

Note: You can use `<body>` or `<div>` as a containing element:

- [Why should I use a container div in HTML?][Containing DIV]
- [Using the <body> element as a wrapper][Containing BODY]

### Step 2 - Backgrounds

The next lowest hanging fruit is the background. By defining backgrounds right off the bat your major widths suddenly become apparent. This manifesto is not a course on CSS so I won't get into styling details, but backgrounds are typically:

- Single colors like eggshell white
- A repeating pattern
- A color with a horizontal gradient

Backgrounds are rarely a single large image because of bandwidth cost.

To implement your background, set your `<body>` tags background-color property either to a specific color, or to a repeating image. If a gradient is involved you can use CSS3 or an image to achieve the effect. Whatever images you do use for the background, make it as small and optimized as possible without losing the look you are after.

If you're using my CSS organization structure, put your background styles in `_layout.sass`. It's a layout component.

NOTE: When using Compass use `image-url("")` instead of `url()`:

    background: image-url("fixtures/bg-texture.gif") 0 0 repeat-x

### Step 3 - Grab Images

The next not like to do is grab all the images I will need for the website, and that I can't re-create using CSS3. For example, in the mockup above I will need the ABC logo, a sample profile picture, some icons, but I can re-create the header gradients and rounded corners with CSS. I'm not yet sure about the company logo, but the point is grabbed the images you will need at the beginning of the project so that they are there for you when you need them.

When grabbing images here is the structure I use to organize them:

app<br>
|-- assets<br>
|&nbsp;&nbsp;&nbsp;|-- images<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **fixtures**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **icons**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **logos**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **pics**

Fixtures are things like shims or other structural components of a website. The other three folders are self-explanatory.

### Step 4 - Fonts

Start sampling fonts to determine font-family, font-size, and color. Organize what you find in your _define.sass file. The names you use to define these colors can be very specific, but as you move along you'll begin to notice groupings and can reorganize and rename things as you work.

The overall font-family is probably the most important thing you'll define right now. I use [CSS Font Stack][] to help me define the font-family. Some additional resources for you include:

- [Better CSS Font Stacks][Better Stacks]
- [Revised Font Stack][Revised Stack]
- [Web Fonts Can Be Nice (Honest)][Nice Fonts]
- [Complete Guide to Pre-Installed Fonts in Linux, Mac, and Windows][Complete Font Guide]

NOTE: As you're moving along there'll be times that you will need to add a note for yourself so that you can revisit something. When adding notes in your code I like to use something like this:

    // FIXME ccm: the note goes in here.

    or

    // TODO ccm: the note goes in here.

This way I can grep for "FIXME ccm", where ccm are my initials, and find my notes.

### Step 5 - Sectioning Content (layout/application.html.haml)

Here's where we really begin to code the basic high-level questions above. At the highest level, sectioning content is the same as building your base layout template in a Rails project (layout/application.html.haml). I typically start a project using the base template described in the HTML Organization section of this manifesto. From this starting point you can add or remove things from _head.html.haml and _scripts.html.haml because they include everything plus the kitchen sink. Adjust the HTML, class names, and incorporate new elements as the project requires.

Here are a few resources that will help you choose semantically correct elements for your base layout:

- [HTML5 Element Flowchart][Flowchart]
- [Structural Tags in HTML5][Structural Tags]
- [HTML5 section, aside, header, nav, footer elements – not as obvious as they sound][Not Obvious]
- [What Beautiful HTML Code Looks like][Beautiful HTML]
- [HTML 5 Outliner][]

To visualize your code output it helps to use border outlines on major sections or use Compass' [grid-background mixin][grid-background].

    .outline
      border: 1px solid red

For the demo project here is what my application layout looks like:

    !!!
    = head
    %body
      = chromeframe
      %header{:id => 'hd', :role => "banner"}
        #container
          = render :partial => 'shared/logo'
          = render :partial => 'shared/utility'
      #container
        = render :partial => 'shared/tabs'
        #main{:role => "main"}
          = render :partial => 'shared/breadcrumbs'
          = yield
        = render :partial => 'shared/footer'
    = scripts

A slight variation in our foundation [layout file][application] to accommodate the design needs of this project. Using our foundation markup with Compass grid backgrounds on, here's what our project looks like:

![][step-5]

### Step 6 - Start with %header and %footer

Once your application layout is in place, begin coding the header and footer. I find these two sections to be the most straightforward. Headers typically contain a logo, maybe a tagline or slogan, a navigational element, and sometimes a utility element. Footers usually have a pretty standard set of links like: about, contact, terms, and then a copyright notice and some social networking icons. I don't mean to say that sites should be this way, many are not, but the fact of the matter is that most are. Because of this I just like to get these sections out of the way. Like the background, they are the lowest hanging fruit, they will frame most of the pages in your application, and when you first see the coded header section all shiny and new, you will feel like and know you're getting somewhere!

NOTE: Leave a placeholder for your navigation, we will work on this in the next step.

So starting with the header (don't forget to use your magnifying tool to really see what's going on):

1.  Grab the logo. Trim any excess transparent space around the logo. In Photoshop use "Image/Trim..." and save it in your assets/images/logo directory as logo.gif and logo.png. In Photoshop use "File/Save for Web and Devices...".

    Note: This manifesto is most definitely not a Photoshop tutorial, but in case you didn't know, or for those of you new to Photoshop, there is a tool that will help you locate the layer in which the element you are after is in. On the top of the Photoshop tools palette there is a button with an arrow and crosshair icon. Click it. The top toolbar will change and that same button will be located on the far left of the new toolbar. Immediately to the right of it there is a checkbox with the name "Auto-Select: [Group/Layer]". Check this off. Finding your elements in your layers palette will now be that much easier. In my workflow I then grab the highlighted group or layer and drag it over to a new Photoshop window to isolate it. Besides using this tool you can also toggle layers on and off by clicking the eye icon on the layers palette beside each layer until you find what you're looking for or isolate an element.

    ![][auto-select]

2.  Set a background color for your header. Use Photoshop's eyedropper tool to discover the color. If you use an image for your header this color will serve as a fallback.

    ![][eyedropper]

    Note: Try to keep all of your colors in the _define.sass partial. As your application grows you'll be thankful for this. Use a naming convention that makes sense and keeps things grouped and organized. See the examples in the CSS Organization chapter.

3.  If you're header background includes gradients, isolate and slice it. Repeat it across the header along the X axis. Slice it to 5 pixels wide if it's repeating horizontally.

    When slicing in Photoshop, isolate the image in a fresh window, trim any excess space, and use Image/Canvas Size... to shrink the canvas on the left and right sides down to 5 pixels. In Photoshop File/Save for Web and Devices... as bg-header.gif/.png under asset/images/fixtures.

4.  In your CSS file set the header height. Photoshops "Image/Canvas Size..." tool will also give you an accurate measurement of the images height, which in turn is your headers height.

5.  Now that you have all the pieces, you can start implementing them.

    My logo code looks something like this:

        = link_to image_tag('logos/logo.png', :alt => 'XXX', :width => '##', :height => '##'), root_path, :title => '', :id => 'logo'

        #logo
          float: left
          margin: 10px 0  0

    My header background:

        header
          background: image-url("fixtures/bg-header.png") 0 0 repeat-x
          background-color: $bg-header
          div
            width: 980px
            height: 58px
            margin: 0 auto

And so on...

As your coding, there should be three things you should keep in mind:

1.  Candidates for Sprite-hood.
2.  Font sizes and colors and how you can most efficiently organize them.
3.  Using CSS to accomplish some of the image effects.

For the later I like to start with images because doing so gives me images I can fallback on. In Step 10 we will begin to replace these with more modern and bandwidth efficient CSS3 properties.

NOTE: In some cases just go with the CSS3 and don't bother with chopping images; like rounded corners because what is the default? A square corner, not a bad degradation.

But why image defaults at all? The reason is because some browsers may not be able to use the latest and greatest CSS3 techniques. Maybe pollyfills are out of the question because JavaScript is not available on the device? Whatever the case, for those situations we can serve up the fallback styles we created initially.

Regarding pollyfills and fallbacks, a super helpful tool you should familiarize yourself with as a front end coder is [Modernizr][]. I discuss this feature detection tool in greater detail in the JavaScript Library section of this manifesto.

So here's what the project is looking like so far:

![][step-6]

### Step 7 - Navigation

Now that the header and footer are complete it's time to code the navigation. Definitely check out the Navigation chapter, and here are some useful resources:

- Chris Coyier, a prolific writer for [CSS Tricks][], has written extensively on the subject of tabs. Go to his blog and search for "Tab" or "Navigation" and you will find a wealth of information and CSS How To's.

- [A List Apart][] is another great source of information for navigation and How To's.

- Since we are using the Rails stack and jQuery, might as well check those sources out too. I'm not a huge fan of [jQuery UI][] but it is tried and true.

### Step 8 - HTML for the Main Content

Now we get down to the nitty-gritty, tactical vs strategic work. If your mockup were a newspaper layout, what would the sections be? How is it organized? Keep this in mind. Here are some references that might help you hone your skills in this:

- [Grouping content][]
- [Content models][]

Start with a blank canvas, i.e. in my text editor, and literally start placing content in appropriate tags. I mean literally; image by image, header by header, list by list, paragraph by paragraph, start taking the words and mages in your mockup and putting them into appropriate elements in your view file.

As you start moving through sections of your mockup, start grabbing any remaining icons or images that you have not grabbed from your mockup already and place them in their appropriate folders per the HTML Organization chapter of this manifesto. Some things will simply be placeholders, like profile pictures. You can delete your placeholders out later.

Coding everything semantically correct is a practice in trial and error. In addition to the resources in step 4, Mozilla Developer Network's article "[Sections and Outlines of an HTML5 Document][HTML5 Document]" describes in detail the difference between HTML4 and HTML5 document structure. [HTML5 Doctor][] has some great HTML5 semantic specific articles that will help you get organized. If you are new to all this, or rusty, I recommend reviewing the following "element" articles:

- [%article][]
- [%section][]
- [HTML5 articles and sections: what’s the difference? ][The Difference]
- [%div][]
- [%aside][]
- [%header][]
- [%footer][]
- [%nav][]

Here's what I have up until now:

![][step-8]

You might need to readjust your application layout file as you move along, that's okay, this is the time to do that. You may also find that you initially placed something in your _layout.sass styles, only to realize later that really belongs in _pages.sass. That happens to me all of the time, half the time with anticipation. In those cases I usually add a little // FIXME ccm: note.

### Step 9 - Adding Styles

Like in the previous step we'll take it section by section, image by image, font by font, etc. First, I like to get the layout positioning out-of-the-way. Here we're mostly dealing with widths, margin and padding, and borders. Next, I go from section to section, making each section look exactly like the mockup. As I move along, and since all my font colors are defined in _define.sass, I begin to see patterns emerging and can consolidate and reorganize fonts into logical groups.

For example, my font colors are looking like this:

    // fonts...

    $white:             #fff
    $font-tab:          #0089ce
    $font-util-name:    #fff
    $font-util-login:   #b2ecff
    $font-footer:       #666
    $font-number-icon:  #fff
    $font-h1:           #252525
    $font-h2:           #0089ce
    $font-h3:           #333
    $font-gray:         #999
    $font-gray-2:       #a0a0a0
    $font-gray-3:       #666
    $font-red:          #bc1117
    $font-li:           #666

Notice the repetition?

Step nine is really the place where everything happens stylewise. We started slicing and dicing with a blank canvas, added semantically correct HTML5 containers, then content, and here in step 9 we start positioning and styling, from section to section... and at the end of this  methodical process here is what I am left with:

![][step-9]

A styled webpage almost completely identical to the mockup, however, created through HTML5 and CSS3 with a minimal amount of imagery.

### Step 10 - Sprites and CSS3 for Images

Save your sprite and CSS3 for image work – like replacing image gradients – for the tail end of slicing and dicing mockups. Doing so will give you enough material to work with in terms of images that can be grouped together in a sprite, and will not greatly affect other team members who may already be using your work.

I recommend using Compass' automated sprite utility for icons from the get-go. Here is a great screen cast to get you started on that:

[Railscast #334: Compass CSS Sprites][Railscasts]

Why do this from the get-go? Well you know you will have icons and you already have a folder for them, so as you come upon new icons simply create them and drop them into that folder; Compass will generate/update a sprite and give you all the classes you will need.


[grid system]:          http://www.subtraction.com/pics/0703/grids_are_good.pdf
[grid-background]:      http://compass-style.org/reference/compass/layout/grid_background/

[Susy]:                 https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp7-susy.md#susy

[application]:          https://github.com/maxxiimo/base-haml/blob/master/views/layouts/application.html.haml
[Containing DIV]:       http://stackoverflow.com/questions/354739/why-should-i-use-a-container-div-in-html
[Containing BODY]:      http://csswizardry.com/2011/01/using-the-body-element-as-a-wrapper/
[CSS Font Stack]:       http://cssfontstack.com/
[Better Stacks]:        http://unitinteractive.com/blog/2008/06/26/better-css-font-stacks/
[Revised Stack]:        http://www.awayback.com/revised-font-stack/
[Nice Fonts]:           http://aversionfour.petercolesdc.com/web-fonts-nice-honest/
[Complete Font Guide]:  http://www.apaddedcell.com/web-fonts
[Flowchart]:            http://html5doctor.com/downloads/h5d-sectioning-flowchart.png
[Structural Tags]:      http://orderedlist.com/resources/html-css/structural-tags-in-html5/
[Not Obvious]:          http://www.anthonycalzadilla.com/2010/08/html5-section-aside-header-nav-footer-elements-not-as-obvious-as-they-sound/
[Beautiful HTML]:       http://css-tricks.com/what-beautiful-html-code-looks-like/
[HTML 5 Outliner]:      http://gsnedders.html5.org/outliner/
[Modernizr]:            http://modernizr.com/
[CSS Tricks]:           http://css-tricks.com/
[A List Apart]:         http://www.alistapart.com/
[jQuery UI]:            http://jqueryui.com/
[HTML5 Document]:       https://developer.mozilla.org/en-US/docs/Sections_and_Outlines_of_an_HTML5_document
[HTML5 Doctor]:         http://html5doctor.com/article-archive/
[%article]:             http://html5doctor.com/the-article-element/
[%section]:             http://html5doctor.com/the-section-element/
[The Difference]:       http://www.brucelawson.co.uk/2010/html5-articles-and-sections-whats-the-difference/
[%div]:                 http://html5doctor.com/you-can-still-use-div/
[%aside]:               http://html5doctor.com/aside-revisited/
[%header]:              http://html5doctor.com/the-header-element/
[%footer]:              http://html5doctor.com/the-footer-element-update/
[%nav]:                 http://html5doctor.com/nav-element/

[Grouping content]:     http://developers.whatwg.org/grouping-content.html
[Content models]:       http://developers.whatwg.org/content-models.html

[Railscasts]:           http://railscasts.com/episodes/334-compass-css-sprites

[mockup]:               http://chrismaxwell.com/manifesto/chp-11/mockup-700px.jpg
[step-5]:               http://chrismaxwell.com/manifesto/chp-11/grids.gif
[auto-select]:          http://chrismaxwell.com/manifesto/chp-11/auto-select.gif
[eyedropper]:           http://chrismaxwell.com/manifesto/chp-11/eyedropper.gif
[step-6]:               http://chrismaxwell.com/manifesto/chp-11/finished-footer.gif
[step-8]:               http://chrismaxwell.com/manifesto/chp-11/HTML-no-styles-sm.gif
[step-9]:               http://chrismaxwell.com/manifesto/chp-11/job-details-700px.jpg

## TODO / write:

Measure twice, cut once.

Trial and error.

Varying specificity.

Getting things in place.

First try to use padding and margins, try to convert inline elements to inline-blocks, consider using floats, then try absolute positioning.

Work on what is needed, not on every possible contingency plan you can think of.
