Information Architecting
------------------------

Now that we have reviewed the three pillars of foundation work: [markup][], [styles][], and [mobile][], it's time to delve into actually building a websites/application. The best place to start is with the splash page or application console: its navigation, content, interaction, layout, and look and feel. The homepage is of critical importance to your project. Most of the time it is the first thing a user will see, and how they will understand your [whatever your building] and how they will [whatever they will do]. It also sets the tone and unifying theme for every subsequent page or functionality.

The key to being successful in building your application splash page and/or console can be summed up in one word: **Storytelling**.

Back in 2008, at "An Event Apart: Boston," I listened to [Jason Santa Maria][] -- then the Creative Director of Happy Cog Studios -- give a presentation called "Good Design Ain't Easy." He described how stories were being told by design, with the designer in effect becoming the narrator. Another presenter at Fidelity Investments that same year also talked about storytelling and its importance in design. Although I no longer remember his name, I do remember his talks thesis: people understand and remember stories.

These talks have stuck with me over the years and have become the manner in which I view website site design; as storytelling. What follows is an explanation of how to build a story for your website, and translate that into code and the sites look and feel (styles). As a front end developer, without getting super complex or requiring a gazillion dollars, there are three basic ways to go about this:

1. Start from scratch and architect and design everything yourself.
2. Work with a designer from the get-go and implement a design mockup into your foundation work.
3. Start from scratch and architect yourself, then get help from a designer on the look and feel.

In this chapter we're going to mostly focus on option 1. Hiring a designer from the get-go is not a bad idea -- graphic design and front end engineering are two complete different skill sets -- but perhaps there isn't money in the budget to hire a designer, or this responsibility falls on your lap, or maybe you just want to do it yourself.

NOTE: As a consultant brought into a project, oftentimes design mockups have already been developed and it's now my job to integrate them into the application. The next chapter, [Slicing and Dicing Mockups][Slicing and Dicing] will dive into the mechanics of doing exactly that.

### A Mosaic of Information

To build our stories the first thing we need to understand is what it means to organize an applications information. As I mentioned in [Chapter 1][Chapter 1 Quote]:

> As a front end person, sometimes called an Information Architect, when I think about layout I literally think about how a site is laid out on a screen. I don't think in terms of code, but more so in terms of organization of information and function for an end-user's consumption.

How does "organizing information and function" relate to storytelling?

A layout is really a mosaic of information that tells (conveys) something: a particular type of story. This information obviously was grouped together based on some criteria, and then placed on a website "page" that ultimately is viewed by an end-user. It had to be organized in some logical way to make absolute sense to the end-user, and probably designed to invite/entice/cause the end-user to take the next step or action, i.e. turn the page in the story.

### The Storyline

The unifying message behind this mosaic (blocks) of information is the storyline. Before content can be discovered, grouped, and placed in a layout the narrator, in this case you, has to have the stories general theme in mind. For example, the storyline might be:

> I'm a great Web site for finding a job...a job that is perfect for you, you should join me, if you do you will have access to tons of perfect jobs and your life will change for the better forever!

In this storyline example -- with my Information Architect (IA) hat on -- I immediately see several major blocks of information:

1.  What is the site in 10 words or less -- possibly a summary box.
2.  How do I join -- a sign-up section.
3.  An area that describes the benefits of the site -- maybe user testimonials.
4.  The obvious table stakes to this story, the side story:
    - A logo
    - Legalese (Copyright, ToS, Privacy)
    - Non-legal footer type info (Feedback, About, Contact, Site Map)

...and as the front end developer I'm already beginning to imagine how these blocks of information will be conveyed and coded to fit into our foundation markup and/or used by our backend development team. This is exactly what you will need to do. Think of an overriding storyline, organize it into blocks of information, then begin to imagine how it will be conveyed and coded.

### Gathering and Organizing Information

Before you begin coding though, it's important to take a few preliminary steps. What follows are different techniques I use to gather all the blocks of information that will ultimately make up the sites story, i.e. users experience.

NOTE: Throughout this process I highly recommend keeping the book "[Don't Make Me Think][]" by Steve Krug nearby as a reference. It’s a good read and everything he says is so darn obvious, and all there in one place.

#### Index Card Exercise

The first technique involves the use of index cards to create a physical inventory of possible information components. It's best to do this exercise with others, especially stakeholders in the project. Here are the steps I follow:

**Step 1:** Write down in a word or two on an index card what the card represents: content, function, a navigational element, an image, video, whatever.

Think of as many components to the page or application as you can - I prefer dealing with a single view at a time.

NOTE: Color coding is helpful. You can also use a digital equivalent to index cards like PowerPoint, or even a single sheet of paper (as a list of items), but index cards are best. You can buy a pack of 200 index cards for under a dollar, so don't be afraid to get nitty-gritty with what you define as an information component.

**Step 2:** Lay out the index cards on a table and organize them into logical groups like navigational or footer areas.

**Step 3:** Start eliminating all the cards you don't want to include.

Here's a practical example. I need a new website for my practice "ViewThought". My storyline goes something like this:

> We are a great website design, development and user experience shop. We have tons of experience, have worked with a bunch of different clients who are all happy with our work, and we really care about what we do. We specialize in Ruby on Rails, and we pay special attention to what your users will see. You should hire us! ...or give us a call and learn more.

I immediately can see a few index card entries in my storyline and start writing out everything I can think of. Beside my own ideas though, it's a good idea to do some basic research like see what competitors or similar services are doing with their websites.

TIP: It's a good idea to bookmark a bunch of sites to review and reference throughout the process. It's sometimes helpful to add a simple tally on the bottom of cards to see how many sites reference use that particular element.

Here's what all my entries look like laid out on a table:

![][Index Before]

I have 200 index cards laid out and grouped as navigation, content, or footer information. As I review I begin to remove components I don't plan to use. I also start to think about where information will be placed. I want to call attention to different parts of the story depending on its relevance and importance to the story. These components I move higher up on the table. Basically I think like a newspaper layout editor.

After evaluating and reorganizing here is what I'm left with:

![][Index After]

Quite a bit less, and through the process I really have a great idea about what my site will look like and how I'm going to start coding, but I need to whittle it down even further since we're going to use the mobile first approach. We need to shed even more. Here's what I'm left with:

![][Index Mobile]

...And there you have it, the application in its absolute simplest form doing only the things that are most important. From here we can build up to the desktop.

Check out how this design group uses index cards:

- [Responsive Design Case Study][Case Study]

As a front end developer with years of practice, a huge part of me just wants to bypass this exercise and start coding (and change things on the fly as I move along). So why don't I? Experience has shown me that the manual process of labeling index cards and laying them out forces me to reflect and think outside of my coding box. It helps me discover new ideas, visualize and refine the information architecture, and not work in isolation (i.e. include others in the process). I find that by doing the exercise there's just enough chance of a better outcome that it's worth trying.

#### Prototyping on Paper

There are a number of applications out there that can help you prototype, but I prefer to go old-school with a pencil and paper. For presentational purposes you can transfer this exercise to PowerPoint or some other application for prototyping, but don't get bogged down and waste time doing so. Paper is highly portable, can be digitized (scan), requires no electricity or Internet connectivity, can easily be shared with others, and its use is a skill that is common between all stakeholders.

So with the index card exercise done, the next step in my process is to take the resulting information architecture and create a prototype. Doing so will help you better define the layout, visualize what the site will look like on a screen, visualize how pages interconnect, and give you plenty of room for trial and error. It also provides you with some additional and inexpensive opportunities for stakeholder input, and further reflection and brainstorming, before you begin coding.

TIP: As I prototype I've always got an eye on my bookmarked reference websites, and/or some of the inspirational sites listed below.

Here are some device mockup resources that will help you sketch:

- [Paper][]
- [Interface Sketch][]
- [Responsive Sketchsheets][]

Here's what my paper prototype process looks like:

![][Prototype]

The end result: a well-defined user interface layout for my entire application.

### Wireframing

**No More Exercises!** At this point it's time to start coding. From the exercises above you have absolutely everything you need to start coding with confidence that the site's information architecture and layout are pretty darn close to what you will ultimately develop.

It's the blueprint, and what you code moving forward will serve as your living wireframe. A living wireframe in that if clients/teammates/stakeholders need to review beyond the early exercises, you can send them to a live URL where they can click through to simulate the actual application (and view it on different devices). Any changes you make will be reflected immediately, which they'll love, and so will you because everything from this point and moving forward is just an iteration in the development process.

Because you laid out your applications [markup][], [styles][], and [mobile][] groundwork in chapters 1 through 3 -- and hopefully have deployed on Heroku or elsewhere -- what you wireframe here will be production ready, and in this section we will begin to transform our paper prototype into a working wireframe.

An assumption I will make here is that you already are a proficient front end coder, so going into how to go about writing basic markup from the prototypes we just developed is something I won't get into. After codifying my prototypes here is what I have:

!!! NEED IMAGE !!!

Pretty bare-bones, but that will soon change.

#### Content

A word on content. I have all of my content for the most part, but regarding the actual content for your project, if you have it great! If not, this article gives a nice overview of how content blocks can be used in situations where content is not known, perhaps a client has not yet delivered it:

- [Content, First?][Content First]

##### Lorem Ipsum

I for one don't mind using Lorem Ipsum as content placeholders. Here is a roundup of Rails Gems for it:

[The Ruby Toolbox][Toolbox 1]

There's a lot of Lorem Ipsum generator services out there, here are a few (some of them are kind of funny):

- [html-ipsum][]
- [lipsum][]
- [Fillerama][]
- [Samuel L. Ipsum][]
- [Hipster Ipsum][]
- [Gangsta Lorem Ipsum][]
- [Cupcake Ipsum][]
- [Bacon Ipsum][]

##### Image Placeholders

Image placeholders in different sizes and styles are also plentiful (the second link will give you a pretty compreshensive list to choose from):

- [The Ruby Toolbox][Toolbox 2]
- [List of Dummy Image Generators][Image Generators]
- [Functional Placeholder Images][Cambelt]
- [Holder.js][]

### Design

So we basically have a pretty blank wireframe. We need to add some spice to it through our design. Just by looking at your site your users should be able to understand what they're looking at, your design must help communicate your story. To illustrate how simple this can be take a look at this 2007 website concept:

- http://noonebelongsheremorethanyou.com/00025

It illustrates to me the simplicity of storytelling and engaging the user, and ultimately delivering a message to entice an action.

In the case of "View Thought" part of the story is: "We are a great website design, development and user experience shop...we pay special attention to what your users will see," so we better deliver some great design that will help tell the story! To communicate this story, on top of the content and layout we have just finished wireframing, we're going to have to use a combination of fonts, color, images, and anything else I can think of to help View Thought tell it's story in such a way that users just get it.

#### Look and Feel

The combination of fonts, color, images is a sites look and feel. What follows are some ideas and resources to help you create your site's look and feel:

- Use a framework. We listed several frameworks you can use in [Chapter 2][styles].

- Reverse engineer pieces of things you already like.

- Find a plug-in.

- Hire a designer. With your layout set via our wireframe work half of the designers work is done. Now he or she needs to pull it all together with a stellar look and feel. When hiring a designer, make sure you let them know that the layout you have in place is not set in stone. This way your designer can add their experience to the project. Here are some resources for finding designers:

  - XXX

- Get a freebie and port it over to your application.

  - [Premium Pixels][]

- Buy a template. Templates are significantly less expensive than hiring a designer. As a front end coder implementing them into your layout should be a breeze. Here are some template resources:

  - XXX

- Read a tutorial.

#### Inspiration

In addition to reviewing competitor sites or similar services to help generate ideas, the following sites may also inspire or provide you with best practices/design patterns:

1.  [Awwwards][]

    > Awwwards are the awards that recognize and promote the talent and effort of the best developers, designers and web agencies in the world.

2.  [Pattern Tap][]

    > ...It's a living classroom, where designers learn what is working well on the Web and why.

3.  [UI Patterns][]
    > User Interface Design patterns are recurring solutions that solve common design problems. Design patterns are standard reference points for the experienced user interface designer.

4.  [siteInspire][]

    > siteInspire is showcase and CSS gallery featuring the best web design today.

5.  [Codrops][]
    > Codrops is a web design and development blog that publishes articles and tutorials about the latest web trends, techniques and new possibilities.

    Here are a few Codrops examples:
    - [Stop, Look, Click: Attention-Grabbing Elements in Web Design][Codrops 1]
    - [Make a Statement with Type][Codrops 2]
    - [Creative Background Styles and Trends in Web Design][Codrops 3]
    - [Dashboard Design Elements for the Win][Codrops 4]

#### Mobile

Since for advocating a mobile first design paradigm, it would be wrong to not include some mobile inspiration:

[AppSites][]

> App Sites is a showcase of beautiful iPhone, iPad & Mac app websites.

[Mobile Patterns][]

#### Responsive Navigation

[Responsive Navigation Patterns][Responsive Navigation]
[Complex Navigation Patterns for Responsive Design][Complex Navigation]

### Feedback

One very important thing to practice when designing interfaces is do nothing in isolation, and consider everything you think as intuitive to be wrong! (until proven otherwise) Iterating is key. Get feedback from your end users and refine. If you can't get to them, then ask your neighbor, a friend, or try something like:

1.  [Concept Feedback][]

    > Get Website Feedback and Increase Conversion Rates
    > Expert analysis, detailed recommendations and solutions you can implement today.

2.  [IntuitHQ][]

    > Get useful, actionable results, improve usability in no time, and create a site your users will love.

3.  [Loop11][]

    > Loop11 is a remote usability testing tool that enables you to test the user-experience of any website and identify navigational and usability issues. Get the hard facts about your website quickly and cost effectively!

4.  [Silverback][]

    > Guerrilla usability testing software for designers and developers

5.  [UserTesting.com][]

    > Usability Testing Has Never Been Easier
    > The fastest, cheapest way to find out why users leave your website.

6.  Steve Krug wrote a second book on usability testing, and gives a basic demo of it on YouTube:
    - [Rocket Surgery Made Easy by Steve Krug: Usability Demo][Rocket Surgery]

### What We've Done

Just remember, less is more and KISS (Keep It Simple Stupid). Revise and release often.

[markup]:               https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md
[styles]:               https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[mobile]:               https://github.com/maxxiimo/the-front-end-manifesto/blob/master/mobile-foundation.md
[Jason Santa Maria]:    http://jasonsantamaria.com/
[Slicing and Dicing]:   https://github.com/maxxiimo/the-front-end-manifesto/blob/master/slicing-and-dicing-mockups.md
[Chapter 1 Quote]:      https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-markup.md#the-application-layout
[Premium Pixels]:       http://www.premiumpixels.com/
[Awwwards]:             http://www.awwwards.com/
[Pattern Tap]:          http://patterntap.com/
[UI Patterns]:          http://ui-patterns.com/
[siteInspire]:          http://siteinspire.com/showcase
[Codrops]:              http://tympanus.net/codrops/
[Codrops 1]:            http://tympanus.net/codrops/2012/09/28/stop-look-click-attention-grabbing-elements-in-web-design/
[Codrops 2]:            http://tympanus.net/codrops/2012/09/26/make-a-statement-with-type/
[Codrops 3]:            http://tympanus.net/codrops/2012/08/17/creative-background-styles-and-trends-in-web-design/
[Codrops 4]:            http://tympanus.net/codrops/2012/09/20/dashboard-design-elements-for-the-win/
[AppSites]:             http://appsites.com/
[Mobile Patterns]:      http://www.mobile-patterns.com/
[Complex Navigation]:   http://bradfrostweb.com/blog/web/complex-navigation-patterns-for-responsive-design/
[Responsive Navigation]: http://bradfrostweb.com/blog/web/responsive-nav-patterns/
[Content First]:        http://alwaystwisted.com/post.php?s=2012-10-13-content-first
[Toolbox 1]:            https://www.ruby-toolbox.com/search?utf8=%E2%9C%93&q=lorem+ipsum
[html-ipsum]]:          http://html-ipsum.com/
[lipsum]:               http://www.lipsum.com/
[Fillerama]:            http://chrisvalleskey.com/fillerama/
[Samuel L. Ipsum]:      http://slipsum.com/
[Hipster Ipsum]:        http://hipsteripsum.me/
[Gangsta Lorem Ipsum]:  http://lorizzle.nl/
[Cupcake Ipsum]:        http://cupcakeipsum.com/
[Bacon Ipsum]:          http://baconipsum.com/
[Toolbox 2]:            https://www.ruby-toolbox.com/search?utf8=%E2%9C%93&q=image+placeholders
[Image Generators]:     http://www.russellheimlich.com/blog/list-of-dummy-image-generators/
[Cambelt]:              http://cambelt.co/
[Holder.js]:            http://imsky.github.com/holder/
[Case Study]:           http://builtbyboon.com/blog/responsive-design-case-study
[Paper]:                http://generatedpaper.com/en/wireframing
[Interface Sketch]:     http://interfacesketch.tumblr.com/
[Responsive Sketchsheets]: http://zurb.com/playground/responsive-sketchsheets
[Don't Make Me Think]:  http://www.sensible.com/index.html
[Concept Feedback]:     http://www.conceptfeedback.com/
[IntuitHQ]:             http://www.intuitionhq.com/
[Loop11]:               http://www.loop11.com/
[Silverback]:           http://silverbackapp.com/
[UserTesting.com]:      http://www.usertesting.com/
[Rocket Surgery]:       http://www.youtube.com/watch?v=QckIzHC99Xc&feature=player_embedded

[Index Before]:         http://chrismaxwell.com/manifesto/index-cards/index-cards-before.jpg
[Index After]:          http://chrismaxwell.com/manifesto/index-cards/index-cards-after.jpg
[Index Mobile]:         http://chrismaxwell.com/manifesto/index-cards/index-cards-mobile.jpg
[Prototype]:            http://chrismaxwell.com/manifesto/paper/prototype.jpg
