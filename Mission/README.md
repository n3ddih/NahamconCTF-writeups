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
