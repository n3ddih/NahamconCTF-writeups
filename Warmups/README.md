# Warmups
Writeups for *warmups* category

## Veebee
File: [<ins>veebee.vbe</ins>](./files/veebee.vbe)

If you use window just run the program

![image](https://user-images.githubusercontent.com/80664686/111112180-4ab49480-8592-11eb-945f-53de84f53ef0.png)
>I don't know how to run it on Linux though

## Chicken Wings
File: [<ins>chicken_wings</ins>](./files/chicken_wings)

Content:
```
♐●♋♑❀♏📁🖮🖲📂♍♏⌛🖰♐🖮📂🖰📂🖰🖰♍📁🗏🖮🖰♌📂♍📁♋🗏♌♎♍🖲♏❝
```

Copy this string to google I found that this is **wingding font**. Using a *winding translator* online to get the flag:
```
flag{e0791ce68f718188c0378b1c0a3bdc9e}
```

## Buzz
File: [<ins>buzz</ins>](./files/buzz)

Using `file` command:
```
$ file buzz
buzz: compress'd data 16 bits
```
After searching on google, I found out that the file extension is .z, then using command `uncompress` to uncompress to file
```
$ mv buzz buzz.z
$ uncompress buzz.z
$ cat buzz
flag{b3a33db7ba04c4c9052ea06d9ff17869}
```

## Pollex
File: [<ins>pollex</ins>](./files/pollex)

Using `file` command:
```
$ file pollex
pollex: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, Exif Standard: [TIFF image data, little-endian, direntries=5, description=Man giving thumb up on dark black background., software=Google], baseline, precision 8, 424x283, components 3
```

Using `exiftool`:
```
$ exiftool pollex                                                                                           
ExifTool Version Number         : 12.16
File Name                       : pollex
Directory                       : .
File Size                       : 37 KiB
File Modification Date/Time     : 2021:03:13 12:25:47+07:00
File Access Date/Time           : 2021:03:15 13:46:26+07:00
File Inode Change Date/Time     : 2021:03:13 12:26:08+07:00
File Permissions                : rwxrwxrwx
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Exif Byte Order                 : Little-endian (Intel, II)
Image Description               : Man giving thumb up on dark black background.
Software                        : Google
Artist                          : Stevanovic Igor
Copyright                       : (C)2013 Stevanovic Igor, all rights reserved
Exif Version                    : 0220
Color Space                     : sRGB
Interoperability Index          : R98 - DCF basic file (sRGB)
Interoperability Version        : 0100
Compression                     : JPEG (old-style)
Thumbnail Offset                : 334
Thumbnail Length                : 26693
XMP Toolkit                     : XMP Core 4.4.0-Exiv2
Creator Tool                    : Google
Description                     : Man giving thumb up on dark black background.
Rights                          : (C)2013 Stevanovic Igor, all rights reserved
Creator                         : Stevanovic Igor
Current IPTC Digest             : c7c2ff906c74de09234ddcb2c831803b
Envelope Record Version         : 4
Coded Character Set             : UTF8
Application Record Version      : 4
By-line                         : Stevanovic Igor
Credit                          : igor - Fotolia
Copyright Notice                : (C)2013 Stevanovic Igor, all rights reserved
Caption-Abstract                : Man giving thumb up on dark black background.
IPTC Digest                     : c7c2ff906c74de09234ddcb2c831803b
Image Width                     : 424
Image Height                    : 283
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 424x283
Megapixels                      : 0.120
Thumbnail Image                 : (Binary data 26693 bytes, use -b option to extract)
```

The last line showed that there is a *Thumbnail Image* inside

Then I found the way to *extract thumbnail image* in the [*exiftool manual*](https://exiftool.org/exiftool_pod.html)

```
$ exiftool pollex -b -ThumbnailImage > thumbnail.jpg
```

The output image show the flag:

![thumbnail](https://user-images.githubusercontent.com/80664686/111123908-78a1d500-85a2-11eb-979d-576d71c2f422.jpg)

## Shoelaces

![shoelaces](https://user-images.githubusercontent.com/80664686/111125122-d97ddd00-85a3-11eb-9234-464f20039cf0.jpg)

After seeing the *challenge name* and the *image* we can guess it's about `strings` command:

```
$ strings shoelaces.jpg | grep flag                                                                             
flag{137288e960a3ae9b148e8a7db16a69b0}
```

## esab64

Content:
```
mxWYntnZiVjMxEjY0kDOhZWZ4cjYxIGZwQmY2ATMxEzNlFjNl13X
```
esab is the reverse string of base so this challange is about *base64* and *reverse string*
```
$ cat esab64 | rev | base64 -d | rev
flag{fb5211b498afe87b1bd0db601117e16e}_
```
> The `rev` command is to revese a string, `base64 -d` is to decode a base64 encoded string </br>
> If you have trouble just go through every '|' to have a better grasp

## Eight Circle
File: [<ins>eighth_circle</ins>](./files/eighth_circle)

The file content seems like a mess here @@
```
$ cat eighth_circle
D'`r#LK\[}{{EUUTet,r*qo'nmlk5ihVB0S!>w<<)9xqYonsrqj0hPlkdcb(`Hd]#a`_A@VzZY;Qu8NMRQJn1MLKJCg*)ED=a$:?>7[;:981w/4-,P*p(L,%*)"!~}CB"!~}_uzs9wpotsrqj0Qmfkdcba'H^]\[Z~^W?[TSRWPt7MLKo2NMFj-IHG@dD&<;@?>76Z{9276/.R21q/.-&J*j(!E%$d"y?`_{ts9qpon4lTjohg-eMihg`&^cb[!_X@VzZ<RWVOTSLpP2HMFEDhBAFE>=BA:^8=6;:981Uvu-,10/(Lm%*)(!~D1
```
After some searching, I found out that the challenge related to Malbodge
>Malbolge is a public domain esoteric programming language invented by Ben Olmstead in 1998, named after the <ins>eighth circle of hell</ins> in Dante's Inferno, the Malebolge

You can easily find a [*Malbolge Interpreter online*](http://malbolge.doleczek.pl/) to view the content

![image](https://user-images.githubusercontent.com/80664686/111242633-260ff980-8632-11eb-924b-21a1f295dc6e.png)

## Car keys

Description:
```
We found this note on someone's key chain! It reads... ygqa{6y980e0101e8qq361977eqe06508q3rt}? There was another key that was engraved with the word QWERTY, too...
```

Haven't got the solution yet but you still can read [here](https://github.com/xnomas/Nahamcon-2021-Writeups/tree/main/The_warmups)
