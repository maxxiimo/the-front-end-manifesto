Style Guides
------------

SUGGESTIONS

-------------------------------
Consistent use of preprocessor:
-------------------------------

It would be better to pick a format such as .sass and .scss, and stick with it sitewide. Syntax varies slightly between the two, which could be an issue for some developers new to preprocessors.


------------------------------
Consistent use of indentation:
------------------------------

In some cases – for example forms.scss – both spaces and tabs are used for indentation.


------------------------------
Hierarchical style formatting:
------------------------------

There is no set standard to the order/listing of styles, but adopting something makes it easier to find things.

For example:

display: block
position: absolute
top: 10px
-------------
width: 100px
height: 100px
margin: 10px
padding: 10px
-------------
font-family: Ariel
font-size: 90%
color: #fff
-------------
border: 1px solid #000
background: url(/images/.png) 0 0 no-repeat
-------------

vendor prefixes


Hierarchy Explanation:

The 1st group deals with type definition and positioning of elements.

The 2nd group deals with element size and spacing.

The 3rd and 4th group deal more with look and feel.

The last group deals with vendor prefixes and is preceded with a line space.


----------------
Use of labeling:
----------------

Within individual stylesheets, it would be helpful to use a system of labeling in order to modularize and better organize/manage related styles.

/* Major Section
  ============================================================================

/*  Heading
  -----------------------

/* subdivision


Removal of legacy code:

Old code tends to clutter stylesheets. Rather than delete obsolete/legacy styles, or leave them within working stylesheets, it might be useful to create a graveyard stylesheet; graveyard.sass, where such styles are accessible (just in case) until ultimately disposed of.

For example, advisor/invitations.sass, beginning on line 164 to line 354 are no longer used, and this appears not to be the case: //  old invitations stuff


-------------
Group styles:
-------------

Invitations could be grouped in one stylesheet rather than multiple invitation stylesheets, then subdivided appropriately in one stylesheet.

Doing so will reduce duplication, for example:

advisor/client/invitations.sass

    textarea
      width: 565px
      padding: 10px 15px 10px 15px
      margin-top: 7px
      font-family: Georgia, 'Times New Roman', serif
      font-size: 15px
      height: 150px
      color: #BBB
      &:focus
        color: #222

advisor/invitations.sass

    textarea
      width: 565px
      padding: 10px 15px 10px 15px
      margin-top: 7px
      font-family: Georgia, 'Times New Roman', serif
      font-size: 15px
      height: 150px
      color: #BBB
      &:focus
        color: #222


---------------------
Optimize specificity:
---------------------

This might be considered too much:

stylesheets/advisor/client/invitations.sass

    #advisor_clients_invitations section#invite_clients form li#invitation_email_input input[type="text"]

    #advisor_clients_invitations section#invite_clients form li#invitation_email_input input[type="text"], #advisor_clients_invitations section#invite_clients form li#invitation_first_name_input input[type="text"], #advisor_clients_invitations section#invite_clients form li#invitation_last_name_input input[type="text"]


-----------------------------------------------
Define in-house styles over third-party styles:
-----------------------------------------------

Personally I would never use Formtastic, too rigid, but since it is popular I recommend not using its styles. You end up having to override quite a bit.


-------------------
Standardize styles:
-------------------

For example, all forms should use the same label color, size, and placement. Within invitations alone there are several different styles even within the same form.


--------------
Use variables:
--------------

For example, label colors could be specified in a variable called "$label_color". Changes then become global, and label colors become consistent, rather than isolated, difficult to find, and inconsistent.


----------------------
Consistency pet peeve:
----------------------

This is more of a pet peeve than anything, but when using Photoshop's color palette to discern or copy colors specified in a Photoshop mockup, the hex values are always in lowercase, so as a standard, and to be consistent, when defining colors in a application use lowercase:

color: #bbb and not color: #BBB

While on the subject, Photoshop also uses hyphens when saving images for the Web:

image-name.gif

... so when adding images to the assets directory try to use that convention since the vast majority of images will probably be produced by Photoshop and will have that convention.





[Front-end Style Guides][Style Guides]





[Style Guides]:         http://24ways.org/2011/front-end-style-guides
