Foundation Markup
=================

As an Information Architect (IA), when I think about an applications layout I literally think about how a site is "laid out" on a screen. I think in terms of the organization of information and function for an end-user's consumption. In this IA role, when speaking about layout I might say something like, "Wow! That's a great layout," or "I don't like the layout of this site, it's too confusing, maybe you should move this over there."

<br>

![][Layout]

When I switch hats, as a Rails developer, I look at layout as the Rails templating framework in which all of my front end code lives, and from where it will interact via Rails with the outside world.

As a Rails Front End Engineer, you will wear both hats. In [Chapter 6][] we dive deeply into information architecting, but for now our focus will be strictly on laying out our foundation markup, and getting it right per our front end coding [manifesto][Manifesto].

Let's get started.

Views
-----

As much as Rails is a framework, within it lives a smaller templating framework made up of predominantly HTML. These are our views and where we will work in Chapter 1.

View code can be found in two high-level folders within a Rails application: the *helpers* and the *views* folders. Here is where you'll find these folders by default in any Rails 3.0 or greater project:

app<br>
|-- assets<br>
|-- controllers<br>
|-- **helpers**<br>
|-- mailers<br>
|-- models<br>
|-- **views**<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-- **layout**<br>
&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- application.html.haml<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-- **shared**

The *views* folder is where most of the action takes place and can be further subdivided into of the *layout* and *shared* folders, which as you will soon discover are home to the majority of your foundation front end code.

The heart of this view framework is *application.html.haml*. Most view code from other parts of an application pass through and become framed by *application.html.haml* before being served to browsers.

### The Code

To help you along I will provide links to [starter code][] we will use or reference throughout this book. Feel free to use this code for your own projects.

Structurally in a Rails application, our starter code files and folders fall into place as follows:

app<br>
|-- assets<br>
|&nbsp;&nbsp;&nbsp;|-- images<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **fixtures**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **icons**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **logos**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **pics**<br>
|&nbsp;&nbsp;&nbsp;|-- javascripts<br>
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [application.js][]<br>
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [site.js][site]<br>
|-- helpers<br>
|&nbsp;&nbsp;&nbsp;|-- [application_helper.rb][application_helper]<br>
|-- views<br>
|&nbsp;&nbsp;&nbsp;|-- layout<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_chromeframe.html.haml][_chromeframe]<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_head.html.haml][_head]<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [_scripts.html.haml][_scripts]<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- [application.html.haml][application]<br>
|&nbsp;&nbsp;&nbsp;|-- shared<br>
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_footer.html.haml][_footer]<br>
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_logo.html.haml][_logo]<br>
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [_navigation.html.haml][_navigation]<br>
|-- vendor<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-- assets<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- javascripts<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [jquery-1.9.1.min.js][jquery]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [modernizr-2.6.2.min][modernizer]<br>
[.gitignore][]<br>
[Gemfile][]<br>
[README.md][]

The default Rails file structure and application files are pretty much identical. In the next section we will replace some existing files that come out of the box by default with our starter code, and add a few new files and folders (new folders depicted above in bold, new or replacement files are links).

NOTE: Our starter code is an implementation of [HTML5 Boilerplate][] code (v 4.2.0) in haml and arranged for a Rails project. In my experience the best place to reference when building front end view templates is HTML5 Boilerplate. This resource is an ongoing collaboration between expert front end developers and the community. To better understand HTML5 Boilerplate as it applies to Rails, the following article is helpful:

- [Guide to HTML5 Boilerplate for Rails Developers][H5BP for Rails]

Set Up
------

Before we begin to explore the code that make up our views, there are a few things you will need to do to follow along with this book:

1.  Clone this books [starter code][]:

        git clone git@github.com:maxxiimo/base-haml.git

2.  Create a brand-new Rails 3.2 application.

        $ rails new <name>

    NOTE: A great reference for doing this correctly is Chapter 1 of Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

3. Complete the groundwork tasks.

4. Prep and launch your application

### Groundwork Tasks

With any new Rails application their are some very basic groundwork tasks that should be completed.

#### Task 1: Version Control

In the Rails world [Git][] and [Github][] are the versioning sytem and service of choice. Here are the steps to follow when creating a new Rails application:

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

The last two deletions will be replaced in the next task by files from our [starter code][]: *application.html.haml* and *README.md*.

Commit your changes.

#### Task 3: Add Starter Code

Go ahead and copy all the files and folders from your cloned starter code repository into your existing application structure.

Commit your changes.

The following files should have been modified or added to your repository:

![][New Files]

#### Task 4: Gemfile

With every new application Rails generates a Gemfile with a lot of commented out lines. You don't need all of these comments, they take up a lot of space and clutter things up. For our [Gemfile][] we will start with Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" Gemfile example and add a few additional gems we will use like Compass:

      # Compass specific gems.
      gem 'compass-rails'
      gem 'oily_png'
      gem 'susy'

Or some better error testing gems, which you may uncomment if you plan to use them:

      # http://railscasts.com/episodes/402-better-errors-railspanel
      # gem 'better_errors'
      # gem 'binding_of_caller'
      # gem 'meta_request'

After replacing the default Gemfile with the one found in the cloned starter code, bundle install these gems.

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

[Heroku][] is a cloud application platform used by many members of the Rails community. If you do not already have a Heroku account, you will need to open an account with Heroku, and [set up your computer][Heroku Set Up] with that account. Deploy to Heroku by running the following commands:

    $ heroku create --stack cedar
    $ git push heroku master
    $ heroku rename <new name>

And that's it! Now it's time to Prep and Launch your application.

### Prep and Launch

Prep and the launch your app by following these steps:

**Step 1** - If you do not have a page for your routes to go to, which I'm assuming you don't if this is a brand-new application, create one now. Generate a pages controller with some very basic static pages:

    $ rails generate controller Pages home about site_map terms privacy contact

Make sure to delete the *assets/stylesheets/pages.css.scss* file generated by Rails, we won't be using it. You can also delete *assets/javascripts/pages.js.coffee* if you do not plan to use it.

Commit your changes.

NOTE: If you're not sure what I just did there you should really consider getting Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

**Step 2** - Change your default route to whatever you want your application to default to, and swap out your get routes with match routes:

    # You can have the root of your site routed with "root"
    # just remember to delete public/index.html.
    root :to => 'pages#home'

    match 'home'    => 'pages#home'
    match 'about'   => 'pages#about'
    match 'team'    => 'pages#site_map'
    match 'terms'   => 'pages#terms'
    match 'privacy' => 'pages#privacy'
    match 'contact' => 'pages#contact'

Commit your changes.

**Step 3** - Finally, it's time to launch! If you run WEBrick, your application should now just work with the following command:

    $ rails server

...and in your browser location box type:

    localhost:3000

And with that you should see something like this:

<br>

![][Basic HTML]

Not very attractive! ...but don't worry we'll address that in [Chapter 3][]. What's important here is what's under the hood: an excellent foundation markup base to work with moving forward. In the [next chapter][Chapter 2] we will explore exactly that, what's under the hood.

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/the-manifesto.md
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp2-markup-review.md
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md
[Chapter 6]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp6-information-architecting.md

[starter code]:         https://github.com/maxxiimo/base-haml
[application.js]:       https://github.com/maxxiimo/base-haml/blob/master/assets/javascripts/application.js
[site]:                 https://github.com/maxxiimo/base-haml/blob/master/assets/javascripts/site.js
[application_helper]:   https://github.com/maxxiimo/base-haml/blob/master/helpers/application_helper.rb
[_chromeframe]:         https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_chromeframe.html.haml
[_head]:                https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_head.html.haml
[_scripts]:             https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_scripts.html.haml
[application]:          https://github.com/maxxiimo/base-haml/blob/master/views/layouts/application.html.haml
[_footer]:              https://github.com/maxxiimo/base-haml/blob/master/views/shared/_footer.html.haml
[_logo]:                https://github.com/maxxiimo/base-haml/blob/master/views/shared/_logo.html.haml
[_navigation]:          https://github.com/maxxiimo/base-haml/blob/master/views/shared/_navigation.html.haml
[jquery]:               https://github.com/maxxiimo/base-haml/blob/master/vendor/assets/javascripts/jquery-1.9.1.min.js
[modernizer]:           https://github.com/maxxiimo/base-haml/blob/master/vendor/assets/javascripts/modernizr-2.6.2.min.js
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[README.md]:            https://github.com/maxxiimo/base-haml/blob/master/README.md
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[H5BP for Rails]:       http://railsapps.github.com/rails-html5-boilerplate.html

[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2

[Git]:                  http://git-scm.com/
[Github]:               https://github.com/
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[recommends]:           http://ruby.railstutorial.org/ruby-on-rails-tutorial-book?version=3.2#sec-heroku_setup
[Turbo Sprockets]:      https://github.com/ndbroadbent/turbo-sprockets-rails3
[Heroku]:               https://id.heroku.com/signup
[Heroku Set Up]:        https://devcenter.heroku.com/articles/quickstart

[New Files]:            Http://chrismaxwell.com/manifesto/appendices/new-files.gif
[Layout]:               http://chrismaxwell.com/manifesto/chp-1/layout-sm.png
[Basic HTML]:           http://chrismaxwell.com/manifesto/chp-1/basic-html.png

