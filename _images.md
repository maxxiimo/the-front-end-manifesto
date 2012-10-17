Images
------

### Organization

Start off by creating some basic folders to hold things as you develop such as:

    - assets
    
      - images
        - buttons
        - fixtures*
        - icons
        - logos
    
      - javascripts
      - stylesheets

* Regarding the name "fixtures", I used to call this "assets" before the asset pipeline, but fixtures will do until I think of a better name. It holds things like shims, navigation-pipes, horizontal dividers, basically things that are used to construct an application/page.

Usually my root level folder "images" contains sprites. The corresponding sprite components remain in their appropriate folders like icons, and I use Compass to create my sprites per the Spriting section below. So with an icons sprite my folders might look like this:

    - assets
    
      - images
        - buttons
        - fixtures*
        - icons
          icon1.gif
          icon1.png
          icon2.gif
          icon2.png
          icon3.gif
          icon3.png
        - logos
        icon-sprite.png
        icon-sprite.gif
    
      - javascripts
      - stylesheets

Everything has a place to go, and easily find later. As sites grow your image folders can get out of hand so start with an organization plan in mind. In fact I would just add these folders right off the bat.

### Choosing an Image Format

When saving images I always save a .gif version in addition to a .png, just in case. Ideally images will be displayed as .PNG's, but because of issues with older browsers and other edge cases in which PNG fixes won't suffice I have found having them on hand is a great thing, and creating them at the same time you create your PNG's is easy for yyou or your designer. If you have to support IE6, I prefer to serve these up rather than use a PNG fix.

[Notes on Using PNGS][PNGS]

.jpg's are really reserved for photos and not efficient for things like sprites, structural imagery, plus they do not preserve alpha transparencies which become an issue if backgrounds change in the future (kind of following in a roundabout way the old adage; "measure twice, cut once."). This article gives a good explanation of which to use and when: [Gif Png Jpg Which One To Use][Image Choice]

### optimizing

See Optimization chapter.

### Spriting

I let Compass do all the sprite creation work. Ryan Bates provides an excellent tutorial on [Compass & CSS Sprites][Sprites]. If you or a designer are creating them in most cases it actually is better on the implementation side to have icon sprites line up horizontally (as opposed to vertically). Line up the top edge of each icon on an equidistant grid line whose coordinate is a multiple of 5 pixels, and not picas. For example, the horizontal grid line coordinates for 4 icons that are 16px x 16px might be:

0 (first image)
20px
40px
60px

Using these coordinates make it easier for front end people to map them, so the coresponding code in my stylesheet would use the following XY values for positioning:

0, 0
0, -20px
0, -40px
0, -60px

???? The reason for horizontal alignment is that side-by-side requires a specifically sized element to display the icon in, whereas one single horizontal line of icons can use a specific element to display, or background positioning in the greater containing element such as an anchor tag or a list item. This in turn minimizes the amount of code served and provides for better organization and element manipulation on the coding side. It also marginally future proofs any design changes.

Since yours are:

"Icons for Impact area are ."

Experience has shown me that having extra pixels of blankness between icons can be beneficial. For example, if icons are 28px x 28px, 35px or even 40px gridlines would be good, but not 30px. 

### Responsive Resizing

Rather than tell you how to do it, I'm going to give you some of the best options an explanations out there.

...But I will say that of all the options here, I'm thinking I like [Picturefill][] the best:

> A Responsive Images approach that you can use today, that mimics the proposed picture element using divs, for safety sake.

[24 Ways][] has two good articles on the subject:

[Adaptive Images for Responsive Designs][24 Ways 1]
[Adaptive Images for Responsive Designs… Again][24 Ways 2]

[Better background images for responsive web design][Background Images] does a great job explaining the problem with placing images and knowing where their center is as images are resized, and in a nutshell:

> So what we need is a way for the image to fill both its width and its height at all times, while retaining proportion...

The author then goes on to recommend [jQuery Anystretch][]:

> Anystretch is a jQuery plugin that allows you to add a dynamically-resized background image to any page or block level element. The image will stretch to fit the page/element, and will automatically resize as the window size changes.

When it comes to CSS, [A List Apart][ALA] is a maverick and authority in the field. [Fluid Images][] is a great article/tutorial on the subject of responsive images.

When it comes to responsive web design and progressive enhancements, Filament Group wrote the books (actually two of their books are titles exactly that). [Responsive Images: Experimenting with Context-Aware Image Sizing][Filament] describes a technique using a combination of JavaScript and .htaccess. I'm not recommending this technique, but if you're interested it's worth taking a look.

### Retina Displays

[Clear Eyes][]
[Mo’ Pixels Mo’ Problems][Mo’ Pixels]

> This makes is super easy to handle Retina images in your Rails 3.1+ apps. It adds r_image_tag that can be used in place of the existing image_tag and it'll automatically serve up Retina images to devices that can handle the resolution and normal images otherwise.

[ARIA roles]:           http://www.w3.org/TR/wai-aria/roles#landmark_roles
[PNGS]:                 http://html5boilerplate.com/docs/Using-PNG/
[Sprites]:              http://railscasts.com/episodes/334-compass-css-sprites
                        "Learn how to make CSS sprites with Compass."
[Image Choice]:         http://blogs.sitepoint.com/gif-png-jpg-which-one-to-use/
[Picturefill]:          https://github.com/scottjehl/picturefill/
[24 Ways]:              http://24ways.org/
[24 Ways 1]:            http://24ways.org/2011/adaptive-images-for-responsive-designs
[24 Ways 2]:            http://24ways.org/2011/adaptive-images-for-responsive-designs-again
[Background Images]:    http://elliotjaystocks.com/blog/better-background-images-for-responsive-web-design/
[jQuery Anystretch]:    https://github.com/danmillar/jquery-anystretch
[ALA]:                  http://www.alistapart.com/
[Fluid Images]:         http://www.alistapart.com/articles/fluid-images/
[Filament]:             http://filamentgroup.com/lab/responsive_images_experimenting_with_context_aware_image_sizing/
[Clear Eyes]:           https://github.com/superacidjax/clear_eyes?utm_source=rubyweekly&utm_medium=email
[Mo’ Pixels]:           http://www.alistapart.com/articles/mo-pixels-mo-problems/
