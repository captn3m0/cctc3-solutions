>Bin Ladden (400)

The level gave is a VB-created binary file, that on running asks for a SECRET TEXT.
It was a upx created binary, so we unpacked it using the `upx -d` command on Windows.

```
upx -d Bin.exe 
                       Ultimate Packer for eXecutables
                          Copyright (C) 1996 - 2013
UPX 3.91        Markus Oberhumer, Laszlo Molnar & John Reiser   Sep 30th 2013

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
     20480 <-      8192   40.00%    win32/pe     Bin.exe

Unpacked 1 file.
```

Opening this file in Resource hacker gave us the following string:

![Screenshot of resource hacker](http://i.imgur.com/zq1mIWS.png)

```
%4c%69%30%75%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%53%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%34%75%59%43%30%74%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%75%4c%6d%41%74%4c%69%35%67%4c%69%34%74%4c%6d%41%75%4c%53%35%67%4c%53%34%74%59%43%34%74%4c%69%35%67%4c%69%30%74%59%43%30%75%59%43%30%74%4c%6d%41%75%4c%69%35%67%4c%53%35%67%4c%69%34%75%4c%57%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%31%67%4c%6d%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%35%67%4c%53%30%75%4c%57%41%74%4c%6d%41%74%4c%69%30%75%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%74%4c%57%41%75%4c%69%30%75%59%43%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%69%30%74%59%43%30%75%4c%53%35%67%4c%53%34%74%59%43%34%75%4c%6d%41%74%4c%6d%41%74%4c%69%31%67%4c%53%31%67%4c%69%34%75%59%43%30%75%4c%6d%41%74%4c%69%31%67%4c%69%34%74%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%53%30%3d%4c%69%30%75%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%53%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%34%75%59%43%30%74%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%75%4c%6d%41%74%4c%69%35%67%4c%69%34%74%4c%6d%41%75%4c%53%35%67%4c%53%34%74%59%43%34%74%4c%69%35%67%4c%69%30%74%59%43%30%75%59%43%30%74%4c%6d%41%75%4c%69%35%67%4c%53%35%67%4c%69%34%75%4c%57%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%31%67%4c%6d%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%35%67%4c%53%30%75%4c%57%41%74%4c%6d%41%74%4c%69%30%75%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%74%4c%57%41%75%4c%69%30%75%59%43%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%69%30%74%59%43%30%75%4c%53%35%67%4c%53%34%74%59%43%34%75%4c%6d%41%74%4c%6d%41%74%4c%69%31%67%4c%53%31%67%4c%69%34%75%59%43%30%75%4c%6d%41%74%4c%69%31%67%4c%69%34%74%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%53%30%3d
```

Running unescape over it:

```js
unescape("%4c%69%30%75%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%53%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%34%75%59%43%30%74%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%75%4c%6d%41%74%4c%69%35%67%4c%69%34%74%4c%6d%41%75%4c%53%35%67%4c%53%34%74%59%43%34%74%4c%69%35%67%4c%69%30%74%59%43%30%75%59%43%30%74%4c%6d%41%75%4c%69%35%67%4c%53%35%67%4c%69%34%75%4c%57%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%31%67%4c%6d%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%35%67%4c%53%30%75%4c%57%41%74%4c%6d%41%74%4c%69%30%75%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%74%4c%57%41%75%4c%69%30%75%59%43%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%69%30%74%59%43%30%75%4c%53%35%67%4c%53%34%74%59%43%34%75%4c%6d%41%74%4c%6d%41%74%4c%69%31%67%4c%53%31%67%4c%69%34%75%59%43%30%75%4c%6d%41%74%4c%69%31%67%4c%69%34%74%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%53%30%3d%4c%69%30%75%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%53%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%34%75%59%43%30%74%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%75%4c%6d%41%74%4c%69%35%67%4c%69%34%74%4c%6d%41%75%4c%53%35%67%4c%53%34%74%59%43%34%74%4c%69%35%67%4c%69%30%74%59%43%30%75%59%43%30%74%4c%6d%41%75%4c%69%35%67%4c%53%35%67%4c%69%34%75%4c%57%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%31%67%4c%6d%41%74%4c%69%31%67%4c%69%30%74%4c%57%41%75%4c%53%35%67%4c%53%30%75%4c%57%41%74%4c%6d%41%74%4c%69%30%75%59%43%34%75%4c%6d%41%74%4c%69%35%67%4c%69%30%74%4c%57%41%75%4c%69%30%75%59%43%30%75%4c%57%41%75%4c%53%31%67%4c%6d%41%75%4c%53%35%67%4c%69%34%74%4c%6d%41%74%4c%69%31%67%4c%69%30%74%59%43%30%75%4c%53%35%67%4c%53%34%74%59%43%34%75%4c%6d%41%74%4c%6d%41%74%4c%69%31%67%4c%53%31%67%4c%69%34%75%59%43%30%75%4c%6d%41%74%4c%69%31%67%4c%69%34%74%4c%6d%41%75%4c%69%35%67%4c%53%34%75%59%43%34%74%4c%69%35%67%4c%53%30%3d")
```

We get:

```
Li0uLmAuLi5gLS4uYC4tLi5gLi4tLmAtLi1gLS0uLWAuLS1gLmAuLS4uYC0tYC4uLmAtLi5gLi0uLmAtLi5gLi4tLmAuLS5gLS4tYC4tLi5gLi0tYC0uYC0tLmAuLi5gLS5gLi4uLWAtLi1gLi0tLWAuLS1gLmAtLi1gLi0tLWAuLS5gLS0uLWAtLmAtLi0uYC4uLmAtLi5gLi0tLWAuLi0uYC0uLWAuLS1gLmAuLS5gLi4tLmAtLi1gLi0tYC0uLS5gLS4tYC4uLmAtLmAtLi1gLS1gLi4uYC0uLmAtLi1gLi4tLmAuLi5gLS4uYC4tLi5gLS0=Li0uLmAuLi5gLS4uYC4tLi5gLi4tLmAtLi1gLS0uLWAuLS1gLmAuLS4uYC0tYC4uLmAtLi5gLi0uLmAtLi5gLi4tLmAuLS5gLS4tYC4tLi5gLi0tYC0uYC0tLmAuLi5gLS5gLi4uLWAtLi1gLi0tLWAuLS1gLmAtLi1gLi0tLWAuLS5gLS0uLWAtLmAtLi0uYC4uLmAtLi5gLi0tLWAuLi0uYC0uLWAuLS1gLmAuLS5gLi4tLmAtLi1gLi0tYC0uLS5gLS4tYC4uLmAtLmAtLi1gLS1gLi4uYC0uLmAtLi1gLi4tLmAuLi5gLS4uYC4tLi5gLS0=
```
Clearly, base64.

`cat step2.txt | base64 -d > step3.txt`

```
.-.. ... -.. .-.. ..-. -.- --.- .-- . .-.. -- ... -.. .-.. -.. ..-. .-. -.- .-.. .-- -. --. ... -. ...- -.- .--- .-- . -.- .--- .-. --.- -. -.-. ... -.. .--- ..-. -.- .-- . .-. ..-. -.- .-- -.-. -.- ... -. -.- -- ... -.. -.- ..-. ... -.. .-.. --.-.. ... -.. .-.. ..-. -.- --.- .-- . .-.. -- ... -.. .-.. -.. ..-. .-. -.- .-.. .-- -. --. ... -. ...- -.- .--- .-- . -.- .--- .-. --.- -. -.-. ... -.. .--- ..-. -.- .-- . .-. ..-. -.- .-- -.-. -.- ... -. -.- -- ... -.. -.- ..-. ... -.. .-.. --
```

Looks like morse code (after replacing ` with spaces). Converting using an online tool gives us:

`LSDLFKQWELMSDLDFRKLWNGSNVKJWEKJRQNCSDJFKWERFKWCKSNKMSDKFSDLM`

Entering this as secret text in the Bin.exe program:

![Screenshot of flag](http://i.imgur.com/bAepgKF.png)

We get the flag. Unfortunately, we had to type it by hand because copy doesn't work in dialog boxes.

`444e873497c2f189587befa6ccb2636ca6585517cef23eb8152fca0f09f4035`.