*don't nest to deep*

### iPad

[iOS Human Interface Guidelines][iOS Guidelines]

[iOS Guidelines]: http://developer.apple.com/library/ios/#documentation/UserExperience/Conceptual/MobileHIG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006556-CH1-SW1


### Mobile Development Constraints

[Yehuda Katz][], a Rails core team member, discusses some of the development constraints in mobile in his presentation "[Rails 3 for Mobile Applications][Engine Yard]." Fast-forward to 13:00 to hear a great overview on limitations of mobile, but in summary:

- Poor HTTP caching (back button requires reload)
- Connection drops
- Lost downloads due to connection drops (like JavaScript files)
- Slow connections
- Stale data
- Pay per kB cost structure, i.e. limited bandwidth
- Limited battery (be a good citizen and don't use up users batteries)
- Limited CPU (what was fast on the desktop can be super slow on mobile)


Download data only once

Don't render incrementally, queue up everything and load at once.

Don't send things down that are needed like hiding markup with display: none.

Don't download the same thing on every single request.

Download the boilerplate and HTML templates only once.

Download data prospectively, i.e. think about what the user is going to need and start downloading it.

Application should not break because connection lost, should be able to see stale data.

Think of mobile as just another API client.

#### Application Cache

[rack-offline][]



Offline Apps Part 1
http://railscasts.com/episodes/247-offline-apps-part-1

Rack-Offline for Mobile HTML5 cached App with Rails 3.1 Asset-Pipeline
http://www.igumbi.com/en/blog/rack-offline-html5-mobile-cached-app-with-rails-3-1-asset-pipeline

#### Web Storage

Score keyvalue pairs locally.


Check out minutes 37:00 onwards to see exactly how to set up your rails application.

[jquery-offline][]
[jquery-offline]:       https://github.com/wycats/jquery-offline

[Yehuda Katz]:          http://yehudakatz.com/
[Engine Yard]:          http://www.engineyard.com/video/12678746
[rack-offline]:         https://github.com/wycats/rack-offline



Develop a marker that you can use via search/grep, a bundle package, or IDE capability, to find code you need to revisit. I like to use the following. Add your initials to distinguish yourself from other developers:

    // FIXME ccm:
    /* FIXME ccm: regular comments will show up in your output if comments are not stripped out.


JavaScript Libraries
--------------------

On page load modernizer checks to see what features in your browser are supported, or not. Based off this detection modernizer will add a class on your <html> tag. If the feature is supported, for example CSS transforms, Modernizr will add the class .css-transforms, and if it is not supported .no-css-transforms. You can then hook into these class names to provide more modern features for browsers that will support the feature or fallback to something that will work for a particular browser that does not support it.

    It tests for over 40 next-generation features, all in a matter of milliseconds
    It creates a JavaScript object (named Modernizr) that contains the results of these tests as boolean properties
    It adds classes to the html element that explain precisely what features are and are not natively supported
    It provides a script loader so you can pull in polyfills to backfill functionality in old browsers



[Zepto][]


[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+nettuts+%28Nettuts%2B%29

Good Advice
-----------

[Subliminal User Experience][User Experience]


[User Experience]:      http://24ways.org/2011/subliminal-user-experience




1.  [FitVids.js][]
    > A lightweight, easy-to-use jQuery plugin for fluid width video embeds.

[FitVids.js]:           http://fitvidsjs.com/







What's the better way to load jquery into an application?

- - - - - - - - - - - - - - - - - - - - - - - - - -
SCENARIO 1

%script{:src => "//ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"}
:javascript
  window.jQuery || document.write('<script src="assets/jquery-1.8.3.min.js"><\/script>')

With %head prefetch set as follows:

%link{:rel => "dns-prefetch", :href => "//ajax.googleapis.com"})

In this case you use Google's CDN,  and if the user already has the file cached (likely), you save a trip to the server, if not it cost you an additional server hit. If the CDN is down (unlikely) and the file is not cached, you pull the file from the application server.

Reference: http://html5boilerplate.com/

- - - - - - - - - - - - - - - - - - - - - - - - - -
SCENARIO 2








http://railsapps.github.com/rails-javascript-include-external.html
