Information Architecting
------------------------

Now that we have reviewed the three pillars of foundation work: [markup][], [styles][], and [mobile][], it's time to delve into actually building a websites/application. The best place to start is with the splash page or application console: its navigation, content, interaction, layout, and look and feel. The homepage is of critical importance to your project. Most of the time it is the first thing a user will see, and how they will understand your [whatever your building] and how they will [whatever they will do]. It also sets the tone and unifying theme for every subsequent page or functionality.

The key to being successful in building your application splash page and/or console can be summed up in one word:

Storytelling

Back in 2008 at "An Event Apart: Boston" I listened to [Jason Santa Maria][], then the Creative Director of Happy Cog Studios, give a presentation called "Good Design Ain't Easy." He described how stories were being told by design, with the designer in effect becoming the narrator. Another presenter at Fidelity Investments that same year also talked about storytelling and its importance in design. Although I no longer remember his name, I do remember his talks thesis: people understand and remember stories.

These talks have stuck with me over the years, and have become the manner in which I view site design; as storytelling. What follows is an explanation of how to build a story for your website and translate that into code, and the sites look and feel (styles). As a front end developer, without getting super complex or requiring a gazillion dollars, there are three ways to go about this:

1. Start from scratch and architect and design everything yourself.
2. Work with a designer from the get-go and implement a design mockup into your foundation work.
1. Start from scratch and architect yourself, then get help from a designer on the look and feel.

In this chapter we're going to mostly focus on option 1 and 3. Hiring a designer from the get-go is not a bad idea - design and front end engineering are to complete different skill sets - but perhaps there isn't money in the budget to hire a designer, or this responsibility falls on your lap, or maybe you just want to do it yourself. Typically I have found that as a consultant, when I'm brought into a project design mockups have already been developed and it's now my job to implement them into the application. The next chapter, [Slicing and Dicing Mockups][Slicing and Dicing] will dive into the mechanics of doing exactly that.

### Blocks of Information

To build our stories the first thing we need to do is architect the application. As I mentioned in [chapter 1][markup]:

> As a front end person, sometimes called an Information Architect, when I think about layout I literally think about how a site is laid out on a screen. I don't think in terms of code, but more so in terms of organization of information and function for an end-user's consumption.

How does "organizing information and function" relate to storytelling?

A layout is really a mosaic of information that tells (conveys) something: a particular type of story. This information obviously was grouped together based on some criteria, and then placed on a website "page" that ultimately gets viewed by an end-user. It had to be organized in some logical way to make absolute sense to the end-user, and probably designed to invite/entice/cause the end-user to take the next step or action, i.e. turn the page in the story.

### The Storyline

The unifying message behind this mosaic of information is the storyline. Before content can be discovered, grouped, and placed in a layout, the writer, in this case you, has to have the stories general theme in mind. For example, the storyline might be:

> I'm a great Web site for finding a job...a job that is perfect for you, you should join me, if you do you will have access to tons of perfect jobs and your life will change for the better forever!

In this storyline example - with my Information Architect (IA) hat on - I immediately see several major blocks of information:

1.  What is the site in 10 words or less - possibly a summary box.
2.  How do I join - a sign-up section.
3.  An area that describes the benefits of the site - maybe user testimonials.
4.  The obvious table stakes to this story, the side story:
    - A logo
    - Legalese (Copyright, ToS, Privacy)
    - Non-legal footer type info (Feedback, About, Contact, Site Map)

...and as the front end developer I'm already beginning to imagine how these blocks of information will be conveyed and coded to fit into our foundation markup and/or used by our backend development team. This is exactly what you will need to do. Think of an overriding storyline, organize it into blocks of information, then begin to imagine how it will be conveyed and coded.

### Gathering and Organizing Information

There's more to gathering and organizing information than just creating a storyline. What follows are different techniques I use to gather all the blocks of information that will ultimately make up the users experience. I also highly recommend the book "[Don't Make Me Think][]" by Steve Krug. It’s a good read and everything he says is so darn obvious, and all there in one great reference.

#### Index Card Exercise

To help me along my process I use index cards to create a physical inventory of possible application components. It's best to do this exercise with others, especially stakeholders in the project. You can buy a pack of 200 index cards for under one dollar. Here are the steps I follow:

**Step 1:** Write down in a word or two on an index card - or a bunch of tiny pieces of paper, a digital equivalent like PowerPoint, or even a single sheet of paper (as a list of items) - what the card represents: content, function, a navigational element, an image, video, whatever.

Think of as many components to the page or application as you can - I prefer dealing with a single view at a time.

NOTE: Color coding is helpful.

**Step 2:** Lay out the index cards on a table and organize them into logical groups like navigation.

**Step 3:** Start eliminating all the cards you don't want to include.

Here's a practical example. I need a new website for my practice "ViewThought". My storyline goes something like this:

> We are a great website design, development and user experience shop. We have tons of experience, have worked with a bunch of different clients who are all happy with our work, and we really care about what we do. We specialize in Ruby on Rails, and we pay special attention to what your users will see. You should hire us! ...or give us a call and learn more.

I immediately can see a few index card entries in my storyline, and write out everything I can think of, but I don't stop there. Beside your own ideas, it's good to see what other people are doing, like the sites competitors or similar services or types of websites. I've bookmarked a bunch of sites to review, and as I review them I add more index card entries. For navigation I had a simple tally on the bottom of the cars to see how many of the sites I review use that particular navigation element. Here's what all my entries look like laid out on a table:

![][Index Before]

I have 200 index cards laid out and grouped as navigation, content, or footer information. As I review I begin to remove components I don't plan to use and I also start to think about where information will be placed. I want to call attention to different parts of the story depending on its relevance and importance to the story. These components I move higher up on the page. Basically I think like a newspaper layout editor.

After evaluating and reorganizing here is what I'm left with:

![][Index After]

Quite a bit less, and through the process I really have a great idea on what my site will look like and how I'm going to start coding, but I need to whittle it down even further since we're going to use the mobile first approach. We need to shed even more, and here's what I'm left with:

![][Index Mobile]

...And there you have it, the application in its absolute simplest form doing only the things that are most important to it. From here we can build up to the desktop. From here I will take this architecture and mockup the user interface on paper.

Check out how this design group uses index cards:

- [Responsive Design Case Study][Case Study]

In concluding this section on index carding, as a front end developer with years of practice, a huge part of me just wants to bypass this exercise and start coding (and change things on the fly as I move along). So why do I even bother? Experience has shown me that the manual process of labeling index cards and laying them out forces me to reflect and think outside of my coding box. It helps me discover new ideas, visualize and refine the information architecture, and to not work in isolation, i.e. include others in the process. I find that by doing the exercise there's just enough chance of a better outcome that it's worth trying.

#### Prototyping on Paper

Another exercise you can do - a great follow-up to index carding - is prototype on paper. Doing so will help you determine the layout and visualize what the site will look like on a screen, and how pages interconnect. It also gives you some more opportunities for stakeholder input, and further reflection and brainstorming before you begin coding. Your paper prototype can serve as your coding blueprint.

Here are some resources that will help you sketch:

- [Paper][]
- [Interface Sketch][]
- [Responsive Sketchsheets][]

Also, check out some of the inspirational sites below. Here's what my application looks like on paper:

![][Prototype]

There are a number of applications out there that can help you prototype, but I prefer to go old-school with a pencil and [paper][]. For presentational purposes you can transfer this exercise to PowerPoint or some other application for prototyping, but don't get bogged down and waste time doing so.

Paper is highly portable, can be digitized (scan), requires no electricity or Internet connectivity, can easily be shared with others, and its use is a skill that is common between all stakeholders.

#### Wireframing

No More Exercises! At this point start coding. What you code moving forward will serve as your living wireframe. Remember, you have laid out the groundwork in chapters 1 through 3 for your application and hopefully have deployed on Heroku. If clients need to review beyond these early exercises, there's nothing better than sending them to a URL with content placeholders that they can click through to simulate the actual application.

### Placeholders

Regarding the actual type for your project, if you have it great! If not this article gives a nice overview of how content blocks can be used in situations where type is not known, perhaps a client has not yet delivered it:

- [Content, First?][Content First]

I for one don't mind using Lorem Ipsum.

#### Lorem Ipsum

Here are some great resources for it:

- [][]
- [][]
- [][]
- [][]

#### Image Placeholders

- [][]
- [][]
- [][]
- [][]

### Design

Back in 2008 Jason Santa Maria emphasized in his presentation that design must communicate your story, and that just by looking at your site your users should be able to understand what they're looking at. I mean you don't need a user manual to use Amazon.com do you? (Not including Kindle!) For your application to communicate your story, on top of the content and layout we have begun wireframing, we're going to have to use a combination of fonts, color, images, and anything else we can think of to tell your sites story in such a way that the user just gets it.

To illustrate how simple this can be take a look at this 2007 website concept:

- http://noonebelongsheremorethanyou.com/00025

It illustrates to me the simplicity of storytelling and engaging the user, and ultimately delivering a message to entice an action.

#### Look and Feel

So up until now regarding design I'm writing more conceptually, but as front-end developers we tend to want to just start coding. So let's look at the quickest way to accomplish this and at the same time create a sites look and feel:

- Use a framework. We listed several frameworks you can use in [Chapter 2][styles].

- Reverse engineer pieces of things you already like.

- Find a plug-in.

- Hire a designer. With your layout set half of the designers work is done. Now he or she needs to pull it all together with a stellar look and feel. When hiring a designer, make sure you let them know that the layout you have in place is not set in stone. This way your designer can add their experience to the project. Here are some resources for finding designers:

  - XXX

- Get a freebie.

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
[Prototype 1]:          http://chrismaxwell.com/manifesto/paper/prototype.jpg
