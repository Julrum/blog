---
title: "OverTheWire.org Bandit Level 9 -> Level 10"
date: 2020-03-30T08:14:50Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "grep", strings"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit10.html](http://overthewire.org/wargames/bandit/bandit10.html)

  

# Bandit Level 9 → Level 10

## Level Goal

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, beginning with several ‘=’ characters.

## Commands you may need to solve this level

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

  

Level 9에서 Level 10으로 가려면 data.txt 파일을 열어 비밀번호를 확인해야한다.

여러개의 '=' 문자로 시작하며 사람이 읽을 수 있는 문자열로 저장되어있다고 한다.

  

ssh로 접속한 뒤 `grep` 명령어를 이용하여 확인해 보자

  

[![](https://4.bp.blogspot.com/-tHX97fDB9Ic/WWNQf_qkSzI/AAAAAAAAKrQ/wwU0G3upSTYGUkNCUZe7MEVYk505Uo_TwCLcBGAs/s640/bandit9_00.png)](https://4.bp.blogspot.com/-tHX97fDB9Ic/WWNQf_qkSzI/AAAAAAAAKrQ/wwU0G3upSTYGUkNCUZe7MEVYk505Uo_TwCLcBGAs/s1600/bandit9_00.png)

  
```bash
$ grep '==' data.txt
```
  

Binary file data.txt matches 라는 메세지가 뜬다.

이 메세지는 `grep` 하려는 대상 파일이 바이너리 파일일 경우 발생한다.

  

바이너리 파일을 `grep` 하는 방법은 두가지가 있다.

1. `grep` 명령어 옵션인 `-a` 를 사용하기

2. `strings` 명령어와 `grep` 명령어를 동시에 쓰기

  

두가지 모두 해보자

  

### 1. `grep -a` 이용하기

`grep -a` 옵션을 이용하면 바이너리 파일을 `grep` 할 수 있게 된다.

  

[![](https://4.bp.blogspot.com/-Q1y0efNLF68/WWNQf_RFt1I/AAAAAAAAKrU/Cx5TLDAnYcM7eEXNmKbcmnW3C8b9jvz7gCEwYBhgL/s640/bandit9_01.png)](https://4.bp.blogspot.com/-Q1y0efNLF68/WWNQf_RFt1I/AAAAAAAAKrU/Cx5TLDAnYcM7eEXNmKbcmnW3C8b9jvz7gCEwYBhgL/s1600/bandit9_01.png)

  
```bash
$ grep -a '==' data.txt
```
  

여전히 알아보기 힘들다.

  

### 2. strings 명령어와 grep 명령어를 동시에 사용하기

  

[![](https://2.bp.blogspot.com/-SWZD0OIWnbU/WWNQfwAVjQI/AAAAAAAAKrY/irbUD6CVVUQlxkBKgAO2-P5BFOwrV2dJwCEwYBhgL/s640/bandit9_02.png)](https://2.bp.blogspot.com/-SWZD0OIWnbU/WWNQfwAVjQI/AAAAAAAAKrY/irbUD6CVVUQlxkBKgAO2-P5BFOwrV2dJwCEwYBhgL/s1600/bandit9_02.png)

  
```bash
$ strings data.txt | grep '=='
```
  

`strings` 명령어를 쓰니 좀 더 깔끔하게 나왔다.

  

bandit10으로 가는 비밀번호를 알아 냈다.

truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk