---
title: "OverTheWire.org Bandit Level 6 -> Level 7"
date: 2020-03-30T08:14:43Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "find", "dev/null", "redirection"]
cover: ""
---
[http://overthewire.org/wargames/bandit/bandit7.html](http://overthewire.org/wargames/bandit/bandit7.html)

# Bandit Level 6 → Level 7

## Level Goal

The password for the next level is stored **somewhere on the server** and has all of the following properties:

-   owned by user bandit7
-   owned by group bandit6
-   33 bytes in size

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`, `grep`

  

Level 6에서 Level 7로 가기 위해서는 서버 어딘가에 존재하는 파일을 찾아야 한다.

이 파일은 user가 bandit7로 되어 있고 group은 bandit6으로 되어있으며 크기는 33 바이트라고 한다.

  

이번에도 `find` 명령어를 이용하여 파일을 찾아보겠다.

  

명령어 `find`의 옵션인 `-user`, `-group`, `-size` 를 이용해보자.

  

[![](https://1.bp.blogspot.com/-m5EtSU_R0nw/WWNNbIz5s6I/AAAAAAAAKqo/FnfcOq1-RCYkGQbVhZYtcBoLxHmq_mVjQCLcBGAs/s640/bandit6_00.png)](https://1.bp.blogspot.com/-m5EtSU_R0nw/WWNNbIz5s6I/AAAAAAAAKqo/FnfcOq1-RCYkGQbVhZYtcBoLxHmq_mVjQCLcBGAs/s1600/bandit6_00.png)

  
```bash
$ find / -user bandit7 -group bandit6 -size 33c
```
  

접근권한없음 에러메세지가 잔뜩 뜬다.

이런 메세지들은 리눅스에서 블랙홀처럼 작동하는 /dev/null이라는 폴더로 리다이렉트 해버리자.

  

[![](https://4.bp.blogspot.com/-9s7N6VWJrow/WWNNbEakUEI/AAAAAAAAKqs/xSkdDIeCQ6YGeWM5v4ZbGNzAsqelH9z8wCEwYBhgL/s640/bandit6_01.png)](https://4.bp.blogspot.com/-9s7N6VWJrow/WWNNbEakUEI/AAAAAAAAKqs/xSkdDIeCQ6YGeWM5v4ZbGNzAsqelH9z8wCEwYBhgL/s1600/bandit6_01.png)

  
```bash
$ find / -user bandit7 -group bandit6 -size 33c 2&gt;/dev/null
```
  

#### 추가설명

##### /dev/null

유닉스와 리눅스 시스템에는 블랙홀처럼 동작하는 /dev/null 이라는 파일이 있다.

어떠한 작업의 출력되는 내용을 보고 싶지 않을 때 /dev/null으로 그 출력을 보내면 아무것도 보여지지 않는다.

  

##### redirection

리다이렉션은 표준입력, 표준출력, 표준에러를 화면이 아닌 파일로 대체하는 것을 말한다.

표준입력, 표준출력, 표준에러는 각각 숫자로 1, 2, 3으로 표현한다.

`>` : 표준출력을 새로운 파일로

`>>` : 표준출력을 기존파일에 덧붙임

`<` : 표준입력을 파일에서

`1>` : 표준출력을 파일로

`2>` : 표준에러를 파일로

`>&2` : 표준출력, 표준에러를 파일로

  

##### `2>/dev/null`

에러메세지(permission denied)를 /dev/null로 리다이렉트해서 화면에 보여지지 않도록 하라는 의미이다.

  

user가 bandit7이고, group가 bandit6이며 파일크기가 33바이트인 파일을 찾았다.

/var/lib/dpkg/info/bandit7.password 이 파일을 열어보자

  

[![](https://3.bp.blogspot.com/-csRNfeUxfUg/WWNNbEk5JGI/AAAAAAAAKqw/lHo9M2EFWzYHCtXbD3aS2pUdnOuCfrevACEwYBhgL/s640/bandit6_02.png)](https://3.bp.blogspot.com/-csRNfeUxfUg/WWNNbEk5JGI/AAAAAAAAKqw/lHo9M2EFWzYHCtXbD3aS2pUdnOuCfrevACEwYBhgL/s1600/bandit6_02.png)

  
```bash
$ cat /var/lib/dpkg/info/bandit7.password
```
  

bandit7의 비밀번호를 얻었다.

HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
