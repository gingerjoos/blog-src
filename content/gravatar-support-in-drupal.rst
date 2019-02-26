Gravatar support  in Drupal
###########################
:date: 2009-11-04 19:22
:author: admin
:category: drupal
:tags: drupal, gravatar
:slug: gravatar-support-in-drupal

If you've been using Wordpress you probably know about Gravatar.
Gravatar is an abbreviation for "Globally Recognized Avatar". It's a
service which provides an avatar across sites. While Gravatar support is
built-in in Wordpress, it requires an external module to be installed in
Drupal. Recently I had to use the module in a Drupal 5 instance.

The module provides a gravatar only for comments. You can have the
module insert the gravatar into the comment body itself or have it
provide a field in the comment object ($comment->gravatar) which can be
used by the theme. It does this by using the hook\_comment() .

In our case though, we needed it to show the gravatar instead of the
user picture if the user had not uploaded any. This was very easy to do.
The key function here is \_gravatar\_get\_gravatar(). You can provide it
any or all of these parameters - mail, default, size or rating. Mail is
the email id of the user. Gravatar can supply a unique generated avatar
in case the email id you send them is not that of a registered Gravatar
user. This can be of many types - identicon, wavatar or monsterid. Which
of these are what you want, is specified in the default parameter. The
size is of course, the size. The gravatars uploaded come with a rating -
G, PG, R or X. You can specify a maximum rating with the rating
parameter. You can read more about the `gravatar
parameters <http://en.gravatar.com/site/implement/url>`__.

You can pass whichever of these parameters you want to
\_gravatar\_get\_gravatar() and it will return to you the url of the
gravatar. Now pass this to the theme\_gravatar() function in the
gravatar module.

|  $picture = theme('gravatar',$gravatar\_url,$username,$url);[/sourcecode]
|  You have to do all of this in the theme\_user\_picture function of
   your theme. If your theme is something like -
|  function THEMENAME\_user\_picture($account) {
|  if (variable\_get('user\_pictures', 0)) {
|  if ($account->picture && file\_exists($account->picture)) {
|  $picture = file\_create\_url($account->picture);
|  }
|  else if (variable\_get('user\_picture\_default', '')) {
|  $picture = variable\_get('user\_picture\_default', '');
|  }

|  You could change it to something like -
|
|  function THEMENAME\_user\_picture($account) {
|    if (variable\_get('user\_pictures', 0)) {
|    if ($account->picture && file\_exists($account->picture)) {
|    $picture = file\_create\_url($account->picture);
|  }
|  else if (user\_access('use gravatar', $account) &&
   (!user\_access('disable own gravatar', $account) \|\|
   !isset($account->gravatar) \|\| $account->gravatar)) {
|  $picture = \_gravatar\_get\_gravatar(array('mail' =>
   $account->mail));
|  return theme('gravatar',$picture,$account->name,'');
|  }
|  else if (variable\_get('user\_picture\_default', '')) {
|  $picture = variable\_get('user\_picture\_default', '');
|  }
|  You could even rewrite the default theme\_gravatar provided by the
   gravatar module with your own THEMENAME\_gravatar theme function.
