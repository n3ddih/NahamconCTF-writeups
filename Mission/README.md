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
Scroll down a little then we can see a list of people and a flag 😸
