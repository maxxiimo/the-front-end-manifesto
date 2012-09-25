
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




*Designers should use pixels.*




*don't nest to deep*

#hd
  height: 58px
  background: image-url("fixtures/bg-header.png") 0 0 repeat-x
  background-color: $bg-header

#logo
  float: left
  margin: 16px 0  0
  &:hover
    text-decoration: none
