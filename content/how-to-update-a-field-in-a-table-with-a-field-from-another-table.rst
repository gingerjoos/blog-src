How to update a field in a table with a field from another table
################################################################
:date: 2010-12-07 15:15
:author: admin
:category: code
:tags: mysql, update
:slug: how-to-update-a-field-in-a-table-with-a-field-from-another-table

I needed a table which gave the map between the URLs and nodes in
drupal. I ended up creating a table like this :

 

| CREATE TABLE \`nid\_url\_map\` (
|  \`nid\` int(10) NOT NULL DEFAULT '0',
|  \`url\` varchar(255) DEFAULT NULL,
|  \`type\` varchar(32) DEFAULT NULL,
|  PRIMARY KEY (\`nid\`)
| ) ENGINE=InnoDB DEFAULT CHARSET=utf8

To populate this table I used the url\_alias table :

| CREATE TABLE \`url\_alias\` (
|  \`pid\` int(10) unsigned NOT NULL AUTO\_INCREMENT,
|  \`src\` varchar(128) NOT NULL DEFAULT '',
|  \`dst\` varchar(128) NOT NULL DEFAULT '',
|  \`language\` varchar(12) NOT NULL DEFAULT '',
|  \`nid\` int(11) NOT NULL DEFAULT '0',
|  PRIMARY KEY (\`pid\`),
|  UNIQUE KEY \`dst\_language\` (\`dst\`,\`language\`),
|  KEY \`src\_language\` (\`src\`,\`language\`),
|  KEY \`nid\` (\`nid\`)
| ) ENGINE=MyISAM AUTO\_INCREMENT=267714 DEFAULT CHARSET=utf8

This is the query I ran at first to populate the table :

| INSERT IGNORE INTO nid\_url\_map (nid,url)
| SELECT SUBSTR(src,6) AS nid,dst AS url FROM url\_alias
| WHERE src LIKE 'node/%';

The url\_alias table maps the internal url ( in the form of node/ID ) to
the pretty URL of the page ( eg. comedy/monty-python-spam ) . Now what
remained was the type. The node type is available in the node table :

| CREATE TABLE \`node\` (
|  \`nid\` int(10) unsigned NOT NULL AUTO\_INCREMENT,
|  \`vid\` int(10) unsigned NOT NULL DEFAULT '0',
|  \`type\` varchar(32) NOT NULL DEFAULT '',
|  \`language\` varchar(12) NOT NULL DEFAULT '',
|  \`title\` varchar(255) NOT NULL DEFAULT '',
|  \`uid\` int(11) NOT NULL DEFAULT '0',
|  \`status\` int(11) NOT NULL DEFAULT '1',
|  \`created\` int(11) NOT NULL DEFAULT '0',
|  \`changed\` int(11) NOT NULL DEFAULT '0',
|  \`comment\` int(11) NOT NULL DEFAULT '0',
|  \`promote\` int(11) NOT NULL DEFAULT '0',
|  \`moderate\` int(11) NOT NULL DEFAULT '0',
|  \`sticky\` int(11) NOT NULL DEFAULT '0',
|  \`tnid\` int(10) unsigned NOT NULL DEFAULT '0',
|  \`translate\` int(11) NOT NULL DEFAULT '0',
|  \`titlehash\` char(32) DEFAULT '',
|  PRIMARY KEY (\`nid\`),
|  UNIQUE KEY \`vid\` (\`vid\`),
|  KEY \`node\_changed\` (\`changed\`),
|  KEY \`node\_created\` (\`created\`),
|  KEY \`node\_moderate\` (\`moderate\`),
|  KEY \`node\_promote\_status\` (\`promote\`,\`status\`),
|  KEY \`node\_status\_type\` (\`status\`,\`type\`,\`nid\`),
|  KEY \`node\_title\_type\` (\`title\`,\`type\`(4)),
|  KEY \`node\_type\` (\`type\`(4)),
|  KEY \`uid\` (\`uid\`),
|  KEY \`tnid\` (\`tnid\`),
|  KEY \`translate\` (\`translate\`),
|  KEY \`title\` (\`title\`),
|  KEY \`titlehash\` (\`titlehash\`)
| ) ENGINE=MyISAM AUTO\_INCREMENT=197121 DEFAULT CHARSET=utf8

I referred the MySQL man page on the
`UPDATE <http://dev.mysql.com/doc/refman/5.0/en/update.html>`__ query.
Found a useful query in the comments there. In case I need to use this
one again, here's where I'm gonna refer :)

| UPDATE nid\_url\_map,node
| SET nid\_url\_map.type = node.type
| WHERE nid\_url\_map.nid = node.nid;

 

There you go, easy peasy :)
