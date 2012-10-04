Getting Started
---------------

This chapter could be called a cut-and-paste chapter in that I will provide tried-and-true code that you can cut and paste into your application to build your projects foundation markup and styles. In the next chapter we will begin to learn about the organization of the code in this chapter, but for now these are the steps necessary to start your Rails application out right, from the front end view coders perspective. Let's get started.

### Groundwork

Assuming you just created a brand spanking new Rails application, you should set up your .gemfile and .gitignore files right off the bat as follows:

#### .gemfile

Your .gemfile will change radically throughout the lifespan of your project. With a new application Rails generates one with a lot of comments and commented out lines. You don't need these right now, so let's get rid of them, they take up a lot of space and clutter things up. If you ever want to see them again in the future, review your git history or you can always create a new app. Without comments, here is what you're left with:

    source 'https://rubygems.org'

    gem 'rails', '3.2.8'
    
    gem 'sqlite3'
    
    group :assets do
      gem 'sass-rails',   '~> 3.2.3'
      gem 'coffee-rails', '~> 3.2.1'
      gem 'uglifier', '>= 1.0.3'
    end
    
    gem 'jquery-rails'

To this I'm going to add gems that I know for certain I will work with, and borrowing from the best I use Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]" .gemfile example with a few additions:

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

Since I typically use compass, I added the compass-rails and oily_png gems here. You may not want to, but if you do, smart choice.

NOTE: Michael Hartl recommends using the following flag on your first bundle:

    bundle install --without production

Doing so installs your .gemfile gems, but prevents the installation of the production gems. You only have to do this once.

#### .gitignore

For my .gitignore file here is what I use; mostly borrowed from [HTML 5 Boilerplate][H5BP .gitignore]:

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

The last section "Local" contains files or folders I like to use to save things within the application, but only on my local machine:

- scratch.* - I use this as a code graveyard: snippets of code I am no longer using but not yet ready to completely get rid of.

- public/source - A folder for original third-party files or source code integrated into my application; Photoshop files; original images; basically the original copies of where things came from.

Some additional useful .gitignore ideas:

- [Ignore files][]
- [A Collection of Useful .gitignore Templates][.gitignore]

### Foundation Markup: The Application Layout

As a front end person, sometimes called an Information Architect, when I think about layout I literally think about how a site is laid out on a screen. I don't think in terms of code, but more so in terms of organization of information and function for an end-user's consumption. In this role when speaking about "layout" I might say something like, "Wow! That's a great layout," or "I don't like the layout of this site, it's too confusing."

When I switch hats, as a front end coder I look at layout as the view framework in which all of my front-end code lives and interacts with the outside world via different browsers and devices. In other words it's what a desktop or mobile browser takes and turns into something visual that an end user can understand and interact with, i.e. consume.

As a Rails front-end developer, you will wear both hats, plus take on a third role in which you provide the handshake between the backend and the front-end. To be successful you must understand how the code you produce will be used by your colleagues, and you need to be able to reach into your models and controllers via instance variables, helper methods, erb, but before you do these things you need to layout a solid foundation.

As much as Rails is a framework, within this framework lives a tinier front end framework; your foundation markup. Until Rails 3.0, where this foundation "lived" and the conventions for using it were very much a no man's land. It was a disorganized dumping ground for HTML, CSS, JavaScript, and Ruby: the wild wild West of coding. Since Rails 3.0 things have become "civilized" and within these new conventions we will begin to build our layout. By the Way, I first heard the view layer referred to as a "no man's land" and the "West" in John Athayde and Bruce Williams' preface to [The Rails View: Create a Beautiful and Maintainable User Experience][The Rails View]. These guys are masters in this subject and  I highly recommend reading their book.

#### Where Does It Live?

So what is this tiny view framework within a framework? Well, it is predominantly HTML organized in specific folders of your application with styles and interactivity added via CSS and JavaScript (and Flash, but less and less these days). In Rails the heart of this view framework and all the code related to it lives in what we refer to as the layout template, which is typically broken up into different related files called partials which are all being pulled together into the whole. View code from other parts of the application for the most part pass through this layout and become framed by the layout template (with styles and JavaScript pulled in) before being rendered to the end-user.

The front end structure I'm describing primarily lives in two high-level folders within your Rails application: the helpers and the views folders. The views folder is where the real action takes place and can be further subdivided into the Layout and Shared folders, which are home to the majority of your foundation front end code. Here's what it looks like and where you'll find these folders in any Rails 3.0 or greater project:

Project
  - assets
  - controllers
  - **helpers**
  - mailers
  - models
  - app
    - **views**
      - **layout**
      - **shared**

#### The Code

Our goal is to writes and organize the components of our layout in such a way that different browsers and devices can consistently, correctly, and efficiently display visual information to the end-user, and backend coders can understand and plug into it with ease. To help you along this path you can grab my [Starter Code][]:

- https://github.com/maxxiimo/base-haml

This is an implementation of [HTML5 Boilerplate][] code in haml.

NOTE: I have included some necessary asset folders and files that coincide with the defaults I will provide in this chapter. Since I'm using modernizr, I add the require in application.js as follows:

    //= require jquery
    //= require jquery_ujs
    //= require modernizr-2.5.3.min
    //= require_tree .

#### HTML5 Boilerplate

In coding copy and learn from the best, improve, then give back. I find that the best place to reference when building front end view templates is [HTML5 Boilerplate][]. This resource is an ongoing collaboration between expert front-end developers and the community.

To better understand it (and my implementation), the following sites are also worth a visit:

- [An Unofficial Guide to the HTML5 Boilerplate][Unofficial Guide]
- [Guide to HTML5 Boilerplate for Rails Developers][Boilerplate for Rails]

#### Where Do Things Go?

Code wise you have access to everything I would use when starting a new application, my [base files][Starter Code]. Structurally, these files fall into place as follows:

Project
  - assets
    - images
      - **fixtures**
      - **icons**
      - **logos**
      - **pics**
    - **javascripts**
  - controllers
  - helpers
    **application_helper.rb**
  - mailers
  - models
  - app
    - views
      - layout
        - **_chromeframe.html.haml**
        - **_head.html.haml**
        - **_scripts.html.haml**
        - **application.html.haml**
      - shared
        - **_footer.html.haml**
        - **_logo.html.haml**
        - **_navigation.html.haml**

Once you download these files, perform the steps below.

**Step 1** - Delete the default index.html file in your Public folder, and the rails.png image in your Assets/Images folder, as well as the application.html.erb file you are replacing with application.html.haml.

**Step 2** - If you do not have a page for your routes to go to, which I'm assuming you don't if this is a brand-new application, create one now. I'm going to generate a Pages controller now to match my footer links:

    rails generate controller Pages home about site_map terms privacy contact --no-test-framework

Make sure to delete the pages.css.scss file generated by Rails, we won't be using it.

NOTE: If you're not sure what I just did there you should really consider getting Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

**Step 3** - Finally, in your default route to:

    # You can have the root of your site routed with "root"
    # just remember to delete public/index.html.
    root :to => 'pages#home' 

#### What Did We Just Do?

I'm going to defer answering this question to the [Organization][] chapter to this book. Suffice it to say that you have a working foundation markup for your application. If you grabbed every single one of my base files and folders and organized them into a brand-new Rails application exactly like I describe above, your Rails application will work just fine minus styles. As long as you have a page ready to display, things should look something like this:

![][Basic HTML]

Not very attractive! Let's fix that somewhat with CSS.

### Styles

For your applications foundation styles we'll use my base CSS files, or you can make up your own, but before you add styles to your application, and if you're planning to use Compass, you need to set it up.

#### Compass Set Up

1.  Add 'compass-rails' to your gemfile. For more explicit directions from the gem source take a look at: [compass-rails][]

2.  Run "bundle exec compass init" and then delete the 3 stylesheets generated by Compass. We're going to use our own.

3.  Add the following commented out code to your config/compass.rb file generated in step one:

        # To allow compass to import partials from subdirectories per:
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
        # additional_import_paths = ["app/assets/stylesheets/<name>", "app/assets/stylesheets/<name>"]
        #
        # To compile in the necessary debugging information for FireSass.
        # sass_options = {:debug_info => true}

    I add these because chances are I may need them. You should definitely check out [FireSass][]. It allows you to see exactly which sass partial styles are coming from.

4.  Delete your application.css file and replace with application.scss. 

    NOTE: Your base application file needs to use the .scss syntax, however, other partials can use the .sass syntax, which is my preference.

5.  Use @import to organize styles rather than Sprockets. Add the following reminder at the top of application.scss:
        
        /*
         * Important! Do *not* use Sprockets "require" syntax.
         * Use @import to include other stylesheets and Compass mixins.
         */

    NOTE: You can use sprockets require syntax, however per the explanation found at of the [compass-rails][] gem source it is probably not a good idea.

6.  If you find your system has a problem with sass partials and underscores when precompiling, add the following to your config/application.rb file:

        # Precompile *all* assets, except those that start with underscore per:
        # http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
        config.assets.precompile << /(^[^_\/]|\/[^_])[^\/]*$/

That's pretty much it!

Some additional resources for working with Compass include:

- [Getting Compass to Work With Rails 3.1 (and 3.2)][Getting Compass to Work]
- [How I Use Compass With Rails 3.1][How I Use Compass]
- [Sass, Compass, and the Rails 3.1 Asset Pipeline][Asset Pipeline]

#### The Styles

Now that Compass is set up, grab everything from here:

- https://github.com/maxxiimo/base-css

...and paste these files and subfolder into your assets/styles directory. Simple as that. Here is what your page will look like:

![][Basic HTML with Styles]

It's pretty basic, but much better than before.

#### What Did We Just Do?

We essentially added some very basic css and resets, but more important than this – there are really not that many styles included – is the way in which we organized our styles. As you move along any project, stylesheets can become behemoths, unmanageable, and downright confusing. To avoid this it's highly advisable to start a project with some kind of organizational structure in place from the get-go.

To learn more about CSS Organization, check out the CSS Organization section of the [Organization][] chapter. This section describes why and how to organize styles within application.scss and more. The HTML Organization section covers why and how to organize your markup foundation. Although this book is designed for developers who already know their way around a Rails application, it's worth taking a look at.


[RoR Tutorial]:            http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[H5BP .gitignore]:         https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:     http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
                           "An augmented .gitignore file"
[Ignore files]:            http://help.github.com/ignore-files/
[.gitignore]:              https://github.com/github/gitignore
[The Rails View]:          http://pragprog.com/book/warv/the-rails-view
[Starter Code]:            https://github.com/maxxiimo/base-haml
[HTML5 Boilerplate]:       http://html5boilerplate.com/
[Unofficial Guide]:        http://designreviver.com/articles/an-unofficial-guide-to-the-html5-boilerplate/
[Boilerplate for Rails]:   http://railsapps.github.com/rails-html5-boilerplate.html
[Organization]:            https://github.com/maxxiimo/railsviews/blob/master/Organization.md
[compass-rails]:           https://github.com/Compass/compass-rails
[FireSass]:                https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/
[Getting Compass to Work]: http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[How I Use Compass]:       http://austintech.com/blog/2011/08/19/how-i-use-compass-with-rails-3-1/
[Asset Pipeline]:          http://www.engineyard.com/blog/2011/sass-compass-and-the-rails-3-1-asset-pipeline/


[Basic HTML]:              http://chrismaxwell.com/rails-views/assets/getting-started/base-html-no-styles.png
[Basic HTML with Styles]:  http://chrismaxwell.com/rails-views/assets/getting-started/base-html-files-with-styles.png