# h4ched
[Back to Tryhackme page](../index.md)

---

## pcapng analysis

- The attacker is trying to log into a specific service. What service is this?
**FTP**

- There is a very popular tool by Van Hauser which can be used to brute force a series of services. What is the name of this tool?
**hydra**

- The attacker is trying to log on with a specific username. What is the username?
**Jenny**

- What is the user's password?
**password123**

- What is the current FTP working directory after the attacker logged in?
**/var/www/html**

- The attacker uploaded a backdoor. What is the backdoor's filename?
**shell.php**

- The backdoor can be downloaded from a specific URL, as it is located inside the uploaded file. What is the full URL?
**http://pentestmonkey.net/tools/php-reverse-shell**

- Which command did the attacker manually execute after getting a reverse shell?
**whoami**

- What is the computer's hostname?
**wir3**

- Which command did the attacker execute to spawn a new TTY shell?
**python3 -c 'import pty; pty.spawn("/bin/bash")'**

- Which command was executed to gain a root shell?
**sudo su**

- The attacker downloaded something from GitHub. What is the name of the GitHub project?
**Reptile**

- The project can be used to install a stealthy backdoor on the system. It can be very hard to detect. What is this type of backdoor called?
**Rootkit**

---

## Recovering machine

### Enumeration

Let's try to get back machine!
Let's enumerate machine using Nmap.

![nmap scan](nmap%20scan.png)

There are 2 open ports i.e FTP and HTTP.

Let's try to login FTP by bruteforcing password.

---

### Bruteforcing

Let's try to bruteforce password using hydra.

![hydra bruteforcing](hydra%20bruteforcing.png)

So password for user jenny is now changed to 987654321.
Let's login into FTP and upload our reverse shell.

![FTP Php reverse shell](php%20reverse%20shell.png)

---

## Reverse shell
Let's get reverse shell.
Executing that file from HTTP link gives us reverse shell.
Let's try privilege escalation and get root flag.
We can switch to user jenny because we already bruteforced password for that account.

![root flag](h4ched%20root%20flag.png)

Got root flag!

---

## Source :
- [Tryhackme room](https://tryhackme.com/room/h4cked)
