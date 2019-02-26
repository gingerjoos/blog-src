How I recovered my Thunderbird mail from backup
###############################################
:date: 2010-02-02 17:04
:author: admin
:category: technology
:slug: how-i-recovered-my-thunderbird-mail-from-backup

So the best way to backup your mails from Thunderbird is to `copy your
complete profile
directory <http://www.mozilla.org/support/thunderbird/profile#backup>`__.
Follow these steps for `restoring your
mail <http://www.mozilla.org/support/thunderbird/profile#move>`__.

The fool that I am, instead of copying the full profile directory I
ended up backing up just the Mail subdirectory in the profile directory.
It took me a while to figure out how to restore the backup, so I thought
I would share it with you.

The first thing you do is install Thunderbird (if you haven't already).
Now Run( Windows : Start->Run or press Win key+r ; Mac/Linux - you're
smart enough to know :P ) this command "thunderbird.exe
-profilemanager". Create a dummy profile - just have some dummy email
address in there. Now exit Thunderbird.

Next step is to `find your newly created profile
directory <http://www.mozilla.org/support/thunderbird/profile#locate>`__.
Locate the Mail directory in there. Now you have to copy 2 files from
your backup - both have the same name. One has a .msf extension and the
other has no extension. I had created a separate thunderbird mail folder
with a filter and I needed to backup just that one alone. So I just
copied those 2 files (from the Inbox.sbd directory) and put them in the
Local Folders subdirectory in the Mail directory (which already had
empty files like Trash and Trash.msf).

The file without extension - this is the actual mail file. It's in the
`mbox <http://en.wikipedia.org/wiki/Mbox>`__ format. The other is an
index file.

**Acknowledgements :**

I posted a `question on Aardvark <http://vark.com/t/eee11d>`__ -
http://vark.com/t/eee11d. I got replies from Shel and Moez. I would like
to thank both of them for helping me out.
