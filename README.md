Front End Code Manifesto
========================

by Chris Maxwell

*High-performing, efficient,*  
*Un-bloated,*  
*Modularized and Organized*

**Front End Code**


Personal views and direction on front end coding, from a Ruby on Rails perspective.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/">
  <img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png" /></a>
<br />This work is licensed under a 
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License</a>.


Table of Contents
-----------------

- The Manifesto
- Preprocessors and Frameworks
  - Sass and Less
  - Twitter Bootstrap
  - Compass
  - Blueprint
  - Compressing and the Asset Pipeline
- CSS Organization
  - Rails Manifest vs. Sass Partials
  - Use Labeling System
  - Naming Conventions
- Mobile First
  - Where Do Styles Go?
  - User Agents or Media Queries
- HTML Organization
  - Where to Put Things
  - IE 6
  - %head and Boilerplate
  - The Title
  - JavaScript
- Slicing and Dicing Mockups
  - Step 1 - Backgrounds
  - Step 2 - Set Widths
  - Step 3 - Fonts
  - Step 4 - Sectioning Content (layout/application.html.haml)
  - Step 5 - Start with %header and %footer
  - Step 6 - Navigation
  - Step 7 - HTML for the Main Content
  - Step 8 - Sprites and CSS3
- Images
  - Organization
  - Choosing an Image Format
  - Spriting
  - Responsive Resizing
- Optimization
- Refactoring
- Tools
- Accessibility
  - Standardize Your Links
  - Use ARIA Roles
- Email Coding
- .gemfile
- .gitignore
- Resets
- Getting the Fonts Right
  - font-family
- Optimization
- Search Engine Optimization
- Style Guides
- Good Advice
- JavaScript Libraries
- Layout
  - Organization
  - content_for and :yield
- Navigation
  - Types
  - CSS
  - Context Awareness Patterns
- Storytelling


### Fancy/Sassy Buttons

To great compass plug-in resources available to you for creating good-looking cross browser buttons are [Fancy Buttons][] and [Sassy Buttons][]. Whichever you choose to use, this is how you would install the plug-in:

**Step 1**

Add the gem 'fancy-buttons' or gem 'sassy-buttons' to assets group of your gemfile:

    group :assets do
      gem 'sass-rails',   '~> 3.2.3'
      gem 'coffee-rails', '~> 3.2.1'
      gem 'uglifier', '>= 1.0.3'
    
      # Compass specific gems.
      gem 'compass-rails'
      gem 'fancy-buttons'
      gem 'sassy-buttons'
      gem 'oily_png'
    end

**Step 2**

Import it, preferably from application.scss per the CSS Organization chapter:

    /* FORMS
      ============================================================================ */
    @import "fancy-buttons";
    @import "sassy-buttons";
    @import "forms";

IMPORTANT: Make sure your import appears before wherever you include the button mixin, otherwise you will get an error. In my case the mixin was found in "forms", and I made the mistake of placing my import below @import "forms". I was scratching my head for an hour before I realized the stupid mistake!

**Step 3**

bundle install

**Step 4**

Install button assets:

    bundle exec compass install fancy-buttons
    
    or
    
    bundle exec compass install sassy-buttons

**Step 5**

Include the most basic mixin and expand from there:

    button
      +fancy-button or +sassy-button
    
    alternatively (syntax)...
    
    button
      @include fancy-button or @include +sassy-button

[Fancy Buttons]:        http://brandonmathis.com/projects/fancy-buttons/
[Sassy Buttons]:        http://jaredhardy.com/sassy-buttons/
