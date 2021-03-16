# Forensics
Writeups for *Forensics* category 🕵️

## Parseltongue
File: [<ins>parseltongue</ins>](./files/parseltongue)

Using `file` command:
```
$ file parseltongue
parseltongue: python 3.8 byte-compiled
```
Searching on google I found out that this can be decompiled using [uncompyle6](https://pypi.org/project/uncompyle6/)
> uncompyle6 translates Python bytecode back into equivalent Python source code. It accepts bytecodes from Python version 1.0 to version 3.8

Nice! So now I will need to figure out how to use this

As in the document it said:
>Run: $ uncompyle6 *compiled-python-file-pyc-or-pyo*

I just need to add .pyc to `parseltongue` file
```
$ uncompyle6 parseltongue.pyc > parseltongue.py
```
>NOTE: You need to have python 3.8 to run this. If there's a problem just follow [this](https://linuxize.com/post/how-to-install-python-3-8-on-ubuntu-18-04/)

```
import Crypto.Util.number as l2b
import random
sszz = [
 'aposlogahs', 'apsle', 'Sine', 'aʃe', 'bei∫ed', 'tuif', 'Kura', 'Vera', 'pard', 'pardshesl', 'bo∫', 'Gara', 'vinth', 'Pelʃis', 'keilsing', 'khair', 'tikni', 'Bana', 'Slehara', 'koukh', 'kups', 'dai', 'Andi', 'dorʃe', 'doʃe', 'sloʃe', 'kaʃe', 'Sarna', 'Suu', 'giʃe', 'Gorna', 'ass-girou', 'dros', 'feslure', 'hasli', 'riʃan', 'fraeslis', 'vris', 'gatsi', 'runʃe', 'Tira', 'hishe', 'einʃe', 'hesleuf', 'Firna', 'Baʃ', 'ʃem', 'ai', 'ine', 'dinʃe', 'Negei', 'slanp', 'ʃena', 'sliʃe', 'dati', 'slifai', 'Kuine', 'Ha', 'nisl', 'ʃe', 'Sobne', 'bna', 'Sora', 'ovith', 'houk', 'parknent', 'fasar', 'nesha', 'praughs', 'Pura', 'ʃine', 'ʃane', 'gisan', 'rai∫e', 'kata', 'Ara', 'Nigi', 'akaʃe', 'rashe', 'slan', 'Derne', 'Tina', 'snart', 'gariʃe', 'kerashe', 'stabsle', 'Fasi', 'Peina', 'Tasi', 'Sekusi', 'Harne', 'kapi', 'Athne', 'vaʃe', 'asl', 'ʃik', 'agiro', 'vei', 'Asuna', 'Teʃ', 'Fiʃ', 'Doʃ', 'ʃira', 'Haʃ', 'Vuʃ', 'vindovth', 'Bira', 'Sa', 'Slu', 'ou', 'iangsteur']
zzss = b'\x07\x1c\x0e\x14\x17\n\x06\x03\x0cJ\x00@G\x0e\x017X\x0b\x04W\xf8\xb5\x03P\x06\x0f\x80\xea\x9b\x00\x05A\x16\\\x00.\x17\x0f'
s = False
z = True
ss = s & z
z = abs(ss) - abs(z)
zz = ss | z
z = zz - z - z
zz = z | z
z = zz << zz
s = ss >> ss
sz = s << z
zs = z << s
z = zs - sz
ss = str(z).replace(str(zs), str(ss).replace(str(ss), str(z).replace(str(z), '')))
sss = bytes(ss.join(sszz), 'utf-8')
zzz = bytes([_a ^ _b for _a, _b in zip(sss, zzss)])
ssszzz = bytes([_a ^ _b for _a, _b in zip(zzz, zzss)])
sss += b'S'
ssss = []
ss = sss[:len(sss) // 2]
zz = sss[len(sss) // 2:]
for s in range(len(ss)):
    ssss.append(ss[s] ^ zz[s])
else:
    if 5 == 1:
        print(' '.join([random.choice(sszz).upper() for _ in range(random.randrange(5, 10))]))
    else:
        print(' '.join([random.choice(sszz).upper() for _ in range(random.randrange(5, 10))]))
```

I tried understanding the code but it still too confusing to me 🤦

What I did was using `print()` to view every variables' value and eventually get the flag
```
b'\x07\x1c\x0e\x14\x17\n\x06\x03\x0cJ\x00@G\x0e\x017X\x0b\x04W\xf8\xb5\x03P\x06\x0f\x80\xea\x9b\x00\x05A\x16\\\x00.\x17\x0f'

b'aposlogahsapsleSinea\xca\x83ebei\xe2\x88\xabedtuifKuraVerapardpardsheslbo\xe2\x88\xabGaravinthPel\xca\x83iskeilsingkhairtikniBanaSleharakoukhkupsdaiAndidor\xca\x83edo\xca\x83eslo\xca\x83eka\xca\x83eSarnaSuugi\xca\x83eGornaass-giroudrosfeslurehasliri\xca\x83anfraeslisvrisgatsirun\xca\x83eTirahisheein\xca\x83ehesleufFirnaBa\xca\x83\xca\x83emaiinedin\xca\x83eNegeislanp\xca\x83enasli\xca\x83edatislifaiKuineHanisl\xca\x83eSobnebnaSoraovithhoukparknentfasarneshapraughsPura\xca\x83ine\xca\x83anegisanrai\xe2\x88\xabekataAraNigiaka\xca\x83erasheslanDerneTinasnartgari\xca\x83ekerashestabsleFasiPeinaTasiSekusiHarnekapiAthneva\xca\x83easl\xca\x83ikagiroveiAsunaTe\xca\x83Fi\xca\x83Do\xca\x83\xca\x83iraHa\xca\x83Vu\xca\x83vindovthBiraSaSluouiangsteur'

b'flag{eabd9a04bdd1ea626f2cfbb0ea5c5feb}'

b'aposlogahsapsleSinea\xca\x83ebei\xe2\x88\xabedtuifKur'
b'aposlogahsapsleSinea\xca\x83ebei\xe2\x88\xabedtuifKuraVerapardpardsheslbo\xe2\x88\xabGaravinthPel\xca\x83iskeilsingkhairtikniBanaSleharakoukhkupsdaiAndidor\xca\x83edo\xca\x83eslo\xca\x83eka\xca\x83eSarnaSuugi\xca\x83eGornaass-giroudrosfeslurehasliri\xca\x83anfraeslisvrisgatsirun\xca\x83eTirahisheein\xca\x83ehesleufFirnaBa\xca\x83\xca\x83emaiinedin\xca\x83eNegeislanp\xca\x83enasli\xca\x83edatislifaiKuineHanisl\xca\x83eSobnebnaSoraovithhoukparknentfasarneshapraughsPura\xca\x83ine\xca\x83anegisanrai\xe2\x88\xabekataAraNigiaka\xca\x83erasheslanDerneTinasnartgari\xca\x83ekerashestabsleFasiPeinaTasiSekusiHarnekapiAthneva\xca\x83easl\xca\x83ikagiroveiAsunaTe\xca\x83Fi\xca\x83Do\xca\x83\xca\x83iraHa\xca\x83Vu\xca\x83vindovthBiraSaSluouiangsteurS'
TIRA KAPI ƩIK FASI SNART APSLE
```
That was soo random and lucky also 🤡

## Henpeck
File: [<ins>henpeck.pcap</ins>](./files/henpeck.pcap)

Openning the file we can see USB protocol (I've seen many but a haven't done anything 😧)
![image](https://user-images.githubusercontent.com/80664686/111259056-c412bc80-8650-11eb-87d9-05d011512fd3.png)

After a while searching for writeups and documents I found the two most helpful
[this](https://abawazeeer.medium.com/kaizen-ctf-2018-reverse-engineer-usb-keystrok-from-pcap-file-2412351679f4) for some grasp on the challenge

and [this](https://ctftime.org/writeup/7293)

First we need to identify which packets to look at and filter it out

![image](https://user-images.githubusercontent.com/80664686/111259350-49966c80-8651-11eb-9cee-23f6f7364b24.png)

Next we need to figure out how to get the data out and output it to *data.txt*

```
$ tshark -r ./henpeck.pcap -Y 'frame.len == 72 && !(usb.capdata == 00:00:00:00:00:00:00:00)' -T fields -e usb.capdata > data.txt
0000160000000000
0000120000000000
00002c0000000000
0000170000000000
...
```
We need to have ":" between each byte. Ex: 00:00:00:00:00:00:00:00

You can do it manually or just use `sed` like below
```
$ cat data.txt | sed 's/../:&/g2' > data.txt
```

Then use the python script from the external link I left above to parse the data
```
usb_codes = {
    0x04:"aA", 0x05:"bB", 0x06:"cC", 0x07:"dD", 0x08:"eE", 0x09:"fF",
    0x0A:"gG", 0x0B:"hH", 0x0C:"iI", 0x0D:"jJ", 0x0E:"kK", 0x0F:"lL",
    0x10:"mM", 0x11:"nN", 0x12:"oO", 0x13:"pP", 0x14:"qQ", 0x15:"rR",
    0x16:"sS", 0x17:"tT", 0x18:"uU", 0x19:"vV", 0x1A:"wW", 0x1B:"xX",
    0x1C:"yY", 0x1D:"zZ", 0x1E:"1!", 0x1F:"2@", 0x20:"3#", 0x21:"4$",
    0x22:"5%", 0x23:"6^", 0x24:"7&", 0x25:"8*", 0x26:"9(", 0x27:"0)",
    0x2C:"  ", 0x2D:"-_", 0x2E:"=+", 0x2F:"[{", 0x30:"]}",  0x32:"#~",
    0x33:";:", 0x34:"'\"",  0x36:",<",  0x37:".>"
    }

lines = ["","","","",""]
        
pos = 0

for x in open("data.txt","r").readlines():
    code = int(x[6:8],16)
    
    if code == 0:
        continue
    # newline or down arrow - move down
    if code == 0x51 or code == 0x28:
        pos += 1
        continue
    # up arrow - move up
    if code == 0x52:
        pos -= 1
        continue

    # select the character based on the Shift key
    if int(x[0:2],16) == 2:
        lines[pos] += usb_codes[code][1]
    else:
        lines[pos] += usb_codes[code][0]
        
    
for x in lines:
    print x
```
Run the script and we have the flag 🎆
```
$ python script.py                                                                                             
so the answer is flag{f7733e0093b7d281dd0a30fcf34a9634} hahahah lol
c

```

## Typewriter
File: [<ins>typewriter.zip</ins>](https://drive.google.com/file/d/1aYkNCZmN3uj1UDrHDVeGvvw5yuQer0kd/view?usp=sharing)

Description:
```
A CONSTELLATIONS employee had his machine crash and he lost all his work. Thankfully IT managed to get a memory dump. Can you recover his work? 
```
Notable words are `memory dump`

The most common tool to analyze a memory dump is [volatility](https://github.com/volatilityfoundation/volatility/wiki/Volatility-Usage)

>For all the command references go [here](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference)</br>

If you're using Kali Linux you can install it by `apt install volatility`

First of all, I need to know what is the profile of the image using `imageinfo`
```
$ volatility -f ./image.bin imageinfo
Volatility Foundation Volatility Framework 2.6
INFO    : volatility.debug    : Determining profile based on KDBG search...
          Suggested Profile(s) : Win7SP1x86_23418, Win7SP0x86, Win7SP1x86_24000, Win7SP1x86
                     AS Layer1 : IA32PagedMemoryPae (Kernel AS)
                     AS Layer2 : FileAddressSpace (/mnt/f/CTF/nahamcon/forensics/typewriter/image.bin)
                      PAE type : PAE
                           DTB : 0x185000L
                          KDBG : 0x8293bde8L
          Number of Processors : 1
     Image Type (Service Pack) : 1
                KPCR for CPU 0 : 0x80b97000L
             KUSER_SHARED_DATA : 0xffdf0000L
           Image date and time : 2021-02-21 16:25:49 UTC+0000
     Image local date and time : 2021-02-21 08:25:49 -0800
```
The suggested profile has some results but I'm just gonna stick to the first one

After that, just scan for files in the image
```
$ volatility -f ./image.bin --profile=Win7SP1x86_23418 filescan
Volatility Foundation Volatility Framework 2.6
Offset(P)            #Ptr   #Hnd Access Name
------------------ ------ ------ ------ ----
0x0000000021f2ff80     15      0 RW-rwd \Device\HarddiskVolume1\$Mft
0x0000000022093598      3      1 R--rwd \Device\HarddiskVolume1\ProgramData\Microsoft\Diagnosis\Sideload
0x00000000222f60c0      1      0 RW-rwd \Device\HarddiskVolume1\$Directory
0x00000000222f61c0     16      0 R--r-d \Device\HarddiskVolume1\Windows\System32\drivers\atapi.sys
0x000000002248e160      4      0 R--r-d \Device\HarddiskVolume1\Windows\Fonts\msyi.ttf
0x000000002248e2e0      8      0 R--r-- \Device\HarddiskVolume1\Windows\System32\KBDUS.DLL
0x000000002248e7e0      5      0 R--r-d \Device\HarddiskVolume1\Windows\Fonts\taile.ttf
...
```
The result is *a lot* 😐
So lets just assume the flag might just gonna be in the *Desktop* or have the *.txt, docx, ...* extension. This time use `grep`
```
$ cat volatility/filescan.txt| grep -E "docx|txt"
0x000000007e615f80      8      0 -W---- \Device\HarddiskVolume1\Users\IEUser\Desktop\~$NFIDENTIAL DOCUMENT.docx
0x000000007e841f80      8      0 RW-r-- \Device\HarddiskVolume1\Users\IEUser\Desktop\CONFIDENTIAL DOCUMENT.docx
0x000000007e8e9178      1      1 -W-rw- \Device\HarddiskVolume1\Users\IEUser\AppData\Local\Temp\FXSAPIDebugLogFile.txt
0x000000007eb665b8      2      1 RW-r-- \Device\HarddiskVolume1\Users\IEUser\Desktop\CONFIDENTIAL DOCUMENT.docx
```
That `CONFIDENTIAL DOCUMENT.docx` looks kinda sus 🤔

Now just find a way to download the file
```
$ volatility -f ./image.bin --profile=Win7SP1x86_23418 dumpfiles -Q 0x000000007e841f80 -D .
Volatility Foundation Volatility Framework 2.6
DataSectionObject 0x7e841f80   None   \Device\HarddiskVolume1\Users\IEUser\Desktop\CONFIDENTIAL DOCUMENT.docx
SharedCacheMap 0x7e841f80   None   \Device\HarddiskVolume1\Users\IEUser\Desktop\CONFIDENTIAL DOCUMENT.docx
```
Finally just change the extension of the downloaded file to .docx and you're good to go
