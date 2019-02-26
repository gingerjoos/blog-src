ForeignKey to custom user model in Django
#########################################
:date: 2013-07-16 14:30
:author: admin
:category: django
:slug: foreignkey-to-custom-user-model-in-django

Came across this problem when running a syncdb in Django (>=1.5) :
| `` CommandError: One or more models did not validate: APP.ModelName: 'user' defines a relation with the model 'auth.User', which has been swapped out. Update the relation to point at settings.AUTH_USER_MODEL.``

So you define a custom user model and add the appropriate line to the
settings.py file. Then you add a ForeignKey from a model in your app the
way the `Django
doc <https://docs.djangoproject.com/en/1.5/topics/auth/customizing/#django.contrib.auth.get_user_model>`__
tells you to. And then you see this (the one above) error when you run a
syncdb.

We hit upon this problem. The reason this happened was that the
AUTH\_USER\_MODEL setting was below the INSTALLED\_APPS in the
settings.py file. Django will not handle forward referencing in this
case. The solution is to simply move the AUTH\_USER\_MODEL setting above
the INSTALLED\_APPS settting.
