SQLyog on Linux
###############
:date: 2011-01-16 08:40
:author: admin
:category: code
:tags: Linux, mysql, mysqlyog, sqlyog, wine
:slug: sqlyog-on-linux

Run `SQLyog <http://webyog.com/en/>`__ on Linux with
`WINE <http://en.wikipedia.org/wiki/Wine_(software)>`__. You can
`download the sqlyog windows
installer <http://code.google.com/p/sqlyog/downloads/list>`__ and just
run it with WINE. SQLyog is my favourite GUI client. It is lightweight
and powerful. I use the community edition which comes free. The paid
versions of the app are awesome. I particularly miss the autocomplete
feature. This feature autocompletes table names, field names, query
commands etc. on tab press. I have used the MySQL query browser, but
there's no comparison.

The problem with SQLyog being that it runs only on windows :( . I tried
alternatives - phpmyadmin, MySQL query browser - but none of them quite
measured up against SQLyog. So I decided to try and get it working on my
linux box ( Ubuntu Maverick - 10.10 ). I use Wine version wine-1.3.11 .
Downloaded the latest installer from the community edition project page.
Ran the installer with Wine and voila! That was it :)

|sqlyog running on wine in Ubuntu|

.. |sqlyog running on wine in Ubuntu| image:: http://gingerjoos.com/blog/wp-content/uploads/2011/01/ubuntu-sqlyog-wine-300x168.png
   :target: http://gingerjoos.com/blog/wp-content/uploads/2011/01/ubuntu-sqlyog-wine.png
