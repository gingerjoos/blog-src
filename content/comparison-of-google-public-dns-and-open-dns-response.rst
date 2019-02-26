Comparison of Google Public DNS and Open DNS response
#####################################################
:date: 2009-12-05 13:03
:author: admin
:category: technology
:tags: dns, google, opendns
:slug: comparison-of-google-public-dns-and-open-dns-response

`Google announced <http://googleblog.blogspot.com/2009/12/introducing-google-public-dns.html>`__
that it's making 2 `DNS servers available
publicly <http://code.google.com/speed/public-dns/>`__. The servers are
8.8.8.8 and 8.8.4.4 . They've also given\ `configuration
instructions <http://code.google.com/speed/public-dns/docs/using.html>`__
on their DNS page. I configured my /etc/resolv.conf to refer to Google's
DNS. Before this I ran some quick tests using
`dig <http://linux.die.net/man/1/dig>`__ to compare it with
`OpenDNS <http://www.opendns.com/>`__.
|  [sourcecode language="text"]
|  $ dig @208.67.222.222 gingerjoos.com

| ; <<>> DiG 9.4.2 <<>> @208.67.222.222 gingerjoos.com
|  ; (1 server found)
|  ;; global options: printcmd
|  ;; Got answer:
|  ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 1273
|  ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

| ;; QUESTION SECTION:
|  ;gingerjoos.com. IN A

| ;; ANSWER SECTION:
|  gingerjoos.com. 14400 IN A 208.113.199.196

| ;; Query time: 751 msec
|  ;; SERVER: 208.67.222.222#53(208.67.222.222)
|  ;; WHEN: Fri Dec 4 09:13:58 2009
|  ;; MSG SIZE rcvd: 48

$ dig @8.8.8.8 gingerjoos.com

| ; <<>> DiG 9.4.2 <<>> @8.8.8.8 gingerjoos.com
|  ; (1 server found)
|  ;; global options: printcmd
|  ;; Got answer:
|  ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2594
|  ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

| ;; QUESTION SECTION:
|  ;gingerjoos.com. IN A

| ;; ANSWER SECTION:
|  gingerjoos.com. 14400 IN A 208.113.199.196

| ;; Query time: 616 msec
|  ;; SERVER: 8.8.8.8#53(8.8.8.8)
|  ;; WHEN: Fri Dec 4 09:14:09 2009
|  ;; MSG SIZE rcvd: 48

$ dig @8.8.4.4 gingerjoos.com

| ; <<>> DiG 9.4.2 <<>> @8.8.4.4 gingerjoos.com
|  ; (1 server found)
|  ;; global options: printcmd
|  ;; Got answer:
|  ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34741
|  ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

| ;; QUESTION SECTION:
|  ;gingerjoos.com. IN A

| ;; ANSWER SECTION:
|  gingerjoos.com. 14321 IN A 208.113.199.196

| ;; Query time: 123 msec
|  ;; SERVER: 8.8.4.4#53(8.8.4.4)
|  ;; WHEN: Fri Dec 4 09:15:28 2009
|  ;; MSG SIZE rcvd: 48
|  [/sourcecode]

Dig allows you to directly query a DNS server and get its reply. It
shows stats from that query - response. The stat we're interested in is
this one

**;; Query time: 123 msec**

The IP 208.67.222.222 is the address of the OpenDNS server. Let's try
one more query

[sourcecode language="text"]

$ dig @208.67.222.222 mec.ac.in

| ; <<>> DiG 9.4.2 <<>> @208.67.222.222 mec.ac.in
|  ; (1 server found)
|  ;; global options:  printcmd
|  ;; Got answer:
|  ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44308
|  ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

| ;; QUESTION SECTION:
|  ;mec.ac.in.                     IN      A

| ;; ANSWER SECTION:
|  mec.ac.in.              604800  IN      A       210.212.232.132

| ;; Query time: 389 msec
|  ;; SERVER: 208.67.222.222#53(208.67.222.222)
|  ;; WHEN: Sat Dec  5 12:38:57 2009
|  ;; MSG SIZE  rcvd: 43

$ dig @8.8.8.8 mec.ac.in

| ; <<>> DiG 9.4.2 <<>> @8.8.8.8 mec.ac.in
|  ; (1 server found)
|  ;; global options:  printcmd
|  ;; Got answer:
|  ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56600
|  ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

| ;; QUESTION SECTION:
|  ;mec.ac.in.                     IN      A

| ;; ANSWER SECTION:
|  mec.ac.in.              160448  IN      A       210.212.232.131

| ;; Query time: 121 msec
|  ;; SERVER: 8.8.8.8#53(8.8.8.8)
|  ;; WHEN: Sat Dec  5 12:39:06 2009
|  ;; MSG SIZE  rcvd: 43

[/sourcecode]

You can try more queries and see for yourself. At least as of now Google
DNS seems to be faster.
