Mobile Browsers
---------------

Chapter 1 and 2 are great, really great in my opinion ;-), but what about mobile? What about iPads? What about mobile browsers!! In the old days all you really had to worry about "cross anything" were browser issues. I mean on the fringe back then there was talk about desktop screen sizes, but it could be overlooked. 

Nowadays you cannot overlook screen sizes. You better believe that people are going to look at your website on a mobile phone or some kind of tablet, especially the iPad. In fact I think this is pretty much common knowledge and accepted, so let's just deal with it. How? In a word... Responsive.

### Responsive Web Design

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][Responsive]". 


### Mobile First

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing application and turned it into a mobile app (pre-smartphones). The result was a precise definition of the applications basic information architecture, no more no less. As an Information Architect with this experience, and knowing that today more than likely most of my users have or will have a smart phone soon, I like to architect with the mobile user in mind first, or in the very least simultaneously. Doing so allows me to architect with less fluff and develop mobile styles right from the get-go.

It's not easy doing it this way, especially after years in years where mobile was an afterthought, or not even considered at all.

### Where Do Styles Go?

Some argue that including mobile and print* styles in the same partials will help you remember that they are there. I personally won't forget about mobile styles, and neither will you. I think mobile styles should be a separate beast altogether, and here is why: 

- Keep them separate and you can serve lighter, device specific stylesheets.
- As applications grow and user needs change, it might become necessary to add someone to your team who specializes in mobile. No need to clutter up their work.
- Mobile and desktop are different beasts, and these divergent paths require significantly different view approaches.

### User Agents or Media Queries

Personally, I prefer to use user agents to serve up the correct styles and HTML. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" does a great job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. To get you started, if you're not sure where to begin, take a look at Ryan Bates screencast "[Mobile Devices] []".

* It is not uncommon to generalize print styles in a separate stylesheet.


????
"Because the assets all concatenate into one file, there are no seperate files to be included on a view-by-view basis." [Asset Pipeline for Dummies][Asset Pipeline]

[Responsive]:           http://www.alistapart.com/articles/responsive-web-design/
[Media Queries]:        http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices
