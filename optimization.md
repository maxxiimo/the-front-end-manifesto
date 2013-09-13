Optimization
------------

Chris Coyier of [CSS-Tricks][] recently published a video called "[Let's Do Simple Stuff to Make Our Websites Faster][Simple Stuff]". Take a look at the first 10 minutes of this video, it gives a stellar overview and introduction into optimization. I particularly like some of the material he brings into the discussion from other thought leaders. The research of one in particular illustrates why optimization in the front end is so important:

> 80-90% of the end-user response time is spent on the frontend.

\- ["The Performance Golden Rule"][Golden Rule] by Steve Souders

If you're interested, also check out Steve Sounders article:

- [High Performance Web Sites: The Importance of Front-End Performance][Performance]

Now shift over to mobile, and according to "[Early findings: 97% of mobile end-user response time happens at the front end][97%]" the performance Golden rule number increases significantly.

### Gzipping

[gzipWTF][]

Research this: https://help.heroku.com/search/gzip

### Caching

[Caching with Rails: An overview][Caching]

#### Client-Side

In client-side caching the browser stores website assets. When these assets are cached, the browser does not need to request them from the server again thereby saving the user a round-trip in communication and delivery of an asset.

> The fastest HTTP request is the one not made.
\- Anonymous

You tell browsers how long to cache things for.



Serve up different image formats depending on the size of the image.



##### Caching Styles

Versioning stylesheets breaks the cache.


#### Server-Side

Script loaders. Asynchronously or in parallel.


**Step 1**: Add

https://github.com/rumblelabs/asset_sync
https://devcenter.heroku.com/articles/cdn-asset-host-rails31
http://blog.firmhouse.com/complete-guide-to-serving-your-rails-assets-over-s3-with-asset_sync

http://stackoverflow.com/questions/11261805/rails-3-font-face-failing-in-production-with-firefox
http://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html#how-do-i-enable-cors

http://thisbythem.com/blog/rails-heroku-cloudfront-font-assets/

### Image Optimization

Mac
[CodeKit][]

Windows
[PNGGauntlet][]
[ImageOptim][]
[Pngcrush][]
[PngUtils][]

Linux
[Trimage][]

### Compressing and the Asset Pipeline

Now that we have image optimization covered, let's take a look at compressing and the asset pipeline. First, why do we need to compress? The answer is optimization: byte savings, decreased load times, and less trips to the server. In the old days I might have used something like one of the following to compress and minify my code:

- [CSS Compressor & Minifier][CSS compressor]
- [Google Minify][]
- [Online JavaScript/CSS Compression Using YUI Compressor][YUI Compressor]

These days the asset pipeline does it all for you.

> The asset pipeline has three goals:
> precompile, concatenate and minify assets into one central path.

\- [Asset Pipeline for Dummies][Asset Pipeline]

The only thing I'll add to this is just remember to precompile before you deploy to production:

    bundle exec rake assets:precompile

For more details on asset pipeline compression follow these links:

- [CSS compression][]
- [JavaScript Compression][JS Compression]
- [Using Your Own Compressor][Generic Compressor]

### Spriting






[Optimize browser rendering][Browser Rendering]

[Writing efficient CSS][Efficient CSS]

[Making the Web Fast(er)][Fast(er)]



[Trimage][]


[The Essentials of Zepto.js][Zepto]



### What We've Done

- We took a look at how Rails helps us optimize the styles we produce through compression and the asset pipeline.


[CSS-Tricks]:           http://css-tricks.com/
[Simple Stuff]:         http://css-tricks.com/video-screencasts/114-lets-do-simple-stuff-to-make-our-websites-faster/
[Golden Rule]:          http://www.stevesouders.com/blog/2012/02/10/the-performance-golden-rule/
[Performance]:          http://developer.yahoo.com/blogs/ydn/posts/2007/03/high_performanc/
[97%]:                  http://www.webperformancetoday.com/2011/04/20/desktop-vs-mobile-web-page-load-speed/
[gzipWTF]:              http://gzipwtf.com/
[Caching]:              http://edgeguides.rubyonrails.org/caching_with_rails.html
[CodeKit]:              http://incident57.com/codekit/
[PNGGauntlet]:          http://pnggauntlet.com/
[ImageOptim]:           http://imageoptim.com/
[Pngcrush]:             http://pmt.sourceforge.net/pngcrush/
[PngUtils]:             http://gnuwin32.sourceforge.net/packages/pngutils.htm
[Trimage]:              http://trimage.org/
[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/

[CSS Compressor]:       http://www.minifycss.com/css-compressor/
[Google Minify]:        https://code.google.com/p/minify/
[YUI Compressor]:       http://www.refresh-sf.com/yui/
[Asset Pipeline]:       http://coderberry.me/blog/2012/04/24/asset-pipeline-for-dummies/
                        "The Rails asset pipeline from the ground up."
[CSS Compression]:      http://edgeguides.rubyonrails.org/asset_pipeline.html#css-compression
[JS Compression]:       http://edgeguides.rubyonrails.org/asset_pipeline.html#javascript-compression
[Generic Compressor]:   http://edgeguides.rubyonrails.org/asset_pipeline.html#using-your-own-compressor


[Browser Rendering]:    https://developers.google.com/speed/docs/best-practices/rendering
[Efficient CSS]:        https://developer.mozilla.org/en/Writing_Efficient_CSS
[Fast(er)]:             http://www.igvita.com/slides/2012/railsconf-making-the-web-faster/#1
                        "RailsConf 2012"
