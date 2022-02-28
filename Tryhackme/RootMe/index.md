# RootMe
[Backt to Tryhackme page](../index.md)

---

## Enumeration
Using Nmap , we got there are 2 open ports.

![nmap scan](nmap%20scan.png)

---

## Website

![Website](Website.png)

Doesn't have any hiddent details. Although PHPSESSID is shown indicating PHP is used in backend.
- --
## Directory Enumeration
Using gobuster , we get 2 directories like panel and uploads.
Panel shows form to upload file.
Uploads shows files uploaded from panels form.

![gobuster](gobuster.png)

---

## PHP Reverse shell 
Panel can be used to upload file so I cloned [php-reverse-shell](https://github.com/pentestmonkey/php-reverse-shell) repository. 

![php reverse shell](php%20reverse%20shell.png)

Tried uploading shell but failed.
![php rejected](php%20rejected.png)

Googled how to bypass php and found this on [website](https://vulp3cula.gitbook.io/hackers-grimoire/exploitation/web-application/file-upload-bypass).

![change file extension](change%20file%20extension.png)

Changing .php to .phtml bypassed.

![phtml accepted](phtml%20accepted.png)

---

## Shell access
Tried running file from opening it through uploads directory.
It gave error.

![shell execution failed](shell%20execution%20failed.png)

But surprisingly , I got reverse shell.

![Reverse shell](Reverse%20shell.png)
- --
## User flag
Found User flag.

![user flag](user%20flag.png)

- --
## SUID explotation
Tryhackme question specifically asked about SUID so checked for that.

![suid finding](suid%20finding.png)

Checked [gtfobins python suid](https://gtfobins.github.io/gtfobins/python/#suid).

![gtfobins suid python](gtfobins%20suid%20python.png)

I got root access.

![root access](root%20access.png)
- --
## Root flag

![user flag](user%20flag.png)

- --
### Source
- [RootMe Walkthrough ](https://infosecwriteups.com/tryhackme-rootme-ctf-walkthrough-detailed-a7c521df7339)
- [Php reverse shell code](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)
- [file upload bypass](https://vulp3cula.gitbook.io/hackers-grimoire/exploitation/web-application/file-upload-bypass)


