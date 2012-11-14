Appendices
----------

### Groundwork

Wih any Rails application their is some very basic groundwork that needs to be done; creating the application and using some kind of versioning system. In the Rails world Git and Github are the versioning sytem and service of choice. Here are the steps I follow to set this up:

    $ rails new <name> --no-test-framework
    Switch to new project folder.
    $ git init
    $ git add .
    $ git commit -am "Initial commit."
    $ git remote add origin git@github.com:<Github username>/<application name>.git
    Create a new repo at Github.
    $ git push -u origin master

Next, I immediately copy my standard boilerplate Gemfile and .gitignore files into my application, and deploy to Heroku.

#### Gemfile

With every new application Rails generates a Gemfile with a lot of commented out lines. You don't need all of these comments, they take up a lot of space and clutter things up. Once removed here is what your left with:

    source 'https://rubygems.org'

    gem 'rails', '3.2.8'

    gem 'sqlite3'

    group :assets do
      gem 'sass-rails',   '~> 3.2.3'
      gem 'coffee-rails', '~> 3.2.1'
      gem 'uglifier', '>= 1.0.3'
    end

    gem 'jquery-rails'

To this I add the gems that I know I will use, and in my case Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" Gemfile example pretty much sums up my base [Gemfile][] with a few minor additions:

    source 'https://rubygems.org'

    gem 'rails', '3.2.8'

    group :development, :test do
      gem 'sqlite3',      '1.3.5'
      gem 'rspec-rails',  '2.11.0'
    end

    # Gems used only for assets and not required
    # in production environments by default.
    group :assets do
      gem 'sass-rails',   '3.2.5'
      gem 'coffee-rails', '3.2.2'
      gem 'uglifier',     '1.2.3'

      # Compass specific gems.
      gem 'compass-rails'
      gem 'oily_png'
    end

    gem 'jquery-rails',   '2.0.2'
    gem 'haml-rails'

    # See https://github.com/ndbroadbent/turbo-sprockets-rails3
    # gem 'turbo-sprockets-rails3'

    group :test do
      gem 'capybara',     '1.1.2'
    end

    group :production do
      gem 'pg',           '0.12.2'
    end

Since I typically use compass, I added the compass-rails and oily_png gems as well.

NOTE: Michael Hartl recommends using the following flag on your first bundle:

    $ bundle install --without production

Doing so installs your Gemfile gems, but prevents the installation of the production gems. You only have to do this once.

Finally, you should set up rspec now:

    $ rails generate rspec:install

For faster asset precompiles check out:

- [Turbo Sprockets for Rails 3.2.x][Turbo Sprockets]

#### .gitignore

For my [.gitignore][] file here is what I use (mostly borrowed from [HTML 5 Boilerplate][H5BP .gitignore]):

    # Ignore bundler config
    /.bundle

    # Ignore the default SQLite database
    /db/*.sqlite3

    # Ignore all logfiles and tempfiles
    /log/*.log
    /tmp

    # Numerous always-ignore extensions
    *.diff
    *.err
    *.orig
    *.log
    *.rej
    *.swo
    *.swp
    *.vi
    *~
    *.sass-cache

    # OS or Editor folders
    .DS_Store
    Thumbs.db
    .cache
    .project
    .settings
    .tmproj
    *.esproj
    nbproject
    *.sublime-project
    *.sublime-workspace

    # Dreamweaver added files
    _notes
    dwsync.xml

    # Komodo
    *.komodoproject
    .komodotools

    # Folders to ignore
    .hg
    .svn
    .CVS
    intermediate
    publish
    .idea
    doc/

    # Local
    scratch.*
    public/source

NOTE: The last section "Local" contains files or folders I use to save things within the application, but only on my local machine:

- __scratch.*__ - I use this as a code graveyard; snippets of code I am no longer using but not yet ready to completely get rid of.

- __public/source__ - A folder for original third-party files or source code integrated into my application; Photoshop files; original images; basically the original copies of where things came from.

Here are some additional useful .gitignore ideas:

- [Ignore files][]
- [A Collection of Useful .gitignore Templates][.gitignore]

#### Deployment

Finally I deploy on Heroku by running the following commands:

    $ heroku create --stack cedar
    $ git push heroku master
    $ heroku rename <new name>

Obviously, I already have an account.

### Frameworks

Frameworks give you a whole boatload of base styles that are instantly accessible through your HTML tags or specified class names. Frameworks include base font sizes and rhythm, default formats for almost every kind of HTML tag, and by simply dropping in the frameworks class names you can add some great looking styles to your project that are built to work, with very few hitches, across all browsers. On top of that you get grid systems, prebuilt scripts for commonly used functions like pop-ups, modals and menu systems. The list goes on.

In so far as responsive frameworks go, the following article gives you a nice comparison:

- [Responsive CSS Framework Comparison][Framework Comparison]

Here is a brief framework roundup worth taking a look at for your project.

#### Compass

So right off the bat I have to say that I love [Compass][]. It's powerful, it's well-documented, it's widely used, there are a ton of extensions for it, and it generally makes life easier for me.

> Compass is an open-source CSS Authoring Framework.

I'm pretty biased on this one, and all the [starter CSS ][] files we will use in our foundation styles incorporate Compass so there's not much else to say other than that it almost doesn't belong in this section since it's really not a framework but rather a utility. It's here though because you can add all kinds of framework components like:

- [Responsive grids for Compass][Responsive Grids] or [Zen Grids][]
- [Sassy Buttons][] or [Fancy Buttons][]

...and essentially create your own look and feel. Most traditional frameworks on the other hand just give you styles. If you want to break free it takes some tinkering.

When working with Compass the following resource may be useful to you:

- [35 Great Resources for Compass and Sass][35 Great Resources]

#### Twitter Bootstrap

I like [Twitter Bootstrap][]. It's a great place to learn about best practices for any application or framework, and you can get some amazing designs in absolutely no time. It's well-documented, but here's the problem: it's built on [Less][], and use it and your site will look pretty much like everyone else's. Of course you can override styles, but I'm just sayin'.

> Sleek, intuitive, and powerful front-end framework for faster and easier web development.

Getting it to work with Rails is not impossible, hardly, but if you go this path there are some choices to consider:

- [Twitter Bootstrap, Less, and Sass: Understanding Your Options for Rails 3.1][Options]

#### Blueprint

[Blueprint][], in my opinion, is the granddaddy of all frameworks. I used to use Blueprint all of the time, and Compass makes it readily available. It's tried-and-true, and a good choice, but I rarely use it these days. I'm not too crazy about it's look and feel. It does seem to be more of a minimalist framework - which is not a bad thing.

> Blueprint is a CSS framework, which aims to cut down on your development time. It gives you a solid foundation to build your project on top of, with an easy-to-use grid, sensible typography, useful plugins, and even a stylesheet for printing.

#### YUI

 I've used YUI and personally I'm not too crazy about its grid system which is a pretty major component to any framework - so I generally stay away.

> YUI is a free, open source JavaScript and CSS library for building richly interactive web applications.
\- [YUI website][]

#### Foundation 3

I haven't used Foundation, but I'm interested.

> The most advanced responsive front-end framework in the world.
\- [Zurb website][]

#### Skeleton

I also haven't use Skeleton, but soon enough.

> A Beautiful Boilerplate for Responsive, Mobile-Friendly Development
\- [Skeleton website][]

### Grid Systems

You just can't believe how many grid system there are out there so here is a roundup for you to choose from (in alphabetical order):

1.  [320 and Up][]

    > ‘320 and Up’ is a lightweight, easy to use and content first responsive web design boilerplate.

2.  [34Grid][]

    > 34Grid is a Responsive Grid System based on "equally distributed columns" layout basis. In contrast to other great grid systems (@see bottom of page), 34Grid provides equally distributed columns for each row. (and also column complements for inequal distributions)

3.  [Columnal][]

    > The Columnal CSS grid system is a “remix” of a couple others with some custom code thrown in. The elastic grid system is borrowed from cssgrid.net, while some code inspiration (and the idea for subcolumns) are taken from 960.gs.

4.  [Frameless][]

    > Dig responsive design? Hate fluid grids? Try a Frameless grid.

5.  [Golden Grid System ][]

    > A folding grid for responsive design.

6.  [Fluid Baseline Grid System][]

    > The FBG system was built with typographic standards in mind and combines principals of fluid-column layouts, baseline grids and mobile-first responsive design into a resolution independent and device agnostic framework.

7.  [Responsive GS][]

    > Fluid grid CSS framework for fast, intuitive development of responsive websites. Available in 12, 16 and 24 columns with media queries for all standard devices, clearfix, and optional reset.

8.  [Responsive Grid System][]

    > The Responsive Grid System isn't a framework. It's not a boilerplate either. It's a quick, easy & flexible way to create a responsive web site.

9.  [rwdgrid][]

    > rwdgrid is just another Grid system based on popular 960grid , which is responsive and ranges from mobile, tablet, laptops and wide screen displays.

10. [SimpleGrid][]

    > Responsive. Infinite nesting. One class per element. Simple.

11. [1140 CSS Grid][]

    > The 1140 grid fits perfectly into a 1280 monitor. On smaller monitors it becomes fluid and adapts to the width of the browser.

12. [Gridiculous][]

    > Gridiculous was created after I tried out a bunch of different responsive grids and realized that none of them offered all of the features I required. First and foremost, I wanted to make sure that the grid would work from a large desktop monitor through to a tablet and all the way down to a mobile phone. That's why Gridiculous starts off at 1200px and works itself down to 320px.

### Mobile Solutions Roundup

To get started, if you're not sure where to begin or as a review, take a look at this round up of mobile solutions:

1.  Ryan Bates screencast "[Mobile Devices][]".

2.  The tutorial "[How to Build a Mobile Rails 3.1 App][How to Build]" demonstrates how to use the [mobylette][] and [jquery_mobile_rails][] gems. The mobylette gem handles requests and allows your controller to respond with a :mobile format, while the jquery-mobile-rails gem adds [jQuery Mobile][] files to your asset pipeline: which helps make everything look great and work like a native mobile app.

3.  Much like mobylette, [mobile-fu][] detects mobile requests and allows your application to respond with a :mobile format.

4.  There is a rack-based detection solution called [mobvious][]:

    > Mobvious detects whether your app / website is being accessed by a phone, or by a tablet, or by a personal computer. You can then use this information throughout your app. (E.g. fork your front-end code with regard to device type. There is a [plugin][mobvious-rails] for Ruby on Rails that helps you with this.)

    The [mobvious-rails][] gem allows you to:

    > Access detected device type easily from controllers and views.<br>
    > Execute code for given device types only. Both in controllers and views.<br>
    > Do the above stuff also in your CoffeeScript.

5.  [Agent_orange][agent_orange] looks interesting. Although stable, it has its issues per the maintainers readme.

6.  [UserAgent][] is a Ruby library that parses and compares HTTP User Agents.

7.  [Browser][] is a gem that allows you to test for the browser being used including mobile browsers, and includes ActionController integration.

8.  In the tutorial "[Mobile Devices and Rails: Maintaining your Sanity][Maintain Sanity]" the author proposes placing mobile templates in a separate directory, then when requests come in from a mobile subdomain, like m.domain.com, these templates are served. If the templates are not available, the requester is served regular view templates; freeing you up from having to create two templates for every action. Users can switch between the two templates, and user agent detection is employed.

9.  If you're looking to beef up your detection capabilities, the following services are available (includes free and paid plans).
    - [Handset Detection][]
    - [Akamai][]
    - [DeviceAtlas][]
    - [scientiamobile][]

10. You can also tap into the [WURFL][] database.

11. Here is a list of "[Mobile Browser ID (User-Agent) Strings][Mobile Strings]" you could incorporate into your project if you wanted to get granular.


[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[Turbo Sprockets]:      https://github.com/ndbroadbent/turbo-sprockets-rails3
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:  http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
[Ignore files]:         http://help.github.com/ignore-files/
[.gitignore]:           https://github.com/github/gitignore

[Framework Comparison]: http://responsive.vermilion.com/compare.php
[Compass]:              http://compass-style.org/
[Sassy Buttons]:        http://jaredhardy.com/sassy-buttons/
[Fancy Buttons]:        http://brandonmathis.com/projects/fancy-buttons/
[Responsive Grids]:     http://susy.oddbird.net/
[Zen Grids]:            http://zengrids.com/
[35 Great Resources]:   http://fuelyourcoding.com/35-great-resources-for-compass-and-sass/
[Twitter Bootstrap]:    http://twitter.github.com/bootstrap/
[Options]:              http://rubysource.com/twitter-bootstrap-less-and-sass-understanding-your-options-for-rails-3-1/
[Blueprint]:            http://www.blueprintcss.org/
[YUI website]:          http://yuilibrary.com/
[Zurb website]:         http://foundation.zurb.com/
[Skeleton website]:     http://www.getskeleton.com/

[320 and Up]:           http://stuffandnonsense.co.uk/projects/320andup/
[34Grid]:               http://34grid.com/
[Columnal]:             http://www.columnal.com/
[Frameless]:            http://framelessgrid.com/
[Golden Grid System ]:  http://goldengridsystem.com/
[Fluid Baseline Grid System]:http://fluidbaselinegrid.com/
[Responsive GS]:        http://responsive.gs/
[Responsive Grid System]:http://www.responsivegridsystem.com/
[rwdgrid]:              http://rwdgrid.com/
[SimpleGrid]:           http://simplegrid.info/
[1140 CSS Grid]:        http://cssgrid.net/
[Gridiculous]:          http://gridiculo.us/

[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices
[mobylette]:            https://github.com/tscolari/mobylette
[jquery_mobile_rails]:  https://github.com/tscolari/jquery-mobile-rails
[How to Build]:         https://dev.tscolari.me/2011/09/15/how-to-build-a-mobile-rails-3-dot-1-app/
[mobile-fu]:            https://github.com/brendanlim/mobile-fu
[jQuery Mobile]:        http://jquerymobile.com/demos/1.2.0/
[mobvious]:             https://github.com/jistr/mobvious
[mobvious-rails]:       https://github.com/jistr/mobvious-rails
[agent_orange]:         https://github.com/kevinelliott/agent_orange
[UserAgent]:            https://github.com/josh/useragent
[Browser]:              https://github.com/fnando/browser
[Maintain Sanity]:      http://erniemiller.org/2011/01/05/mobile-devices-and-rails-maintaining-your-sanity/
[Handset Detection]:    http://code.google.com/p/mobile-device-detection-ruby-on-rails/
[Akamai]:               http://www.akamai.com/html/solutions/mobile_detection_redirect.html
[DeviceAtlas]:          https://deviceatlas.com/
[scientiamobile]:       http://www.scientiamobile.com/
[WURFL]:                http://wurfl.sourceforge.net/
[Mobile Strings]:       http://www.zytrax.com/tech/web/mobile_ids.html
