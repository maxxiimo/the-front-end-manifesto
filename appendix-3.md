Appendix 3
----------

### Mobile Solutions Roundup

To get started, if you're not sure where to begin or as a review, take a look at this round up of mobile solutions:

1.  Ryan Bates screencast "[Mobile Devices][]".

2.  The tutorial "[How to Build a Mobile Rails 3.1 App][How to Build]" demonstrates -- although slightly dated from the gem -- how to use the authors [mobylette][] and [jquery_mobile_rails][] gems. Mobylette handles requests and allows your controller to respond with a :mobile format, while jquery-mobile-rails adds [jQuery Mobile][] files to your asset pipeline: which helps make everything look great and work like a native mobile app.

3.  Much like mobylette, [mobile-fu][] detects mobile requests and allows your application to respond with a :mobile format.

4.  There is a rack-based detection solution called [mobvious][]:

    > Mobvious detects whether your app / website is being accessed by a phone, or by a tablet, or by a personal computer. You can then use this information throughout your app. (E.g. fork your front-end code with regard to device type. There is a [plugin][mobvious-rails] for Ruby on Rails that helps you with this.)

    The [mobvious-rails][] gem allows you to:

    > Access detected device type easily from controllers and views.<br>
    > Execute code for given device types only. Both in controllers and views.<br>
    > Do the above stuff also in your CoffeeScript.

5.  [Agent_orange][agent_orange] looks interesting. Although stable, it has its issues per the maintainers readme.

6.  [UserAgent][] is a Ruby library that parses and compares HTTP User Agents.

7.  [Browser][] is a gem that allows you to test for the browser being used including mobile browsers, and includes ActionController integration.

8.  In the tutorial "[Mobile Devices and Rails: Maintaining your Sanity][Maintain Sanity]" the author proposes placing mobile templates in a separate directory, then when requests come in from a mobile subdomain, like m.domain.com, these templates are served. If the templates are not available, the requester is served regular view templates; freeing you up from having to create two templates for every action. Users can switch between the two templates, and user agent detection is employed.

9.  If you're looking to beef up your detection capabilities, the following services are available (includes free and paid plans).
    - [Handset Detection][]
    - [Akamai][]
    - [DeviceAtlas][]
    - [scientiamobile][]

10. You can also tap into the [WURFL][] database.

11. Here is a list of "[Mobile Browser ID (User-Agent) Strings][Mobile Strings]" you could incorporate into your project if you wanted to get granular.

[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices
[mobylette]:            https://github.com/tscolari/mobylette
[jquery_mobile_rails]:  https://github.com/tscolari/jquery-mobile-rails
[How to Build]:         https://dev.tscolari.me/2011/09/15/how-to-build-a-mobile-rails-3-dot-1-app/
[mobile-fu]:            https://github.com/brendanlim/mobile-fu
[jQuery Mobile]:        http://jquerymobile.com/demos/1.2.0/
[mobvious]:             https://github.com/jistr/mobvious
[mobvious-rails]:       https://github.com/jistr/mobvious-rails
[agent_orange]:         https://github.com/kevinelliott/agent_orange
[UserAgent]:            https://github.com/josh/useragent
[Browser]:              https://github.com/fnando/browser
[Maintain Sanity]:      http://erniemiller.org/2011/01/05/mobile-devices-and-rails-maintaining-your-sanity/
[Handset Detection]:    http://code.google.com/p/mobile-device-detection-ruby-on-rails/
[Akamai]:               http://www.akamai.com/html/solutions/mobile_detection_redirect.html
[DeviceAtlas]:          https://deviceatlas.com/
[scientiamobile]:       http://www.scientiamobile.com/
[WURFL]:                http://wurfl.sourceforge.net/
[Mobile Strings]:       http://www.zytrax.com/tech/web/mobile_ids.html
