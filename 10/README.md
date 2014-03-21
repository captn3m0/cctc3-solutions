This was an easier level than 9, but with a similar approach. The image is in this 
directory. The level title was 

>Hidden Objects (800)

The image file given to us was 70b6234f544af0132629aa6ec4be926dab59bb0b.png, with
the file name being sha1(l33t), making us think l33t conversion would be involved in
the level, but it turned out to be a red-herring.

`exiftool 70b6234f544af0132629aa6ec4be926dab59bb0b.png` gives us the following:

```
ExifTool Version Number         : 8.60
File Name                       : 70b6234f544af0132629aa6ec4be926dab59bb0b.png
Directory                       : .
File Size                       : 177 kB
File Modification Date/Time     : 2014:03:20 17:17:30+05:30
File Permissions                : rw-rw-r--
File Type                       : PNG
MIME Type                       : image/png
Image Width                     : 384
Image Height                    : 216
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Exif Byte Order                 : Little-endian (Intel, II)
Image Description               : http://manytools.org/
Thumbnail Offset                : 90
Thumbnail Length                : 4108
Image Size                      : 384x216
Thumbnail Image                 : (Binary data 4108 bytes, use -b option to extract)
```

We go to <http://manytools.org>, where we find a stego tool under the hacker tools section.
Running our image against that, we get the following:

`3030303030233030304f4f233030304f4f2330304f4f4f233030303030234f30303030233030304f4f23303030303023303030304f2330304f30234f3030303023304f23303030304f2330304f4f4f234f30303030234f30303023303030304f2330234f4f30303023304f23303030304f234f3030233030304f4f234f4f4f4f4f233030303030234f4f4f4f3023303030303023303030304f23303030304f234f30303030234f30303030234f303030233030303030234f4f4f4f30234f4f30303023304f234f30303030234f303030233030304f4f234f4f4f4f4f23303030303023304f234f30303030234f3030233030303030233030303030233030304f4f23304f4f4f4f233030303030234f4f4f4f3023303030303023303030304f234f30303030234f303030234f4f303030234f4f4f303023303030304f233023303030304f23303030304f23303030304f233030303030233030304f4f23303030304f23303030304f2330233030303030234f4f303030233030303030234f4f4f4f30233030304f4f234f4f4f4f4f23303030304f233023303030303023303030304f23303030304f233030303030233030304f4f23303030303023303030304f2330233030304f4f2330304f4f4f233030303030234f30303030234f30303030234f4f4f303023303030304f2330304f3023303030304f23303030304f23303030303023304f4f4f4f233030304f4f2330304f4f4f`

Converting this using xxd, we get:

`xxd -r -p message.txt step2.txt`

```
00000#000OO#000OO#00OOO#00000#O0000#000OO#00000#0000O#00O0#O0000#0O#0000O#00OOO#O0000#O000#0000O#0#OO000#0O#0000O#O00#000OO#OOOOO#00000#OOOO0#00000#0000O#0000O#O0000#O0000#O000#00000#OOOO0#OO000#0O#O0000#O000#000OO#OOOOO#00000#0O#O0000#O00#00000#00000#000OO#0OOOO#00000#OOOO0#00000#0000O#O0000#O000#OO000#OOO00#0000O#0#0000O#0000O#0000O#00000#000OO#0000O#0000O#0#00000#OO000#00000#OOOO0#000OO#OOOOO#0000O#0#00000#0000O#0000O#00000#000OO#00000#0000O#0#000OO#00OOO#00000#O0000#O0000#OOO00#0000O#00O0#0000O#0000O#00000#0OOOO#000OO#00OOO
```

After that I was stumped for a while. We tried converting this to base 3 among other
things but it didn't work. Finally, it stumped me to try morse code. Taking `0` as `.`, 
`#` as space, and `O` as `-`, we get:

```
..... ...-- ...-- ..--- ..... -.... ...-- ..... ....- ..-. -.... .- ....- ..--- -.... -... ....- . --... .- ....- -.. ...-- ----- ..... ----. ..... ....- ....- -.... -.... -... ..... ----. --... .- -.... -... ...-- ----- ..... .- -.... -.. ..... ..... ...-- .---- ..... ----. ..... ....- -.... -... --... ---.. ....- . ....- ....- ....- ..... ...-- ....- ....- . ..... --... ..... ----. ...-- ----- ....- . ..... ....- ....- ..... ...-- ..... ....- . ...-- ..--- ..... -.... -.... ---.. ....- ..-. ....- ....- ..... .---- ...-- ..---
```

Converting this using an online morse tool, we get:

`533256354f6a426b4e7a4d305954466b597a6b305a6d553159546b784e4445344e5759304e5445354e3256684f445132`

The fact that this was a hex string made me sure that we were on the right track.
After that it was, another use of xxd and base64 to get the answer:

`xxd -r -p step4.txt step5`

`S2V5OjBkNzM0YTFkYzk0ZmU1YTkxNDE4NWY0NTE5N2VhODQ2`

This looks like base64, lets try that:

`cat step5 |base64 -d`

This gives us the answer:

`Key:0d734a1dc94fe5a914185f45197ea846`
