# Easy Peasy
[Back to Tryhackme page](../index.md)

---

## Enumeration
Let's start enumeration of machine using nmap.

![nmap 1](nmap%201.png)

Seems only HTTP port is open but that answer is not right. Let's do full port scan for this machine. Starting all port scan and side by side doing enumeration of HTTP port.

![](nmap%202.png)

![](nmap%203.png)

So there are 3 open ports (One shows closed). So 2 ports have HTTP and 1 port has SSH service. 

---

## Directory enumeration Port 80
Let's focus on HTTP on port 80 first. Starting with directory enumeration with gobuster tool.

![gobuster 1](gobuster%201.png)

So /hidden is directory we found. Let's check its source code.

![hidden source](hidden%20source.png)

Nothing interesting here. Let's further enumerate this /hidden directory.

![gobuster 2](gobuster%202.png)

Enumerating further , I got another directory in hidden directory. So /hidden/whatever is new found directory. Let's check source code of this one too.

![whatever source](whatever%20source.png)

Hidden base64 encoded string. Let's decode it.

![flag 1](flag%201.png)

---

## Directory enumeration Port 65524
Let's start directory enumeration on this port's HTTP using gobuster.

![gobuster 3](gobuster%203.png)

Robots.txt is only interesting file here. Let's check source code of it.

![robots txt](robots%20source.png)

User agent a18672860d0510e5ab6699730763b250 is allowed to access / . I tried enumeration machine with gobuster again with this user agent and nothing significant found here. I checked if this is hash and it is. 

![hash identifier](hash%20identifier.png)

It is md5 hash so tried cracking it with [crackstation](https://crackstation.net/). After some trying around I googled hash and got this [website](https://md5hashing.net/hash/md5/a18672860d0510e5ab6699730763b250) who gave second flag.

![flag 2](flag%202.png)

---

## Finding flag 3
> Note : Tried finding flag3 but nothing found. Checked [writeup](https://www.aldeid.com/wiki/TryHackMe-Easy-Peasy) at this point. Flag is hidden in source code of home page.

![flag 3](flag%203.png)

---

## Hidden directory
On same line , there was hidden directory mentioned on page's source code.

![hidden directory](hidden%20directory.png)

We got base encoded string here. 

![base62 encoded string](base62%20decode.png)

Tried many base decoding format and base62 decoding gives us directory name. 

---

## Getting password hash
Checking directory gives us password hash.

![nothing source](nothing%20source.png)

Cracking this hash using john the ripper and easypeasy.txt as wordlist.

![hash cracking](hash%20cracked.png)

we got password here but where do we use that? I checked again that there is image on website. Let's check if there is anything interesting there.

![steghide](steghide.png)

We got username as boring and binary password hidden in this image.

![ssh password](ssh%20password.png)

We got SSH password. Not the best way to store password !

---
## User flag
Let's get user flag. Login into SSH.

![user flag](easy%20peasy%20user%20flag.png)

Got user flag here.

---
## Root flag
Cron was mentioned for room tag. So let's check crontab.

![crontab](cron%20job.png)

.mysecretcronjob.sh is cronjob running. It is running with sudo permissions.
We can add this [reverse shell code](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#bash-tcp) to get reverse shell. We can update cronjob. 

![bash reverse shell](bash%20reverse%20shell.png)

![injecting cronjob](injecting%20cronjob.png)

Got reverse shell after few seconds.

![reverse shell](reverse%20root%20shell.png)

I checked root flag with this command.
```bash
find / -type f -name *root* 2>/dev/null
```

![root flag](easy%20peasy%20root%20flag.png)

Got location of root flag and root flag too!

---

### Sources :
- [Easy Peasy Tryhackme](https://tryhackme.com/room/easypeasyctf)