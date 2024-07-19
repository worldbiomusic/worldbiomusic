# 설명
다른 프로그램, 프로토콜, 데이터 구조 등등 과 구별하기 위한 식별 코드

# 참고
- 설명 좋음: https://bitcoin.stackexchange.com/a/43191
```
The magic number is not something specific to bitcoin.

Magic numbers are used in computer science for both files and protocols. They identify the type of the file/data structure. A program receiving such a file/data structure can check the magic number and immediately know the supposed type of that file/data structure.

This is what the Unix/Linux command file uses to quickly identify the type of file. It only requires to check only the first bytes of a file to determine its (supposed) type. A list of files and their magic numbers can be found here.

Protocols like bitcoin use data structures to talk to each other (e.g. propagating blocks through the network). Nodes check the first bytes to identify the type of data structure.

Another use of magic numbers is that you can check the type of the file or data structure on a text editor. E.g. while a png image is binary if you open it with a text editor you will notice that it starts with .PNG..... Another example, the SMB protocol replies start with FFSMB. Note, however, that this is not always the case.

Other files/structures have magic numbers that do not make much sense; they may be some geeky code or inside joke of the developers that chose it.

So that is what it is used for. As far as I can tell 0xD9B4BEF9 is quite arbitrary... but maybe there is some meaning for its creator
```
