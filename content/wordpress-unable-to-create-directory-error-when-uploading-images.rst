Wordpress - Unable to create directory error when uploading images
##################################################################
:date: 2010-11-16 20:12
:author: admin
:category: technology
:tags: image upload, wordpress
:slug: wordpress-unable-to-create-directory-error-when-uploading-images

Unable to create directory<DIRECTORY NAME> . Is its parent directory
writable by the server?

This error seem familiar to you? I got this error when trying to upload
an image on wordpress. I checked the directory mentioned in the error
and it did not exist. It so happened that Dreamhost had moved the my
blog to another server. Wordpress was trying to save the image to a
location that existed in the old server. I went to Settings -> Media
Settings -> Uploading Files and then changed the "Store Uploads in this
folder" setting to "wp-content/uploads". Before the changed it pointed
to the directory in my old server. This change fixed the problems with
uploading files.
