Slicing and Dicing Mockups
--------------------------

Take a look at the whole for a few minutes. Just absorb it, understand it.

Then look at the major layout elements, i.e. the framework of the site, and begin to ask yourself some basic high-level questions like:

1.  How wide is it? 960px, 980px, 1040px?

2.  Is the width fluid or static?

3.  Can it be divided into 3 major sections: header, body, footer?

4.  Where is the main navigation? Is there a utility navigation? Is the navigation tabs, links, what?

5.  Is the footer stuck on the bottom or flow with the text?

6.  Does the designer use a grid system?

7.  Is the header the same width as the main body?

8.  Are gradients used? In the header and outer sides of the main body?

9.  Where's the logo? Will need special attention?

10. Anything interesting going on with the background?

When you finish answering these questions you can then start to write code that will hold these elements. This initial base HTML layout is the most important step in the process. Take your time, think about semantics, how sections will interrelate and in some cases interact; how they may be affected by future changes; compartmentalize things in such a way that your code is efficient, organized, and less likely to require repetition (as in DRY).

As the underlying structure comes together in your mind, you can start to look at content within the body, the overall look and feel derived from colors and fonts, and you can begin to start to think about whether you will use CSS or JavaScript to create various effects.

The truth of a matter as slicing mockups is pretty easy and straightforward because there are only so many ways to organize a page layout, and all of the components within a page layout are pretty standard, I mean you have paragraphs and headers and links, the way to get around through navigation, and so forth. At the same time since a designer's artistic expression and look and feel of the site is very subjective mockup to mockup it requires a certain amount of art based on experience. There is no formula for doing it, just basic guidelines.


### Backgrounds

Backgrounds are generally single colors like eggshell white, a repeating pattern, or a color with a horizontal gradient. Rarely are they a giant image because these take up a lot of bandwidth. Set the background-color property either to a specific color or a repeating image. If the gradient is involved you can use CSS 3 or an image. Whatever images you do use for the background, make them as small as possible that will allow you the same time to create the affect when repeated.