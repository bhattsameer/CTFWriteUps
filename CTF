# Mirzapur
CTF Writeup

1.  CTF url is given, Let's see what is there\...
![](./media/image11.png)

2.  I checked the source of the page and there I found
> Mirzapur\_ka\_Rasta.js
![](./media/image9.png)

3.  The JS code written inside was\...
![](./media/image5.png)

4.  Let's call the Desi\_Katta() function\...
![](./media/image7.png)

5.  Check the alertBox it looks like a path to some directory\...
![](./media/image1.png)

6.  Going there only gave me more and more web pages\...
![](./media/image10.png)

7.  One of the URL linked there has parameter "id" and the value was 1. I tried SQL injection with many tempore scripts but no luck. After a few times I got the hint that not every parameter is vulnerable to SQL injection. Hence I tried file retrieval and it was a success.

> ?id=/etc/passwd
![](./media/image8.png)

8.  From /etc/passwd we have the user "munna". But what is the password??? Let's check Bash History for clues\...
> id=/home/munna/.bash\_history
![](./media/image6.png)

9.  Looks like the user have typed password along with passwd command without giving enter.(or at least the CTF builder wants to tell us that). SSH Done. It was RBash. The PATH variable lead me to this directory and the available commands were very few. Also, we have an interesting language that we can use "LUA".
![](./media/image2.png)

10. A quick search on google gave me lua to shell\...
![](./media/image4.png)

11. Once I am out of RBash I tried grep command and two flags at once...
![](./media/image3.png)
