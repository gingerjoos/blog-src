How to join split files
#######################
:date: 2009-06-24 13:46
:author: admin
:category: Linux
:tags: Linux
:slug: how-to-join-split-files

This is sort of a follow-up to my previous post which talked about `how
you can use the split command in Linux to create split files which can
be joined with hjsplit on
Windows <http://gingerjoos.com/blog/linux/hjsplit-and-linux-split>`__.
My theory is that hjsplit does the same thing split does - which is just
take the file and split it into the required number of pieces. No
special headers or padding or compression or stuff. If that's true, it
should be easy as a pie to join the files split with hjsplit

To join files split with split, what I would do is use cat. Like this
:
|  $cat xaa xab xac xad xae > debian-testing-i386-DVD-1.iso

Here xaa, xab, xac, xad and xae are the split files and
debian-testing-i386-DVD-1.iso is the file after the join. I believe this
should work fine for split files got from hjsplit too. Since I'm too
lazy to go try it out in my friend's Windows machine, I'll leave it here
at that. Do let me know if anyone's tried it :)
