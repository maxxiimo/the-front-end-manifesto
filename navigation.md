Navigation
----------

### Tabs

When creating tabbed navigation in a Rails application checkout:

1.  [Tabs on Rails][]
2.  [Tabulous][]

...but there can only be one, and here are some differences that may sway your opinion {depending on your project of course}. [Tabs on Rails][] will allow multiple tab groups, for example one for admins and another for users, or two different sets of tabs on the same page. [Tabulous][] will not. It makes the assumption that only one set of tabs will be used per application. [Tabulous][] does provide an integrated set of sub tabs.

I'm a big fan of keeping view related code in your views, especially text, and generally don't like to use third-party plug-ins that do otherwise. Tab configuration code for [Tabs on Rails][] is located in the view as opposed to a configuration file elsewhere. [Tabulous][] uses a configuration file called app/tabs/tabulous.rb and a helper within your views: <%= tabs %>. [Tabs on Rails][] seems to be more flexible in terms of output and configuration, while [Tabulous][] is opinionated and stringent in its configuration structure, but provides a rake task to help you get configuration formatting right.

As far as styling the tabs go, the following articles by Chris Coyier will get you well on your way:

1.  [(Better) Tabs with Round Out Borders][Better Tabs]
2.  [Better Linkable Tabs][]
3.  [Tabs with Round Out Borders][Round Out Tabs]
4.  [Organic Tabs][]

[Tabs on Rails]:        http://www.simonecarletti.com/code/tabs_on_rails/
[Tabulous]:             https://github.com/techiferous/tabulous
[Better Tabs]:          http://css-tricks.com/better-tabs-with-round-out-borders/
[Better Linkable Tabs]: http://css-tricks.com/better-linkable-tabs/
[Round Out Tabs]:       http://css-tricks.com/tabs-with-round-out-borders/
[Organic Tabs]:         http://css-tricks.com/organic-tabs/