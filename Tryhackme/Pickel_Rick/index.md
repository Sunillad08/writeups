# Pickel Rick 
[Back to Tryhackme page](../index.md)
- --
## Pickel Rick description
" This Rick and Morty themed challenge requires you to exploit a webserver to find 3 ingredients that will help Rick make his potion to transform himself back into a human from a pickle. "
Machine listed as Easy of tryhackme.com
- --
## First glance
Challenge requires to find 3 different flags.
- --
## Starting machine
On starting machine , first checked it on web browser if servers website.
Yes it indeed.
- --
## Nmap scan

![Nmap result](Nmap%20result.png)

- --
## Website

![website](website.png)

HTML content had username mentioned!
Then I checked robots.txt

![robot text](robot%20text.png)

- --
## SSH bruteforcing
Tried to ssh bruteforce but ssh service was not allowing login so ssh was dead end!
- --
## Directory enumeration
Tried directory enumeration using dirb but didn't got any interesting results
At this point , I tried random keywords such as login , admin , rick and many more
I checked for walkthrough then were he said login.php , which I clearly forgot to try.
- --
## Login bruteforcing
I tried login bruteforcing using hydra but it didn't give any result.
Then I tried robot.txt content as password which surprisingly worked.

![login](login.png)

- --
## Portal.php
After login , input box for command entry was provided.

![portal](portal.png)

- --
## Flag 1
Tried cat text file but it was blocked
Then I tried it as URL format and it worked

![flag1](flag1.png)

Did same for clue.

![clue](clue.png)
- --
## Flag 2
I was stuck at this point , as clue said to check for directories.
I kept doing directory enumeration with dirb.
After a point I felt like it was rabbit hole so I checked walkthrough again.
Clearly I didn't think to check my current directory.
I checked home folder as video said.

![flag2](flag2.png)
- --
## Flag 3
Walkthrough video also pointed out sudo was for everyone .
So found flag3

![flag3](flag3.png)

- --
## Lessons learnt
- Always write clues 
- Check for current directory with pwd
- Don't over complicate enumeration
- --
### Source
- [Tryhackme machine](https://tryhackme.com/room/picklerick)
- [Walkthrough video](https://youtu.be/buGpoedodiw)