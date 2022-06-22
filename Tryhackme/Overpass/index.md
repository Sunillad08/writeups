# Overpass
[Back to Tryhackme Page](../index.md)

---

## Enumeration
Starting machine enumeration using nmap.

![nmap](nmap.png)

There are 2 open ports i.e. SSH and HTTP.
Let's focus on HTTP first.

---

## HTTP
Starting directory enumeration using gobuster.

![gobuster](gobuster.png)

There is admin directory. Let's check that one.

![admin login](login%20page.png)

This is admin login page , it passes information to login.js file.

![login.js](login%20js.png)

Login js passes information to /api/login point. 

> I tried sql injection , authentication bypass methods but couldn't crack it so I check a [walkthrough](https://youtu.be/qhUKA0t2T8M). 

We have to create a cookie as SessionToken .

![cookie](cookie.png)

and we are logged in . There is private rsa_id key.

![rsa_id](rsa_id%20login.png)

---

## Hash cracking
Let's crack password for private key using john.

![john id_rsa](john%20id_rsa.png)

We got passphrase as "james13".

---

## SSH Login
Let's log into SSH.

![user flag](overpass%20user%20flag.png)

We got user flag.

---

## Privilege escalation
Cron tag was mentioned on room so let's check crontab.

![crontab](cron%20job.png)

So there is cron job that get buildscript.sh from overpass.thm and runs it.
Let's check host file for overpass.thm . We can update it to forward request to our machine.

![updated host](updated%20host.png)

Let's setup our side now. I created /downloads/src path in my tmp folder. Also created buildscript.sh which gives reverse shell to my machine.

![hosting file](hosting%20build%20script.png)

I changed port to 80 so machine can request file.

Now we wait till machine requests our buildscript.sh

![Setup](setup%20host.png)


---

## Root flag
We got root flag!

![root flag](overpass%20root%20flag.png)

---

### Sources :
- [Tryhackme Overpass room](https://tryhackme.com/room/overpass)
- [Walkthrough](https://youtu.be/qhUKA0t2T8M)