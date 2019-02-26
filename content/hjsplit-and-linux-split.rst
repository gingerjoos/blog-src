hjsplit and linux split
#######################
:date: 2009-06-23 00:58
:author: admin
:category: Linux
:slug: hjsplit-and-linux-split

The other day I had to fit in a 4.4 GB file (A Debian testing dvd iso
image, if you want to know) on a 4 GB thumb drive. This, of course, is
not possible. So I had to split the file into chunks, transfer them
twice, take them to my friend's windows machine and use hjsplit to join
the files. How did I split the file so hjsplit could read it, when I
didn't use the linux version of hjsplit?

It looks like hjsplit splits its files by just cutting them into pieces.
This is exactly what is done by the split command. Which is probably why
I could use the linux split to split the file into a format hjsplit
could join.

You could use a command similar to this one if you want to try it out :

$ split -b900M -d
/home/anirudh/downloads/debian/debian-testing-i386-DVD-1.iso
debian-testing-i386-DVD-1.iso.

the '-b' option is used to specify the size of each chunk - 900 MB in
this case. '-d' means the output should be numeric (000,001,002...). Now
we specify the large file and a prefix to attach to the generated
filenames (note the dot at the end). This command will generate files :

debian-testing-i386-DVD-1.iso.000

debian-testing-i386-DVD-1.iso.001

debian-testing-i386-DVD-1.iso.002

debian-testing-i386-DVD-1.iso.003

debian-testing-i386-DVD-1.iso.004

Now this should be relatively easy to join with hjsplit. Do some
renaming if required.

 

Edit :

meaculpa has noted that split starts renaming its files with 000 and not
001 as required by hjsplit. Please check `his comment
below <#comment-51>`__ for the solution.

As a follow up to this post, I had written another on `how to join the
split files in
linux <http://gingerjoos.com/blog/linux/how-to-join-split-files>`__. You
can `check it out as
well <http://gingerjoos.com/blog/linux/how-to-join-split-files>`__.
