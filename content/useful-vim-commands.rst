Useful vim commands
###################
:date: 2009-06-04 12:06
:author: admin
:category: Linux, technology
:tags: useful vi commands, useful vim commands, vi, vim, vim enhanced, vim keyboard shortcuts, vim shortcuts
:slug: useful-vim-commands

I use `vim <http://en.wikipedia.org/wiki/Vim_(text_editor)>`__ at work
for most of my text editing purposes. Vim is a very powerful editor.
However, it comes with a somewhat steep learning curve. The best place
to learn it would be the vimtutor program. It's got a pretty good "for
dummies" approach which is useful if you haven't used an editor even
remotely powerful as this one before. If you're short of time, the best
way to learn it is to just jump in and start using it. Since it's been
around a long time, it has pretty much most features a developer needs.
So if you have a need and don't know how to get it done with vim, then
use `this site <http://www.google.com>`__.

To start off using vim, let me give you a very quick and dirty first few
steps. To open a file, simply use vim <filename>. You most likely have
vi pointing to vim. Plus, most of these commands work with other vi's
anyway. So I'll be using vi instead of vim henceforth.

Now that you have a file open, you would like to enter some stuff in?
The basic thing you need to know about vi is that it has many modes.
From the default mode(command mode) you need to press 'i' to enter the
insert mode. In this mode you can type stuff in and it will show up on
the screen. The command mode is where you issue commands to vi (But you
can't enter text). To go back from the insert mode to command mode press
the escape key.

Now that you've typed some random stuff in, escape to the command mode.
Now try pressing ':w' i.e. (shift+;)w. W is for "write". This saves the
file and leaves you still in the editor. If you want to get out of the
editor, you type in one more command 'q' so it becomes ':wq'. In case
you want to get out of it without saving, use ':q!'. The other way to
save and quit is to go to the command mode and hit shift+z+z.

With vi, the traditional way to navigate (in command mode) is to use
l,k,j,h keys(right,up,down,left). That's like the a,w,s,d in gaming.
It's a timesaver for people who are comfortable with it. Vim allows you
to use the arrow keys as well, which is a real convenience.

That covers the bare minimum basics for us.

Once you start using vi you start looking for ways to accomplish tasks
using it. There is a whole lot of material out there in the World Wide
Web which will help you out. Google is your friend, use it :)

I will tell you some of the frequently used options/shortcuts I use with
vim.

Going to a specific line : Type in ':25' to go to line number 25 (in
command mode). You can open a file at a specific line by typing

$ vi +25 FILENAME

This will open the file and take you to line 25. Now that you're there,
perhaps you would like to delete the next 5 lines? No problem - just hit
d5d. The 5 in the middle says 5 and dd is for deleting lines. You will
find this a common pattern with most vi commands. Just hitting dd will
remove a single line. Similarly you can do d5w to remove 5 words and dw
to remove a single word.

Copy paste is a walk in the  park. Hit y7y to copy 7 lines. Now press p
to paste. That's it. Cut paste? Hit d7d and then press p to paste after
navigating to where you want to paste it.

The other approach to doing all this is to send a command. Hit
':201,225y' to copy lines from 201 to 225. Similarly ':201,225d' deletes
lines from 201 to 225. To jump to a line you can use ':25'. This jumps
to line number 25.

One useful shortcut when you don't want to remember the line numbers is
the use of markers. I can mark any 2 lines , say line numbers 201 and
225, and perform an action on them by using the name of the markers. Go
to line number 201 and hit 'ma'. This will mark that line with the
marker 'a'. Do the same with line 225 and mark it with 'b'. Instead of
uisng ':201,225d' to delete lines 201 to 225, now you can use the a and
b markers to delete the lines thus - ":'a,'bd".

That was just a small snapshot of the commands that I use on vi. You can
use a lot other features, like for instance
`macros <http://www.oreillynet.com/mac/blog/2006/07/more_vim_save_time_with_macros_1.html>`__,
and enhance your editing experience. This should help you get started
though. Let me know if this has been useful. Good luck and happy hacking
:)
