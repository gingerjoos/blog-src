Pirate tweet
############
:date: 2009-09-28 12:41
:author: admin
:category: code
:tags: International Talk Like a Pirate Day, libcurl, php, pirate tweet, piratespeak, simplexml, twitter, yahoo, yql
:slug: pirate-tweet

September 19 is `International Talk Like a Pirate
Day <http://en.wikipedia.org/wiki/International_Talk_Like_a_Pirate_Day>`__.For
this day, the `Yahoo! Query
Language <http://developer.yahoo.com/yql/>`__ (YQL) team `announced on
the YDN blog that they were bringing out a "pirate
table" <http://developer.yahoo.net/blog/archives/2009/09/ahoy_mates_conv.html>`__.
This table would allow us to translate plain English to piratespeak
using YQL. I had been meaning to play around with YQL a bit and took
this opportunity to dive in. I couldn't complete it in time for
September 19 because of work, but managed to finally get it in some
shape today. What I made is something I call "Pirate Tweet".

`Pirate tweet <http://labs.gingerjoos.com/piratetweet/>`__ allows you to
`read your most recent tweets in
piratespeak <http://labs.gingerjoos.com/piratetweet/>`__. Just enter a
twitter username and you get the tweets in piratespeak. You can get the
source at http://labs.gingerjoos.com/piratetweet/piratetweet.tar.gz .
Please do link back to this post if you do use it. It is written in PHP
and uses PHP's builtin SimpleXML as well as libcurl. What is in there is
just a rough basic barebones quick-and-dirty stuff. It includes an
index.php file which takes care of spitting out the actual html. The
common.php file does the actual processing. pirate-tweet.css file is
some very basic css.

| The twitter RSS feed for a user is something like http://twitter.com/statuses/user\_timeline/USERNAME.rss . This is fed into the YQL query which does the translation, like this
|  SELECT \* FROM piratespeak.translate
|  WHERE html IN
|  (SELECT description FROM rss
|  WHERE url = "http://twitter.com/statuses/user\_timeline/USERNAME.rss")
|  So you send this query to http://query.yahooapis.com/v1/public/yql with the params
| 
| $params = array ( 'q'      => $query, 'format' => 'xml', 'env'    => 'store://kid666.com/piratespeak', );

So that's basically what it does. Hope someone finds this useful :)

I must say that YQL seems like a very interesting tool. Hopefully the MS
- Yahoo! deal will have no negative impact on it. Without doubt, YQL is
the star in Yahoo!'s products for developers. The ability to express
data as queries is mind - blowing. Looking forward to doing more stuff
with YQL.

Known issues :

Even links are passed as is to the YQL query. This results in, for
example, http://is.gd/3oBWf to become http://be.gd/3oBWf .

| Acknowledgment :
|  Much thanks to the `YQL <http://developer.yahoo.com/yql/>`__ guys at Yahoo! and their `wonderful documentation <http://developer.yahoo.com/yql/guide/>`__.

Also see :

`Previously mentioned blog
post <http://developer.yahoo.net/blog/archives/2009/09/ahoy_mates_conv.html>`__
has some more stuff using the same table.

`Chris
Heilmann <http://www.wait-till-i.com/2009/09/17/tools-for-talk-like-a-pirate-day/>`__
made some stuff with the table as well. Do check it out.
