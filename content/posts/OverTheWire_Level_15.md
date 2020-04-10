---
title: "OverTheWire.org Bandit Level 14 -> Level 15"
date: 2020-04-10T13:42:42Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "ssh", "telnet", "nc"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit15.html](http://overthewire.org/wargames/bandit/bandit15.html)

# Bandit Level 14 → Level 15

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

## Commands you may need to solve this level

`ssh`, `telnet`, `nc`, `openssl`, `s_client`, `nmap`

## Helpful Reading Material

-   [How the Internet works in 5 minutes (YouTube)](https://www.youtube.com/watch?v=7_LPdttKXPc) (Not completely accurate, but good enough for beginners)
-   [IP Addresses](http://computer.howstuffworks.com/web-server5.htm)
-   [IP Address on Wikipedia](http://en.wikipedia.org/wiki/IP_address)
-   [Localhost on Wikipedia](http://en.wikipedia.org/wiki/Localhost)
-   [Ports](http://computer.howstuffworks.com/web-server8.htm)
-   [Port (computer networking) on Wikipedia](http://en.wikipedia.org/wiki/Port_(computer_networking))

Level 14에서 Level 15로 가기 위한 이번 단계의 목표를 보자.

다음 레벨의 암호는 현재 레벨의 암호를 localhost의 포트 30000에 제출하여 검색 할 수 있습니다.

  

localhost 300000 포트에 14레벨의 비밀번호를 입력하면 다음 단계의 비밀번호를 찾을 수 있다고 한다. 지난 단계에서 했던 방식으로 접속해보자.

  
```bash
$ ssh -p 300000 bandit15@localhost
```
  

[![](https://4.bp.blogspot.com/-8alAmTtwnLo/WWmD5VPFCVI/AAAAAAAAKvY/k5HEtBhAoJErh1CCN6SmDtTuRIkmPztSQCLcBGAs/s640/bandit14_00.png)](https://4.bp.blogspot.com/-8alAmTtwnLo/WWmD5VPFCVI/AAAAAAAAKvY/k5HEtBhAoJErh1CCN6SmDtTuRIkmPztSQCLcBGAs/s1600/bandit14_00.png)

  

하지만 이번에는 `ssh` 명령어는 보안상 연결을 할 수 없다고 출력된다. `ssh` 명령어 대신에 `telnet` 와 `nc` 명령어를 사용해 보자.

  
```bash
$ telnet localhost 30000
```
  

위의 명령어를 입력한 뒤 bandit13에서 얻은 비밀번호를 입력하면 아래와 같이 bandit15로 갈 수 있는 비밀번호를 얻을 수 있게 된다.

  

[![](https://2.bp.blogspot.com/-a0AegFSs0Us/WWmD5ZwuqzI/AAAAAAAAKvQ/KUF8wDKHDaAvjQ4Ui-71LZnZzI57vDMxwCEwYBhgL/s640/bandit14_01.png)](https://2.bp.blogspot.com/-a0AegFSs0Us/WWmD5ZwuqzI/AAAAAAAAKvQ/KUF8wDKHDaAvjQ4Ui-71LZnZzI57vDMxwCEwYBhgL/s1600/bandit14_01.png)

  

`nc` 명령어로도 가능하다.
```bash
$ nc localhost 30000
```
  

[![](https://3.bp.blogspot.com/-m4pSy2ZJjmU/WWmD5YI0IoI/AAAAAAAAKvU/SoSk5d5oUIUTwrYmGffmYvOg16vyVcajgCEwYBhgL/s640/bandit14_02.png)](https://3.bp.blogspot.com/-m4pSy2ZJjmU/WWmD5YI0IoI/AAAAAAAAKvU/SoSk5d5oUIUTwrYmGffmYvOg16vyVcajgCEwYBhgL/s1600/bandit14_02.png)

  

비밀번호는 BfMYroe26WYalil77FoDi9qh59eK5xNr 이다.