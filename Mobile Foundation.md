Mobile Foundation
-----------------

Chapter 1 and 2 are great, really great in my opinion ;-), but what about mobile? What about iPads? What about mobile browsers!! In the old days all you really had to worry about "cross anything" were browser issues. I mean on the fringe back then there was talk about desktop screen sizes, but it could be overlooked. 

Nowadays you cannot overlook screen sizes. You better believe that people are going to look at your website on a mobile phone or some kind of tablet, especially an iPad. In fact I think this is pretty much [common knowledge][], so let's just deal with it. How? Let's explore in this chapter.

### Mobile First

Once upon a time ago when I worked for Fidelity Investments' FEB Design unit, we took an existing application and turned it into a mobile app (pre-smartphones). The result was a precise definition of the applications basic information architecture, no more no less. As an Information Architect with this experience, the [Mobile First][] design paradigm makes sense. I don't think anyone can afford to consider mobile design as an afterthought anymore.

Yes, we did layout are foundation markup and styles with the desktop in mind, and that is fine and as it should be, but as we move into the next chapter we actually start thinking about how to build an application, and we do so tackle it from the mobile first perspective.

By the end of this chapter we will have completed our foundation work underrated tackle any browser, device, or screen size.

### Plan of Attack

With Ruby on Rails there are three ways we can tackle mobile browsers:

1.  Detecting user agents to serve mobile specific markup and styles.

2.  Detecting screen sizes via media queries to serve up responsive styles (that also can hide markup via display: none).

3.  A hybrid of 1 and 2.

I'm undecided about which method I prefer insofar as 1 and 2 go. My gut tells me to separate concerns. Anyway, here are my thoughts on the subject:

- Keep them separate and you can serve lighter, device specific stylesheets. This translates to less complexity and better performance.
- Did I mention complexity?
- As applications grow and user needs change, it might become necessary to separate mobile out completely. If you start out separate this transition might be easier.
- Keep styles together, and no one will be left out, i.e. you won't forget to work on one while working on the other.
- Designing for a mobile device, a tablet device, and a desktop could be time-consuming, response styles can accommodate all three.

Right now "responsive" based on media queries is the rage. The article "[CSS MediaQuery for Mobile is Fool’s Gold][Media Queries]" does a great job of illustrating why media queries might not be the silver bullet for serving up mobile styles and content. There is one quote there that the author uses that resonates with me:

> Create a product, don’t re-imagine one for small screens. Great mobile products are created, never ported.
\- [Brian Fling][]

Whatever you decide, keep in mind that there are a spectrum of needs and responsive may in fact be the silver bullet for some sites on that spectrum. For example my personal website most certainly won't need mobile specific geolocation capabilities, and all on all, the changes required between screens is minor. In this case why not use media queries and keep things together?

> Only using responsive design for Basecamp mobile would have been like fitting a Prius body to a Hummer… under-the-hood it would have been all wrong.
\[Behind the speed: Basecamp mobile][Basecamp Mobile]

In this chapter we will explore both plans of attack.

### User Agent Sniffing

Back at Fidelity mobile was a complete separate concern from desktops, it had to be. I worked there slightly before smart phones emerged, and back then smallscreen devices oftentimes did not allow CSS, or existed behind a walled garden that did not allow JavaScript or HTML tables or some other kind of limitation. Back then there were so many different types of devices, rules, and screen sizes, and it was our objective to cover 99.999% [possibly exaggerated by me] of all small screen devices out there. Why? Imagine a billionaire customer from Bahrain trying to look at his or her Fidelity portfolio on some obscure cell phone and nothing showing up! [rationale also made up by me]

To accomplish ubiquity we developed a super dumbed down HTML 1.0 interface that would work on 90% of all small screen devices, remember pre-smart phone, and for the remaining devices serve up alternative markup that would display content correctly and consistent with the company's brand/look and feel.  How do we know when to serve up the correct markup? By analyzing the devices user agent (HTTP_ACCEPT header and HTTP_USER_AGENT header). Over time with all the customers that fidelity had, the company developed an exhaustive database of devices their customers used which included the device's screen size, operating system, and other pertinent information. With that information they could tailor out markup that would work on the majority of their clients smallscreen devices.

Fast-forward to today, with smart phones for the most part we now concentrate solely on screen size (and hooking into a device's native functionality as a non-native entity, but that's for another chapter). One huge difference between then and now is the mobile browser. With its maturity and ubiquity across these devices, as front end developers we can concentrate on real estate, and like my days at Fidelity, will use the user agent to determine what markup and styles to serve.

#### An Introduction

To get started, if you're not sure where to begin, take a look at Ryan Bates screencast "[Mobile Devices][]".


### Responsive Web Design

Ethan Marcotte is widely credited for coining the term "Responsive Web Design" in his 2010 article "[Responsive Web Design][Responsive]". 

[This Is Responsive][]

### Where Do Styles Go?

Some argue that including mobile and print* styles in the same partials will help you remember that they are there. 







????
"Because the assets all concatenate into one file, there are no seperate files to be included on a view-by-view basis." [Asset Pipeline for Dummies][Asset Pipeline]

[common knowledge]:     http://www.themobileplaybook.com/en-us/#/cover
[Mobile First]:         http://www.abookapart.com/products/mobile-first
[Media Queries]:        http://blog.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
[Brian Fling]:          http://shop.oreilly.com/product/9780596155452.do
[Basecamp Mobile]:      http://37signals.com/svn/posts/3269-behind-the-speed-basecamp-mobile               
[Mobile Devices]:       http://railscasts.com/episodes/199-mobile-devices

[Responsive]:           http://www.alistapart.com/articles/responsive-web-design/
[This Is Responsive]:   http://bradfrost.github.com/this-is-responsive/index.html

