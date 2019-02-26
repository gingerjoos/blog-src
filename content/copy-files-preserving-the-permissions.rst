Copy files preserving the permissions
#####################################
:date: 2009-10-01 20:52
:author: admin
:category: Linux
:tags: commands, copy files, Linux, preserve permissions, unix
:slug: copy-files-preserving-the-permissions

You might have come across a situation where your regular usage of the
`cp command <http://en.wikipedia.org/wiki/Cp_%28Unix%29>`__ for copying
files in your linux box was not enough because while copying you needed
to preserve the permissions of the files. Fret not, for help is at hand.
Take a look at the man page for cp :

``-p     same as --preserve=mode,ownership,timestamps``

``--preserve[=ATTR_LIST] preserve the specified attributes (default: mode,ownership,timestamps), if possible additional attributes: context, links, all``

So that's it. just use the -p flag to do the copying. Here's an example
where I copy a single file while preserving permissions.

``cp -p oldfile ~/new_dest/``

To copy a whole directory, I use the -r flag as well.

``cp -rp some_dir ~/new_dest/``

You can use the --preserve flag to keep whatever attributes you need.
For the record, there's one more related flag

`` --no-preserve=ATTR_LIST               don't preserve the specified attributes``
