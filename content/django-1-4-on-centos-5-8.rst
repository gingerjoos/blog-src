Django 1.4 on CentOS 5.8
########################
:date: 2012-08-24 18:25
:author: admin
:category: technology
:tags: centos, django, Linux
:slug: django-1-4-on-centos-5-8

The default python version (2.4.3) on Centos 5.8 is `not supported for
Django
1.4 <https://docs.djangoproject.com/en/dev/faq/install/#what-python-version-can-i-use-with-django>`__
. Here's how to get Django 1.4 running on Centos 5.8 . Steps here are
probably useful for future/different versions.

**Step 1 : Enable EPEL**

`EPEL <http://fedoraproject.org/wiki/EPEL/FAQ#What_is_EPEL.3F>`__ has
newer version of Python available in it's repo. The first step is to
enable it. The command you need to `enable the EPEL
repo <http://blueapples.livejournal.com/217776.html>`__ is :

`` # rpm -ivh http://mirror.chpc.utah.edu/pub/epel/5/x86_64/epel-release-5-4.noarch.rpm``

 Once you install the package you've enabled EPEL.

**Step 2 : Install Python 2.6 and easy\_install**

`` #yum install python26-distribute``

 This will install python 2.6 and easy\_install

**Step 3 : Install pip**

`` #easy_install-2.6 pip``

Now that you've pip installed, we can get started on install
virtualenv and virtualenvwrapper.

**Step 4 : virtualenv and virtualenvwrapper**

`` #pip install virtualenvwrapper``
will install virtualenvwrapper and virtualenv. Now you need to add
some lines to your .bashrc


`` export WORKON_HOME=~/.virtualenvs  export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python26  source /usr/bin/virtualenvwrapper.sh ``

(Make sure to create the ~/.virtualenvs directory if it isn't already
created.)

 Now activate the changes to your bashrc by doing

 `` #source ~/.bashrc``

**Step 5 : Create a virtual environment for your Django project**

You can do this by running

 `` # mkvirtualenv my-env``

Once you run this you will automatically switch to the new
virtualenv. Your shell prompt will be prefixed with (my-venv)

**Step 6 : Install Django**

Change to the directory you want to install Django in. Then run :
 ``  (my-venv)#pip install Django``

Bonus!
~~~~~~

1. \ **Installing MySQL-python** :

First install

 `` #yum install mysql-devel``

 and then install MySQL-python
 `` (my-venv)#pip install MySQL-python``

2. **Installing Gunicorn**

`` (my-venv)#pip install gunicorn``


3. **requirements.txt**

It's often easier to just have a list of pip packages to install for a
particular project in a file. Conventionally, it's named
requirements.txt

 `` (my-venv)#pip install -r requirements.txt``

 will install all the packages given in the requirements.txt

 `` (my-venv)#pip freeze``

Will show you a list of packages installed by pip currently.
Something like this :

 `` Django==1.4  MySQL-python==1.2.3  wsgiref==0.1.2 ``

 You can take this list directly and put it into the requirements.txt

 `` (my-env)# pip freeze > requirements.txt``
