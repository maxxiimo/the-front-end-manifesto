HTML Organization
-----------------

### Naming Conventions

When naming HTML files try to stay within REST conventions, i.e. index.html.haml, show.html.haml, etc.. When naming outside of REST be short and concise, use names that indicate what the files function or purpose is. Keep in mind that file names tend to trickle down to classes.

When naming HTML files separate words with underscores: a_great_file_name.html.haml

For partials, if there are several related to an individual file, group them by using the parent files name or abbreviation. If there is no parent file per se, use a common function or purpose to group the partials, for example:

    _tabs.html.haml
    _tabs_sub_nav.html.haml

### Where to Put Things

Partials are great to use to:

1.  Increase readability of your code
2.  Keep things organized
3.  Reuse code, i.e. keep things DRY
4.  Encapsulate logic, although helper methods are preferred

The key is not to go knots and partial everything. If you do that, finding things becomes a wild goose chase.

So starting from the top, separate your layout/application.html.haml into partials like:

1. _head.html.haml
2. _script.html.haml
    
3. _logo.html.haml
4. _navigation.html.haml
5. _footer.html.haml

For the first two partials locate these in the same layout folder as application.html.haml -- NOT in the shared folder --- because they are essentially integral to the layout/application.html.haml file. Use helper methods to pull them in:

    def head
      render :partial => 'layouts/head'
    end
    
    def scripts
      render :partial => 'layouts/scripts'
    end

For the second three locate these in the shared folder. I separate logo and navigation into their own partials rather than use something like _banner.html.haml or _header.html.haml to hold them because often times logos and navigation vary between clients or functional areas within an application. When you start  the project you don't necessarily see this coming, but needs do change so you might as well lay them out in such a way that you can easily get at them in the future.

Do all this, and your application.html.haml file might look something like this:

    !!!
    = head
    %body
      %header{:id => 'hd', :role => "banner"}
        = render :partial => 'shared/logo'
        = render :partial => 'shared/navigation'
      #main{:role => "main"}
        = yield
      = render :partial => 'shared/footer'
    = scripts

Concise and simple. Also note the use of [ARIA roles][]. It's good practice to always consider users that require assistive technology to browse your application.

### IE 6

These days most people like to just forget about IE 6, it's old, "We're not supporting it, those users need to update!" ...But here's the problem, those users are still out there, even if they don't want to be. Have you ever been in your local library and checked out the super old machines people have to use there? So what I propose is a compromise. Don't waste your time developing for IE 6 but give those users notice and ability via [Chrome Frame][]. Add the following partial to your layouts folder:

    /[if lt IE 7 ]
      %p.chromeframe
        Your browser is
        %em ancient!
        %a{:href => "http://browsehappy.com/"} Upgrade to a different browser or
        %a{:href => "http://www.google.com/chromeframe/?redirect=true"} install Google Chrome Frame to experience this site.

Here is the corresponding helper method:

    def chromeframe
      render :partial => 'layouts/chromeframe'
    end

So now your application layout file will look like this:

    !!!
    = head
    %body
      = chromeframe
      %header{:id => 'hd', :role => "banner"}
        = render :partial => 'shared/logo'
        = render :partial => 'shared/navigation'
      #main{:role => "main"}
        = yield
      = render :partial => 'shared/footer'
    = scripts

### %head and Boilerplate

There is so much you can put in your %head that it can get pretty confusing. I base all of my projects off of parts of [HTML5 Boilerplate][]. To learn more check out [HTML head options][], all of the research on best practices and why has been done for you. Just pick and choose what works for you. You can use my haml template to start:

https://github.com/maxxiimo/base-files/blob/master/_head.html.haml

Everything is nice and neat in haml and with only the ones I think you should use (plus all the other options commented out).

[<head> Examples][]

### The Title

    %title= content_for?(:title) ? yield(:title) : "XXX"

### JavaScript

Generally it is best to put JavaScript at the very bottom of the page. Doing so will allow the page to render before scripts are loaded, but some scripts such as modernizr need to load before your HTML so naturally I include them in _head.html.haml. To accommodate all other JavaScript files I use a _scripts.html.haml partial located in the layout folder.


[Chrome Frame]:         https://developers.google.com/chrome/chrome-frame/
[HTML5 Boilerplate]:    http://html5boilerplate.com/
[HTML head options]:    http://html5boilerplate.com/docs/html-head/
[<head> Examples]       https://gist.github.com/581868
