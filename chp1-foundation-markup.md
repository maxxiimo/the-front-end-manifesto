Foundation Markup
=================

As an Information Architect (IA), when I think about an applications layout I literally think about how a site is "laid out" on a screen. I think in terms of the organization of information and function for an end-user's consumption. In this IA role, when speaking about layout I might say something like, "Wow! That's a great layout," or "I don't like the layout of this site, it's too confusing, maybe you should move this over there."
<br>
<br>
![][Layout]

When I switch hats, as a Rails developer, I look at layout as the Rails view framework in which all of my front end code lives, and from where it will interact via Rails with the outside world.

As a Rails Front End Engineer, you will wear both hats. In [Chapter 4][] we will dive deeply into information architecting, but for now our focus will be strictly on coding, and getting it right per our [manifesto][Manifesto], for both end-users and backend developers.

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

The heart of this view framework is referred to as the layout template: *application.html.haml* by default. Most view code from other parts of an application pass through and become framed by *application.html.haml* before being served and rendered by browsers.

The Code
--------

Our starter code is an implementation of [HTML5 Boilerplate][] code (v 4.0.1) in haml and arranged for a Rails project.

In coding copy and learn from the best, improve, then give back. I find that the best place to reference when building front end view templates is HTML5 Boilerplate. This resource is an ongoing collaboration between expert front end developers and the community.

To better understand HTML5 Boilerplate as it applies to Rails, the following article is helpful:

- [Guide to HTML5 Boilerplate for Rails Developers][H5BP for Rails]

Structurally in a Rails application, our [starter code][] files and folders fall into place as follows:

app<br>
|-- assets<br>
|&nbsp;&nbsp;&nbsp;|-- images<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **fixtures**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **icons**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **logos**<br>
|&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;|-- **pics**<br>
|&nbsp;&nbsp;&nbsp;|-- javascripts<br>
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [application.js][application]<br>
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
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [jquery-1.8.3.min.js][jquery]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|-- [modernizr-2.6.2.min][modernizer]<br>
[.gitignore][]<br>
[Gemfile][]<br>
[README.md][]

The default Rails application file structure is pretty much identical minus a few files and folders. We're going to replace some existing files and add a few new files and folders (new folders in bold, new or replacement files are links).

### Set Up

Before we begin to explore the code that make up our views, there are a few things you will need to do to follow along with this book:

1.  Clone this books [starter code][]:

        git clone git@github.com:maxxiimo/base-haml.git

2.  Create a brand-new Rails 3.2 application.

        $ rails new <name>

    NOTE: A great reference for doing this correctly is Chapter 1 of Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

3. Complete the [Groundwork Tasks][Groundwork] section of the Appendices.

### Prep the App

Prep your app by following these steps:

**Step 1** - If you do not have a page for your routes to go to, which I'm assuming you don't if this is a brand-new application, create one now. Generate a pages controller to match the footer links:

    $ rails generate controller Pages home about site_map terms privacy contact

Make sure to delete the *assets/stylesheets/pages.css.scss* file generated by Rails, we won't be using it. You can also delete *assets/javascripts/pages.js.coffee* if you do not plan to use it.

NOTE: If you're not sure what I just did there you should really consider getting Michael Hartl's "[Ruby on Rails Tutorial][RoR Tutorial]".

**Step 2** - Finally, change your default route to whatever you want your application to default to:

    # You can have the root of your site routed with "root"
    # just remember to delete public/index.html.
    root :to => 'pages#home'

If you run WEBrick, your application should now just work.

    $ rails server

### End Result

Although not apparent yet, i.e. visually, we have created an excellent foundation for your application. With everything in place, and given that you followed all the steps above, your homepage should look something like this:

<br>

![][Basic HTML]

Not very attractive! ...but don't worry we'll address that in the [next chapter][Chapter 2].

Organization
------------

Let's dissect what we've done.

### Partials

All of the files in our layouts and shared folders could all be grouped together in one file: *application.html.haml*, but by convention and in keeping with our [manifesto][Manifesto]:

> Be consistent, keep code well organized, readable and DRY.

...we separate parts of the file into partials that feed back into *application.html.haml*:

view/layout

1. [_head.html.haml][_head]
2. [_scripts.html.haml][_scripts]

view/shared

3. [_logo.html.haml][_logo]
4. [_navigation.html.haml][_navigation]
5. [_footer.html.haml][_footer]

Partials 1 and 2 are located in the same layout folder as *application.html.haml* – NOT in the shared folder – because they are essentially integral to the *layout/application.html.haml* file. Some developers like to locate these partials in the shared folder, but to me it makes more sense to put them in the layout folder. The files in the shared folder, on the other hand, may be shared by multiple layout files and feel more "markup" like; much like the many more shared partials you will create along the development cycle.

To pull these integral partials into *application.html.haml* I like to use helper methods:

    def head
      render :partial => 'layouts/head'
    end

    def scripts
      render :partial => 'layouts/scripts'
    end

It looks cleaner than the render method.

    = head

    vs.

    = render :partial => 'shared/head'

> Seek perfection and excellence, write beautiful code.

\- [Manifesto][]

You may have noticed that I separated logo and navigation into their own partials rather than use something like *_banner.html.haml* or *_header.html.haml* to hold both. Often times logos and navigation vary between clients or functional areas within an application. When you start a project you don't necessarily see this coming, but needs do change so you might as well lay them out in such a way that you and backend developers can easily get at them in the future.

> Future proof code.

> Provide intelligent and semantically correct hooks and code snippets for backend teams.

\- [Manifesto][]

The end result of our organizational efforts is a very succinct *application.html.haml* file:

    !!!
    -# Uncomment if you want to address IE browser issues via these classes/method.
    -# http://paulirish.com/2008/conditional-stylesheets-vs-css-hacks-answer-neither/
    -# /[if lt IE 7]><html class="no-js lt-ie9 lt-ie8 lt-ie7" lang="en"> <![endif]
    -# /[if IE 7]>   <html class="no-js lt-ie9 lt-ie8" lang="en"> <![endif]
    -# /[if IE 8]>   <html class="no-js lt-ie9" lang="en"> <![endif]
    -# /[if gt IE 8]><!-->
    %html.no-js{:lang => "en"}
      -# /<![endif]

      = head
      %body
        = chromeframe
        %header{:role => "banner"}
          = render :partial => 'shared/logo'
          = render :partial => 'shared/navigation'
        #main{:role => "main"}
          = yield
        = render :partial => 'shared/footer'
        = scripts

Other than all the Internet Explorer conditions, it's concise and simple. If you plan to use those conditionals just uncomment each line, if not, feel free to delete them. Also note the use of [ARIA roles][]:

    %header{:role => "banner"}

It's good practice to always consider users that require assistive technology.

> Think in terms of all use cases including and especially accessibility.

\- [Manifesto][]

### JavaScript

I don't think I have found a more comprehensive overview of JavaScript in Rails than Daniel Kehoe's article:

- [Unholy Rails: External Scripts, jQuery Plugins, and Page-Specific JavaScript][Unholy Rails]

In so far as our *application.html.haml* organization goes, generally it is best to put JavaScript at the very bottom of your markup. Doing so will allow pages to render before scripts are loaded. In other words, they won't hold up the show.

Some scripts though, such as modernizr, need to load before your HTML does and therefore are called through a Rails JavaScript include tag in [_head.html.haml][_head]:

    = javascript_include_tag "application"

The JavaScript include tag specifies a manifest file called [application.js][application], which in turn requires the modernizer script:

    //= require modernizr-2.6.2.min
    //= require jquery-1.8.3.min
    //= require site

> Sprockets uses manifest files to determine which assets to include and serve. These manifest files contain directives — instructions that tell Sprockets which files to require in order to build a single CSS or JavaScript file. With these directives, Sprockets loads the files specified, processes them if necessary, concatenates them into one single file and then compresses them.

\- [Asset Pipeline - Manifest Files and Directives][Manifest Files]

The [_scripts.html.haml][_scripts] partial is designed for additional scripts, and located at the bottom of *application.html.haml*, after all our markup.

### What to Put in \<head>

If you haven't already noticed, there is quite a bit of commented code in [_head.html.haml][_head]. The reason for this is that there are a lot of things that can be added to this file, but might not be needed. I provide the bare minimum. Everything else, commented out, is just there in case it's needed. Feel free to cherry pick through this commented code and delete what you do not need.

For an explanation on what you might need and what some of this code does check out:

- [Helpful things to keep in your \<head>][Helpful Things]

### The Title

You may have also noticed that I use the following snippet of code in [\<head>][_head]:

    %title= content_for?(:title) ? yield(:title) : "XXX"

It is designed to provide a title for each page your end-users visit. If a unique title does not exist for any particular page, the default "XXX" title is given. Obviously change this.

NOTE: Never put title text in your controllers. Text belongs in views and should stay there whenever humanly possible.

> Abstract logic out of views, keep view code out of controllers.

\- [Manifesto][]

Add the following to the top of any page you wish to add a unique title to:

    - content_for :title do
      Some Cool Title

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


Moving Forward
--------------

Before we move on to styles, there are a few things we need to consider when adding files and organizing code within our framework moving forward.

### Using Partials

Partials help:

1.  Increase readability of your code
2.  Keep things organized
3.  Reuse code, i.e. keep things DRY
4.  Encapsulate logic, although helper methods are preferred

The key is not to go nuts and partial out everything. If you do that, finding things can become a wild goose chase for backend coders trying to figure out where the markup they need lives.

> Provide intelligent and semantically correct hooks and code snippets for backend teams.

> Be consistent, keep code well organized, readable and DRY.

> KISS (keep it simple stupid)

\- [Manifesto][]

### Naming Conventions

When naming HTML files try to stay within REST conventions, i.e. *index.html.haml*, *show.html.haml*, etc. When naming outside of REST be short and concise, use names that indicate what the files function or purpose are.

When naming HTML files separate words with underscores:

    a_great_file_name.html.haml

For partials, if there are several related to an individual file, group them by using the parent files name or abbreviation. If there is no parent file per se, use a common function or purpose to group the partials, for example:

    _tabs.html.haml
    _tabs_sub_nav.html.haml

> Seek perfection and excellence, write beautiful code.

> Provide intelligent and semantically correct hooks and code snippets for backend teams.

> Be consistent, keep code well organized, readable and DRY.

> KISS (keep it simple stupid)

\- [Manifesto][]

### IE 6

These days most people like to just forget about IE 6, it's old, "we're not supporting it, those users need to update!" ...But here's the problem, those users are still out there, even if they don't want to be. Have you ever been to your local public library and checked out the super old machines people have to use there? I sometimes go just to see what an application I'm working on will look like in older browsers.

So what I propose is a compromise for those of you who don't want to waste your time developing for IE 6; give those users notice and ability via [Chrome Frame][]. Our [starter code][] includes this by default in the [following partial][_chromeframe]:

    /[if lt IE 7 ]
      %p.chromeframe
        Your browser is
        %em ancient!
        %a{:href => "http://browsehappy.com/"} Upgrade to a different browser
        or
        %a{:href => "http://www.google.com/chromeframe/?redirect=true"} activate Google Chrome Frame
        to experience this site.

Here is the corresponding helper method:

    def chromeframe
      render :partial => 'layouts/chromeframe'
    end

> As a web developer, you’re working with IT every day. Upgrading doesn’t worry you; it’s easy and everyone should do it. But are you neglecting to consider:
>
>- Large organizations and government departments. Those businesses may have 10-year IT plans. Desktops are locked-down and users can’t upgrade. Even when a company wants to move forward, migrating thousands of users is not quick, simple or inexpensive.
>- Windows XP users. One in four people use XP and that figure is higher for business users. Upgrading beyond IE8 is not an option.
>- You are not an average user. Most people do not understand IT. Many are terrified of it — or certainly worried they’ll break their PC. Migrating from something they know is a risk regardless of the benefits.

\- [Is Internet Explorer Development Really a Waste of Time?][Waste of Time]

I should mention that the author of this article follows up with a solution in his follow-up article:

- [How to Use Responsive Web Design to Support Old Browsers][RWD for IE]

What We've Done
---------------

- We started this chapter by laying out the groundwork for our foundation markup.
- We then began to discuss what an application layout is, from the front end coder's perspective, and how it is organized in a Rails application.
- We then grabbed all of the starter code for this chapter, our foundation markup, and integrated it into a new Rails application.
- Finally, we took a look at how this foundation markup is organized, and briefly reviewed legacy browsers.

In the [next chapter][Chapter 2], we will begin to set up our foundation styles.

[Chapter 4]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp4-information-architecting.md
[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/the-manifesto.md
[RoR Tutorial]:         http://ruby.railstutorial.org/book/ruby-on-rails-tutorial?version=3.2
[Groundwork]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendix-1.md#groundwork-tasks
[starter code]:         https://github.com/maxxiimo/base-haml

[HTML5 Boilerplate]:    http://html5boilerplate.com/
[H5BP for Rails]:       http://railsapps.github.com/rails-html5-boilerplate.html

[application]:          https://github.com/maxxiimo/base-haml/blob/master/assets/javascripts/application.js
[site]:                 https://github.com/maxxiimo/base-haml/blob/master/assets/javascripts/site.js
[application_helper]:   https://github.com/maxxiimo/base-haml/blob/master/helpers/application_helper.rb
[_chromeframe]:         https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_chromeframe.html.haml
[_head]:                https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_head.html.haml
[_scripts]:             https://github.com/maxxiimo/base-haml/blob/master/views/layouts/_scripts.html.haml
[application]:          https://github.com/maxxiimo/base-haml/blob/master/views/layouts/application.html.haml
[_footer]:              https://github.com/maxxiimo/base-haml/blob/master/views/shared/_footer.html.haml
[_logo]:                https://github.com/maxxiimo/base-haml/blob/master/views/shared/_logo.html.haml
[_navigation]:          https://github.com/maxxiimo/base-haml/blob/master/views/shared/_navigation.html.haml
[jquery]:               https://github.com/maxxiimo/base-haml/blob/master/vendor/assets/javascripts/jquery-1.8.3.min.js
[modernizer]:           https://github.com/maxxiimo/base-haml/blob/master/vendor/assets/javascripts/modernizr-2.6.2.min.js
[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[Gemfile]:              https://github.com/maxxiimo/base-haml/blob/master/Gemfile
[README.md]:            https://github.com/maxxiimo/base-haml/blob/master/README.md

[ARIA roles]:           http://www.w3.org/TR/wai-aria/roles#landmark_roles
[Unholy Rails]:         http://railsapps.github.com/rails-javascript-include-external.html
[Manifest Files]:       http://guides.rubyonrails.org/asset_pipeline.html#manifest-files-and-directives
[Helpful Things]:       https://gist.github.com/1981339
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:  http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
[Ignore files]:         http://help.github.com/ignore-files/
[Templates]:            https://github.com/github/gitignore
[Chrome Frame]:         https://developers.google.com/chrome/chrome-frame/
[Waste of Time]:        http://www.sitepoint.com/is-internet-explorer-development-really-a-waste-of-time/
[RWD for IE]:           http://www.sitepoint.com/support-old-browsers-responsive-web-design/
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp2-foundation-styles.md


[Layout]:               http://chrismaxwell.com/manifesto/chp-1/layout.png
[Basic HTML]:           http://chrismaxwell.com/manifesto/chp-1/base-html-no-styles.jpg
