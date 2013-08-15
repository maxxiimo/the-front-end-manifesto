Markup Review
=============

In the [previous chapter][Chapter 1] we discussed what an application layout is, from the front end coders perspective. More importantly, we laid out the groundwork for our foundation markup by integrating our [starter code][] into a new Rails application. Let's dissect that work.

Organization
------------

### Partials

All of the files in our layouts and shared folders could be grouped together in one file: *application.html.haml*, but by convention and in keeping with our [manifesto][Manifesto]:

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
    -# Uncomment if you want to address IE browser issues via these classes.
    -# http://paulirish.com/2008/conditional-stylesheets-vs-css-hacks-answer-neither/
    -# /[if lt IE 7] <html class="no-js lt-ie9 lt-ie8 lt-ie7" lang="en">
    -# /[if IE 7] <html class="no-js lt-ie9 lt-ie8" lang="en">
    -# /[if IE 8] <html class="no-js lt-ie9" lang="en">
    -# :plain
    -#   <!--[if gt IE 8] -->
    %html{:lang => "en"}
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

It's good practice to always [consider][] users that require assistive technology.

> Think in terms of all use cases including and especially accessibility.

\- [Manifesto][]

### JavaScript

I don't think I have found a more comprehensive overview of JavaScript in Rails than Daniel Kehoe's article:

- [Unholy Rails: External Scripts, jQuery Plugins, and Page-Specific JavaScript][Unholy Rails]

In so far as our *application.html.haml* organization goes, generally it is best to put JavaScript at the very bottom of your markup. Doing so will allow pages to render before scripts are loaded. In other words, they won't hold up the show.

The [_scripts.html.haml][_scripts] partial is designed exactly for this and additional scripts. It is located at the bottom of *application.html.haml*, after all our markup.

The JavaScript include tag found their specifies a manifest file called [application.js][], which in turn requires your scripts:

    //= require jquery
    //= require jquery_ujs
    //= require site

> Sprockets uses manifest files to determine which assets to include and serve. These manifest files contain directives — instructions that tell Sprockets which files to require in order to build a single CSS or JavaScript file. With these directives, Sprockets loads the files specified, processes them if necessary, concatenates them into one single file and then compresses them.

\- [Asset Pipeline - Manifest Files and Directives][Manifest Files]

Some scripts though, such as modernizr, need to load before your HTML does and therefore are called before the body of your markup through a Rails JavaScript include tag in [_head.html.haml][_head]:

    = javascript_include_tag "modernizr-2.6.2.min"

To get this to precompile you will need to add the following to *production.rb*:

    config.assets.precompile += %w( modernizr-2.6.2.min )

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
    graveyard.sass
    public/source
    vendor/source
    local_env.yml

You may use these files or folders to save things within the application, but only on your local machine:

- __scratch.*__ - A code scratchpad and graveyard; snippets of code I may use, or I am no longer using but not yet ready to completely get rid of. Examples: scratch.rb, scratch.html.haml, scratch.sass, scratch.txt.

- __graveyard.sass__ - A graveyard for CSS.

- __public/source__ and __vendor/source__ - Folders for original third-party files or source code integrated into the application; Photoshop files; original images; basically the original copies of where things came from.

- __local_env.yml__ - ignore file to place ENV variables into.

Replace the default .gitignore with the one found in your cloned starter code. Commit your changes.

Here are some additional useful .gitignore ideas:

- [Ignore files][]
- [A Collection of Useful .gitignore Templates][Templates]


Moving Forward with Markup
--------------------------

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

In the [next chapter][Chapter 3], we will begin to set up our foundation styles.

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md#foundation-markup
[Chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp2-markup-review.md#markup-review
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md#foundation-styles

[starter code]:         https://github.com/maxxiimo/base-haml

[_head]:                https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_head.html.haml
[_scripts]:             https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_scripts.html.haml
[_logo]:                https://github.com/maxxiimo/base-haml/blob/master/app/views/shared/_logo.html.haml
[_navigation]:          https://github.com/maxxiimo/base-haml/blob/master/app/views/shared/_navigation.html.haml
[_footer]:              https://github.com/maxxiimo/base-haml/blob/master/app/views/shared/_footer.html.haml
[ARIA roles]:           http://www.w3.org/TR/wai-aria/roles#landmark_roles
[consider]:             http://a11yproject.com/checklist.html

[Unholy Rails]:         http://railsapps.github.com/rails-javascript-include-external.html
[application.js]:       https://github.com/maxxiimo/base-haml/blob/master/assets/javascripts/application.js
[Manifest Files]:       http://guides.rubyonrails.org/asset_pipeline.html#manifest-files-and-directives

[Helpful Things]:       https://gist.github.com/1981339

[.gitignore]:           https://github.com/maxxiimo/base-haml/blob/master/.gitignore
[H5BP .gitignore]:      https://github.com/h5bp/html5-boilerplate/blob/master/.gitignore
[Tutorial .gitignore]:  http://ruby.railstutorial.org/chapters/beginning?version=3.2#code:gitignore]
[Ignore files]:         http://help.github.com/ignore-files/
[Templates]:            https://github.com/github/gitignore

[Chrome Frame]:         https://developers.google.com/chrome/chrome-frame/
[_chromeframe]:         https://github.com/maxxiimo/base-haml/blob/master/app/views/layouts/_chromeframe.html.haml
[Waste of Time]:        http://www.sitepoint.com/is-internet-explorer-development-really-a-waste-of-time/
[RWD for IE]:           http://www.sitepoint.com/support-old-browsers-responsive-web-design/
