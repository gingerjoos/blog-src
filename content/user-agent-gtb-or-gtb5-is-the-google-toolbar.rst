User agent GTB or GTB5 is the Google Toolbar
############################################
:date: 2009-10-05 23:02
:author: admin
:category: technology
:tags: google, user agent
:slug: user-agent-gtb-or-gtb5-is-the-google-toolbar

Was checking out this blog's visitor stats recently when I came across
this User Agent
``"Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2 GTB5"``. 
I was wondering what GTB5 was. Some googling and testing later I found
out that GTB is in fact the Google Toolbar. To compare, here's the UA of
a Firefox browser with Google Toolbar installed :

``"Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2 GTB5"``

And here's another Firefox without it :

``"Mozilla/5.0 (Windows; U; Windows NT 6.0; en-GB; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)"``

Also, if you plan to capture the UA string in the Apache logs, make sure
that feature is turned on. Your `LogFormat
directive <http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#logformat>`__
must have something like ``\"%{User-Agent}i\"`` in it. For eg,

``LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined``

You can check the `Apache documentation on custom log
formats <http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#formats>`__
for more info. If you're using XAMPP/LAMPP, you might want to comment
out

``CustomLog logs/access_log common``

line in your httpd.conf and uncomment

``CustomLog logs/access_log combined``

line.
