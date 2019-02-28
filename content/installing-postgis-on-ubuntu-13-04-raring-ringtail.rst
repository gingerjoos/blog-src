Installing PostGIS on Ubuntu 13.04 Raring Ringtail
##################################################
:date: 2013-08-02 18:49
:author: admin
:category: technology
:tags: postgis, postgres, raring, ubuntu, code
:slug: installing-postgis-on-ubuntu-13-04-raring-ringtail

It's as simple as


::

    sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
    sudo apt-get install postgresql-9.1-postgis-2.0-scripts

You might see alternate instructions asking you to install `Sharpie's
PPA <https://launchpad.net/~sharpie/+archive/postgis-stable>`__, but it
works only for Ubuntu Precise. The instructions in the `PostGIS trac
wiki <http://trac.osgeo.org/postgis/wiki/UsersWikiPostGIS20Ubuntu1304>`__
is also broken ‐ you will get an error like so :

::

    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:

    The following packages have unmet dependencies:
     postgis : Depends: libgdal1h (>= 1.9.0) but it is not going to be installed
    E: Unable to correct problems, you have held broken packages.

This problem has been raised and a `solution found in the PostGIS Trac
Issue tracker <http://trac.osgeo.org/osgeo/ticket/1154#comment:12>`__.
The first two lines are what needs to be done.
