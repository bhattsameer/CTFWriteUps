
CTF Writeup

CTF url is given, Let's see what is there\...

## Challange 1:

The name of the challange was **GEO**, One URL was provided and we need to find the flag.

![](./media/1.png)

While Intercepting the request in burp and observing the request, I found XML data passing inside one parameter. Also observed the it is **geoserver** so I searched for some geoserver related vulnerabilities on google and github and found one exploit.

![](./media/2.png)

Using above script I have created one payload to read **/etc/passwd** and and used it inside the request parameter and :boom: we got content of /etc/passwd.

![](./media/3.png)

Observing the /etc/passwd I found there is one **nsctf** user, so next in the payload I have added **/home/nsctf** and observed that there is one file **\_\_flag1\_\_**.

![](./media/4.png)

In the next payload we are reading the file using **/home/nsctf/\_\_flag1\_\_** and :boom: we got our first flag.

*flag was : nsctf{XX3_i5_aw3s0m3}*

![](./media/5.png)


