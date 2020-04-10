---
title: "OverTheWire.org Bandit Level 16 -> Level 17"
date: 2020-04-10T13:42:47Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command"]
cover: ""
draft: true
---

[http://overthewire.org/wargames/bandit/bandit17.html](http://overthewire.org/wargames/bandit/bandit17.html)

# Bandit Level 16 → Level 17

## Level Goal

The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Commands you may need to solve this level

`ssh`, `telnet`, `nc`, `openssl`, `s_client`, `nmap`

## Helpful Reading Material

-   [Port scanner on Wikipedia](http://en.wikipedia.org/wiki/Port_scanner)

Level 16에서 Level 17로 가기 위한 레벨의 목표를 읽어보자.

현제 레벨의 암호를 31000 ~ 32000 범위의 localhost에 있는 포트에 제출하면 다음 레벨에 대한 인증을 검색 할 수 있습니다. 먼저 이 포트 중 어느 포트에서 서버가 수신 대기 중인지 확인하십시오. 그런 다음 SSL 을 말하는 사람과 그렇지 않은 사람을 찾으십시오. 다음 자격 증명을 제공하는 서버는 1개 뿐입니다. 다른 서버는 보내는 모든 내용을 사용자에게 간단히 보냅니다.