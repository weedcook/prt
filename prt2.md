```
root@yangqi:~# tmp_path=/opt/aa/tt/ && mkdir -p $tmp_path && cd $tmp_path && touch a b c
root@yangqi:/opt/aa/tt# ls -l
total 0
-rw-r--r-- 1 root root 0 Mar 24 01:45 a
-rw-r--r-- 1 root root 0 Mar 24 01:45 b
-rw-r--r-- 1 root root 0 Mar 24 01:45 c
root@yangqi:/opt/aa/tt# chown abc:testabc *
root@yangqi:/opt/aa/tt# ls -l
total 0
-rw-r--r-- 1 abc testabc 0 Mar 24 01:45 a
-rw-r--r-- 1 abc testabc 0 Mar 24 01:45 b
-rw-r--r-- 1 abc testabc 0 Mar 24 01:45 c
root@yangqi:/opt/aa/tt# 
root@yangqi:~# cd
root@yangqi:~# 
```
```
root@yangqi:/opt# mkdir tmp
root@yangqi:/opt# chmod -R ug+rwx tmp
root@yangqi:/opt# chmod -R o-rwx tmp
root@yangqi:/opt# ls -l
total 32
drwxr-xr-x 3 root root    4096 Mar 24 01:43 aa
drwxr-xr-x 3 root root    4096 Mar 24 00:52 aaa
drwxr-xr-x 2 abc  root    4096 Mar 24 01:29 abc
drwxr-xr-x 3 root root    4096 Mar 24 00:49 data1
drwxr-xr-x 2 root root    4096 Mar 24 01:25 nginx1.8.5
-rw-r--r-- 1 root root       0 Mar 24 00:57 test3
drwxr-xr-x 2 root testabc 4096 Mar 24 01:33 testabc
drwxrwx--- 2 root root    4096 Mar 24 07:55 tmp
drwxr-xr-x 2 root root    4096 Mar 24 02:00 tmp1
root@yangqi:/opt# 

```
```
root@yangqi:/opt# chmod 751 tmp1
root@yangqi:/opt# stat tmp1
  File: tmp1
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: fd00h/64768d	Inode: 660654      Links: 2
Access: (0751/drwxr-x--x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2021-03-24 08:00:50.784823390 +0000
Modify: 2021-03-24 08:00:50.784823390 +0000
Change: 2021-03-24 08:01:37.836299799 +0000
 Birth: -
root@yangqi:/opt# 

root@yangqi:/opt#
```
```
root@yangqi:~# useradd -u 1000 -d /home/web -N www
root@yangqi:~# groupadd web
root@yangqi:~# usermod -a -G web www
root@yangqi:~# id www
uid=8888(www) gid=100(users) groups=100(users),1003(web)
root@yangqi:~#
```
