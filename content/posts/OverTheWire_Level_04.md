---
title: "OverTheWire.org Bandit Level 3 -> Level 4"
date: 2020-03-30T08:14:34Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit4.html](http://overthewire.org/wargames/bandit/bandit4.html)

  

# Bandit Level 3 → Level 4

## Level Goal

The password for the next level is stored in a hidden file in the **inhere** directory.

## Commands you may need to solve this level

`ls`, `cd`, `cat`, `file`, `du`, `find`

  

Level 3에서 Level 4로 가기 위해서는 'inhere'이라는 디렉토리 안에 숨겨진 파일을 찾아야 한다.

  

`ssh`에 접속한 후 홈 디렉토리에서 `ls` 명령어를 이용하여 inhere 디렉토리와 inhere 디렉토리 안에 있는 숨김파일을 확인해 보겠다.

  

[![](https://3.bp.blogspot.com/-vLtDeXaRmko/WWNIUmYZagI/AAAAAAAAKp4/szRREdti0Qon-NynuuzfoPzlDPZnbasCQCLcBGAs/s640/bandit3_00.png)](https://3.bp.blogspot.com/-vLtDeXaRmko/WWNIUmYZagI/AAAAAAAAKp4/szRREdti0Qon-NynuuzfoPzlDPZnbasCQCLcBGAs/s1600/bandit3_00.png)

  

명령어 `ls` 옵션

  

- `-a` : 디렉토리 내의 모든 파일 출력
- `-i ls -` : 파일의 inode와 함께 출력한다.
- `-l` : 파일 허용 여부, 소유자, 그룹, 크기, 날짜 등을 출력한다.
- `-m` : 파일을 쉼표로 구분하여 가로로 출력한다.
- `-r` : 정렬 옵션이 선택되었을 때, 그 역순으로 출력한다.
- `-s` : KB 단위의 파일 크기를 출력한다.
- `-t` : 최근에 만들어진 파일 순서대로 출력한다.
- `-x` : 파일 순서를 세로로 출력한다.
- `-F` : 파일의 형태와 함깨 출력한다. 출력되는 파일의 형태는 `*`, `@`, `|`, `=` 등이며, 이것은 각각 실행 파일, 심볼릭 링크, FiFO 소켓을 나타낸다.
- `-R` : 서브 디렉토리의 내용을 포함하여 출력한다.
- `-S` : 파일 크기가 큰 순서로 출력한다.
- `-U` : 정렬하여 출력한다.
- `-1` : 라인당 한 파일씩 출력한다.
- `--help` : 도움말을 화면상에 나타낸다.
- `--version` : `ls`의 파일 버전과 함께 출력한다.

  

찾아보니 홈 디렉토리에 'inhere'이라는 이름의 디렉토리가 있음을 찾았고 그 안에는 '.hidden'이라는 이름의 파일을 찾을 수 있다.

  

`cat` 명령어를 이용하여 '.inhere' 파일 안의 내용물을 확인해 보자.

  

[![](https://3.bp.blogspot.com/-bbpUD0IjE2U/WWNIyhDFmvI/AAAAAAAAKqA/b_T5RnTEvZ4zs_-cGWk5BU2nvtT1im1jACLcBGAs/s640/bandit3_01.png)](https://3.bp.blogspot.com/-bbpUD0IjE2U/WWNIyhDFmvI/AAAAAAAAKqA/b_T5RnTEvZ4zs_-cGWk5BU2nvtT1im1jACLcBGAs/s1600/bandit3_01.png)

  
```bash
$ cat inhere/.hidden
```
  

bandit4로 갈 수 있는 비밀번호를 찾았다.

pIwrPrtPN36QITSp3EQaw936yaFoFgAB