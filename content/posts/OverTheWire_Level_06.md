---
title: "OverTheWire.org Bandit Level 5 -> Level 6"
date: 2020-03-30T08:14:39Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "find", "cat"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit6.html](http://overthewire.org/wargames/bandit/bandit6.html)

# Bandit Level 5 → Level 6

## Level Goal

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

-   human-readable
-   1033 bytes in size
-   not executable

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`

  

Level 5에서 Level 6으로 가기위해서 'inhere' 디렉토리 안에 있는 어떤 파일을 열어야 한다고 한다.  이 파일은 사람이 읽을 수 있으며 1033bytes의 크기를 가지고 있으며 실행 불가능하다고 한다.

  

먼저 ssh로 서버에 접속을 한다.

  

[![](https://2.bp.blogspot.com/-NfAHWQsLxd0/WWNLv6mpZ8I/AAAAAAAAKqU/tN8w2jsSyaUTJZJpuUYvj4CZ4_j1KjzGwCLcBGAs/s640/bandit5_00.png)](https://2.bp.blogspot.com/-NfAHWQsLxd0/WWNLv6mpZ8I/AAAAAAAAKqU/tN8w2jsSyaUTJZJpuUYvj4CZ4_j1KjzGwCLcBGAs/s1600/bandit5_00.png)

  

위에 제시된 조건을 이용하여 `find` 명령어를 사용하여 해당되는 파일을 찾을 수 있다.

  

`find` 명령어에서 `-size` 옵션을 이용하면 파일크기와 일치하는 파일의 리스트를 확인할 수 있다.

  
```bash
find \[경로\] -size \[파일크기/-파일크기/+파일크기\]\[b/c/k/w\]
```
  

파일의 크기 앞에 `+` 가 붙으면 이상, `-` 가 붙으면 이하를 뜻하며,

`b`,`c`,`k`,`w`는 각각 블록단위(512KB), byte, killobyte, 2byte(word)를 의미한다.

  

`find -size` 명령어를 이용하여 'inhere' 디렉토리에서 1033 바이트 크기인 파일의 리스트를 출력해보겠다.

  

[![](https://4.bp.blogspot.com/-qhf-gwf_Rcc/WWNLwHtaNyI/AAAAAAAAKqY/QeinIT2h-5EYXIr90dHjMqQIs5wUwL0uACEwYBhgL/s640/bandit5_01.png)](https://4.bp.blogspot.com/-qhf-gwf_Rcc/WWNLwHtaNyI/AAAAAAAAKqY/QeinIT2h-5EYXIr90dHjMqQIs5wUwL0uACEwYBhgL/s1600/bandit5_01.png)

  
```bash
$ find ./inhere -size 1033c -ls
```
  

크기가 1033 바이트인 파일은

./inhere/maybehere07/.file2 하나 밖에 존재하지 않는다.

이 파일을 열어보도록 하자.

  

[![](https://2.bp.blogspot.com/-u-YQf167OXs/WWNLwPISrDI/AAAAAAAAKqc/jsNsRXgrSQUjcYUW2yFFexI_nZeFiERgACEwYBhgL/s640/bandit5_02.png)](https://2.bp.blogspot.com/-u-YQf167OXs/WWNLwPISrDI/AAAAAAAAKqc/jsNsRXgrSQUjcYUW2yFFexI_nZeFiERgACEwYBhgL/s1600/bandit5_02.png)

  
```bash
$ cat ./inhere/maybehere07/.file2
```
  

bandit6으로 갈 수 있는 비밀번호를 얻었다.

DXjZPULLxYr17uwoI01bNLQbtFemEgo7