---
title: "OverTheWire.org Bandit Level 4 -> Level 5"
date: 2020-03-30T08:14:37Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "cat"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit5.html](http://overthewire.org/wargames/bandit/bandit5.html)

# Bandit Level 4 → Level 5

## Level Goal

The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`

  

Level 4에서 Level 5로 가기 위해서는 'inhere' 디렉토리 안에 사람이 읽을 수 있는 포맷으로 파일이 존재한다고 한다. 그리고 터미널이 지저분해지면 `reset`이라는 명령어를 이용하라는 팁도 주었다. (`reset` 이라는 명령어 말고 `clear` 이라는 명령어를 사용해도 상관 없다.)

  

ssh에 접속 한 후 `cd` 명령어를 이용하여 'inhere' 디렉토리에 들어간 후 `ls` 명령어로 'inhere' 어떤 파일이 있는지 확인해 보았다.

  
```bash
$ cd inhere/
```
```bash
$ ls -a
```
  

[![](https://4.bp.blogspot.com/-X32Fzs0td3U/WWNKeGGDDwI/AAAAAAAAKqI/CzuiHrjTKXMbV7-xvdFmDMsnZY81kM45gCLcBGAs/s640/bandit4_00.png)](https://4.bp.blogspot.com/-X32Fzs0td3U/WWNKeGGDDwI/AAAAAAAAKqI/CzuiHrjTKXMbV7-xvdFmDMsnZY81kM45gCLcBGAs/s1600/bandit4_00.png)

  

파일이 10개가 존재하는 것을 알 수 있다. 이 파일들을 하나 하나 열어보니 '-file07'의 내용물이 사람이 읽을 수 있는 형태였다.

  
```bash
$ cat ./-file07
```
  

[![](https://1.bp.blogspot.com/-_-WEAY-qBZE/WWNKkU9vMqI/AAAAAAAAKqM/R7s-Ef38gv8bLHi05ypMgoZ1x3k63qKawCLcBGAs/s640/bandit4_01.png)](https://1.bp.blogspot.com/-_-WEAY-qBZE/WWNKkU9vMqI/AAAAAAAAKqM/R7s-Ef38gv8bLHi05ypMgoZ1x3k63qKawCLcBGAs/s1600/bandit4_01.png)

  

이 파일 안에 있는 내용이 다음으로 가기 위한 비밀번호이다.

  

koReBOKuIDDepwhWk7jZC0RTdopnAYKh