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

Start with the background. This manifesto is not a course on CSS, but backgrounds are generally single colors like eggshell white, a repeating pattern, or a color with a horizontal gradient. They rarely are a large image because these take up a lot of bandwidth. To implement your background set your body background-color property either to a specific color, or the background property to a repeating image. If you're using my organization structure the body tag can be found in the _layout.sass file. If a gradient is involved you can use CSS 3 or an image to achieve the effect. Whatever images you do use for the background, make it as small and optimized as possible without losing the effect you want when repeated.

Remember, when using Compass use image-url("") instead of url():

    background: image-url("fixtures/bg-texture.gif")

### Step 2 - Sectioning Content

Here's where we really begin to code the basic high-level questions above. Think in terms of your base layout in layout/application.html.haml. I typically start a project using my base template described in the HTML Organization section, then review the mockup from top to bottom and adjust my base template or incorporate elements into it. Here are a few resources that will help you choose semantically correct elements:

[HTML5 Element Flowchart][Flowchart]
[Structural Tags in HTML5][Structural Tags]
[HTML5 section, aside, header, nav, footer elements – not as obvious as they sound][Not Obvious]
[What Beautiful HTML Code Looks like][Beautiful HTML]



### Step  - Grouping Content

Now we get down to the nitty-gritty and for this I'm just going to give you some references that might help you hone your skills:

[Grouping content][]
[Content models][]

[grid system]:          http://www.subtraction.com/pics/0703/grids_are_good.pdf
[grid-background]:      http://compass-style.org/reference/compass/layout/grid_background/
[Flowchart]:            http://html5doctor.com/downloads/h5d-sectioning-flowchart.png
[Structural Tags]:      http://orderedlist.com/resources/html-css/structural-tags-in-html5/
[Not Obvious]:          http://www.anthonycalzadilla.com/2010/08/html5-section-aside-header-nav-footer-elements-not-as-obvious-as-they-sound/           
[Beautiful HTML]:       http://css-tricks.com/what-beautiful-html-code-looks-like/

[Grouping content]:     http://developers.whatwg.org/grouping-content.html
[Content models]:       http://developers.whatwg.org/content-models.html

