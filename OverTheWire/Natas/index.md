# Natas
[Back to Index page](../index.md)

---

**Natas teaches the basics of serverside web-security.**

---

## Natas 0
> Username : natas0
> Password  : natas0

Checking source html of website gives us password fro next level.

![natas0](natas%200.png)

---

## Natas 1
> Username : natas1
> Password  : gtVrDuiDfck831PqWsLEZy5gyDz1clto

Right clicking is disabled but we can do view-source and easily get password.

![natas1](natas%201.png)

---

## Natas 2
> Username : natas2
> password  : ZluruAthQk7Q2MqmDeTiUij2ZvWy2mBi

There is no content on website but rather one pixel image embedded. Which has path of files/pixel.png . Checking files we get file called users.txt .

![natas 2](natas%202.png)

---

## Natas 3
> Username : natas3
> Password  : sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14

Even google can't find it so it's clear google is disallowed so checking robots.txt gives us path to secret directory. Got user.txt file there and it has password for level 4.

![natas 3 1](natas%203%201.png)

![natas 3 2](natas%203%202.png)

![natas 3 3](natas%203%203.png)

---

## Natas 4
> Username : natas4
> Password  : Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ

Only authorized referrer was allowed so added burpsuite proxy and changed referrer to said site. Got password for next level.

![natas 4 1](natas%204%201.png)

![natas 4 2](natas%204%202.png)

![natas 4 3](natas%204%203.png)

---

## Natas 5
> Username : natas5
> Password  : iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq 

Checking cookie section clearly shows loggedin value as 0 so changing cookie value gives us password to next level.

![natas 5 1](natas%205%201.png)

![natas 5 2](natas%205%202.png)

---

## Natas 6
> Username : natas6
> Password  : aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1

We check source code to follow where input is passed , we find that secret key is called from file called includes/secret.inc.  Checking that file gives us value for secret key. We got password for next level.

![natas 6 1](natas%206%201.png)

![natas 6 2](natas%206%202.png)

![natas 6 3](natas%206%203.png)

![natas 6 4](natas%206%204.png)

---

## Natas 7
> Username : natas7
> Password  : 7z3hEENjQtflzgnT29q7wAvMNfZdh0i9

As we can see , page?=PATH is how files are called here. Simple Local File Inclusion(LFI) challenge.

![natas 7 1](natas%207%201.png)

![natas 7 2](natas%207%202.png)

---

## Natas 8
> Username : natas8
> Password  : DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe 

Checking page source , we can see our input in going through process and checked to encoded secret. We can just reverse the process applied on input on encoded secret key and get secret input.

![natas 8 1](natas%208%201.png)

![natas 8 2](natas%208%202.png)

![natas 8 3](natas%208%203.png)

---

## Natas 9
> Username : natas9
> Password  : W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl

We can see that passthru function passes our input. We can add "; cat /etc/natas_webpass/natas10 ;" as input and get password for next level.

![natas 9 1](natas%209%201.png)

![natas 9 2](natas%209%202.png)

---

## Natas 10
> Username : natas10
> Password  : nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu

Similar task as last challenge but now input's are checked before passing them to passthru function. Although little challenging to find exploit , rather than entering it as seperate command , we can simply pass our file as another file to check in grep alongside dictionary.txt.

Manipulated command : grep -i **. /etc/natas_webpass/natas11** dictionary.txt

![natas10 1](natas%2010%201.png)

![natas11 2](natas%2010%202.png)

---

## Natas 11
> Username : natas11
> Password  : U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK