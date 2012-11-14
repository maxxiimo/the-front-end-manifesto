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
