---
title: "OverTheWire_Level_1"
date: 2020-03-30T07:52:30Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "ssh", "cat", "ls"]
cover: ""
---

OverTheWire Bandit을 풀어보면서 리눅스의 기초적인 명령어를 익혀보려 한다,

  

[http://overthewire.org/wargames/bandit/bandit0.html](http://overthewire.org/wargames/bandit/bandit0.html)

  

# Bandit Level 0

## Level Goal

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is **bandit.labs.overthewire.org**, on port 2220. The username is **bandit0** and the password is **bandit0**. Once logged in, go to the [Level 1](http://overthewire.org/wargames/bandit/bandit1.html) page to find out how to beat Level 1.

## Commands you may need to solve this level

`ssh`

## Helpful Reading Material

-   [Secure Shell (SSH) on Wikipedia](http://en.wikipedia.org/wiki/Secure_Shell)
-   [How to use SSH on wikiHow](http://www.wikihow.com/Use-SSH)

  

Level 0의 목표는 bandit.labs.overthewire.org에 접속하는 것이다. Putty를 이용하여 접속하는 방법이 있을 수 있으나 나는 우분투 내장 터미널을 이용할 것이다.

  

먼저 SSH를 설치해보도록 하자
```bash
$ sudo apt-get install openssh-server
```
  

설치가 되었으면 이제 위에서 제시한 주소로 접속해야한다.

  

접속할 떄의 명령어는 다음과 같다.
```bash
ssh 아이디@주소 -p포트
```
  

우리는 bandit0 이라는 아이디로 bandit.labs.overthewire.org를 접속할 것이며 포트는 2220이다. 그러므로 우리가 입력해야할 명령어는 다음과 같다.
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p2220
```
  

[![](https://1.bp.blogspot.com/-wtkplKZriao/WWH6T_8-lTI/AAAAAAAAKoo/RYtZfGIyagEYFzX7LQAbrb7xNJwKn96nQCLcBGAs/s640/bandit0%25EC%25A0%2591%25EC%2586%258D.png)](https://1.bp.blogspot.com/-wtkplKZriao/WWH6T_8-lTI/AAAAAAAAKoo/RYtZfGIyagEYFzX7LQAbrb7xNJwKn96nQCLcBGAs/s1600/bandit0%25EC%25A0%2591%25EC%2586%258D.png)

  

다음과 같이 창이 뜨면 비밀번호는 위에 나와있는 bandit0을 입력한다.

  

[![](https://3.bp.blogspot.com/-S3e2gcu8dm4/WWH7TFd_oLI/AAAAAAAAKo0/PGzPV3gtx9MOq5vwZG5HvhmmpNssmqBzgCLcBGAs/s640/bandit0_01.png)](https://3.bp.blogspot.com/-S3e2gcu8dm4/WWH7TFd_oLI/AAAAAAAAKo0/PGzPV3gtx9MOq5vwZG5HvhmmpNssmqBzgCLcBGAs/s1600/bandit0_01.png)

  

  

이제 Level 0에서 Level 1로 어떻게 가는지 확인해 보자

[http://overthewire.org/wargames/bandit/bandit1.html](http://overthewire.org/wargames/bandit/bandit1.html)

  

# Bandit Level 0 → Level 1

## Level Goal

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`

  

홈 디렉토리에 있는 'readme'라는 파일을 열면 Level 1로 갈 수 있는 비밀번호가 있따고 한다.

  

현재 홈 디렉토리에 어떤 파일들이 있나 확인해 보겠다.

명령어로 `ls`를 치면 현재 있는 파일들이 나열되고 `ls -a`를 치면 숨겨져 있던 모든 파일을 출력할 수 있다.

  

[![](https://2.bp.blogspot.com/-X0yl4LOu99U/WWH7S1Tp4VI/AAAAAAAAKos/awtlshWF8CM6smSCVPPza0oYiLICuF9qgCLcBGAs/s640/bandit0_02.png)](https://2.bp.blogspot.com/-X0yl4LOu99U/WWH7S1Tp4VI/AAAAAAAAKos/awtlshWF8CM6smSCVPPza0oYiLICuF9qgCLcBGAs/s1600/bandit0_02.png)

  

readme 파일이 보이므로 이 파일을 보겠다. 파일 내용을 볼 때에는 `cat`이라는 명령어를 사용한다.
```bash
$ cat readme
```
  

[![](https://3.bp.blogspot.com/-fsNiIAMKPXw/WWH7TCCB3jI/AAAAAAAAKow/9anYYYSfVQs0caSnrsC2U9EhKmjA0NIAQCLcBGAs/s640/bandit0_03.png)](https://3.bp.blogspot.com/-fsNiIAMKPXw/WWH7TCCB3jI/AAAAAAAAKow/9anYYYSfVQs0caSnrsC2U9EhKmjA0NIAQCLcBGAs/s1600/bandit0_03.png)

  

위와 같이 뜬 boJ9jbbUNNfktd78OOpsqOltutMc3MY1 가 다음 bandit1의 비밀번호가 된다.