# Brooklyn Nine Nine
[Back to Tryhackme page](../index.md)
- --
## Enumeration
Started nmap service scan on given ip

![nmap output](nmap%20output.png)

3 services found:
ftp , ssh and http
- --
## http
opened website 

![http output](http%20output.png)

Hint was given about stenography in html content!
Also tried to dirb to find subdirectories but nothing special found.
- --
## ftp
anonymous login to ftp server.

![ftp output](ftp%20output.png)

3 usernames were revealed. Jake , Amy and Holt.
Jake has weak password and holt will be angry suggests holt has important position.
- --
## ssh
Searched about how to bruteforce ssh password
[ssh bruteforce using hydra article](https://linuxconfig.org/ssh-password-testing-with-hydra-on-kali-linux)

![ssh password brute force](ssh%20password%20brute%20force.png)

- --
## flag finding
By login into ssh  , found user flag

![user flag](../Wonderland/user%20flag.png)

Didn't understood how to find root access go googled about room
[Room walkthrough](https://musyokaian.medium.com/brooklyn-nine-nine-walkthrough-tryhackme-8c3c5791d6b7)

Got it how to do privilege escalation with [cheatsheet](https://gtfobins.github.io/gtfobins/less/#sudo)

![root flag](../Wgel/root%20flag.png)

- --
Done with my first machine! 