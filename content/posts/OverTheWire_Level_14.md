---
title: "OverTheWire.org Bandit Level 13 -> Level 14"
date: 2020-04-10T13:42:40Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command" "ssh", "sshkey"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit14.html](http://overthewire.org/wargames/bandit/bandit14.html)

  

# Bandit Level 13 → Level 14

## Level Goal

The password for the next level is stored in **/etc/bandit\_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on

## Commands you may need to solve this level

`ssh`, `telnet`, `nc`, `openssl`, `s_client`, `nmap`

## Helpful Reading Material

-   [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Level 13에서 Level 14로 가기 위한 이번 레벨의 목표를 확인해 보자.

다음 레벨의 암호는 /etc/bandit\_pass/bandit14에 저장되며 bandit14 사용자 만 읽을 수 있습니다. 이 수준에서는 다음 암호를 얻지 못하지만 다음 수준으로 로그인하는데 사용할 수 있는 개인 SSH 키를 얻습니다. 참고 : localhost는 작업중인 시스템을 나타내는 호스트 이름입니다.

  

비밀번호를 알아내고 싶으나 사용자가 bandit14로 정해져 있습니다. ssh로 필요한권한을 획득한 다음에 비밀번호를 알아내면 됩니다. 먼저 어떤 파일이 있는지 `ls` 명령어로 확인해 봅니다.

  

[![](https://1.bp.blogspot.com/-3skO7NVw4_w/WWl2xUPupbI/AAAAAAAAKu8/2eTxjk_LUUgDKUlRe6XTBDGzRyyE_9PSwCLcBGAs/s640/bandit13_00.png)](https://1.bp.blogspot.com/-3skO7NVw4_w/WWl2xUPupbI/AAAAAAAAKu8/2eTxjk_LUUgDKUlRe6XTBDGzRyyE_9PSwCLcBGAs/s1600/bandit13_00.png)

  

sshkey.private 라는 이름의 개인키를 찾을 수 있습니다. 이 개인키를 이용아여 bandit14에 접속을 할 수 있습니다.

  
```bash
$ ssh -i ./sshkey.private bandit14@localhost
```
> localhost : 컴퓨터 네트워크에서 사용하는 루프백 호스트명으로 자신의 컴퓨터를 의미한다.

> `-i` :RSA 인증을 위한 비밀 키를 읽어 올 파일을 선택한다.

  

[![](https://3.bp.blogspot.com/-YYYrA2G9l5k/WWl2xXzI3kI/AAAAAAAAKu4/ATHifDhigPIRa5ZW18axMYQzc_638-NuwCEwYBhgL/s640/bandit13_01.png)](https://3.bp.blogspot.com/-YYYrA2G9l5k/WWl2xXzI3kI/AAAAAAAAKu4/ATHifDhigPIRa5ZW18axMYQzc_638-NuwCEwYBhgL/s1600/bandit13_01.png)

  

`Are you sure you want to continue connection (yes/no)?` 라는 문구가 뜨면 yes 를 입력하여 계속 진행한다.

  

  

진행이 완료되면 비로소 bandit14의 권한을 획득하게 되었음을 알 수 있다. 권한을 받은 상태에서 `cat` 명령어를 사용하여 비밀번호를 보자

  
```bash
$ cat /etc/bandit\_pass/bandit14
```
  

[![](https://3.bp.blogspot.com/-2KQ5vRoG5Fk/WWl2xZA1orI/AAAAAAAAKvA/RNPVmuyQfXYE-KhZE7X2lAjh5R7hUagZwCEwYBhgL/s640/bandit13_02.png)](https://3.bp.blogspot.com/-2KQ5vRoG5Fk/WWl2xZA1orI/AAAAAAAAKvA/RNPVmuyQfXYE-KhZE7X2lAjh5R7hUagZwCEwYBhgL/s1600/bandit13_02.png)

  

비밀번호는 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e 이다.