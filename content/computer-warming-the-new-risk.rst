Computer Warming - the new risk?!
#################################
:date: 2006-12-30 13:02
:author: admin
:category: technology
:tags: computer security, technology
:slug: computer-warming-the-new-risk

Happened to come across `a pointer in
Slashdot <http://yro.slashdot.org/article.pl?sid=06/12/30/0645249&from=rss>`__
to a `Wired
article <http://www.wired.com/news/technology/0,72375-0.html?tw=rss.technology>`__. 
From the article -

    BERLIN -- A security researcher has a devised a novel attack on
    online anonymity systems in which he literally takes a computer's
    temperature over the Internet.

    The attack uses a phenomenon called "clock skew" -- the tendency for
    the precise clocks in modern computers to drift off of the correct
    time at slightly different rates, which can be affected by heat.

As I understand it, the basic premise goes like this. It seems possible
to identify a computer based on `clock
skew <http://en.wikipedia.org/wiki/Clock_skew>`__. Clock skew is
unavoidable although most digital systems try their best to reduce it.
You change the temperature, you change the clock skew. So overload a
particular server suddenly and there is a change in its clock. This
means the time stored on that server also changes. Now use timestamps to
find the server which has drifted off. This is not the entire story,
read more at
`Wired <http://www.wired.com/news/technology/0,72375-0.html?tw=rss.technology>`__.

This is a rather roundabout way of doing things. Not really the best way
to do it, but what it does show is that such things are possible.
Perhaps this concept might be useful in some other context. Personally,
I don't expect such attacks to come in anytime in the future. There are
far simpler and effective ways and it doesn't make sense to use such a
complicated method.
