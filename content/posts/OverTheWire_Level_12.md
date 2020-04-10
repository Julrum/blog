---
title: "OverTheWire.org Bandit Level 11 -> Level 12"
date: 2020-04-10T13:42:33Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "Rot13", "tr"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit12.html](http://overthewire.org/wargames/bandit/bandit12.html)

# Bandit Level 11 → Level 12

## Level Goal

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Commands you may need to solve this level

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

## Helpful Reading Material

-   [Rot13 on Wikipedia](http://en.wikipedia.org/wiki/Rot13)

Level 11에서 Level 12로 가기 위해 data.txt 파일 안에 있는 비밀번호를 찾아야 한다. data.txt 안에 소문자 (a-z)와 대문자 (A-Z)문자는 13 위치만큼 회전되어 있다고 한다.

  

ssh에 접속한 다음에 명령어 `ls`로 어떤 파일이 존재하는지 확인해 본다.
```bash
$ ls
```
  

[![](https://1.bp.blogspot.com/-bLyoi7iI344/WWXax0khkcI/AAAAAAAAKtM/QGarZJt-7_Mhal00novc8QYe9h-PBgNSgCEwYBhgL/s640/bandit11_00.png)](https://1.bp.blogspot.com/-bLyoi7iI344/WWXax0khkcI/AAAAAAAAKtM/QGarZJt-7_Mhal00novc8QYe9h-PBgNSgCEwYBhgL/s1600/bandit11_00.png)

  

data.txt가 홈 디렉토리에 존재하는 것을 확인할 수 있다.

명령어 `cat`을 이용하여 파일 안을 살펴보자.
```bash
$ cat data.txt
```
  

[![](https://4.bp.blogspot.com/-fz8hfykn19I/WWXax3n3uZI/AAAAAAAAKtQ/tgrpTfyxDLcJ9XUAX8R9P3dTYqd6XWnVACEwYBhgL/s640/bandit11_01.png)](https://4.bp.blogspot.com/-fz8hfykn19I/WWXax3n3uZI/AAAAAAAAKtQ/tgrpTfyxDLcJ9XUAX8R9P3dTYqd6XWnVACEwYBhgL/s1600/bandit11_01.png)

  

ROT13으로 암호화 되어있는 문장을 발견할 수 있다.

  

### ROT13이란?

ROT13은 1980년대 초반의 net.jokes 뉴스그룹에서 유래하였다. 원래 목적은 보기에 따라서 모욕적일 수 있는 내용이나, 유머에서 가장 중요한 마지막 줄들을 실수로 미리 보는 일이 없도록 하려는 것이었다. 처음에는 모욕적인 농담을 다른 뉴스그룹에 올려서 분류하려 하기도 했으나, 관리자들은 그런 뉴스그룹을 만드는 것이 마치 어떤 모욕적인 내용이라도 해당 그룹에 올리면 문제가 없다는 식으로 보일 수 있다는 이유로 이를 반대했다. ROT13은 그 단순함 때문에 이런 용도에 알맞았다.
  

ROT13은 영어 알파벳을 다른 영어 알파벳으로 치환만 하기 때문에, 알파벳 이외의 일반적이지 않은 문자를 처리하지 못하는 뉴스리더에서도 문제를 발생시키지 않았따. ROT13은 영어에서 가능한 25가지의 카이사르 암호(ROT-1부터 ROT-25까지) 중에서 암호화와 복호화가 같은 유일한 방법이었기 때문에 선택되었다. (만약 영어 알파벳이 26자가 아니라, 폴란드어같이 더 많거나 하와이어같이 더 적었다면 다른 방법이 선택되었을 것이다.)
  

손으로 메시지를 암호화하고 복호화할 수도 있지만, 자동으로 암호화나 복호화를 해 주는 것이 더 편리하다. 예를 들어 ROT13이 만들어진 지 얼마 안 있어 뉴스리더 소프트웨어들은 자동으로 복호화하는 기능을 지원하였으며, 유닉스 계열 시스템들은 tr(transliterate의 약자)이라는 표준 유틸리티를 지원하기 때문에 다음과 같은 방법으로 ROT13 암호화 및 복호화를 할 수 있다.

  
ex)
```bash
$ echo "Or fher gb qevax lbhe Binyqvar" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
```bash
$ Be sure to drink your Ovaltine
```
  

위에 나온 방법으로 이 문제도 해결하면 된다.

  

[![](https://4.bp.blogspot.com/-DL7c_9ten-4/WWXaxzivKjI/AAAAAAAAKtU/JdI2B4t6mUYu2TiE0_D1iYRmvndbYzSFACEwYBhgL/s640/bandit11_02.png)](https://4.bp.blogspot.com/-DL7c_9ten-4/WWXaxzivKjI/AAAAAAAAKtU/JdI2B4t6mUYu2TiE0_D1iYRmvndbYzSFACEwYBhgL/s1600/bandit11_02.png)

  
```bash
$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
  

비밀번호는 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu 이다.