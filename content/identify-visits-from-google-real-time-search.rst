Identify visits from Google Real time search
############################################
:date: 2010-05-06 18:29
:author: admin
:category: from the web
:tags: apache, google real time search
:slug: identify-visits-from-google-real-time-search

Recently Google released its `real time
search <http://googleblog.blogspot.com/2009/12/relevance-meets-real-time-web.html>`__
feature. If you want to figure out from your Apache access logs which
results are coming from the Google real time search, then you have to
look at the referrer field. The Google search referrer url will have a
param tbs=rltm in it. rltm stands for real time.
