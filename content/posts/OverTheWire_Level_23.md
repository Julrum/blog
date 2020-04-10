---
title: "OverTheWire.org Bandit Level 22 -> Level 23"
date: 2020-04-10T13:43:05Z
categories: ["essay"]
tags: ["overthewire", "bandit", "command"]
cover: ""
draft: true
---

[http://overthewire.org/wargames/bandit/bandit23.html](http://overthewire.org/wargames/bandit/bandit23.html)

  

# Bandit Level 22 → Level 23

## Level Goal

A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

## Commands you may need to solve this level

`cron`, `crontab`, `crontab(5)` (use `man 5 crontab` to access this)