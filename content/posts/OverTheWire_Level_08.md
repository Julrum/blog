---
title: "OverTheWire.org Bandit Level 7 -> Level 8"
date: 2020-03-30T08:14:46Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "grep"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit8.html](http://overthewire.org/wargames/bandit/bandit8.html)

  

# Bandit Level 7 → Level 8

## Level Goal

The password for the next level is stored in the file **data.txt** next to the word **millionth**

## Commands you may need to solve this level

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

  

Level 7에서 Level 8로 가기 위해서는 data.txt 파일안에 있는 비밀번호를 읽어야한다. data.txt 안에 비밀번호는 'millionth' 단어 옆에 위치해 있다고 한다.

  

먼저 ssh에 접속한다.

  

[![](https://1.bp.blogspot.com/-eamkiMENz1Q/WWXMfoJ7bvI/AAAAAAAAKs0/Yz1eMuB56XQ9UGdnHee2Ukp0m_RAfOJ7QCLcBGAs/s640/bandit7_00.png)](https://1.bp.blogspot.com/-eamkiMENz1Q/WWXMfoJ7bvI/AAAAAAAAKs0/Yz1eMuB56XQ9UGdnHee2Ukp0m_RAfOJ7QCLcBGAs/s1600/bandit7_00.png)

  

파일을 한 번 열어보자
```bash
$ cat data.txt
```
  

[![](https://4.bp.blogspot.com/-QRXPV6rTVY8/WWXMf3LmsGI/AAAAAAAAKs8/hIZFyvj1rTUNU2PB9Dno6p6QgPRN_I6gwCLcBGAs/s640/bandit7_01.png)](https://4.bp.blogspot.com/-QRXPV6rTVY8/WWXMf3LmsGI/AAAAAAAAKs8/hIZFyvj1rTUNU2PB9Dno6p6QgPRN_I6gwCLcBGAs/s1600/bandit7_01.png)

  

상당히 많은 양의 정보가 나오는 것을 알 수 있다.

위에서 'millionth'라는 단어 옆에 비밀번호가 존재한다는 힌트를 이용하자.

특정 단어를 찾는 명령어 `grep`을 사용해보자
```bash
$ grep millionth data.txt
```
  

[![](https://3.bp.blogspot.com/-8mx9JLE7jfo/WWXMfzok1pI/AAAAAAAAKs4/6-WxOS3g2OsuvYFxW2BQlwqc5yXyEo3YwCLcBGAs/s640/bandit7_02.png)](https://3.bp.blogspot.com/-8mx9JLE7jfo/WWXMfzok1pI/AAAAAAAAKs4/6-WxOS3g2OsuvYFxW2BQlwqc5yXyEo3YwCLcBGAs/s1600/bandit7_02.png)

  

millionth 단어 옆에 위치하는 저것이 비밀번호이다.

cvX2JJa4CFALtqS87jk27qwqGhBM9plV