Preprocessors and Frameworks
----------------------------

### Sass and Less

Probably the two most well-known dynamic stylesheet preprocessors out there are [Sass][] and [Less][].

[Sass][] is the sister of [Haml][], and my preprocessor of choice as well as the default preprocessor in Rails 3.X. Besides being awesome, you are more than likely going to predominantly see Sass used in projects you work on, so if you haven't dived in already, you should.

When using sass you have a choice in syntax; .sass or .scss. I prefer .sass. The rank-and-file will more than likely go with .scss because it looks familiar (similar to CSS), and because that is what ships out-of-the-box in Rails, however, .sass is cleaner/terser (IMHO). To help you decide on syntax for you read this:

[Sass vs. SCSS: Which Syntax is Better?][Sass vs. SCSS]

Note: When using Sass or Haml these two resources are absolutely indispensable:

[css2sass][]

[Html2Haml][]

In terms of other preprocessors, [Less][] is the runner-up. That's all I'm going to say about that for now (see Twitter Bootstrap below).

### Twitter Bootstrap

[I like it][Twitter Bootstrap]. It's a great place to learn about best practices for any application or framework. It's well-documented, but here's the problem: it's built on [Less][], and use it and your site will look pretty much like everyone else's. Of course you can override styles, but I'm just sayin'.

Getting it to work with Rails is not impossible, hardly, but does give you some choices to consider:

[Twitter Bootstrap, Less, and Sass: Understanding Your Options for Rails 3.1][Options]

### Compass

[I love it][Compass].

The following resources will help you set up compass in your rails project:

- [compass-rails][]
- [Getting Compass to Work With Rails 3.1 (and 3.2)][Working]
- [35 Great Resources for Compass and Sass][35 Great Resources]

### Blueprint


### Compressing and the Asset Pipeline

Why compress? Byte savings, decrease load times. In the old days I might have used something like these to compress and minify my code:

[CSS Compressor & Minifier][CSS compressor]
[Google Minify][]
[Online JavaScript/CSS Compression Using YUI Compressor][YUI Compressor]

These days the asset pipeline does it all for you.

> The asset pipeline has three goals:
> precompile, concatenate and minify assets into one central path.
>
> - [Asset Pipeline for Dummies][Asset Pipeline]

Just remember to precompile before you deploy to production:

    bundle exec rake assets:precompile

[Sass]:                 http://sass-lang.com/
[Less]:                 http://lesscss.org/
[Haml]:                 http://haml-lang.com/
[Sass vs. SCSS]:        http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better
[css2sass]:             http://css2sass.heroku.com/
[Html2Haml]:            http://html2haml.heroku.com/
[Twitter Bootstrap]:    http://twitter.github.com/bootstrap/
[Options]:              http://rubysource.com/twitter-bootstrap-less-and-sass-understanding-your-options-for-rails-3-1/
[Compass]:              http://compass-style.org/
[compass-rails]:        https://github.com/Compass/compass-rails/blob/master/README.md
[Working]:              http://blog.55minutes.com/2012/01/getting-compass-to-work-with-rails-31-and-32/
[35 Great Resources]:   http://fuelyourcoding.com/35-great-resources-for-compass-and-sass/
[Blueprint]:            http://www.blueprintcss.org/
[CSS Compressor]:       http://www.minifycss.com/css-compressor/
[Google Minify]:        https://code.google.com/p/minify/
[YUI Compressor]:       http://www.refresh-sf.com/yui/
[Asset Pipeline]:       http://coderberry.me/blog/2012/04/24/asset-pipeline-for-dummies/
                        "The Rails asset pipeline from the ground up."
