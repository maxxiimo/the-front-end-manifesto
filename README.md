Rails Views
===========

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

- [Front End Coder's Manifesto][The Manifesto]
- [Foundation Markup][]
  -  Groundwork
    - .gemfile
    - .gitignore
  -  The Application Layout
    - A Framework within a Framework
    - Where Does It Live?
    - The Code
    - Where Do Things Go?
    - What to Put in <head>
    - Partials
    - The Title
    - JavaScript
  - Moving Forward
    - Naming Conventions
    - Using Partials
    - IE 6
  - What We've Done
- [Foundation Styles][]
  - Compass Set Up
  - Stylesheet Set Up
  - CSS Organization
    - Style TOC
    - Resets
  - Moving Forward
    - Modularize Styles
    - Use a Labeling System
    - Naming Conventions
  - Keep it DRY!
    - Consolidate
    - Variables
    - Includes
    - Mixins
- [Preprocessors and Frameworks][]
  - Sass and Less
  - Twitter Bootstrap
  - Compass
  - Blueprint
  - Compressing and the Asset Pipeline
- [Slicing and Dicing Mockups][]
  - Step 1 - Backgrounds
  - Step 2 - Set Widths
  - Step 3 - Fonts
  - Step 4 - Images
  - Step 5 - Sectioning Content (layout/application.html.haml)
  - Step 6 - Start with %header and %footer
  - Step 8 - Navigation
  - Step 9 - HTML for the Main Content
  - Step 10 - Sprites and CSS3 for Images
- [Mobile First][]
  - Where Do Styles Go?
  - User Agents or Media Queries
- [Navigation][]
- [Gradients][]
- [Images][]
  - Organization
  - Choosing an Image Format
  - Spriting
  - Responsive Resizing
  - Retina Displays
- [Forms][]
  - Basic Form Structure
  - Ordered List or Paragraphs?
  - Fieldsets and Legends
  - Extras
  - FormHelpers
- [Optimization][]
- [Refactoring][]
- [Tools][]
  -.gemfile
  -.gitignore
- [Accessibility][]
  - Standardize Your Links
  - Use ARIA Roles
- [Email Coding][]
- [Resets][]
- [Getting the Fonts Right][]
  - font-family
- [Search Engine Optimization][]
- [Style Guides][]
- [Good Advice][]
- [JavaScript Libraries][]
- [Layout][]
  - Organization
  - content_for and :yield
- [Navigation][]
  - Types
  - CSS
  - Context Awareness Patterns
- [Storytelling][]

[The Manifesto]:                     https://github.com/maxxiimo/railsviews/blob/master/The%20Manifesto.md
[Foundation Markup]:                 https://github.com/maxxiimo/railsviews/blob/master/Foundation%20Markup.md
[Foundation Styles]:                 https://github.com/maxxiimo/railsviews/blob/master/Foundation%20Styles.md
[Preprocessors and Frameworks]:      https://github.com/maxxiimo/railsviews/blob/master/Preprocessors%20and%20Frameworks.md
[Mobile First]:                      https://github.com/maxxiimo/railsviews/blob/master/Mobile%20First.md
[Slicing and Dicing Mockups]:        https://github.com/maxxiimo/railsviews/blob/master/Slicing%20and%20Dicing%20Mockups.md
[Navigation]:                        https://github.com/maxxiimo/railsviews/blob/master/Navigation.md
[Gradients]:                         https://github.com/maxxiimo/railsviews/blob/master/Gradients.md
[Images]:                            https://github.com/maxxiimo/railsviews/blob/master/Images.md
[Forms]:                             https://github.com/maxxiimo/railsviews/blob/master/Forms.md
[Optimization]:                      https://github.com/maxxiimo/railsviews/blob/master/Optimization.md
[Refactoring]:                       https://github.com/maxxiimo/railsviews/blob/master/Refactoring.md
[Tools]:                             https://github.com/maxxiimo/railsviews/blob/master/Tools.md
[Accessibility]:                     https://github.com/maxxiimo/railsviews/blob/master/Accessibility.md
[Email Coding]:                      https://github.com/maxxiimo/railsviews/blob/master/Email%20Coding.md
[Resets]:                            https://github.com/maxxiimo/railsviews/blob/master/Resets.md
[Getting the Fonts Right]:           https://github.com/maxxiimo/railsviews/blob/master/Getting%20the%20Fonts%20Right.md
[Search Engine Optimization]:        https://github.com/maxxiimo/railsviews/blob/master/Search%20Engine%20Optimization.md
[Style Guides]:                      https://github.com/maxxiimo/railsviews/blob/master/Style%20Guides.md
[Good Advice]:                       https://github.com/maxxiimo/railsviews/blob/master/Good%20Advice.md
[JavaScript Libraries]:              https://github.com/maxxiimo/railsviews/blob/master/JavaScript%20Libraries.md
[Layout]:                            https://github.com/maxxiimo/railsviews/blob/master/Layout.md
[Navigation]:                        https://github.com/maxxiimo/railsviews/blob/master/Navigation.md
[Storytelling]:                      https://github.com/maxxiimo/railsviews/blob/master/Storytelling.md
