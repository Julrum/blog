---
title: "OverTheWire.org Bandit Level 15 -> Level 16"
date: 2020-04-10T13:42:45Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "openssl", "s_client"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit16.html](http://overthewire.org/wargames/bandit/bandit16.html)

  

# Bandit Level 15 → Level 16

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

**Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign\_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**

## Commands you may need to solve this level

`ssh`, `telnet`, `nc`, `openssl`, `s_client`, `nmap`

## Helpful Reading Material

-   [Secure Socket Layer/Transport Layer Security on Wikipedia](http://en.wikipedia.org/wiki/Secure_Socket_Layer)
-   [OpenSSL Cookbook - Testing with OpenSSL](https://www.feistyduck.com/library/openssl-cookbook/online/ch-testing-with-openssl.html)

Level 15에서 Level 16으로 가기 위해서 위의 목표를 읽어보자.

  

다음 레벨의 암호는 SSL 암호화를 사용하여 localhost의 포트 30001에 현재 레빌의 암호를 제출하여 검색할 수 있습니다. 도움이 되는 메모 : "HEARTBEATING" 및 "Read R BLOCK" 이 나온다면 `-ign_eof`를 사용하고 `man` 명령어의 "CONNECTED COMMANDS"을 읽으십시오. 'R'과 'Q' 옆에 'B' 명령이 해당 버전에서도 작동합니다.

  

이번 문제는 SSL의 `openssl`, `s_client`을 이용한 문제이다.

  
```bash
$ openssl s_client -connect localhost:30001
```
  

[![](https://4.bp.blogspot.com/-sfv3tk1TxtA/WXasYgGGOVI/AAAAAAAAKwA/jTsiV4DTzIQqwJqzInakd5OmWEhB9Cv0ACLcBGAs/s640/bandit15_00.png)](https://4.bp.blogspot.com/-sfv3tk1TxtA/WXasYgGGOVI/AAAAAAAAKwA/jTsiV4DTzIQqwJqzInakd5OmWEhB9Cv0ACLcBGAs/s1600/bandit15_00.png)

  

위와 같이 30001 포트로 접속을 시도하여 현재 패스워드를 입력해도 `HEARTBEATING read R BLOCK` 메세지만 출력되고 우리가 원하는 다음 레벨로 갈 수 있는 비밀번호는 나타나지 않는다.

  

`-ign_eof` 옵션을 사용하여 파일의 끝나도 프로그램이 중단되는 것을 막아보자.

  
```bash
$ openssl s_client -connect localhost:30001 -ign\_eof
```
  

[![](https://3.bp.blogspot.com/--6vjK_2_0E4/WXasYqiafzI/AAAAAAAAKwE/VhbA6lDr5yUWyRJEECO2eA9HnWdnqZnwACLcBGAs/s640/bandit15_01.png)](https://3.bp.blogspot.com/--6vjK_2_0E4/WXasYqiafzI/AAAAAAAAKwE/VhbA6lDr5yUWyRJEECO2eA9HnWdnqZnwACLcBGAs/s1600/bandit15_01.png)

  

비밀번호는 cluFn7wTiGryunymYOu4RcffSxQluehd이다.