# Mission

Writeups for category `Misson` 💥</br>
Page: [constellations.page](https://constellations.page/)

## Bionic
Locate the [robots.txt](https://en.wikipedia.org/wiki/Robots_exclusion_standard) file
```
User-agent: *
Disallow: /meet-the-team.html

flag{33b5240485dda77430d3de22996297a1}  # this flag is for `Bionic`
```

## Meet The Team
Description:
```
Recover the list of employees working at CONSTELLATIONS.
HINT: "Can we please stop sharing our version control software out on our website?"
```

After inspecting the [list of version control softwares](https://en.wikipedia.org/wiki/List_of_version-control_software) I saw git. So the `.git` folder might be on the web

Visiting https://constellations.page/.git/ returns a permission denied page
![image](https://user-images.githubusercontent.com/80664686/111409762-2976b400-870a-11eb-9862-e7876f90111f.png)

We can use [GitTools](https://github.com/internetwache/GitTools) to expoit it

Firstly, let's use `dumper` module
>This tool can be used to download as much as possible from the found .git repository from webservers which do not have directory listing enabled.

```
$ mper.sh https://constellations.page/.git/ .
```
At this point if you have visited `meet-the-team.html` file, there's a message said that:
>...our team has decided to no longer publicize employee names and info
Does that means it used to be pubicized? 🤔 And I should roll back the previous commit to view its content?

Using `$ git log`
```
commit e7d4663ac6b436f95684c8bfc428cef0d7731455 (HEAD)
Author: Leo Rison <leo.rison@constellations.page>
Date:   Tue Feb 23 19:20:14 2021 -0500

    Management said I need to remove the team details so I redacted that page and added it to robots.txt

commit 4c88ac1c56fe228267cf415c3ef87d7c3b8abd60
Author: Leo Rison <leo.rison@constellations.page>
Date:   Tue Feb 23 19:19:32 2021 -0500

    Added the Meet The Team page

commit 1142cc3145fdba8d9eb8f9c9e7ee79bdfda64d9a
Author: Leo Rison <leo.rison@constellations.page>
Date:   Tue Feb 23 18:53:50 2021 -0500

    Added initial assets and landing page
```
The target here is when it first added the *Meet the team page*

Just use `git show`:
```
$ git show 4c88ac1c56fe228267cf415c3ef87d7c3b8abd60
```
Scroll down a little then we can see a list of people with a flag 😸

## Gus

At the end of the website there's a link to Github 

![image](https://user-images.githubusercontent.com/80664686/111432069-217d3b00-872f-11eb-8e72-e54e78feaf77.png)

There's nothing there but 1 person in people tab, which is the person we are looking for *Gus Rodry*

Just tinkering around with the most recent update repo and you'll get the flag
```
# NOTE:
# This flag submits for the `Gus` challenge you should see after solving `Meet The Team`, after you solve `Bionic`

flag{84d5cc7e162895fa0a5834f1efdd0b32}
```
>NOTE: there's a *id_rsa* file, which might be used for remote ssh connection in the future

## Hercules

In the *followers* list of Gus there is a person name *HerculesScox*

Tinkering around will give you the flag too 🤪
> NOTE: there's a possible credential:</br>hercules:starstruckherc

## Lyra

From the previous challenge `Meet The Team` we know that full name of Lyra is *Lyra Patte*

Searching the name on Twitter give us an account: https://twitter.com/LyraPatte

![image](https://user-images.githubusercontent.com/80664686/111471745-cca3e980-875b-11eb-8043-9608ca8df47e.png)

There's one specific post of the user that has a link to the *constellations* website

https://constellations.page/constellations-documents/1/

There's a number in the URL so we're gonna try to change it to see if it gives something else.

Just some ordinary stuffs until it hits 5

![image](https://user-images.githubusercontent.com/80664686/111473419-99faf080-875d-11eb-8f93-124a28846bd2.png)

>This action relate to a vulnerability called [IDOR](https://portswigger.net/web-security/access-control/idor)

Seem like that's the flag of Lyra 🥳

>NOTE: The list might be useful since its about default password. Better save it of later. Just make 2 files: one contains username and other has password.

## Orion

Just the same as Lyra, we can find the account of *Orion*

https://twitter.com/OrionMorra

![image](https://user-images.githubusercontent.com/80664686/111494798-5ca05e00-8771-11eb-8940-db9906f6bdea.png)

There's also a post that show the flag directly

>NOTE: a possible credentials:</br>orion:start4love4life

## Leo

Searching on Twitter doesn't get anything (or 1 person but it's not right)

Putting the full name `Leo Rison` to google and found an instagram account: https://www.instagram.com/_leorison/

![image](https://user-images.githubusercontent.com/80664686/111496028-8017d880-8772-11eb-89cb-6fcc1e64c6ec.png)

Every post here are just memes about [vim](https://en.wikipedia.org/wiki/Vim_(text_editor)). Except for 1 QR code, scanning the code we get:
```
flag{636db5f4f0e36908a4f1a4edc5b0676e}

A password for Leo is constelleorising
```
There are our flag 🥂

>NOTE: possible credential:</br>leo:constelleorising
