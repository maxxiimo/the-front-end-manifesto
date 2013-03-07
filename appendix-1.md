Appendix 1
----------

### Groundwork Tasks

With any Rails application their are some very basic groundwork tasks that needs to be done; creating the application and using some kind of versioning system. In the Rails world Git and Github are the versioning sytem and service of choice. Here are the steps I follow to set this up:

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

    gem 'rails', '3.2.12'

    gem 'jquery-rails', '2.0.2'
    gem 'haml-rails'

    group :development, :test do
      gem 'sqlite3', '1.3.5'
      gem 'rspec-rails', '2.11.0'
    end

    # Gems used only for assets and not required
    # in production environments by default.
    group :assets do
      gem 'sass-rails', '3.2.5'
      gem 'coffee-rails', '3.2.2'
      gem 'uglifier', '1.2.3'

      # Compass specific gems.
      gem 'compass-rails'
      gem 'oily_png'
      gem 'susy'
    end

    # See https://github.com/ndbroadbent/turbo-sprockets-rails3
    # gem 'turbo-sprockets-rails3'

    group :production do
      gem 'pg', '0.12.2'
    end

Since I typically use compass, I added the compass-rails and oily_png gems and the Susy plugin as well.

NOTE: Michael Hartl [recommends][] using the following flag on your first bundle:

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

[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[recommends]:           http://ruby.railstutorial.org/ruby-on-rails-tutorial-book?version=3.2#sec-heroku_setup
[Turbo Sprockets]:      https://github.com/ndbroadbent/turbo-sprockets-rails3
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:  http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
[Ignore files]:         http://help.github.com/ignore-files/
[.gitignore]:           https://github.com/github/gitignore
