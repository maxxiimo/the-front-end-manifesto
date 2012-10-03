Getting Started
---------------

This chapter could be called a cut-and-paste chapter in that I will provide tried-and-true code that you can cut and paste into your application. Here you get the steps necessary to start your rails application right, from the front end view coders perspective. The Layout and Styles sections of this chapter in addition to providing code dive into understanding the organization of those areas of your web application. Let's get started.

### Groundwork

Assuming you just created a brand spanking new rails application, I would set up your .gemfile and .gitignore files right off the bat as follows:

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

I get rid of all the scruff, comments, which leaves me with:

source 'https://rubygems.org'

    gem 'rails', '3.2.8'
    
    gem 'sqlite3'
    
    group :assets do
      gem 'sass-rails',   '~> 3.2.3'
      gem 'coffee-rails', '~> 3.2.1'
      gem 'uglifier', '>= 1.0.3'
    end
    
    gem 'jquery-rails'

There of certain things that I know I will work with, and borrowing from the best I use Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" .gemfile example with a few additions to organize my base .gemfile as follows:

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
    
    group :test do
      gem 'capybara',     '1.1.2'
    end
    
    group :production do
      gem 'pg',           '0.12.2'
    end

Since I typically use compass, I added the compass-rails and oily_png gems here. You may not want to. If you do, a smart choice, check out the [Using Compass][] chapter of this book to learn how to add compass to your application.

NOTE: Michael Hartl recommends using the following flag on your first bundle:

    bundle install --without production

Doing so installs your .gemfile gems, but prevents the installation of the production gems. You only have to do this once.

#### .gitignore

For my .gitignore file here is what I use; mostly borrowed from [HTML 5 Boilerplate][H5BP .gitignore] and Michael Hartl's [Ruby and Rails Tutorial][Tutorial .gitignore]:

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

### Layout

As a front end person, sometimes called an Information Architect, when I think about layout I literally think about how a site is laid out on a screen. I don't think in terms of code, but more so in terms of organization of information and function for an end-user's cconsumption. In this role when speaking about "layout" I might say something like, "Wow! That's a great layout" or, "I don't like the layout of this site, it's too confusing."

When I switch hats, as a front end coder I look at layout as the view framework in which all of my front-end code lives and interacts with the outside world, i.e. via different browsers and devices. It's what a desktop or mobile browser takes and turns into something visual that an end user can understand and interact with, i.e. consume. As much as Rails is a framework, within this greater framework lives a tinier front end framework that we front end coders work with. Until Rails 3.0, where this framework lived and the conventions for using it were very much no man's land, sometimes a dumping ground, and oftentimes the wild wild West of coding. Since Rails 3.0 things are becoming more civilized, and front end coding recognized as a discipline in its own right.

So what is this tiny view framework within a framework you speak of? Well, it is predominantly HTML with style and interactivity added to it via CSS and JavaScript (and Flash, less unless though). In Rails the heart of this view framework lives in what we refer to as the layout template which is typically broken up into different related files called partials that are all being called together into the whole. View code from other parts of the application pass through sso to speak and become framed by the layout template(s) before being rendered to the end-user.

#### Where Does It Live?

The front end structure I'm describing primarily lives in two folders within your Rails application: the helpers and the views folders. The views folder can be further subdivided into the Layout and Shared folders, which are home to the majority of your base front end code. Here's what it looks like and where you'll find these folders in any Rails 3.0 or greater project:

Project
  - assets
  - controllers
  - helpers
  - mailers
  - models
  - app
    - views
      - layout
      - shared

#### Give Me the Code!

Our goal is to writes and organize these components of our layout in such a way that different browsers and devices can consistently, correctly, and efficiently display visual information to the end-user, and backend coders can understand and plug-in to it with ease. To help you along this path you can grab my starter code from here:

https://github.com/maxxiimo/base-haml

This is an implementation of [HTML5 Boilerplate][] code in haml.

NOTE: I have included some necessary asset folders and files that coincide with the defaults I will provide in this chapter. Since I'm using modernizr, I add the require in application.js as follows:

    //= require jquery
    //= require jquery_ujs
    //= require modernizr-2.5.3.min
    //= require_tree .

#### HTML5 Boilerplate

In coding copy and learn from the best, improve, then give back. I find that the best place to reference when building front end view templates is [HTML5 Boilerplate][]. This resource is an ongoing collaboration between expert front-end developers and the community.

To better understand it (and my implementation), the following sites are also worth a visit:

[An Unofficial Guide to the HTML5 Boilerplate][Unofficial Guide]
[Guide to HTML5 Boilerplate for Rails Developers][Boilerplate for Rails]

#### Where Do Things Go?

Code wise you have access to everything I would use when starting a new application, my [base files][]. Structurally, they fall into place as follows:

Project
  - assets
  - controllers
  - helpers
    application_helper.rb
  - mailers
  - models
  - app
    - views
      - layout
        _chromeframe.html.haml
        _head.html.haml
        _scripts.html.haml
        application.html.haml
      - shared
        _footer.html.haml
        _logo.html.haml
        _navigation.html.haml

If you grab every single one of my base files and organize them into a brand-new Rails application exactly like I describe above, your Rails application will work just fine minus styles and the logo image referenced in those files, once you perform the steps below. At least it should! I'm testing it right now in a brand-new Rails 3.2 application and it's working just fine.

*Step 1* - Delete the default index.html file in your Public folder, and the rails.png image in your Assets/Images folder, as well as the application.html.erb file you are replacing with application.html.haml.

*Step 2* - If you do not have a page for your routes to go to, which I'm assuming you don't if this is a brand-new application, create one now. I'm going to generate a Pages controller now to match my footer links:

    rails generate controller Pages home about site_map terms privacy contact --no-test-framework

Make sure to delete the pages.css.scss file generated by Rails, we won't be using it.

NOTE: If you're not sure what I just did there you should really consider getting Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

*Step 3* - Finally, in your default route to:

    # You can have the root of your site routed with "root"
    # just remember to delete public/index.html.
    root :to => 'pages#home' 

#### What Did We Just Do?

I'm going to defer answering this question to the [Organization][] chapter to this book. Suffice it to say that you have a working base application, but as you probably can see it doesn't look good. Let's fix that with CSS.

### Styles

For styles if you grab everything in the following directory:

https://github.com/maxxiimo/base-css

...and paste these files and subfolder into your assets/styles directory, you will have added my recommended base stylesheets to your project. Simple as that, and since you included the sass-rails and compass-rails gems in your .gemfile, everything should just work.

#### What's in There?

So what are in these styles? Well obviously these are the base CSS files I start any application with and they contain some very basic styles and resets. What is more important here are not styles, because there are really not that many included, but the way in which styles are organized. As you move along your project, stylesheets can become behemoths, and that's why I advocate some kind of organization structure from the get-go. You can use mine, or can make up your own. To learn more about CSS Organization, check out the CSS Organization section of the [Organization][] chapter.

### What have we done?



[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[Using Compass]:        https://github.com/maxxiimo/railsviews/blob/master/Using%20Compass.md
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:  http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
                        "An augmented .gitignore file"
[Ignore files]:         http://help.github.com/ignore-files/
[.gitignore]:           https://github.com/github/gitignore
[base files]:           https://github.com/maxxiimo/base-haml
[Organization]:         https://github.com/maxxiimo/railsviews/blob/master/Organization.md