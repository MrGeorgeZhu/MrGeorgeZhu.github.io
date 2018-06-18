---
layout: article
title: GitHub Clone/Push/Pull really slow in China
key: 20180618
tags:
  - GitHub
  - English
---

## Context

I just got back to China today form Seatlle. Today I was trying to clone, 
push and pull from GitHub, but the download speed is really slow. (8 kb/s)

Later I found out that DNS works a little bit differently in China, so it 
was pointing to a slow host.

## Solution

### Find Fastest Hosts

Use https://www.ipaddress.com/ to directly find the fastest IP address to connect
to GitHub.
Look up
* github.com
* github.global.ssl.fastly.net
and copy down the resulting IP address.

### Change Hosts

* Mac
  
Open `/etc/hosts` using your favorite editor (e.g. Nano or Vi).
Add these two lines:
``` 
  <Corresponding IP address> github.com
  <Corresponding IP address> github.global.ssl.fastly.net
```
Then flush DNS using `sudo killall -HUP mDNSResponder` command

* Windows

Open `C:\Windows\System32\drivers\etc\hosts` using your favorite editor
Add the same two lines:
```
	<Corresponding IP address> github.com
	<Corresponding IP address> github.global.ssl.fastly.net
```
Then flush DNS using `ipconfig /flushdns` command

After changing hosts download speed became 1 MB/s!