How to solve the "local edit, incoming delete upon update" issue in SVN
#######################################################################
:date: 2011-08-11 14:46
:author: admin
:category: code
:tags: svn
:slug: how-to-solve-the-local-edit-incoming-delete-upon-update-issue-in-svn

When I removed a file from
`svn <http://en.wikipedia.org/wiki/Apache_Subversion>`__ it caused me
lot of problems. This particular file was in CamelCase and I needed to
replace it with a file in lower case. I svn deleted the CamelCase file
and committed a copy of the lower case file. All this happened in a
windows system. When I updated the checked out branch I got the error :

| At revision 17582.
|  !  +  C FooBar.php
|  >   local edit, incoming delete upon update

Multiple attempts at svn cleanup, svn update etc. failed. I came across
this `stack overflow
thread <http://stackoverflow.com/questions/4317973/svn-how-to-resolve-local-edit-incoming-delete-upon-update-message>`__
which recommended svn resolve. This did not work for me. Further down
the thread I came across another solution which worked.

#. create FooBar.php ( $touch FooBar.php )
#. svn revert it ( $svn revert FooBar.php )
#. Check status ( $svn status ) . It should say ?FooBar.php
#. Now remove FooBar.php ( $rm FooBar.php )

That's it, you're done :)
