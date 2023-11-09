+++
categories = ['bash']
date = '2018-10-13T14:00:00+02:00'
title = 'Notes about stdout && stdin'
description = 'Cheetsheet about stfin, stderr & stdout'
+++


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


-rwxr-xr-x 1 root root 14322 date /bin/cat

0755

1 - execute
2 - write
4 - read
