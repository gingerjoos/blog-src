IRCTC disabled right click
##########################
:date: 2010-06-09 08:02
:author: admin
:category: code, misc
:tags: irctc, javascript
:slug: irctc-disabled-right-click

Many readers of my post on `booking tatkal tickets with Firefox's
autofill forms
extension <http://gingerjoos.com/blog/misc/booking-tatkal-tickets-on-irctc-the-supercool-way>`__
have reported that IRCTC has now disabled right clicks. Not only does
this hamper saving the form, it is also very annoying. I've found a
workaround for this. After you fill in the form do not directly go and
right click to save the form as a profile. Instead paste this code into
the Firefox address bar -

``javascript:void(document.oncontextmenu=null)`` .

This will re-enable the disabled right click. Now proceed as before.

This code can be used on any site that disables right click

Hat tip to this post on "`Re-Enable Right-Click When Web Pages Turn It
Off <http://www.tech-recipes.com/rx/501/re-enable-right-click-when-web-pages-turn-it-off/>`__\ "
