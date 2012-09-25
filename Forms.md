Forms
-----

People tend to have a hard time with forms pretty much across the board, i.e. front-end and backend developers alike. As a front end developer what you will find the greatest difficulty with is styling your forms consistently across browsers and devices. When creating a form, and you have the added benefit of providing your backend developers with the semantic markup for the form I recommend using the following basic structure:

    %form
      %fieldset
        %legend
          %span
        %ol
          %li
            %label
            %input
          %li
            %label
            %input
        

Couple things to note, I use an ordered list rather than an unordered list or paragraphs to keep our inline label and input elements from bunching up on one line. Ordered over unordered because in many cases there is a sequence one follows in filling out a form. Semantically it makes sense, and if styles were for any reason turned off, you would default to a numbered list (as many forms are in the paper world) rather than a bulleted list.

About paragraphs, today you still find front-end developers using paragraphs for their forms. I used them back in the day, in fact this was pretty common 10 years ago, but I think most people have moved to lists. For me a form really is not a bunch of paragraphs with inputs, but rather it's a list of input fields, so why fight it? You can use a paragraph within a list item if it is truly a paragraph. People do that all the time as well, for example:

    %ol
      %li
        %label Something*
        %input
        %p * Explaining something.

Notice also that I use %fieldset and %legend. %fieldset groups related inputs, and %legend will place text on it and is optional. A good example of its use is in a credit card form:

!!! NEED AN IMAGE !!!

I always use %fieldset to group fields even if there is only one group, and I rarely use %legend.

Something you do not see in the minimalist form above is a tabbing order or a relationship between labels and fields. You don't have to add this, but I think it's a good practice to do so. Why leave a user's tabbing experience to chance? Simply add 



= form_for @<name> do |f|

= form_tag

= form_for @<name>, html: {multipart: true} do |f|

= f.label :<name>
= f.text_field :<name>
= f.text_area :<name>, cols: <number>, rows: <number>
= f.file_field :<name>
= f.password_field :<name>
= f.select :<name>, %(<items>)
= f.submit "<text>"