Installing Jetty on CentOS
##########################
:date: 2012-08-29 16:06
:author: admin
:category: Linux
:tags: centos, jetty
:slug: installing-jetty-on-centos

**Step 1 : Enable the jpackage repo**
Download the `jpackage.repo <http://jpackage.org/jpackage50.repo>`__
file to your /etc/yum.repos.d/ directory.
 
 
`` # cd /etc/yum.repos.d/ # wget http://jpackage.org/jpackage50.repo``

| **Step 2 : Install the jetty package you want**

| `` # yum search jetty``

will show you a list of jetty packages you want to install. At the
time of writing you get 2 options - jetty 5 and jetty 6. We installed
jetty 6.

| `` # yum install jetty6``
