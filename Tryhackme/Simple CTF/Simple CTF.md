# Simple CTF
[Tryhackme](../Tryhackme.md)
- --
## Enumeration
Started emunerating using nmap.
![nmap 1](nmap%201.png)

![nmap 2](nmap%202.png)

Note : SSH port was not shown at first but after getting stuck on questions , checked walthrough and found it should be ssh.

![nmap 3](nmap%203.png)

3 open ports of ftp , http and ssh.
- --
## ftp
Logged into ftp and found user name "mitch". Also says mitch have very weak password.

![ftp](ftp.png)
- --
## Website

![website](website.png)

Website doesn't show anything interesting.

Started directory enumaration with gobuster.

![gobuster](gobuster.png)

Found /simple directory.

![simple page](simple%20page.png)
- --
## CVE finding
Checked CMS versions and googled for its exploit.
![cve](cve.png)

Downloaded file and started exploit.

![CMS made simple](CMS%20made%20simple.png)

Note : Script didn't work becuase of my python version. So I checked through walkthrough and got password.
- --
## User flag
Got user flag.

![user flag](../Wonderland/user%20flag.png)
- --
## Root flag
User had sudo privelege for vim.

![gtfobins vim](gtfobins%20vim.png)

![root flag](../Wgel/root%20flag.png)

- --
### Source 
- [Simple CTF walkthrough](https://medium.com/@skylarphenis/tryhackme-simple-ctf-walk-through-e8bb8c8671a9)
- [Exploit-db](https://www.exploit-db.com/exploits/46635)