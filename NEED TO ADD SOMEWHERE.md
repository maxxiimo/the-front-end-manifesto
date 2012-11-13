
*Designers should use pixels.*


*don't nest to deep*


### iPad

[iOS Human Interface Guidelines][iOS Guidelines]

[iOS Guidelines]: http://developer.apple.com/library/ios/#documentation/UserExperience/Conceptual/MobileHIG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006556-CH1-SW1


### Mobile Development Constraints

[Yehuda Katz][] of jQuerry fame and a Rails core team member discusses some of the development constraints in mobile in his presentation "[Rails 3 for Mobile Applications][Engine Yard]." Fast-forward to 13:00 to hear a great overview on limitations of mobile, but in summary:

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
