# Bounty Hacker
[Back to Tryhackme page](../Tryhackme.md)
- --
## Starting point
[Bounty hacker](https://tryhackme.com/room/cowboyhacker) is [tryhackme](https://tryhackme.com) room. Room has tags of linux , tar , privesc and security.
- --
## Enumeration
Using nmap , we found 3 open ports. Port 21,22 and 80. 

![nmap result](nmap%20result.png)
- --
## Website
Visiting website gave us some story and 4 usernames.

![website](website.png)

Viewing source file shows nothing special.

![website source](website%20source.png)

Started directory enumeration using gobuster also showed no result.

![gobuster](gobuster.png)

Images directory was also not interesting.

![images](images.png)

Nothing interesting found so leaving website end here.
- --
## ftp
Focusing of ftp port now.
Connecting to ftp as anonymous.

![ftp](ftp.png)

We got two files named user.txt and locks.txt

![ftp result](ftp%20result.png)

locks.txt is definitely password file.
user.txt shows another username called lin.
- --
## Password cracking
Using hydra , started password bruteforce on ssh port.
Having no idea to start brute force for which user , created user file where I added all possible usernames.
Made mistake here , wrote username with first letter capital so didn't quite work.
After trying lin as user on other terminal found lin is right username.

![hydra](hydra.png)

Password : RedDr4gonSynd1cat3
- --
## SSH
Login SSH , found that user flag was directly located on home path.
- --
## User flag
Got user flag easily.

![user flag](user%20flag.png)
- --
## Root flag
Checked sudo permission for user and tar has sudo permission
Cheking [gtfobins](https://gtfobins.github.io/gtfobins/tar/#sudo) showed tar exploit for sudo.

![gtfobins](gtfobins.png)

Using this gave root permission.
Found root flag.

![root flag](root%20flag.png)

- --
> Note :
> 1. Write username is right case.

This was my first machine which I solved without any help and hints.
![rank](rank.png)

- --
### Source 
- [Bounty Hacker](https://tryhackme.com/room/cowboyhacker)
