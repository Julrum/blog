---
title: "OverTheWire.org Bandit Level 2 -> Level 3"
date: 2020-03-30T08:11:46Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "cat"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit3.html](http://overthewire.org/wargames/bandit/bandit3.html)

  

# Bandit Level 2 → Level 3

## Level Goal

The password for the next level is stored in a file called **spaces in this filename** located in the home directory

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`

## Helpful Reading Material

-   [Google Search for “spaces in filename”](https://www.google.com/search?q=spaces+in+filename)

  

Level 2에서 Level 3으로 가기 위해서는 홈 디렉토리에 있는 'spaces in this filename'이라는 이름을 가진 파일을 열어야 한다.

  

`ssh`에 접속한 후 `cat` 명령어를 사용하여 파일의 내용물을 확인하면 된다. 하지만 이 파일이름에는 공백이 포함되어있으므로

  

[![](https://1.bp.blogspot.com/-bc7TvY1hDX8/WWM7bxcF4EI/AAAAAAAAKpo/MdVbYQnBcrULCpK1PZf2BCCpR6-c4LuKACEwYBhgL/s640/bandit2_00.png)](https://1.bp.blogspot.com/-bc7TvY1hDX8/WWM7bxcF4EI/AAAAAAAAKpo/MdVbYQnBcrULCpK1PZf2BCCpR6-c4LuKACEwYBhgL/s1600/bandit2_00.png)

  
```bash
$ cat spaces in this filename
```
  

을 입력하면 리눅스는 'spaces', 'in', 'this', 'filename' 이라는 5개의 파일을 찾게 될 것이다.

  

이 문제를 해결하기 위해서는 'spaces in this filename'이라는 이름을 하나의 파일의 이름으로 인식시켜주어야 한다. 그러기 위해서는 `""`을 이용하면 된다.

  
```bash
$ cat "spaces in this filename"
```
이라고 입력하면 해결할 수 있다.

  

[![](https://3.bp.blogspot.com/-lTZzJa8wGKY/WWNJTJnVAtI/AAAAAAAAKqE/LVu49p5hi2AxGeDujO2oZU0sV3R2Z3ciACLcBGAs/s640/bandit2_01.png)](https://3.bp.blogspot.com/-lTZzJa8wGKY/WWNJTJnVAtI/AAAAAAAAKqE/LVu49p5hi2AxGeDujO2oZU0sV3R2Z3ciACLcBGAs/s1600/bandit2_01.png)

  

bandit3의 비밀번호를 확인했다.

  

UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK