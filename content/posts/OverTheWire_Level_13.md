---
title: "OverTheWire.org Bandit Level 12 -> Level 13"
date: 2020-04-10T13:42:37Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command", "mkdir", "cp", "mv", "xxd", "file", "gzip", "bzip2", "tar"]
cover: ""
---

[http://overthewire.org/wargames/bandit/bandit13.html](http://overthewire.org/wargames/bandit/bandit13.html)

# Bandit Level 12 → Level 13

## Level Goal

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands you may need to solve this level

`grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`, `mkdir`, `cp`, `mv`

## Helpful Reading Material

-   [Hex dump on Wikipedia](http://en.wikipedia.org/wiki/Hex_dump)

Level 12에서 Level 13으로 가기위해 이 레벨의 목표를 읽어보자.

다음 레벨의 암호는 반복적으로 압축 된 파일의 16 진수 덤프 인 data.txt 파일에 저장됩니다. 이 수준에서는 /tmp 아래에 mkdir을 사용하여 작업 할 수 있는 디렉토리를 만드는 것이 유용할 수 있습니다.

  

ex)
```bash
$ mkdir /tmp/myname123
```
  

그런 다음 `cp`를 이용하여 데이터 파일을 복사하고 `mv`를 사용하여 이름을 비꿉니다.

  

### Hex dump란?

hex dump는 램 또는 파일이나 저장장치에 있는 컴퓨터 데이터의 십육진법적인 보임새이다. 데이터의 hex dump를 보는 것은 주로 디버깅이나 리버스 엔지니어링의 한 부분이다.

hex dump에서, 각 바이트는 2 숫자와 16진법 수로 표현된다. Hex dumps 는 주로 8 또는 16바이트의 행으로 조직되며, 가끔은 흰 공간으로 분리된다. 몇몇 hex dump들은 시작에서나 마지막 라인의 체크섬 바이트에서 16진법의 메모리주소를 갖는다.

비록 이름은 16 기반 출력을 암시하지만, 몇몇 덤핑 소프트웨어는 8기반이나 10기반 출력도 갖는다. 이 프로그램 기증을 갖는 흔한 이름으로, hexdump, od, xxd 그리고 단순히 dump 또는 심지어 D도 있다.

  

위의 내용을 참고하여 문제를 풀어보자.

  

먼저 ssh에 접속하자.

  

[![](https://2.bp.blogspot.com/-2lcsNv5v4T0/WWh0_cCgCeI/AAAAAAAAKtw/SHmp1pnUSR4MkaW6lxMaVeFnClVLyZTiACLcBGAs/s640/bandit12_00.png)](https://2.bp.blogspot.com/-2lcsNv5v4T0/WWh0_cCgCeI/AAAAAAAAKtw/SHmp1pnUSR4MkaW6lxMaVeFnClVLyZTiACLcBGAs/s1600/bandit12_00.png)

  

접속한 후 `ls` 명령어로 파일을 확인해 보자.

  
```bash
$ls -l
```
  

[![](https://3.bp.blogspot.com/-QCImdmD1Ly4/WWh0_ftROcI/AAAAAAAAKt0/UaNJ7VwMLp8MNISkb2m_NIikKXm5F4dPQCEwYBhgL/s640/bandit12_01.png)](https://3.bp.blogspot.com/-QCImdmD1Ly4/WWh0_ftROcI/AAAAAAAAKt0/UaNJ7VwMLp8MNISkb2m_NIikKXm5F4dPQCEwYBhgL/s1600/bandit12_01.png)

  

data.txt 가 존재함을 알 수 있다.

`xxd` 명령어를 사용하여 내용을 바이너리 데이터로 바꿔보자.

  
```bash
$ xxd -r data.txt
```
  

[![](https://2.bp.blogspot.com/-zuk-w5Qn66E/WWh0_a-X3RI/AAAAAAAAKt4/CrOeGWAeE5QbISFwLcNO7-yiM5iiuT59gCEwYBhgL/s640/bandit12_02.png)](https://2.bp.blogspot.com/-zuk-w5Qn66E/WWh0_a-X3RI/AAAAAAAAKt4/CrOeGWAeE5QbISFwLcNO7-yiM5iiuT59gCEwYBhgL/s1600/bandit12_02.png)

  

내용이 꺠져서 나오는 것을 알 수 있다.

작업하기 쉽게 `xxd` 명령을 사용하여 바이너리로 바꾼 파일을 log라는 이름의 파일로 저장하자.


```bash
$ xxd -r data.txt>log
```
  

`file` 명령어를 사용하여 어떤 형식의 파일인지 확인해 봅시다.

  
```bash
$ file log
```
  

[![](https://4.bp.blogspot.com/-PkQxuSpkJnU/WWh1AMliwpI/AAAAAAAAKuE/TZ592F3s6Zs8nOVFTYgAWT0a2rrAcUcvQCEwYBhgL/s640/bandit12_03.png)](https://4.bp.blogspot.com/-PkQxuSpkJnU/WWh1AMliwpI/AAAAAAAAKuE/TZ592F3s6Zs8nOVFTYgAWT0a2rrAcUcvQCEwYBhgL/s1600/bandit12_03.png)

  

위와 같이 `gzip` 형식으로 압축된 파일임을 알 수 있다.

`mv` 명령어를 사용하여 `gzip`의 확장자를 가진 파일로 바꾼뒤 압축을 풀어보자.

  
```bash
$ mv log log.gz
```
```bash
$ gzip -d log.gz
```
  

[![](https://2.bp.blogspot.com/-_D_4EgJsHvA/WWh1ADfqFSI/AAAAAAAAKt8/QN8rEY-P3SACrJfiXGSr5DmtD7OuiBO_wCEwYBhgL/s640/bandit12_04.png)](https://2.bp.blogspot.com/-_D_4EgJsHvA/WWh1ADfqFSI/AAAAAAAAKt8/QN8rEY-P3SACrJfiXGSr5DmtD7OuiBO_wCEwYBhgL/s1600/bandit12_04.png)

  

압축을 푼 뒤에 `cat` 명령어로 열어봤으나 여전히 깨진 상태로 출력된다.

다시 `file` 명령어로 사용해 보니 이번엔 `bzip2`로 압축되어있음을 확인할 수 있었다.

다시 압축을 풀어보자

  
```bash
$ mv log log.bz2
```
```bash
$bzip2 -d log.bz2
```
```bash
$ file log
```
  

`file` 명령어로 다시 열어보니 이번에는 `gzip` 형식으로 압축이 되어있다고 한다.

  

[![](https://4.bp.blogspot.com/-3DsEFDUDI7c/WWh1AQUjwSI/AAAAAAAAKuA/exqPiT6dyEcvddqpCKUYuU-a9G5xbvyVQCEwYBhgL/s640/bandit12_05.png)](https://4.bp.blogspot.com/-3DsEFDUDI7c/WWh1AQUjwSI/AAAAAAAAKuA/exqPiT6dyEcvddqpCKUYuU-a9G5xbvyVQCEwYBhgL/s1600/bandit12_05.png)

  

다시 압축을 풀어보자

  
```bash
$ mv log log.gz
```
```bash
$ gzip -d log.gz
```
```bash
$ file log
```
  

이번에는 `tar` 형식으로 압축이 되어있다고 한다.

  

[![](https://2.bp.blogspot.com/-1MBIePKNYv4/WWh1A59G9dI/AAAAAAAAKuI/kwIMRjNcgK8m_9WkqFVZlYVUODGP9VViACEwYBhgL/s640/bandit12_06.png)](https://2.bp.blogspot.com/-1MBIePKNYv4/WWh1A59G9dI/AAAAAAAAKuI/kwIMRjNcgK8m_9WkqFVZlYVUODGP9VViACEwYBhgL/s1600/bandit12_06.png)

  

다시 압축을 풀어보자

  
```bash
$ mv log log.tar
```
```bash
$ tar -xvf log.tar
```
  

압축을 풀어보니 data5.bin이라는 파일이 나왔다.

  
```bash
$ file data5.bin
```
  

파일을 확인해 보니 이 파일 마저도 tar형식으로 압축이 되어있다고 나온다.

  

[![](https://3.bp.blogspot.com/-4l8wWtVJ9no/WWh1BJ92QfI/AAAAAAAAKuM/GKNNy4FOuw8qN80dlwjXaoTcevoO9cqIQCEwYBhgL/s640/bandit12_07.png)](https://3.bp.blogspot.com/-4l8wWtVJ9no/WWh1BJ92QfI/AAAAAAAAKuM/GKNNy4FOuw8qN80dlwjXaoTcevoO9cqIQCEwYBhgL/s1600/bandit12_07.png)

  

압축푸는 과정을 계속 반복해보자.

  
```bash
$ mv data5.bin log.tar
```
```bash
$ tar -xvf log.tar
```
  

이번에는 data6.bin 파일이 나왔다.

  
```bash
$ file data6.bin
```
  

이번에는 다시 bzip2형식으로 압축되어있다고 한다.

  

[![](https://4.bp.blogspot.com/-kDUWZQFQAKU/WWh1BNCgKxI/AAAAAAAAKuQ/tDojC9WJuTshl5RxTL_G2yiJELOJEgf6ACEwYBhgL/s640/bandit12_08.png)](https://4.bp.blogspot.com/-kDUWZQFQAKU/WWh1BNCgKxI/AAAAAAAAKuQ/tDojC9WJuTshl5RxTL_G2yiJELOJEgf6ACEwYBhgL/s1600/bandit12_08.png)

  
```bash
$ mv data6.bin log.bz2
```
```bash
$ bzip2 -d log.bz2
```
```bash
$ file log
```
  

이번엔 다시 tar 형식으로 압축되어있다고 한다.

  

[![](https://4.bp.blogspot.com/-I5nkdLp3mKk/WWh1BrM0MtI/AAAAAAAAKuY/YBLwn1yWKIs3fnShlTJiCZbeAVBqMw-LQCEwYBhgL/s640/bandit12_09.png)](https://4.bp.blogspot.com/-I5nkdLp3mKk/WWh1BrM0MtI/AAAAAAAAKuY/YBLwn1yWKIs3fnShlTJiCZbeAVBqMw-LQCEwYBhgL/s1600/bandit12_09.png)

  
```bash
$ mv log log.tar
```
```bash
$ tar -xvf log.tar
```
  

압축을 푸니 data8.bin 파일이 나왔다.

  
```bash
$ file data8.bin
```
  

이 파일은 gzip 형식으로 압축되어 있다고 한다.

  

[![](https://3.bp.blogspot.com/-uvVocE_L-VA/WWh1BqGn17I/AAAAAAAAKuU/jZXL_GZiQlQ2n5Ao_ayNAcBvfk9K0PYDgCEwYBhgL/s640/bandit12_10.png)](https://3.bp.blogspot.com/-uvVocE_L-VA/WWh1BqGn17I/AAAAAAAAKuU/jZXL_GZiQlQ2n5Ao_ayNAcBvfk9K0PYDgCEwYBhgL/s1600/bandit12_10.png)

  
```bash
$ mv data8.bin log.gz
```
```bash
$ gzip -d log.gz
```
  

[![](https://2.bp.blogspot.com/-W9w7P58QbSs/WWh1B-JByvI/AAAAAAAAKuc/HO5F0uHRE-gk4aimcN-1ogikx5Gvau7VACEwYBhgL/s640/bandit12_11.png)](https://2.bp.blogspot.com/-W9w7P58QbSs/WWh1B-JByvI/AAAAAAAAKuc/HO5F0uHRE-gk4aimcN-1ogikx5Gvau7VACEwYBhgL/s1600/bandit12_11.png)

  
```bash
$ file log
```
  

드디어 ASCII 로 이루어진 텍스트 파일이 나왔다.

  

[![](https://2.bp.blogspot.com/-C0-9l12zQlA/WWh1CbftByI/AAAAAAAAKug/FaWAuEiezEElsTzzqtWFfm9jXBO91Z4rwCEwYBhgL/s640/bandit12_12.png)](https://2.bp.blogspot.com/-C0-9l12zQlA/WWh1CbftByI/AAAAAAAAKug/FaWAuEiezEElsTzzqtWFfm9jXBO91Z4rwCEwYBhgL/s1600/bandit12_12.png)

  

비밀번호는 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL이다.