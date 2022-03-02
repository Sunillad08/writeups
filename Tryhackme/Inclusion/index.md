# Inclusion
[Back to Tryhackme Page](../index.md)

---

## Enumeration
Let's start enumerating machine with nmap. There are two open ports i.e SSH and HTTP.

![nmap scan](nmap%20scan.png)

Let's focus on HTTP first.

---

## LFI (Local File Inclusion)

Local File Inclusion is an attack technique in which attackers trick a web application into either running or exposing files on a web server. LFI attacks can expose sensitive information, and in severe cases, they can lead to cross-site scripting (XSS) and remote code execution. LFI is listed as one of the OWASP Top 10 web application vulnerabilities.
\- [Website](https://brightsec.com/blog/local-file-inclusion-lfi/)

So by changing PATH in 'article?name=$PATH' , we can change $PATH variable to any file. We can change directory and access anything.

So let's check /etc/shadow and /etc/passwd files first. So after trial and error guessing ../../etc/shadow is giving output.

URL : http://machine-ip/article?name=../../../etc/shadow

![etc shadow](etc%20shadow.png)

Shadow file has username and hashed password of falconfeast. 

URL : http://machine-ip/article?name=../../../etc/passwd

![etc passwd](etc%20passwd.png)

passwd file has clearly given password of falconfeast. Login into SSH using this password for user flag.

![etc passwd zoomed](etc%20passwd%20zoomed.png)

---

## Flags

Login into SSH and got user flag straight away!

![user flag](inclusion%20user%20flag.png)

Rather than doing privilege  escalation , I can just check it by changing file path for root flag. This could have been work for user flag too but file path was not clear for user flag.

URL : http://machine-ip/article?name=../../../root/root.txt

![root flag](inclusion%20root%20flag.png)

Easy LFI machine! :)

---

## Sources :
- [Inclusion room](https://tryhackme.com/room/inclusion)