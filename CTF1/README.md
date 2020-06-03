# #CTFFriday 2020FebWeek4 - Web CTF

* Date: 29nd Feb 2020
* Time: 2:00 to 3:00 PM

## Organized By

| ![](media/rsz_1rsz_netsquare.png)    |![](media/rsz_conclave.png)|
|:-----------------------------------------------:|:---------------------------------------------:|
| Net Square Solutions Pvt. Ltd.                              | NSConclave                             |

## About Me

Hi,

I am [Sameer Bhatt](https://twitter.com/sameer_bhatt5) (Debugger) goes on CTF by name `Turing` and I am currently working in [Net Square Solutions Pvt. Ltd.](https://net-square.com) as a Security Analyst.


## Overview

There were 2 Web challenges and 1 Misc. challenge. The CTF was based on XML attacks and Privilege escalation to get Root access. For solving this challanges you need some basic knowledge of Web, XML and good understanding of command line. 

![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/13.png "Challenges")

------------------------------------------------------------------

## Tools Used
- BurpSuite
 
-------------------------------------------------------------------------
|Challenge 1|
|------------|
|Geo|
|http://nsctf50.ns:8080
http://nsctf90.ns:8080 |
| 100 pts|


**Description**

- After visiting the URL given in the challenge, we have a page containing two links. 

    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/task1.png) 

- I have clicked on second link as the task name was `Geo` and I got goeserver dashboard.

    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/task1_2.png)

-  After that I have clicked on that OpenLayerXml and While Intercepting the request in burp and observing the request, I found XML data passing inside one parameter. Also observed that it is `geoserver` so I searched for some geoserver related vulnerabilities on google and github and found one exploit.
    exploit is one python code.
    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/2.png)

-  Using above script I have created one payload to read **/etc/passwd** and and used it inside the request parameter and :boom: we got content of /etc/passwd.

    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/3.png)

-  Observing the /etc/passwd I found there is one **nsctf** user, so next in the payload I have added **/home/nsctf** and observed that there is one file **\_\_flag1\_\_**.
    
    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/4.png)
    
-  In the next payload reading the file using **/home/nsctf/\_\_flag1\_\_** and :boom: we got our first flag.
    
    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/5.png "flag1")
    
   *flag 1 : nsctf{XX3_i5_aw3s0m3}*
    

-------------------------------------------------------------------
|Challenge 2|
|------------|
|Access|
|can you gain access using nsctf user. 
(50 pts)|

#### Description


As the challenge description says *Can you gain access using nsctf user* the first comes up in my mind is SSH. 

After doing nmap I already observed that ssh is enabled. so all I required is password of nsctf user or I can use key to login with ssh using nsctf user.

-  As I able to read any system file of nsctf user, I tried to read **/home/nsctf/.ssh/id_rsa** and got nsctf user's ssh key.
  
   ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/7.png)
   
-  Using which I am able to do ssh to nsctf user and read **.\_\_flag2\_\_** file.

    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/8.png)
    ![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/9.png) 
    
    *flag2 : nsctf{4d9827f4f06f50d4618c6da61b68634c}*

--------------------------------------------------------

|Challenge 3|
|------------|
|Root|
|Can you become root. 
(100 pts)|

#### Description

As the challenge says we have to escalate our privileges and become root.
First step I did was running command **sudo -l** and observed that we can run zip command as a sudo. so tried below commands:

```
 echo "/bin/sh" > /tmp/win.sh
 sudo zip z.zip * -T -TT /tmp/win.sh 
```

![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/11.png "root")

Lets access the root flag now.

![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/12.png "flag3")

*flag 3: nsctf{574ca321d4b0f3cca3d6763567095b17}*
  
  
And I got the final flag.

Here are the stats from the CTF.

![alt text](https://raw.githubusercontent.com/bhattsameer/CTFWriteUps/master/CTF1/media/14.png "scoreboard") 
  
--------------------------------------------------------
