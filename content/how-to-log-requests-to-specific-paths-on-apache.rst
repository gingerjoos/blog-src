How to log requests to specific paths on Apache
###############################################
:date: 2011-06-23 16:55
:author: admin
:category: technology
:tags: apache
:slug: how-to-log-requests-to-specific-paths-on-apache

It is possible to log requests to specific paths of your website in your
Apache log. Imagine you need to log all access requests to
www.example.com/widgets/ path and whatever is under it in a separate
file. You can use a combination of the
`CustomLog <http://httpd.apache.org/docs/current/mod/mod_log_config.html#customlog>`__
directive and
`SetEnvIf <http://httpd.apache.org/docs/2.2/mod/mod_setenvif.html#setenvif>`__
directive to achieve this. The SetEnvIf directive needs the
mod\_setenvif module enabled.

On a Linux machine you can do this by using the a2enmod command. On my
Ubuntu I ran

``$sudo a2enmod setenvif``

On a Windows machine you probably need to edit the httpd.conf file in
the conf directory of your Apache installation directory.

Once this module is enabled you can issue such directives from your
VirtualHost configuration.

The CustomLog directive allows you to specify how and where logging
should be done. The last parameter that this directive takes is an
environment variable. This environment variable can be set the with
SetEnvIf directive conditionally. What you would do inside the
VirtualHost definition of the domain is something like this

`` SetEnvIf Request_URI '^/widgets/' widget_page=yes``

`` ``

``CustomLog ${APACHE_LOG_DIR}/widgets.example.log combined env=widget_page``

The SetEnvIf module above sets the widget\_page variable as yes if the
Request URI matches the regular expression '^/widgets/'. The CustomLog
directive below it directs Apache to log a request in the combined
format if the widget\_page variable is set.
