Virtualbox and madwifi
######################
:date: 2009-04-06 11:48
:author: admin
:category: Uncategorized
:slug: virtualbox-and-madwifi

Blaaagh.. I hate this!

Tried installing virtualbox on a Compaq C700. The install went
flawlessly. I even tried out some stuff on it. All was well... until I
had to switch on my wi-fi that is. Just wasn't showing up. An ifconfig
-a showed up only eth0 and lo. Googled around a bit. Seems as if madwifi
(the wifi driver) and virtualbox don't go very well together.

You can take a look at this
`ticket <http://madwifi-project.org/ticket/1114>`__.
