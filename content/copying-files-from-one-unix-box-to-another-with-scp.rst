Copying files from one unix box to another with scp
###################################################
:date: 2009-07-31 11:23
:author: admin
:category: technology
:tags: Linux, rcp, scp, ssh, unix, Linux, technology
:slug: copying-files-from-one-unix-box-to-another-with-scp

ssh is a very powerful and widely used protocol in all the Unices. If
you've used the ssh client in your Unix/Linux box, you must have
realised how indispensable it is. There is another indispensable tool
that uses the ssh protocol - scp (secure copy). scp was meant to be an
alternative to unsecure tools like rcp. It has since replaced most such
programs. Since scp uses the ssh protocol, the encryption it uses
ensures security of your data.

| Using scp is simple. It works almost like the regular cp command. The
  basic syntax is
|  ``scp SOURCE DESTINATION``
|  In order to specify the SOURCE or DESTINATION we have a special
   syntax.
|  ``USERNAME@HOST:PATH``

| Let me give you an example :
  ``$scp anirudh@box:/var/www/html/test.html gingerjoos@linux:~/test_dir/``
| Copy /var/www/html/test.html in the machine called "box" as user
  "anirudh" to the box called "linux" as user "gingerjoos" to the path
  HOMEDIR/test\_dir/

That's it :) Simple, right?

| To copy the file to our localmachine, we could do this
| ``$scp anirudh@box:/var/www/html/test.html ~/workarea/``

This would copy the file test.html in the machine called "box" (as user
anirudh) to the localmachine at path HOMEDIR/work\_area/

Interchange the source-destination to copy file in your localmachine to
the remote machine.

| If you want to copy whole directories, use the '-r' flag(recursive
  copy)
|  ``$scp -r ~/workarea/ anirudh@box:~/workdir/``

Since scp is tied to the ssh program, the keys you use to set up
passwordless login with ssh works for scp as well.

Got questions? Got something to add to this? Post your comments below :)
