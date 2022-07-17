# Bolt
[Back to Tryhackme page](../index.md)

---

## Enumeration
Let's start enumeration of machine using Nmap.

![namp scan](Nmap%20scan.png)

Port 8000 has alternate HTTP with Bolt CMS. Room specifically mentions to enumerate this port so let's focus on this.

---

## Bolt CMS
Let's explore all webpages first.

![Message to admin](bolt%20message%20to%20admin.png)

So there are one user named jake as admin with username bolt. 

![bolt message to IT](Bolt%20message%20to%20IT.png)

We got password of admin bolt , it is boltadmin123.

Let's login into portal which is located at /bolt/ directory as mentioned in documentation of Bolt CMS.

---

## RCE Exploit
Let's check Exploit-DB for [RCE](https://www.exploit-db.com/exploits/48296) exploit on Bolt CMS.

![exploitdb rce](exploit-db%20RCE.png)

We can setup metasploit for this CVE.
Let's just add necessary options in selected payload.
Got shell , let's find where flag.txt is located.

![bolt root flag](bolt%20root%20flag.png)

Got flag for bolt.

---

## Source
- [Tryhackme Bolt](https://tryhackme.com/room/bolt)
- [Exploit-DB RCE](https://www.exploit-db.com/exploits/48296)