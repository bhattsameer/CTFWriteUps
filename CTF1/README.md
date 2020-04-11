# CTF1
CTF Writeup

CTF url is given, Let's see what is there\...

## Challange 1:

The name of the challange was **GEO**, One URL was provided and we need to find the flag.
While Intercepting the request in burp and observing the request, I found XML data passing inside one parameter. Also observed the it is **geoserver** so I searched for some geoserver related vulnerabilities on google and github and found one exploit.

