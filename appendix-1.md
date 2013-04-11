Appendix 1
----------

### Groundwork Tasks

With any new Rails application their are some very basic groundwork tasks that should be completed.

#### Task 1: Version Control

In the Rails world Git and Github are the versioning sytem and service of choice. Here are the steps to follow when creating a new Rails application:

    Switch to new project folder.
    $ git init
    $ git add .
    $ git commit -am "Initial commit."
    $ git remote add origin git@github.com:<Github username>/<application name>.git
    Create a new repo at Github.
    $ git push -u origin master

#### Task 2: Remove Unnecessary Files

Out-of-the-box Rails comes with a few files that should be deleted. After testing that your application works, delete:

- public/index.html
- assets/images/rails.png
- app/views/layouts/application.html.erb
- README.rdoc

The last two deletions will be replaced by files from our [starter code][]: *application.html.haml* and *README.md*.

Commit your changes.

#### Task 3: Add Starter Code

Go ahead and copy all the files and folders from your cloned starter code repository into your existing application structure.

Commit your changes.

#### Task 4: Gemfile

With every new application Rails generates a Gemfile with a lot of commented out lines. You don't need all of these comments, they take up a lot of space and clutter things. For our [Gemfile][] we will start with Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" example and add a few additional gems for Compass:

      # Compass specific gems.
      gem 'compass-rails'
      gem 'oily_png'
      gem 'susy'
    end

We replaced the default Gemfile with the one found in the cloned starter code. Install these gems.

IMPORTANT: Michael Hartl [recommends][] using the following flag on your first bundle:

    $ bundle install --without production

Doing so installs your Gemfile gems, but prevents the installation of the production gems. You only have to do this once.

Commit your changes.

#### Task 5: RSpec

To set up rspec run the following:

    $ rails generate rspec:install

Commit your changes.

For faster asset precompiles check out:

- [Turbo Sprockets for Rails 3.2.x][Turbo Sprockets]

#### Task 6: Deployment

Heroku is a cloud application platform used by many members of the Rails community. Deploy to Heroku by running the following commands:

    $ heroku create --stack cedar
    $ git push heroku master
    $ heroku rename <new name>

You will need to set up an account if you don't already have one.

[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[starter code]:         https://github.com/maxxiimo/base-haml
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[recommends]:           http://ruby.railstutorial.org/ruby-on-rails-tutorial-book?version=3.2#sec-heroku_setup
[Turbo Sprockets]:      https://github.com/ndbroadbent/turbo-sprockets-rails3
