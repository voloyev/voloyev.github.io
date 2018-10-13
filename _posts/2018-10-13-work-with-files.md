---
layout: post
title:  "Notes about stdout && stdin"
date:   2018-10-13 14:00
comments: true
categories: bash
---

### Work with strems

|Command               |Description|
|----------------------|------------------------------------------------------------------------------------------------|
|`cmd > file`          | execute program `cmd` and send it output tp `file`, if `file` exists - rewrite it or creates it| 
|`cmd >> file`         | append data from cmd to file|
|`cmd2 < file`         | execute `cmd2` with data from file|
|`cmd3 > file1 < file2`| execute `cmd3` change output and input|
|`cmd | cmd1`          | pipe|
|`cmd 2> errfile`      | send stream of errors to `errfile`|
|`cmd 2>&1 | cmd6`     | add stdout whit stdeer adn send it to `cmd6`|
