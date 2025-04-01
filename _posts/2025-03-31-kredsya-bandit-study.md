---
title: "[Linux] Bandit Study Write-Up (kredsya)"
excerpt: "2025-1학기 Linux Bandit 스터디 Write-Up"
author: kredsya
categories:
    - study
tags:
    - [linux, bandit]
date: 2025-03-31
last_modified_at: 2025-03-31
---

# Level 0 → Level 4

## Level 0

### Goal

SSH로 접속.

### Solve

| host name | user name | password | port |
|---|---|---|---|
| bandit.labs.overthewire.org | bandit0 | bandit0 | 2220 |

```shell
$ ssh bandit0@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password: [<- 여기에 bandit0 입력]
```

### Digression

`-p` 옵션과 포트 넘버를 띄어쓰기로 구분할 필요가 없고, destination보다 앞인지 뒤인지도 상관이 없다.
```shell
$ ssh -p2220 bandit0@bandit.labs.overthewire.org
```

## Level 0 → Level 1

### Goal

home directory `bandit0@bandit:~$`의 readme 읽기기.

### Solve

password는 마스킹 처리했습니다.

```shell
bandit0@bandit:~$ ll
total 24
drwxr-xr-x  2 root    root    4096 Sep 19  2024 ./
drwxr-xr-x 70 root    root    4096 Sep 19  2024 ../
-rw-r--r--  1 root    root     220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root    root    3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root    root     807 Mar 31  2024 .profile
-rw-r-----  1 bandit1 bandit0  438 Sep 19  2024 readme
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ********************************

```

### Digression

`ll`은 `ls -alF`의 약어로 디렉토리 내용을 보기 쉽게 만들어준다.

## Level 1 → Level 2

### Goal

`-` 파일 읽기.

### Solve

```shell
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
********************************
```

### Digression

`.`는 현재 디렉토리를 의미한다. 그래서 `./-`는 `/home/bandit1/-`와 같은 표현이다.

## Level 2 → Level 3

### Goal

파일 이름에 공백이 포함된 파일 읽기.

### Solve

```shell
bandit2@bandit:~$ ll
total 24
drwxr-xr-x  2 root    root    4096 Sep 19  2024 ./
drwxr-xr-x 70 root    root    4096 Sep 19  2024 ../
-rw-r--r--  1 root    root     220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root    root    3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root    root     807 Mar 31  2024 .profile
-rw-r-----  1 bandit3 bandit2   33 Sep 19  2024 spaces in this filename
bandit2@bandit:~$ cat spaces\ in\ this\ filename
********************************
```

### Digression

`\`는 escape character, 제어 문자로 보통 문자 출력을 제어한다. 그 예시로 `\n` line feed, `\r` carriage return 등이 있는데 문법과 겹쳐 출력할 수 없는 일부 특수문자를 출력하기 위해서 사용되기도 한다. `\"` 큰 따옴표 출력이 그 예시이고 공백도 출력할 수 있다.

## Level 3 → Level 4

### Goal

`inhere` 디렉토리 안에 숨겨진 파일 읽기.

### Solve

```shell
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ ls -a inhere
.  ..  ...Hiding-From-You
bandit3@bandit:~$ cat inhere/...Hiding-From-You
********************************
```

### Digression

파일 이름이 `.`으로 시작하면 숨은 파일이 된다. `ls -a` 옵션으로 볼 수 있다.

`ll`은 `-a` 옵션이 포함되어 있으니 `ll` 사용해도 된다.