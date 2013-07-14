Information Architecting
========================

In the first section of this book we laid down the foundation of our application by:

1. Defining our base [markup][Chapter 1] and [styles][Chapter 3].
2. Choosing a [mobile][Chapter 5] content delivery strategy.

Now it's time to build a user experience on this foundation: how your users will understand your [whatever your building] and how they will [whatever they will do]. The key to being successful in building your applications user experience can be summed up in one word: **Storytelling**.

Back in 2008, at "An Event Apart: Boston," I listened to [Jason Santa Maria][] – then the Creative Director of Happy Cog Studios – give a presentation called "Good Design Ain't Easy." He described how stories were being told by design, with the designer in effect becoming the narrator. Another presenter at Fidelity Investments that same year also talked about storytelling and its importance in design. Although I no longer remember his name, I do remember his talks thesis: people understand and remember stories.

These talks have stuck with me over the years, and they have become the way I view information architecting and visual design; as storytelling. What follows is an explanation of how to build a story for your website and translate that into code, and beginning with the [next chapter][Chapter 10] we will begin to explore creating the sites look and feel (visual design) from the same perspective.

As a front end developer, without getting super complex or requiring a gazillion dollars, there are three basic ways to go about designing a website:

1. Start from scratch and architect and design everything yourself.
2. Work with a graphic designer from the get-go and implement a design mockup into your foundation work ([Chapter 14 - Slicing and Dicing Mockups][Chapter 14]).
3. Start from scratch and architect yourself, then get help from a graphic designer on the look and feel.

In this chapter we're going to mostly focus on option 1. Hiring a graphic designer from the get-go is not a bad idea, but perhaps there isn't money in the budget, or this responsibility falls on your lap, or maybe you just want to do it yourself. To illustrate how simple option 1 can be take a look at this 2007 website concept:

- http://noonebelongsheremorethanyou.com/00025

Jason Santa Maria pointed out this site in that presentation he gave. What I like about it is that it demonstrates the simplicity of storytelling: the entire site is written on kitchen appliances! ...and at the same time engages the user and ultimately delivers a message to entice action. We want to do this.

A Mosaic of Information
-----------------------

To build our story we should first explore what it means to organize an applications information and function.

> As a front end person, oftentimes taking the role of Information Architect, when I think about layout I literally think about how a site is laid out on a screen. I don't think in terms of code, but more so in terms of organization of information and function for an end-user's consumption.

\- [Chapter 1 Quote][]

How does "organizing information and function" relate to storytelling? I like to think about it in terms of traditional mosaics. What is a mosaic if not a bunch of smaller things coming together to form a meaningful whole:

> Mosaic is the art of creating images with an assemblage of small pieces of colored glass, stone, or other materials.

\- [Wikipedia][]

Individually, the components of a mosaic are meaningless, but together they form a pattern or an image. Take for example this Roman mosaic of Ulysses, from Carthage:

![][Mosaic]

Is it a meaningless conglomeration of colored tiles or does it tell a story?

A website layout is similar in that it is composed of different blocks of information that together convey a larger whole, a story: composed of text, images, color, function, and more.

As front end developers we choose and arrange what blocks belong together, and through our code create a digital mosaic, a website, that ultimately is viewed and interpreted by our audience. As such we should think of what we create, it's meaning and purpose, as storytelling and ourselves as narrators. It's not as far-fetched as it might sound at first when you consider that most websites are probably designed to invite/entice/cause the user to take a next step or action, i.e. turn the page in the story.

The Storyline
-------------

The unifying message behind this mosaic of information is the storyline or theme. Before content can be discovered, grouped, and placed in a layout, the narrator, in this case you, has to have the stories general theme in mind. For example, the storyline might be:

> I'm a great Web site for finding a job...a job that is perfect for you, you should join me, if you do you will have access to tons of perfect jobs and your life will change for the better forever!

In this storyline example – with my Information Architect (IA) hat on – I immediately see several major blocks of information:

1.  What is the site in 10 words or less – possibly a summary box.
2.  How do I join – a sign-up section.
3.  An area that describes the benefits of the site – maybe user testimonials.
4.  The obvious table stakes to this story, the side story:
    - A logo
    - Legalese (Copyright, ToS, Privacy)
    - Non-legal footer type info (Feedback, About, Contact, Site Map)

...and as the front end developer I'm already beginning to imagine how these blocks of information will be organized and coded into our application and used by our backend development team. This is exactly what you will need to do: think of an overriding storyline, organize it into blocks of information, then begin to imagine how it will be conveyed and coded. Just remember to keep the following tenant of our [Manifesto][] in mind:

> Architect and design for the end user, not developers.

Gathering and Organizing Information
------------------------------------

Before you begin coding though, it's important to take a few preliminary steps. What follows are two techniques for gathering all the blocks of information that will ultimately make up the sites story, help define the user experience, and establish a layout:

1. Index Card Exercise
2. Prototyping on Paper

NOTE: I'm going to make the assumption that you have conducted basic client discovery and subject research for your project. Also, throughout this process I highly recommend keeping the book "[Don't Make Me Think][]" by Steve Krug nearby as a reference. It’s a good read and everything he says is so darn obvious, and all there in one place.

### Index Card Exercise

The first technique involves the use of index cards to create a physical inventory of possible information components. It's best to do this exercise with others, especially stakeholders in the project. Here are the steps I follow:

*Step 1:* Write down in a word or two on an index card what the card represents: content, function, a navigational element, an image, video, whatever.

Think of as many components to the page or application as you can - I prefer dealing with a single view at a time, like the homepage.

NOTE: Color coding is helpful.

*Step 2:* Lay out the index cards on a table, organize them into logical groups like navigational or footer areas.

*Step 3:* Review the cards on the table and start eliminating the cards that you don't want to include. Don't be conservative in eliminating.

> KISS (keep it simple stupid)

\- [Manifesto][]

Here's a practical example and a proof of concept. I need a new website for my practice "View Thought". My storyline goes something like this:

> We are a great website design, development and user experience shop. We have tons of experience, have worked with a bunch of different clients who are all happy with our work, and we really care about what we do. We specialize in Ruby on Rails, and we pay special attention to what your users will see. You should hire us! ...or give us a call and learn more.

I immediately can see a few index card entries in my storyline and start indexing everything I can think of. Beside my own ideas though, it's a good practice to do some basic research and see what competitors or similar services are doing with their websites.

TIP: It's a good idea to bookmark a bunch of sites to review and reference throughout the process. It's sometimes helpful to add a simple tally on the bottom of index cards to see how many sites referenced used that particular element:

![][Index Card Reference]

After completing Step 2 here is what my entries look like laid out on a table:

![][Index Before]

I have 200 index cards laid out and grouped as navigation, content, or footer information. As I review I begin to remove components I don't plan to use. I also start to think about where information will be placed. I want to call attention to different parts of the story depending on its relevance and importance to the story. These components I move higher up on the table. Basically I think like a newspaper layout editor.

After evaluating and reorganizing here is what I'm left with:

![][Index After]

Quite a bit less, and through the process I really have a great grasp on what my site will look like and how I'm going to start coding, but I need to whittle it down even further since we're going to use the mobile first approach.

> Provide for the mobile experience as a forethought.

\- [Manifesto][]

We need to shed even more. Here's what I'm left with after further elimination:

![][Index Mobile]

And there you have it, the application in its absolute simplest form doing only the things that are most important. From here we can build up to the desktop.

NOTE: You can also use a digital equivalent to index cards like PowerPoint, or even a single sheet of paper (as a list of items), but index cards are best. You can buy a pack of 200 index cards for under a dollar so don't be afraid to get nitty-gritty with what you define as an information component.

I find that the process I just described works best for me, but there are other ways to go about this. Check out how this design group uses index cards:

- [Responsive Design Case Study][Case Study]

On a final note on index carding, as a front end developer with years of practice, a huge part of me just wants to bypass this exercise and start coding (and change things on the fly as I move along). So why don't I? Experience has shown me that the manual process of labeling index cards and laying them out forces me to reflect and think outside of my coding box. It helps me discover new ideas, visualize and refine the information architecture, and not work in isolation (i.e. include others in the process). I find that by doing the exercise there's just enough chance of a better outcome that it's worth trying.

> Test across major browsers, devices, and in front of "real-life" users.

> Think in terms of all use cases including and especially accessibility.

> Architect and design for the end user, not developers.

\- [Manifesto][]

### Prototyping on Paper

So with the index card exercise done, the next step in my process is to take the resulting information architecture and create a paper prototype ([sketching][]). Doing so will help you better define the layout, visualize what the site will look like on a screen, visualize how pages interconnect, and give you plenty of room for trial and error. It also provides you with some additional and inexpensive opportunities for stakeholder input, and further reflection and brainstorming before you begin coding.

There are a number of applications out there that can help you prototype, but I prefer to go old-school with pencil and paper. For presentational purposes you can transfer this exercise to PowerPoint or some other application for prototyping, but don't get bogged down and waste time doing so. Paper is highly portable, can be digitized (scan), requires no electricity or Internet connectivity, can easily be shared with others, and its use is a skill that is common between all stakeholders.

Here are some device mockup resources that will help you sketch:

- [Generated Paper][]
- [Interface Sketch][]
- [Responsive Sketchsheets][]
- [UX Sketching And Wireframing Templates For Mobile Projects][Mobile Sketching]

To begin just simply translate what you indexed in the previous section into what it might look like on a screen. Here's what my paper prototype process looks like starting with a blank sheet of paper next to my index cards and ending with a paper prototype:

![][Prototype]

The end result: a well-defined user interface layout for my entire application.

TIP: As you prototype always have an eye on your bookmarked reference websites, and/or some of the [inspirational sites][Appendix 5] listed in the Appendices. Revise and release often.

Here are some inspirational examples of prototyping on paper for your review:

[UI & Wireframe Sketches for your Inspiration][Inspirational]

Wireframing
-----------

**No More Exercises!** At this point it's time to start coding. From the exercises above you have absolutely everything you need to start coding with confidence knowing that the site's information architecture and layout are pretty darn close to what you will ultimately develop.

The prototype is the blueprint, and what you code moving forward will serve as your living wireframe. A living wireframe in that if clients/teammates/stakeholders need to review beyond the early exercises, you can send them to a live URL where they can click through to simulate the actual application (and view it on different devices). Any changes you make will be reflected immediately, which they'll love. For you, everything from this point forward is just an iteration in the development process.

Because you laid out your applications [markup][Chapter 1], [styles][Chapter 3], and [mobile][Chapter 5] groundwork in chapters 1 through 5 – and hopefully have deployed on Heroku or elsewhere – what you wireframe will ultimately be production ready, and in this section we will begin to transform our paper prototype into a working wireframe.

NOTE: An assumption I will make is that you already are a proficient front end coder, so going into how to go about writing basic markup from the prototypes we just developed is something I won't get into.

After codifying my prototypes here is what I have:

![][Wireframe]

![][Laptop]

Pretty bare-bones, but that will soon change.

### Wireframing with Susy

In Chapter 3 we learned how to [install and implement Susy][Chapter 5 - Susy]. It's a powerful tool which I strongly recommend you use. Using it will allow you to quickly layout of the content of your application, set breakpoints, and test across different devices until you zero in on the perfect layout for your project.

One feature that will help you wireframe is the grid background tool:

![][Laptop Grid]

These grid guides are very similar to what [Compass offers][], and can be activated by simply adding the following line to your .container's CSS properties:

    .container
      +container
      +susy-grid-background

### Content

A word on content. If you have it great! If not, the following article gives a nice overview of how content blocks can be used in situations where content is not known, perhaps a client has not yet delivered it:

- [Content, First?][Content First]

I for one don't mind using Lorem Ipsum or images as content placeholders, but nothing can really truly substitute for actual content so if you can find it or create it, do so. I've put together a pretty comprehensive list of [placeholder services][Appendix 6] for your benefit in the Appendices. It includes text and image placeholder services.

Although I like to use [Dummy Image][], I also keep a 1px x 1px transparent gif, sometimes referred to as a shim, in our assets/images/fixtures folder. It can be used as follows to create image placeholders:

    = link_to image_tag('fixtures/shim.gif', :alt => '', :width => '75', :height => '75'), root_path, :title => ''

Don't forget to set the color:

    img
      background-color: gray

Feedback and Testing
--------------------

One very important thing to practice when designing interfaces is do nothing in isolation, and consider everything you think as intuitive to be wrong! (until proven otherwise) Iterating is key. Get feedback from your end users and refine. If you can't get to them, then ask your neighbor, a friend, or try one of the services listed in the [Feedback Services][Appendix 7] of the Appendices.

> Test across major browsers, devices, and in front of "real-life" users.
\- [Manifesto][]

Testing on actual devices is also very important. Resizing a browser window and/or using device simulators cannot substitute for an actual device. The "[Device Testing][Appendix 7]" section in of the Appendices lists several useful articles to get you started on testing or building your own testing lab. As a rule of thumb, test on at least four different devices: desktop, tablet, small tablet, and a smartphone. Walk into the Mac store, or Verizon, or AT&T if you have to and test away.

At the end of our information architecting cycle, with our basic content and layouts in place, here's what we're left with across several different devices:

![][Multidevice]

We were able to rapidly create wireframes across multiple devices by using [Susy breakpoints][Susy]. Now all that we need to do is make our wireframes look pretty! We will tackle this head beginning with Chapter 10, "[Visual Design for the Nondesigner][Chapter 10]".

What We've Done
---------------

In this chapter we began with a discussion on storytelling and how important it is to information architecting and visual design. We then described how storytelling in information architecting is similar to traditional mosaics in that both are comprised of bits of information that together tell a story.

Understanding our own storyline, we began a process of converting our thoughts into a living wireframe through the use of two techniques:

1. Index Card Exercise
2. Prototyping on Paper

Together these two exercises, along with the foundation code we already laid out in chapters 1 -  3, made wireframing a cinch. To further ease the creation process I also recommended the use of Susy, and ended with a quick talk on content.

The end result of this chapter's work is a complete wireframe, ready for the next step in storytelling, but before we move onto visual design consider this for a moment: As front end developers we oftentimes think in terms of boxes. Notice our wireframe is essentially a layout of different content boxes. As we move into design mode [in the next chapter][Chapter 10] we need to completely change how we use our brains.

Just remember, less is more and KISS (Keep It Simple Stupid).

[Manifesto]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/MANIFESTO.md
[Chapter 1]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md#foundation-markup
[Chapter 3]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-foundation-styles.md#foundation-styles
[Chapter 5]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-mobile-foundation.md#mobile-foundation
[Chapter 10]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp10-visual-design-for-the-nondesigner.md#visual-design-for-the-nondesigner
[Chapter 14]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp14-slicing-and-dicing-mockups.md#slicing-and-dicing-mockups
[Appendix 5]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-5
[Appendix 6]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-6
[Appendix 7]:           https://github.com/maxxiimo/the-front-end-manifesto/blob/master/appendices.md#appendix-7

[Jason Santa Maria]:    http://jasonsantamaria.com/

[Chapter 1 Quote]:      https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp1-foundation-markup.md#foundation-markup#the-application-layout
[Wikipedia]:            https://en.wikipedia.org/wiki/Mosaic

[Don't Make Me Think]:  http://www.sensible.com/index.html

[Case Study]:           http://builtbyboon.com/blog/responsive-design-case-study

[sketching]:            http://tympanus.net/codrops/2013/01/29/planning-your-web-design-with-sketches/
[Generated Paper]:      http://generatedpaper.com/en/wireframing
[Interface Sketch]:     http://interfacesketch.tumblr.com/
[Responsive Sketchsheets]: http://zurb.com/playground/responsive-sketchsheets
[Mobile Sketching]:     http://uxdesign.smashingmagazine.com/2012/09/18/free-download-ux-sketching-wireframing-templates-mobile/
[Inspirational]:        http://webdesignledger.com/inspiration/ui-wireframe-sketches-for-your-inspiration

[Chapter 5 - Susy]:     https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp5-mobile-foundation.md#mobile-foundation#using-susy
[Compass offers]:       http://compass-style.org/reference/compass/layout/grid_background/

[Content First]:        http://alwaystwisted.com/post.php?s=2012-10-13-content-first
[Dummy Image]:          http://dummyimage.com

[Susy]:                 https://github.com/maxxiimo/the-front-end-manifesto/blob/master/chp3-mobile-on-rails.md#susy-breakpoints

[Mosaic]:               http://chrismaxwell.com/manifesto/chp-9/mosaic-800px.gif
[Index Card Reference]: http://chrismaxwell.com/manifesto/chp-9/index-cards/index-card-reference.gif
[Index Before]:         http://chrismaxwell.com/manifesto/chp-9/index-cards/index-cards-before.jpg
[Index After]:          http://chrismaxwell.com/manifesto/chp-9/index-cards/index-cards-after.jpg
[Index Mobile]:         http://chrismaxwell.com/manifesto/chp-9/index-cards/index-cards-mobile.jpg
[Prototype]:            http://chrismaxwell.com/manifesto/chp-9/prototype.jpg
[Wireframe]:            http://chrismaxwell.com/manifesto/chp-9/wireframe/ipad-wireframe.gif
[Laptop]:               http://chrismaxwell.com/manifesto/chp-9/wireframe/laptop-home.gif
[Laptop Grid]:          http://chrismaxwell.com/manifesto/chp-9/wireframe/laptop-home-grid.gif
[Multidevice]:          http://chrismaxwell.com/manifesto/chp-9/wireframe/multidevice.gif
