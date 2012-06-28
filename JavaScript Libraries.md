JavaScript Libraries
--------------------

On page load modernizer checks to see what features in your browser are supported, or not. Based off this detection modernizer will add a class on your <html> tag. If the feature is supported, for example CSS transforms, Modernizr will add the class .css-transforms, and if it is not supported .no-css-transforms. You can then hook into these class names to provide more modern features for browsers that will support the feature or fallback to something that will work for a particular browser that does not support it.

    It tests for over 40 next-generation features, all in a matter of milliseconds
    It creates a JavaScript object (named Modernizr) that contains the results of these tests as boolean properties
    It adds classes to the html element that explain precisely what features are and are not natively supported
    It provides a script loader so you can pull in polyfills to backfill functionality in old browsers



[Zepto][]


[Zepto]:                http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-zepto-js/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+nettuts+%28Nettuts%2B%29

