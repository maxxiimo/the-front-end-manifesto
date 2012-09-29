Getting Started
---------------

### Groundwork

Assuming you just created a brand spanking new rails application, I would set up the following right off the bat:

#### .gemfile

Your .gemfile will change radically throughout the lifespan of your project. With a new application you typically get something like this:

    source 'https://rubygems.org'
    
    gem 'rails', '3.2.8'
    
    # Bundle edge Rails instead:
    # gem 'rails', :git => 'git://github.com/rails/rails.git'
    
    gem 'sqlite3'
    
    
    # Gems used only for assets and not required
    # in production environments by default.
    group :assets do
      gem 'sass-rails',   '~> 3.2.3'
      gem 'coffee-rails', '~> 3.2.1'
    
      # See https://github.com/sstephenson/execjs#readme for more supported runtimes
      # gem 'therubyracer', :platforms => :ruby
    
      gem 'uglifier', '>= 1.0.3'
    end
    
    gem 'jquery-rails'
    
    # To use ActiveModel has_secure_password
    # gem 'bcrypt-ruby', '~> 3.0.0'
    
    # To use Jbuilder templates for JSON
    # gem 'jbuilder'
    
    # Use unicorn as the app server
    # gem 'unicorn'
    
    # Deploy with Capistrano
    # gem 'capistrano'
    
    # To use debugger
    # gem 'debugger'

I like to get rid of all the scruff which leaves me with:

source 'https://rubygems.org'

    gem 'rails', '3.2.8'
    
    gem 'sqlite3'
    
    group :assets do
      gem 'sass-rails',   '~> 3.2.3'
      gem 'coffee-rails', '~> 3.2.1'
      gem 'uglifier', '>= 1.0.3'
    end
    
    gem 'jquery-rails'

There of certain things that I know I will work with, and borrowing from the best I use Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" .gemfile example to organize my base .gemfile as follows:

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
      gem 'compass-rails'
      gem 'coffee-rails', '3.2.2'
      gem 'uglifier',     '1.2.3'
    end
    
    gem 'jquery-rails',   '2.0.2'
    gem 'haml-rails'
    
    group :test do
      gem 'capybara',     '1.1.2'
    end
    
    group :production do
      gem 'pg',           '0.12.2'
    end

Since I typically use compass, I added the compass-rails gem here. You may not want to. If you do, a smart choice, check out the [Using Compass][] chapter of this book.

#### .gitignore

Here's what I use, mostly borrowed from [HTML 5 Boilerplate][H5BP .gitignore] and Michael Hartl's [Ruby and Rails Tutorial][RoR Tutorial]:

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

The last section contains files or folders I like to use to save things within the application, but only on my local machine.

- I use scratch.* as a code graveyard: snippets of code I am no longer using but not yet ready to completely get rid of.

- The public/source folder is an area I put original files or source code from 3rd parties that I have integrated
  into my application, Photoshop files, original images, etc.. Basically the original copies of where things came from.

Some additional useful ideas:

[Ignore files][]
[A Collection of Useful .gitignore Templates][.gitignore]

### HTML5

The best place to get started with your underlying HTML5 is:

[HTML5 Boilerplate][]
[An Unofficial Guide to the HTML5 Boilerplate][Unofficial Guide]
[Guide to HTML5 Boilerplate for Rails Developers][Boilerplate for Rails]

Here's my implementation, and all in Haml:

[ADD LINK HERE]

#### What to Put in <head>

There are a lot of things that you could put in your <head> tags, but don't. Obviously just put in What you need. I provide the bare minimum, but everything else as well only commented out:

[ADD GITHUB LINK HERE]

For an explanation on what this stuff is/does check out these two sources:

<https://gist.github.com/1981339>
<http://html5boilerplate.com/docs/html-head/>




[Modernizr HTML5-Cross-browser-Polyfills][]




### CSS




[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[RoR Tutorial]:         http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
                        "An augmented .gitignore file"
[Ignore files]:         http://help.github.com/ignore-files/
[.gitignore]:           https://github.com/github/gitignore
[Using Compass]:        https://github.com/maxxiimo/railsviews/blob/master/Using%20Compass.md
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[Unofficial Guide]:     http://railsapps.github.com/rails-html5-boilerplate.html
[H5BP for Rails]:       http://railsapps.github.com/rails-html5-boilerplate.html
