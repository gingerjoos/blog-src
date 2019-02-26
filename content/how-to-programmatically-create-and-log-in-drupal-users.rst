How to programmatically create and log in drupal users
######################################################
:date: 2010-02-22 20:39
:author: admin
:category: drupal
:tags: drupal, php, user
:slug: how-to-programmatically-create-and-log-in-drupal-users

| Creating a new user is very easy in Drupal 6. Here's how.
| [sourcecode language="php"]

>

$new\_user = array(

| 'name' => $username,
|  'mail' => $mail,
|  'pass' => user\_password(),
|  'status' => 1,
|  'auth\_MODULENAME' => $username
| )

$user = user\_save(NULL,$new\_user)

// log the user in

$user = user\_authenticate($new\_user)

[/sourcecode]

Now for the explanation. We create a $new\_user array with values we
want the newly created user to have. We pass this along to the
`user\_save <http://api.drupal.org/api/function/user_save/6>`__ function
and set the 1st parameter as NULL. From the code comments in the user
module -

    | \* @param $account
    |  \* The $user object for the user to modify or add. If $user->uid is
    |  \* omitted, a new user will be added.
    |  \*
    |  \* @param $array
    |  \* (optional) An array of fields and values to save. For example,
    |  \* array('name' => 'My name'); Setting a field to NULL deletes it from
    |  \* the data column.

So setting the 1st parameter as NULL creates a new user.

The parameters name, mail, pass and status are all self explanatory. The
`user\_password <http://api.drupal.org/api/function/user_password/6>`__
function generates a random password (by default with a length of 10).

The (optional) 'auth\_MODULENAME' element will record the user as being
created externally. This will result in an entry in the authmap table
like this -

| "aid" "uid" "authname" "module"
| "2" "20" "USERNAME" "MODULENAME"

The
`user\_authenticate <http://api.drupal.org/api/function/user_authenticate/6>`__
function logs the user in. This function expects an array as a
parameter. It first loads the user in using the
`user\_load <http://api.drupal.org/api/function/user_load/6>`__ function
and in case of no errors logs the user in.

This approach of logging in a user is useful when we have the array with
us which contains the raw values used to create the user. If all you
have is the uid of the user, then logging the user in is very simple.
Just use the global $user object.

[sourcecode language="php"]

global $user

$account = user\_load( array('name' => 'USERNAME') ); // or
user\_load(UID)

$user = $account

[/sourcecode]

Don't use the user\_authenticate function here as it expects the raw
values(form values). This wil not work -

[sourcecode language="php"]

$account = user\_load( array('name' => 'USERNAME') ); // or
user\_load(UID)

user\_authenticate((array)$account)

[/sourcecode]

It will take whatever password is stored in the user object(the raw
password), md5 it and then run a query to load that user. Since the
password in the query is not the raw password but the md5, the query
will return nothing. This will cause an error in the user\_authenticate
function.

For a direct code example for programmatic log in, check the
`devel <http://drupal.org/project/Devel>`__ module's devel\_switch\_user
function.
