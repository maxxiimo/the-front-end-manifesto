Slicing and Dicing Mockups
--------------------------

Use Adobe Photoshop to work with mockups.

Take a look at the whole for a few minutes. Just absorb it, understand it.

Then look at the major layout elements, i.e. the framework of the site, and begin to ask yourself some basic high-level questions like:

1.  How wide is it? 960px, 980px, 1040px?

2.  Is the width fluid or static?

3.  Can it be divided into major sections like header, main body, footer?

4.  Where is the main navigation? Is there a utility navigation? Is the navigation tabs, links, what?

5.  Is the footer stuck on the bottom or flow with the text?

6.  Does the designer use a [grid system][]? (FYI - Compass has a great [grid-background][] mixin for this.)

7.  Is the header the same width as the main body?

8.  Are gradients used? Are they used in the header and outer sides of the main body?

9.  Where's the logo? Is it standard or does it overlap and need special attention?

10. Anything interesting going on with the background?

These questions are designed to help you start thinking about the code that will hold these elements. This initial base HTML layout is the most important step in the process. Take your time, think about semantics, how sections will interrelate and in some cases interact; how they may be affected by future changes; compartmentalize things in such a way that your code is efficient, organized, and less likely to require repetition (as in DRY).

As the underlying structure comes together in your mind and even on your editor, you can start to look at content within the body, the overall look and feel derived from colors and fonts, and you can begin to start to think about whether you will use CSS or JavaScript to create various effects.

The truth of a matter as slicing mockups is pretty easy and straightforward because there are only so many ways to organize a page layout, and all of the components within a page layout are pretty standard, I mean you have paragraphs and headers and links, a way to get around through navigation, and so forth. But on the other hand a designer's artistic expression and the look and feel of the site are very subjective mockup to mockup. Making a mockup come to life, consistently across devices and browsers, requires a certain amount of art based on experience. There is no formula for doing it, just basic guidelines.

### Step 1 - Backgrounds

Start with the background. This manifesto is not a course on CSSso I won't get to into the details, but backgrounds are typically:

- Single colors like eggshell white
- A repeating pattern
- A color with a horizontal gradient

Backgrounds are rarely are a large image because of bandwidth costs.

To implement your background set your body background-color property either to a specific color, or the background property to a repeating image. If you're using my CSS organization structure, the body tag can be found in the _layout.sass file. If a gradient is involved you can use CSS 3 or an image to achieve the effect. Whatever images you do use for the background, make it as small and optimized as possible without losing the look you or after.

Remember, when using Compass use image-url("") instead of url():

    background: image-url("fixtures/bg-texture.gif") 0 0 repeat-x

### Step 2 -  Set Widths

Pretty straightforward, but doing so early on will lead into step 3.

Note: You can use <body> or <div> as a containing element:

[Why should I use a container div in HTML?][Containing DIV]
[Using the <body> element as a wrapper][Containing BODY]

### Step 3 - Sectioning Content (layout/application.html.haml)

Here's where we really begin to code the basic high-level questions above. Think in terms of your base layout in layout/application.html.haml. I typically start a project using the base template described in the HTML Organization section of this manifesto, I adjust it and incorporate new elements when required. Here are a few resources that will help you choose semantically correct elements for your base layout:

[HTML5 Element Flowchart][Flowchart]
[Structural Tags in HTML5][Structural Tags]
[HTML5 section, aside, header, nav, footer elements – not as obvious as they sound][Not Obvious]
[What Beautiful HTML Code Looks like][Beautiful HTML]

When sectioning content to visualize your code output it helps to use border outlines or Compass' [grid-background mixin][grid-background].

### Step 3 - Start with %header and %footer

Once your application layout is in place, begin coding your pages header and footer. I find these 2 sections the be the most straightforward. Headers typically contain a logo, maybe a tagline or slogan, a navigational element, and sometimes a utility element. Footers usually have a pretty standard set of links like: about, contact, terms, and then a copyright notice and some social networking icons. I don't mean to say that sites should be this way, many are not, but the fact of the matter is that most are. Because of this I just like to get these sections out of the way, they are low hanging fruit as an easy to do, they will frame most of the pages in your application, and when you first see that header section all shiny and new you know you're getting somewhere.

So start with the header, and don't forget to use your magnifying tool to really see what's going on.

1.  Grab the logo. Trim any excess transparent space around the logo In Photoshop Image/Trim... and save it in your assets/images/logo directory as logo.gif and logo.png (File/Save for Web and Devices... in Photoshop).

    Note: This manifesto is most definitely not a Photoshop tutorial, but in case you didn't know or for those of you new to Photoshop, there is a tool that will help you locate the layer in which the element you are after is in. On the top of the tools palette there is a button with an arrow and crosshair icon. Click it. The top toolbar will change and that same button will be located on the far left of the new toolbar. Immediately to the right of it there is a checkbox with the name "Auto-Select: [Group/Layer]". Check this off. Finding your elements in your layers palette will now be that much easier. In my workflow I then grab the highlighted group or layer and drag it over to a new Photoshop window to isolate it. Besides using this tool you can also toggle layers on and off by clicking the eye icon on the layers palette beside each layer until you find what you're looking for or isolate an element.

2.  Set a background color for your header using the eyedropper tool to select a color. If you use an image for your header this color will serve as a fallback.

    Note: Try to keep all of your colors in the _define.sass partial. As your application grows ill be thankful for this, and oh, use a naming convention that makes sense and keeps things grouped and organized.

3.  If you're header background includes gradients slice it, and repeat it across the header along the X axis. Slice it to 5 pixels wide if it's repeating horizontally and consistent across the repetition. When slicing in Photoshop, isolate the image in a fresh window, trim any excess space, and use Image/Canvas Size... to shrink the canvas on the left and right sides down to 5 pixels. In Photoshop File/Save for Web and Devices... as bg-header.gif/.png under asset/images/fixtures.

4.  In your CSS file set the header height. The Image/Canvas Size... tool will also give you an accurate measurement of the images height, which in turn is your headers height.

5.  Start sampling header font colors and organizing the results in your _define.sass file. The names he used to define these colors can be very specific, but as you move along you'll begin to notice groupings and can grep and rename things as you work.

6.  Now that you have all the pieces, you can start implementing them.

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

As your coding there should be three things you should keep in mind; 1) candidates for Sprite-hood, 2) font sizes and colors and how ultimately can most efficiently organize them, and 3) using CSS to accomplish some of the image effects. For the later I like to start with images that I always have available to me as a default, then begin to use CSS3. In some cases just go with the CSS3 and don't bother with chopping images; like rounded corners because what is the default? A square corner, not a bad degradation.

Here's what the project is looking like so far:

!!! NEED AN IMAGE !!!

### Step 4 -  Navigation


### Step  - Grouping Content

Now we get down to the nitty-gritty and for this I'm just going to give you some references that might help you hone your skills:

[Grouping content][]
[Content models][]

### Step  - Sprites



[grid system]:          http://www.subtraction.com/pics/0703/grids_are_good.pdf
[grid-background]:      http://compass-style.org/reference/compass/layout/grid_background/
[Containing DIV]:       http://stackoverflow.com/questions/354739/why-should-i-use-a-container-div-in-html
[Containing BODY]:      http://csswizardry.com/2011/01/using-the-body-element-as-a-wrapper/
[Flowchart]:            http://html5doctor.com/downloads/h5d-sectioning-flowchart.png
[Structural Tags]:      http://orderedlist.com/resources/html-css/structural-tags-in-html5/
[Not Obvious]:          http://www.anthonycalzadilla.com/2010/08/html5-section-aside-header-nav-footer-elements-not-as-obvious-as-they-sound/           
[Beautiful HTML]:       http://css-tricks.com/what-beautiful-html-code-looks-like/

[Grouping content]:     http://developers.whatwg.org/grouping-content.html
[Content models]:       http://developers.whatwg.org/content-models.html

