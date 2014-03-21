The title of the problem was:

>Fig Wonders...? (200)

The level shows us a gif file (pic.gif). Running `strings` over it:

```
$ strings pic.gif 

GIF89aL
ep!ly%ny.u
am+&
h'&d
hkk&
Xs#t
]0}	
[~`l
sbSJl
mg-a
d(vL
m9kL
CI"HN
|%Mt
uT_r
key.txt
key.txt
```

So the key is hidden inside the file somewhere. Exiftool gets us nothing, so we 
tried unzipping the file instead:

```
$ unzip pic.gif

Archive:  pic.gif
warning [pic.gif]:  2351 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: key.txt                 
```

Key.txt contains the flag for the level.