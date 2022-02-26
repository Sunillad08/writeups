# Wonderland
[Back to tryhackme page](../Tryhackme.md)
- --
## Enumeration
Started enumeration machine using nmap , found 2 open port with ssh and http services running.

![Nmap result](Nmap%20result.png)

Only 2 possible attack vector here and http service is major thing here.
So started directory enumeration using gobuster.

Got two interesting directories called img and r.

![gobuster 1](gobuster%201.png)

img shows 3 images but index page only had 1 image so there are more pages , also r directory has next part of story. So let's continue directory enumeration of r.

![gobuster 2](gobuster%202.png)

clearly we can see what "Follow the **rabbit**" means here. SO I checked all directories and reached at end with /r/a/b/b/i/t directory structure.

![gobuster 3](gobuster%203.png)

This directory doesn't go further than this.
Viewing source of this page finds a clue.

![rabbit page source](rabbit%20page%20source.png)

"HowDothTheLittleCrocodileImproveHisShiningTail" is hidden clue. What could this mean??

Currently "alice" , "cat" , "rabbit" are characters in picture.

Let's parallely start ssh bruteforce attack with alice as username.

Checked the clue we got as password and tried loggin in as alice in ssh. Surprisingly it work!!

![ssh login](../Wgel/ssh%20login.png)

- --

![](../Wgel/user%20flag.png)
![](Pasted%20image%2020220120205745.png)

> Incomplete machine