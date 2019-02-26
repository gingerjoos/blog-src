vimdiff - the cool way to diff for vim users
############################################
:date: 2009-10-20 21:30
:author: admin
:category: Linux
:tags: diff, Linux, unix, vim, vimdiff
:slug: vimdiff-the-cool-way-to-diff-for-vim-users

Some of you using the vim editor may not know about a tool that comes
with vim called vimdiff. Vimdiff is an awesome way to diff files if you
are a vim nut. It gives you the power of vim + the power of diff.

How's this different from opening 2 files in vim (with -O option) you
ask ? The difference is that vim will highlight the diff for you.

Fire it up by giving the 2 filenames, say

``$vimdiff old new``

This will bring up a screen like this -

[caption id="" align="aligncenter" width="512"
caption="vimdiff"]\ |vimdiff|\ [/caption]

Now you can move around the 2 parts of the screen with your regular vim
commands. For eg. use (Ctrl+w) + right arrow to move to the right half
of the screen.

[caption id="" align="aligncenter" width="512" caption="vimdiff with
cursor on right half of screen"]\ |vimdiff with cursor on right half of
screen|\ [/caption]

You can copy paste as well. Go to the 2nd line in the left half and
press the y key twice to copy that line. Use (cntrl + w) + right arrow
to move cursor to the 1st line in the right half of the screen. Press p
to paste the copied line below the 1st line.

[caption id="" align="aligncenter" width="512" caption="vimdiff with
copy paste"]\ |vimdiff with copy paste|\ [/caption]

You can go to the first line and delete the two words "a new" by moving
the cursor to "a" and hitting d2w key combo.

[caption id="" align="aligncenter" width="512" caption="vimdiff deletes
words"]\ |vimdiff deletes words|\ [/caption]

Insert "an old" there by going to insert mode(press i key) and then
typing the two words. You'll see that vimdiff does not highlight
anything. This means that there is no difference between the two files.

[caption id="" align="aligncenter" width="512" caption="two files with
no difference in vimdiff"]\ |two files with no difference in
vimdiff|\ [/caption]

Vimdiff is the same as bringing up vim with the -d option. You could do
the same things you did above by using

``$vim -d old new``

|  Bonus :
|  You can also diff 2 URLs directly with vimdiff
|  Try
| 
|  ``$vimdiff 'http://www.google.co.in/search?q=vimdiff' 'http://www.google.co.in/search?q=vim'``
|  You'll first see something like this coming on screen
| 
   `` :!curl -o '/tmp/v959288/1' 'http://www.google.co.in/search\?q=vimdiff' % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current Dload  Upload   Total   Spent    Left  Speed "/tmp/v959288/1" 4L, 5289C :!curl -o '/tmp/v959288/2' 'http://www.google.co.in/search\?q=vim' % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current Dload  Upload   Total   Spent    Left  Speed "/tmp/v959288/2" 4L, 5253C Press ENTER or type command to continue``
|  Now press the ENTER key to see the diff

[caption id="" align="aligncenter" width="512" caption="vimdiff also
works directly with URLs"]\ |vimdiff also works directly with
URLs|\ [/caption]

|  You can throw in ssh into the mix as well. Try something like this
|  ``$vimdiff old <(ssh user@host cat ~/new)``

If you're a vim/vimdiff ninja and know some more tricks, do post them
below :)

Happy hacking...

.. |vimdiff| image:: http://gingerjoos.com/images/vimdiff1.png
   :target: http://gingerjoos.com/images/vimdiff1.png
.. |vimdiff with cursor on right half of screen| image:: http://gingerjoos.com/images/vimdiff2.png
   :target: http://gingerjoos.com/images/vimdiff2.png
.. |vimdiff with copy paste| image:: http://gingerjoos.com/images/vimdiff3.png
   :target: http://gingerjoos.com/images/vimdiff3.png
.. |vimdiff deletes words| image:: http://gingerjoos.com/images/vimdiff4.png
   :target: http://gingerjoos.com/images/vimdiff4.png
.. |two files with no difference in vimdiff| image:: http://gingerjoos.com/images/vimdiff5.png
   :target: http://gingerjoos.com/images/vimdiff5.png
.. |vimdiff also works directly with URLs| image:: http://gingerjoos.com/images/vimdiff6.png
   :target: http://gingerjoos.com/images/vimdiff6.png
