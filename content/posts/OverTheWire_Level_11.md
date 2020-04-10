---
title: "OverTheWire.org Bandit Level 10 -> Level 11"
date: 2020-03-30T08:14:57Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "Base64"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit11.html](http://overthewire.org/wargames/bandit/bandit11.html)

# Bandit Level 10 → Level 11

## Level Goal

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

## Commands you may need to solve this level

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

## Helpful Reading Material

-   [Base64 on Wikipedia](http://en.wikipedia.org/wiki/Base64)

Level 10에서 Level 11로 가려면 data.txt에 있는 비밀번호를 봐야한다. 그런데 base64로 인코드된 데이터를 포함하고 있다고 한다.

  

### base64

데이터를 64종류의 인쇄가능한 숫자만을 이용하여 인코딩하는 방식으로, 그 외의 문자를 처리할 수 없는 통신 환경에서 멀티바이트 문자나 이진 데이터를 처리하는 것을 목적으로 한다.

  

먼저 ssh 에 접속한다.

  

[![](https://3.bp.blogspot.com/-e_NHHc8Q2vE/WWXEK93dDMI/AAAAAAAAKsY/2dZSWCFC3ww819W3AYZD9hEjMPmlX3oyACLcBGAs/s640/bandit10_00.png)](https://3.bp.blogspot.com/-e_NHHc8Q2vE/WWXEK93dDMI/AAAAAAAAKsY/2dZSWCFC3ww819W3AYZD9hEjMPmlX3oyACLcBGAs/s1600/bandit10_00.png)

  

data.txt를 열어본다

  
```bash
$ cat data.txt
```
  

[![](https://4.bp.blogspot.com/-x8PVQpouonY/WWXEKyhCSgI/AAAAAAAAKsc/PpqCULkBw7Eh4H8V8oZ09ogu8nftZlr-ACEwYBhgL/s640/bandit10_01.png)](https://4.bp.blogspot.com/-x8PVQpouonY/WWXEKyhCSgI/AAAAAAAAKsc/PpqCULkBw7Eh4H8V8oZ09ogu8nftZlr-ACEwYBhgL/s1600/bandit10_01.png)

  

뜻을 알 수 없는 문자들로 이루어져있다.

  

먼저 이 파일을 인코딩해보겠다.
```bash
$ base64 data.txt
```
[![](https://4.bp.blogspot.com/-z1tdhMBsvGM/WWXEKkk1IFI/AAAAAAAAKsU/ZRYtIqIXWrs16l_YsxrKMl3EALxlQPgOQCEwYBhgL/s640/bandit10_02.png)](https://4.bp.blogspot.com/-z1tdhMBsvGM/WWXEKkk1IFI/AAAAAAAAKsU/ZRYtIqIXWrs16l_YsxrKMl3EALxlQPgOQCEwYBhgL/s1600/bandit10_02.png)

 여전히 비밀번호를 찾을 수 없다.

  

이번에는 이 파일을 디코딩해보겠다.
```bash
$ base64 -d data.txt
```
  

[![](https://2.bp.blogspot.com/-MnmX_bjvN2I/WWXET93dMdI/AAAAAAAAKsk/rQRFmLUlPRQj0AHgD6sThc52xkGE-h-pQCEwYBhgL/s640/bandit10_03.png)](https://2.bp.blogspot.com/-MnmX_bjvN2I/WWXET93dMdI/AAAAAAAAKsk/rQRFmLUlPRQj0AHgD6sThc52xkGE-h-pQCEwYBhgL/s1600/bandit10_03.png)

  

비밀번호는 IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR 이다.