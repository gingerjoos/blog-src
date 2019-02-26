apt-get with proxy
##################
:date: 2011-08-01 17:50
:author: admin
:category: Linux
:slug: apt-get-with-proxy

You will notice that the proxy settings you provide in the network
settings may not be picked up by apt-get while installing a package. So
if you want to run apt-get via a proxy then you need to use a tool like
proxychains. Proxychains is a tool that allow you to run a command via a
proxy even if the command itself does not support proxies. You can
install proxychains by running apt-get install proxychains. In case this
is not possible for you, then get the proxychains tarball from the
`proxychains site <http://proxychains.sourceforge.net/>`__.Compile and
install - it's very simple to do. Just run ./configure and then make and
make install. Run make install as root.

Once this is done you have proxychains installed in your system.
Proxychains takes its settings from one of 3 files :

| 1)    ./proxychains.conf
|  2)    $(HOME)/.proxychains/proxychains.conf
|  3)    /etc/proxychains.conf

I edited the /etc/proxychains.conf file directly. I have a SOCKS5 proxy
running on localhost over port 8080. So I add an entry towards the end
like this -

socks5  127.0.0.1 8080

Once you have this and have your socks proxy running, you're ready to
start running your commands. Imagine you want to run apt-get update.
This is how it would be done -

$ sudo proxychains apt-get upgrade

That's it :)
