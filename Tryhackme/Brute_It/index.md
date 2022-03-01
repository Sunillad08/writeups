# Brute It
[Back to tryhackme page](../index.md)

---

## Enumeration
Started enumerating machine using nmap. Found 2 open port with ssh and http services running.

![Nmap Result](Nmap%20result.png)

Started directory enumeration using gobuster , found admin panel.
![gobuster result](gobuster.png)

Admin page is login form for admin login.

![admin login page](admin%20login%20page.png)

---

## Bruteforcing 
Starting bruteforce attack on admin login page with hydra.

![admin page bruteforce](hydra%20admin%20bruteforce.png)

Loggin in as admin gave us John's RSA private key and web flag.

![web flag](web%20flag.png)

Here is RSA private key.

![RSA Private key](RSA%20Private%20key.png)

Getting hash from rsa key.

![ssh2john](../Wgel/ssh2john.png)

Cracking hash we got from rsa_id using john.

![John RSA_id cracking](john%20rsa-id%20cracking.png)

We got the passphrase for ssh login. Passphrase is "rockinroll".

---

## Login from SSH
Tried loggin in with rsa id but failed.

![Failed login](ssh%20failed%20login.png)

> Note : Rsa_id permission need to be set as read only. 
>[source](https://docs.rackspace.com/support/how-to/logging-in-with-an-ssh-private-key-on-linuxmac/)

Changing permission gave us ssh shell.

![ssh login](ssh%20login.png)

Got user flag.

![User flag](User%20flag.png)

Got the root flag by exploiting sudo priveleges for cat command.

![gtfobins cat](gtfobins%20cat.png)

![Root flag](root%20flag.png)

Although I got root flag , room demand us to brute force root password.
So I got contents of /etc/shadow and /etc/passwd to my machine. Unshadowed it and tried cracking root password. Surprisingly I got root password.

![root password cracking](root%20password%20cracking.png)

---

### Source
- [Tryhackme room](https://tryhackme.com/room/bruteit)