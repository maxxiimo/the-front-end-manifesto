Information Architecting
------------------------

Now that we have reviewed the three pillars of foundation work: markup, styles, and mobile, it's time to delve into actually building your websites/application. The best place to start is with the splash page or application console: its navigation, content, layout, look and feel. Your homepage and/or application console is of critical importance to your project. Most of the time it is the first thing that a user will see, and how the end-user will understand your [whatever your building] and how they will [whatever they will do], and it sets the tone and unifying theme for every subsequent page or functionality.

The key to being successful in building your application splash page and/or console can be summed up in one word:

Storytelling.

Back in 2008 at "An Event Apart: Boston" I remember listening to [Jason Santa Maria][], then the Creative Director of Happy Cog Studios, give a presentation called "Good Design Ain't Easy." He described how stories were being told by design, with the designer in effect becoming the narrator. When I worked for Fidelity Investments as an  Information Architect, I remember another presenter that same year at the company auditorium sharing his thoughts on storytelling and its importance in design. Although I no longer remember his name, I do remember his talk thesis: people understand and remember stories.

These talks have stuck with me over the years, and have become the manner in which I view site design; as storytelling. What follows is an explanation of how to build a story for your website and translate that into code, and the sites look and feel (styles). As a front end developer, without getting super complex or requiring a gazillion dollars, there are three ways to go about this:

1. Start from scratch and architect and design everything yourself.
2. Work with a designer from the get-go and implement a design mockup into your foundation work.
1. Start from scratch and architect yourself, then get help from a designer on the look and feel.

In this chapter we're going to mostly focus on option 1 and 3. Hiring a designer from the get-go is not a bad idea since design and front end engineering are to complete different skill sets, but perhaps there isn't money in the budget to hire a designer, or this responsibility falls on your lap, or maybe you just want to do it yourself. Typically I have found that as a consultant, when I'm brought into a project design mockups have already been developed and it's now my job to implement them into the application. The next chapter, [Slicing and Dicing Mockups][Slicing and Dicing] will dive into the mechanics of doing exactly that.

### Blocks of Information

Before any design begins though, we need to architect the application. As I mentioned in chapter 1:

> As a front end person, sometimes called an Information Architect, when I think about layout I literally think about how a site is laid out on a screen. I don't think in terms of code, but more so in terms of organization of information and function for an end-user's consumption.

How does how does organizing information and function relate to storytelling?

A layout is really a mosaic of information that tells (conveys) something: a particular type of story. This information was grouped together based on some criteria, and then placed on a website "page" that ultimately gets viewed by an end-user. This information needed to be organized in some logical way to make absolute sense to the end-user, and probably designed to invite/entice/cause the end-user to take the next step or action, i.e. turn the page in the story.

### The Storyline

The unifying message behind this mosaic of information is the storyline. Before content can be discovered, grouped, and placed in a layout, the writer, in this case you, has to have the stories general theme in mind. For example, the storyline might be:

"I'm a great Web site for finding a job...a job that is perfect for you, you should join me, if you do you will have access to tons of perfect jobs and your life will change for the better forever!"

In this theme example – with my Information Architect (IA) hat on – I immediately see several major blocks of information:

1) What is the site in 10 words or less - possibly a summary box.
2) How do I join - a sign-up section.
3) An area that describes the benefits of the site - maybe user testimonials.
4) The obvious table stakes to this story, the side story:
   - A logo
   - Legalese (Copyright, ToS, Privacy)
   - Non-legal footer type info (Feedback, About, Contact, Site Map)

...and as the front end developer I'm already beginning to imagine how these blocks of information will be conveyed. 

This is exactly what you will need to do. Think of an overriding storyline, organize it into blocks of information, then begin to imagine how it will be conveyed.

### Gathering and Organizing Information

To help me along this process, one technique I like to use, whether I know exactly what I'm after or not, is to use index cards to visually create an inventory of possible information blocks:

**Step 1:** Write down in a word or two on an index card (or a bunch of tiny pieces of paper, a digital equivalent like PowerPoint, or even a single sheet of paper as a list of items) what the card represents: content, function, a navigational element, an image, video, whatever. Think of as many components to the page or application as you can – I prefer dealing with a single view at a time.

NOTE: Color coding is helpful.

**Step 2:** Lay the index cards on a table and begin organizing them into logical groupings like navigation. Not all cards need to be included.

It's best to do this exercise with others, most especially stakeholders in the project. This way you can brainstorm, bring in new ideas, and team members, clients, customers can provide input and begin to see progress.

Here's a practical example. I need a new website for my practice "ViewThought". My story theme goes something like this:

"We are a great website design, development and user experience shop. We have tons of experience, have worked with a bunch of different clients who are all happy with our work, and we really care about what we do. We specialize in Ruby on Rails, and we pay special attention to what your users will see. You should hire us! ...or give us a call and learn more."

I immediately can see a few index card entries in my storyline and write out everything I can think of, but I don't stop there. Beside your own genius, it's good practice to see what other people are doing, like the sites competitors or similar services or types of websites. I've bookmarked a bunch of sites to review. As I review them I add more index card entries. Here's what they look like laid out on a table:

***ADD PHOTO HERE***

I have XXX index cards laid out. After evaluating and reorganizing here is what I'm left with:

***ADD PHOTO HERE***

I started this section by saying "whether I know exactly what I'm after or not" because as a front-end coder it is so easy for me to just start coding and change things on the fly as I move along. In fact, I'd rather just do that. The manual process of labeling index cards and laying them out though forces me think outside of the box, and not work in isolation. There's just enough chance of a better outcome by doing the exercise that it's worth doing.

### Prototyping

As I define blocks of information, especially while laying the site out in index cards, I start to think about where information will be placed. I want to call attention to different parts of the story depending on its relevance and importance to the story.

Basically I think like a newspaper layout editor. I also "borrow from the best" to get ideas about my layout by seeing what’s out there on the Web through inspiration sites like the ones listed above. I highly recommend the book "[Don't Make Me Think][]" by Steve Krug. It’s a good read and everything he says is so darn obvious, and all there in one great reference.

I'm a strong proponent of prototyping on paper after you have gathered and organized your blocks of information. Doing so helps you visualize the layout and gives you some more opportunities for input, reflection and brainstorming before you begin coding, plus it is exactly how you will transfer your index card thinking to code. It your blueprint and where you will really think about how the page is going to visually look and function. Paper is also highly portable, requires no electricity, can easily be shared with others, and its use is a skill that is shared by all stakeholders. Here are some resources that will help you sketch:

[Paper][]
[Interface Sketch][]

Here's what my application looks like so far:

***ADD PHOTO HERE***

NOTE: There are a number of applications out there that can help in this process, but I prefer to go old-school with a pencil, eraser and [paper][]. For presentational purposes you can transfer this exercise to PowerPoint or some other application for prototyping, but don't get bogged down and waste time doing so. At this point start coding! Remember, you have laid out the groundwork in chapters 1 through 3 for your application and hopefully have deployed on Heroku. If clients need to review beyond these early exercises, there's nothing better than sending them to a URL with placeholders that they can click through to simulate the actual application.

Finally, when architecting remember that less is more and KISS (Keep It Simple Stupid).

### Look and Feel

Use a framework. We listed several frameworks you can use and [chapter 2][].

Reverse engineer pieces of things you already like.

Find a plug-in.

Hire a designer. With your layout set half of the designers work is done. Now he or she needs to pull it all together with a stellar look and feel. When hiring a designer, make sure you let them know that the layout you have in place is not set in stone. This way your designer can add their experience to the project. Here are some resources for finding designers:

- 

Get a freebie.

- [Premium Pixels][]

Buy a template. Templates are significantly less expensive than hiring a designer. As a front end coder implementing them into your layout should be a breeze. Here are some template resources:

- 

Read a tutorial.

#### Inspiration

In addition to reviewing competitor sites or similar services to help generate ideas, the following sites might also inspire or provide you with best practices/design patterns:

> Awwwards are the awards that recognize and promote the talent and effort of the best developers, designers and web agencies in the world.

\- [Awwwards][]

> ...It’s a living classroom, where designers learn what is working well on the Web and why.

\- [Pattern Tap][]

> User Interface Design patterns are recurring solutions that solve common design problems. Design patterns are standard reference points for the experienced user interface designer.

\- [UI Patterns][]

> siteInspire is showcase and CSS gallery featuring the best web design today.

\- [siteInspire][]

> Codrops is a web design and development blog that publishes articles and tutorials about the latest web trends, techniques and new possibilities.

Here are a few examples:

> Stop, Look, Click: Attention-Grabbing Elements in Web Design

\- [Codrops][Codrops 1]

> Make a Statement with Type

\- [Codrops][Codrops 2]

### Feedback

One very important thing to practice when designing interfaces is do nothing in isolation, and consider everything you think as intuitive to be wrong! (until proven otherwise) Iterating is key. Get feedback from your end users and refine. If you can't get to them, then ask your neighbor, a friend, or try something like:

> Get Website Feedback and Increase Conversion Rates
> Expert analysis, detailed recommendations and solutions you can implement today.

\- [Concept Feedback][]

> Get useful, actionable results, improve usability in no time, and
create a site your users will love.

\- [IntuitHQ][]

> Loop11 is a remote usability testing tool that enables you to test the user-experience of any website and identify navigational and usability issues. Get the hard facts about your website quickly and cost effectively!

\- [Loop11][]

>Guerrilla usability testing software for designers and developers

\- [Silverback][]

> Usability Testing Has Never Been Easier
> The fastest, cheapest way to find out why users leave your website

\- [UserTesting.com][]

Steve Krug your book on usability testing, and gives a basic demo of it on YouTube:

- [Rocket Surgery Made Easy by Steve Krug: Usability Demo][Rocket Surgery]

### What We've Done



[Jason Santa Maria]:    http://jasonsantamaria.com/
[Slicing and Dicing]:   https://github.com/maxxiimo/the-front-end-manifesto/blob/master/slicing-and-dicing-mockups.md
[chapter 2]:            https://github.com/maxxiimo/the-front-end-manifesto/blob/master/foundation-styles.md
[Premium Pixels]:       http://www.premiumpixels.com/
[Awwwards]:             http://www.awwwards.com/
[Pattern Tap]:          http://patterntap.com/
[UI Patterns]:          http://ui-patterns.com/
[siteInspire]:          http://siteinspire.com/showcase
[Codrops 1]:            http://tympanus.net/codrops/2012/09/28/stop-look-click-attention-grabbing-elements-in-web-design/
[Codrops 2]:            http://tympanus.net/codrops/2012/09/26/make-a-statement-with-type/
[Paper]:                http://generatedpaper.com/en/wireframing
[Interface Sketch]:     http://interfacesketch.tumblr.com/
[Don't Make Me Think]:  http://www.sensible.com/index.html
[Concept Feedback]:     http://www.conceptfeedback.com/
[IntuitHQ]:             http://www.intuitionhq.com/
[Loop11]:               http://www.loop11.com/
[Silverback]:           http://silverbackapp.com/
[UserTesting.com]:      http://www.usertesting.com/
[Rocket Surgery]:       http://www.youtube.com/watch?v=QckIzHC99Xc&feature=player_embedded
