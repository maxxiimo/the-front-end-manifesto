Foundation Markup
=================

As a Rails Front End Engineer I look at layout as the Rails templating system where all of my front end code lives and interacts – via Rails – with the outside world. In this chapter of *The Front End Manifesto* we will focus on:

1.  Setting up a basic HTML foundation for an application
2.  Getting it right per our [manifesto][Manifesto]

NOTE: [Chapter 1][Chapter 1 - Coding Design] of the sequel to this book, *Coding Design*, provides a great introduction to information architecting in case you're interested.

Views
-----

The templating system and associated files and folders used in Rails are known as Views, the V in an MVC. View code is primarily found in two high-level folders within a Rails 3.0 or greater application: the `helpers` and the `views` folders...

app<br>
├─ assets<br>
├─ controllers<br>
├─ **helpers**<br>
├─ mailers<br>
├─ models<br>
└─ **views**<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ **layout**<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;└─ application.html.haml<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ **shared**<br>

Most of the action takes place in the `views` folder which can be further subdivided into of the `layout` and `shared` folders – home to the majority of your foundation front end code.

The heart of The Rails templating system is `application.html.haml`. View code from other parts of an application pass through and become framed by `application.html.haml` before being served to browsers.

### The Code

To help you build your own foundation markup I will provide links to generic [starter code][]. I will reference this code throughout this book, and feel free to use this code for your own projects.

Structurally our starter code files and folders fall into place as follows:

app<br>
├─ assets<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ images<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ **fixtures**<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ **icons**<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ **logos**<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;└─ **pics**<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;└─ javascripts<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ [application.js][]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [site.js][site]<br>
├─ helpers<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [application_helper.rb][application_helper]<br>
├─ views<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ layout<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ [_chromeframe.html.haml][_chromeframe]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ [_head.html.haml][_head]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;├─ [_scripts.html.haml][_scripts]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;└─ [application.html.haml][application]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ shared<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ [_footer.html.haml][_footer]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ [_logo.html.haml][_logo]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [_navigation.html.haml][_navigation]<br>
├─ vendor<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ assets<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ javascripts<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─ [jquery-1.9.1.min.js][jquery]<br>
&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [modernizr-2.6.2.min][modernizer]<br>
├─ [.gitignore][]<br>
├─ [Gemfile][]<br>
└─ [README.md][]

The default Rails file and starter code structures are pretty much identical by design. In the next section we will start our own implementation of a rails front-end by creating a new Rails application and replacing out-of-the-box Rails files with our starter code. Folders we add are depicted above in bold. New or replacement files include links to their respective github source for your inspection.

NOTE: Our starter code is an implementation of [HTML5 Boilerplate][] code (v 4.2.0) in haml arranged for a Rails project. In my experience the best place to reference when building front-end view templates is HTML5 Boilerplate. This resource is an ongoing collaboration between expert front-end developers and the community. Although slightly dated, the following article provides a decent overview of HTML5 Boilerplate as it applies to Rails:

- [Guide to HTML5 Boilerplate for Rails Developers][H5BP for Rails]

Foundation Set Up
-----------------

Setting up the foundation markup of a Rails application is super straightforward. In fact if I were you I would just bookmark this page and every time you build a new application follow the Groundwork Tasks and [Prep and Launch][] steps below.

NOTE: The secret sauce comes from the starter code, everything else will be pretty routine from application to application.

### Groundwork Tasks

#### Task 1: Clone Starter Code

Clone this books [starter code][]:

    git clone git@github.com:maxxiimo/base-haml.git

#### Task 2: Create a Rails Application

Create a brand-new Rails application:

    $ rails new <name>

NOTE: A great reference for doing this correctly is Chapter 1 of Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

#### Task 2: Version Control

In the Rails world [Git][] and [Github][] are the versioning sytem and service of choice. Here are the steps to follow when creating a new Rails application:

    **switch to the new project folder**

    $ git init
    $ git add .
    $ git commit -am "Initial commit."
    Create a new repo at Github.
    $ git remote add origin git@github.com:<Github username>/<application name>.git
    $ git push -u origin master

#### Task 3: Remove Unnecessary Files

Out-of-the-box Rails comes with a few files that should be deleted. After testing that your application works, delete:

- public/index.html
- assets/images/rails.png
- app/views/layouts/application.html.erb
- README.rdoc

The last two deletions will be replaced in the next task by files from our [starter code][]: `application.html.haml` and `README.md`.

Commit your changes.

#### Task 4: Add Starter Code

Go ahead and copy all the files and folders from your cloned starter code repository into your existing application structure.

NOTE: You should be able to copy/merge the files into your application in one action. They will fall into place or replace existing files correctly.

Commit your changes.

The following files should have been modified or added to your repository:

![][New Files]

#### Task 5: Gemfile

Our starter code [Gemfile][] includes better error testing gems, which you may uncomment if you plan to use them:

      # http://railscasts.com/episodes/402-better-errors-railspanel
      # gem 'better_errors'
      # gem 'binding_of_caller'
      # gem 'meta_request'

Install these gems:

    $ bundle install --without production

IMPORTANT: Michael Hartl [recommends][] using the '--without production' flag on your first bundle. Doing so installs your Gemfile gems, but prevents the installation of production gems. You only have to do this once.

Commit your changes.

#### Task 6: RSpec

To set up rspec run the following:

    $ rails generate rspec:install

Commit your changes.

For faster asset precompiles check out:

- [Turbo Sprockets for Rails 3.2.x][Turbo Sprockets]

#### Task 7: Deployment

[Heroku][] is a cloud application platform used by many members of the Rails community. If you do not already have a Heroku account, you will need to open an account with Heroku, and [set up your computer][Heroku Set Up] with that account. Deploy to Heroku by running the following commands:

    $ heroku create --stack cedar
    $ git push heroku master
    $ heroku rename <new name>

IMPORTANT: You will have problems precompiling `modernizr-2.6.2.min.js`. It's not part of your manifest, therefore you will need to tell Heroku to precompile this file:

Aadd the following to `production.rb`:

    config.assets.precompile += %w( modernizr-2.6.2.min.js )

And that's it! Now it's time to Prep and Launch your application.

### Prep and Launch

**Step 1**: If you do not have a page for your routes to go to, which I'm assuming you don't if this is a brand-new application, create one now. Generate a pages controller with some very basic static pages:

    $ rails generate controller Pages home about site_map terms privacy contact

Make sure to delete the `assets/stylesheets/pages.css.scss` file generated by Rails, we won't be using it. You can also delete `assets/javascripts/pages.js.coffee` if you do not plan to use it.

Commit your changes.

**Step 2**: Change your default route to whatever you want your application to default to, and swap out your get routes with match routes:

    root :to => 'pages#home'

    match 'home'     => 'pages#home'
    match 'about'    => 'pages#about'
    match 'site_map' => 'pages#site_map'
    match 'terms'    => 'pages#terms'
    match 'privacy'  => 'pages#privacy'
    match 'contact'  => 'pages#contact'

Commit your changes.

**Step 3**: Finally, we'll need to do a little housekeeping. If you open `views/layouts/_head.html.haml` you'll notice quite a lot of commented out code. You can safely delete all of this. It's there to give you options, things you could use but are not entirely necessary.

Also, replace the "XXX" with whatever title and description you would like to use.

    %title= content_for?(:title) ? yield(:title) : "XXX"
    -# alternative title format.
    -# %title= content_for?(:title) ? ("XXX - " + yield(:title)) : "XXX"

    %meta{:name => "description", :content => "XXX"}

NOTE: For title formats you have two choices. Choose one and delete the other. To yield a title from a page add the following code to the top of your views:

    - content_for :title do
      Some Title Here

For example, at the top of `views/pages/home.html.haml`:

    - content_for :title do
      Home

Commit your changes.

**Step 4**: It's time to launch! If you run WEBrick, your application should now just work with the following command:

    $ rails server

...and in your browser location box type:

    localhost:3000

And with that you should see something like this:

<br>

![][Basic HTML]

Not very attractive! ...but don't worry we'll address that in [Chapter 3][]. What's important here is what's under the hood: an excellent foundation markup base to work with moving forward. In the [next chapter][Chapter 2] we will explore exactly that, what's under the hood.

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp2-markup-review.md#markup-review
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md#foundation-styles
[Chapter 1 - Coding Design]: https://github.com/maxxiimo/coding-design/blob/master/chp1-information-architecting.md#information-architecting

[starter code]:         https://github.com/maxxiimo/base-haml
[application.js]:       https://github.com/maxxiimo/base-haml/blob/master/app/assets/javascripts/application.js
[site]:                 https://github.com/maxxiimo/base-haml/blob/master/app/assets/javascripts/site.js
[application_helper]:   https://github.com/maxxiimo/base-haml/blob/master/app/helpers/application_helper.rb
[_chromeframe]:         https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_chromeframe.html.haml
[_head]:                https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_head.html.haml
[_scripts]:             https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_scripts.html.haml
[application]:          https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/application.html.haml
[_footer]:              https://github.com/maxxiimo/base-haml/blob/master/app/views/shared/_footer.html.haml
[_logo]:                https://github.com/maxxiimo/base-haml/blob/master/app/views/shared/_logo.html.haml
[_navigation]:          https://github.com/maxxiimo/base-haml/blob/master/app/views/shared/_navigation.html.haml
[jquery]:               https://github.com/maxxiimo/base-haml/blob/master/vendor/assets/javascripts/jquery-1.9.1.min.js
[modernizer]:           https://github.com/maxxiimo/base-haml/blob/master/vendor/assets/javascripts/modernizr-2.6.2.min.js
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[README.md]:            https://github.com/maxxiimo/base-haml/blob/master/README.md
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[H5BP for Rails]:       http://railsapps.github.com/rails-html5-boilerplate.html

[Prep and Launch]:      https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md#prep-and-launch
[RoR Tutorial]:         http://ruby.railstutorial.org/ruby-on-rails-tutorial-book
[Git]:                  http://git-scm.com/
[Github]:               https://github.com/
[recommends]:           http://ruby.railstutorial.org/ruby-on-rails-tutorial-book?version=3.2#sec-heroku_setup
[Turbo Sprockets]:      https://github.com/ndbroadbent/turbo-sprockets-rails3
[Heroku]:               https://id.heroku.com/signup
[Heroku Set Up]:        https://devcenter.heroku.com/articles/quickstart

[Basic HTML]:           http://chrismaxwell.com/manifesto/chp-1/basic-html.png
[New Files]:            http://chrismaxwell.com/manifesto/chp-1/new-files.gif
