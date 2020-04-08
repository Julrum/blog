---
title: "	
OverTheWire.org Bandit Level 1 -> Level 2"
date: 2020-03-30T08:09:37Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "cat"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit2.html](http://overthewire.org/wargames/bandit/bandit2.html)

# Bandit Level 1 → Level 2

## Level Goal

The password for the next level is stored in a file called **\-** located in the home directory

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`

## Helpful Reading Material

-   [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename)
-   [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](http://tldp.org/LDP/abs/html/special-chars.html)

  

Level 1에서 Level 2로 가기 위해서는 홈 디렉토리에 존재하는 '-' 의 이름을 가지는 파일을 열어 비밀번호를 찾는 것이다.

  

Level 0에서 Level 1로 갈 때와 마찬가지로 `ssh`에 접속한 후 `cat` 명령어를 사용하여 파일의 내용물을 확인하면 된다. 다만 앞과는 다르게 파일 이름이 특수문자이기 때문에 리눅스에서 제대로 인식이 안될 수 있으므로 폴더 경로를 절대 경로(`~/`)로 표현하여 파일로 인식시켜주어야 한다.

  

그러므로 `cat` 명령어를 이용하여 '-' 파일을 열어보자

  

[![](https://1.bp.blogspot.com/-OByYWAWTrDM/WWM6PQk4_yI/AAAAAAAAKpg/17P-WZjQjH00Qtleuly1GLe1RyJp9D1IgCLcBGAs/s640/bandit1_00.png)](https://1.bp.blogspot.com/-OByYWAWTrDM/WWM6PQk4_yI/AAAAAAAAKpg/17P-WZjQjH00Qtleuly1GLe1RyJp9D1IgCLcBGAs/s1600/bandit1_00.png)

  

  
```bash
$ cat ~/-
```
  

bandit2로 가는 비밀번호가 나왔다.

CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9