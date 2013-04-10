Appendix 1
----------

### Groundwork Tasks

With any new Rails application their are some very basic groundwork tasks that should be completed.

#### Version Control

In the Rails world Git and Github are the versioning sytem and service of choice. Here are the steps I follow when creating a new Rails application:

    $ rails new <name>
    Switch to new project folder.
    $ git init
    $ git add .
    $ git commit -am "Initial commit."
    $ git remote add origin git@github.com:<Github username>/<application name>.git
    Create a new repo at Github.
    $ git push -u origin master

#### Deployment

I like Heroku and deploy to it by running the following commands:

    $ heroku create --stack cedar
    $ git push heroku master
    $ heroku rename <new name>

You will need to set up an account if you don't already have one.

#### Remove Unnecessary Files

Delete:

- public/index.html
- assets/images/rails.png
- app/views/layouts/application.html.erb
- README.rdoc

The last two deletions will be replaced by files from our [starter code][]: *application.html.haml* and *README.md*.

Commit your changes.

#### Gemfile

With every new application Rails generates a Gemfile with a lot of commented out lines. You don't need all of these comments, they take up a lot of space and clutter things up. For our [Gemfile][] we will start with Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" example and add a few additional gems for Compass that we will use:

      # Compass specific gems.
      gem 'compass-rails'
      gem 'oily_png'
      gem 'susy'
    end

Replace the default Gemfile with the one found in your cloned starter code.

IMPORTANT: Michael Hartl [recommends][] using the following flag on your first bundle:

    $ bundle install --without production

Doing so installs your Gemfile gems, but prevents the installation of the production gems. You only have to do this once.

Commit your changes.

#### rspec

To set up rspec run the following:

    $ rails generate rspec:install

Commit your changes.

For faster asset precompiles check out:

- [Turbo Sprockets for Rails 3.2.x][Turbo Sprockets]

#### .gitignore

Many files in a Rails application are not necessary to track or share. Git allows you to ignore these files through .gitignore.

Our [.gitignore][]. file is borrowed from [HTML 5 Boilerplate][H5BP .gitignore]) with a few additions:

    # Local
    scratch.*
    public/source
    vendor/source

You may use these files or folders to save things within the application, but only on your local machine:

- __scratch.*__ - A code graveyard; snippets of code I am no longer using but not yet ready to completely get rid of.

- __public/source__ and __vendor/source__ - Folders for original third-party files or source code integrated into the application; Photoshop files; original images; basically the original copies of where things came from.

Replace the default .gitignore with the one found in your cloned starter code. Commit your changes.

Here are some additional useful .gitignore ideas:

- [Ignore files][]
- [A Collection of Useful .gitignore Templates][Templates]

[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[starter code]:         https://github.com/maxxiimo/base-haml
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[recommends]:           http://ruby.railstutorial.org/ruby-on-rails-tutorial-book?version=3.2#sec-heroku_setup
[Turbo Sprockets]:      https://github.com/ndbroadbent/turbo-sprockets-rails3
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:  http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
[Ignore files]:         http://help.github.com/ignore-files/
[Templates]:            https://github.com/github/gitignore
