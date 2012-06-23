Use a Preprocessor
------------------

I use [Sass][]. Long before using a CSS preprocessor I was hooked on Sass's brother [Haml][] and naturally made the progression. More importantly, for you, it is now the default preprocessor in Rails 3.X. Besides being awesome, you are more than likely going to predominantly see Sass used in projects you work on, or by other front-end developers you work with.

If you do use it, go with .sass. The file and rank will probably go with .scss because it looks familiar, and because that is what ships out-of-the-box in Rails, however, .sass is cleaner/terser.

To help you decide, read this:

[Sass vs. SCSS: Which Syntax is Better?][Sass vs. SCSS]

Note: These two resources are absolutely indispensable:

[css2sass][]

[Html2Haml][]

In terms of other preprocessors, [Less][] is the runner-up.

[Twitter Bootstrap, Less, and Sass: Understanding Your Options for Rails 3.1][Options]

### Compressing

Why compress? Byte savings, increase load times.

In the old days I might have used something like these:

[CSS Compressor & Minifier][CSS compressor]
[Google Minify][]
[Online JavaScript/CSS Compression Using YUI Compressor][YUI Compressor]

Compass also provides this ability. But these days with the asset pipeline, all you need to do now is precompile:

    bundle exec rake assets:precompile

> The asset pipeline has three goals:
> precompile, concatenate and minify assets into one central path.
>
> - [Asset Pipeline for Dummies][Asset Pipeline]


[Sass]:                 http://sass-lang.com/
[Haml]:                 http://haml-lang.com/
[Sass vs. SCSS]:        http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better
[css2sass]:             http://css2sass.heroku.com/
[Html2Haml]:            http://html2haml.heroku.com/
[Less]:                 XXXX
[Options]:              http://rubysource.com/twitter-bootstrap-less-and-sass-understanding-your-options-for-rails-3-1/
[CSS Compressor]:       http://www.minifycss.com/css-compressor/
[Google Minify]:        https://code.google.com/p/minify/
[YUI Compressor]:       http://www.refresh-sf.com/yui/
[Asset Pipeline]:       http://coderberry.me/blog/2012/04/24/asset-pipeline-for-dummies/
                        "The Rails asset pipeline from the ground up."