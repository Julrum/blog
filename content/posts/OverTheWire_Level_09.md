---
title: "OverTheWire.org Bandit Level 8 -> Level 9"
date: 2020-03-30T08:14:48Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "sort", "uniq"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit9.html](http://overthewire.org/wargames/bandit/bandit9.html)

  

# Bandit Level 8 → Level 9

## Level Goal

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Commands you may need to solve this level

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

## Helpful Reading Material

-   [The unix commandline: pipes and redirects](http://www.westwind.com/reference/os-x/commandline/pipes.html)

Level 8에서 Level 9로 가기 위해서 data.txt 파일을 확인해봐야한다. 비밀번호는 단 한 문장만 존재한다고 한다.

  

ssh에 접속 한 뒤 `sort`와 `uniq` 명령어를 사용해 비밀번호를 찾도록 하자.

  

`sort` 명령어는 파일의 내용을 정리하는 역할을 하며, `uniq` 명령어는 라인이 몇번 중복되는지 출력하여 확인하면 된다.

  

[![](https://3.bp.blogspot.com/-vHyB5bYOWnA/WWNPv9A0yyI/AAAAAAAAKrI/jxFRUzCQWKwU13o67o1N1EQGkPqhwydqwCLcBGAs/s640/bandit8_00.png)](https://3.bp.blogspot.com/-vHyB5bYOWnA/WWNPv9A0yyI/AAAAAAAAKrI/jxFRUzCQWKwU13o67o1N1EQGkPqhwydqwCLcBGAs/s1600/bandit8_00.png)

  
```bash
$ sort data.txt | uniq -c
```
  

여기서 중복횟수가 1인 문장을 찾아보자

bandit9로 갈 수 있는 비밀번호를 찾았다.

UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR