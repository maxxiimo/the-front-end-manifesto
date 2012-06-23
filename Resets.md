Resets
------

The granddaddy of all resets is Eric Meyer's "Reset CSS". [http://meyerweb.com/eric/tools/css/reset/index.html]

Sometimes I use compass' reset utilities [http://compass-style.org/reference/compass/reset/utilities/] which are based on Eric Meyer's work, but lately my preference has been to use Normalize.css [https://github.com/necolas/normalize.css/]. HTML 5 boilerplate uses normalize.css with slight variations and style additions. The author of Normalize.css describes what it does best:

"Normalize.css is a customisable CSS file that makes browsers render all elements more consistently and in line with modern standards. We researched the differences between default browser styles in order to precisely target only the styles that need normalizing."

I converted Eric Meyer's, and both the original normalize.css and HTML 5 Boilerplate styles to .sass and .scss here:

https://github.com/maxxiimo/sass-resets

In the case of H5BP, I have commented out some of the typographic styles to give myself the option to keep them or move them into more appropriate partials (per the organization section of this manifesto). Here is an example how I might use them:

[Upload to Github.]

The following article briefly outlines the changes in resets moving into HTML 5: 

HTML5 Reset Stylesheet [http://html5doctor.com/html-5-reset-stylesheet/]
