How to dump or export all the table definitions in a MySQL database
###################################################################
:date: 2010-02-05 16:41
:author: admin
:category: code
:tags: mysql, mysqldump
:slug: how-to-dump-or-export-all-the-table-definitions-in-a-mysql-database

So you have  a database with loads of tables. You want the table
definitions of all of them. You don't really need the data.
`mysqldump <http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html>`__ to
the rescue!

[sourcecode]mysqldump -u USERNAME --password=PASSWORD --no-data --opt
DB1 > DUMPFILE[/sourcecode]

That's it! Easy as a pie :) The key here is the --no-data option. It
dumps all the table definitions, but not the table data.

Want to do this for multiple databases? No problem.

[sourcecode]mysqldump -u USERNAME --password=PASSWORD --no-data --opt
--databases DB1 DB2 > DUMPFILE[/sourcecode]

The --databases option allows you to add multiple databases.

[sourcecode]mysqldump -u USERNAME --password=PASSWORD --no-data --opt
--all-databases > DUMPFILE[/sourcecode]

The --all-databases option allows you to dump all the databases.

[sourcecode]mysqldump -u USERNAME --password=PASSWORD --no-data --opt
DB1 --ignore-table DB1.TABLENAME1 --ignore-table DB1.TABLENAME2 >
DUMPFILE[/sourcecode]

--ignore-table option allows you to skip dumping certain tables. Do not
forget to specify the databasename when using this option.

 

Know any more tricks? Let us know in the comments below :)
