# Task 1 - cat: not the pet, but the command!

The 'hacker' has to use the "cat" command to print the contents of the file named "flag". This file contains the flag.

## My solve

**Flag:** `pwn.college{4wqo2vkwf2xDxRW-JccbSm2OW1B.QXxcTN0wyM2AzNzEzW}`

I typed in the "cat" command with the directory to the file named "flag" passed as an argument with the command.

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{4wqo2vkwf2xDxRW-JccbSm2OW1B.QXxcTN0wyM2AzNzEzW}
```

## What I learned
- Learned how to use the cat command to print the contents of a file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 2 - catting absolute paths

The 'hacker' has to use the "cat" command to print the contents of the file named "flag" but this time he has to write the absolute path of the file. This file contains the flag.

## My solve

**Flag:** `pwn.college{4wqo2vkwf2xDxRW-JccbSm2OW1B.QXxcTN0wyM2AzNzEzW}`

I typed in the "cat" command with the absolute directory to the file named "flag" passed as an argument with the command.

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{gZk8IW9AHvlsSPSklFO31iDInyw.QX5ETO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use the cat command to print the contents of a file but the argument passed contained the absolute path of the file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)



# Task 3 - more catting practice

The 'hacker' has to use the "cat" command to print the contents of the file named "flag" but this time the absolute path of the file is unknown. This file contains the flag.

## My solve

**Flag:** `pwn.college{4wqo2vkwf2xDxRW-JccbSm2OW1B.QXxcTN0wyM2AzNzEzW}`

I typed in the "cat" command with the absolute path to the file named "flag" passed as an argument with the command.

```bash
neelaypuranik@Neelays-Laptop:~$ ssh -i ~/key hacker@dojo.pwn.college
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/include/xen/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /usr/include/xen/flag
pwn.college{8sMqJdzPbXEC_LH4GND8GoNWIng.QXwITO0wyM2AzNzEzW}
```
This lead to the flag being printed.

## What I learned
- Learned how to use the cat command to print the contents of a file but the argument passed contained the absolute path of the file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 4 - grepping for a needle in a haystack

The 'hacker' has to use the "grep" command to search the file for lines containing the specified text. The command is of the structure: grep [string to be searched] [path of file to be searched]. The hacker has to search the given file and find the flag.

## My solve

**Flag:** `pwn.college{Qc5eWWkjybfYZgpPHRSjOqXGHOj.QX3EDO0wyM2AzNzEzW}`

I typed in the "grep" command along with the respective arguments.

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{Qc5eWWkjybfYZgpPHRSjOqXGHOj.QX3EDO0wyM2AzNzEzW}
```
This lead to the flag being printed.

## What I learned
- Learned how to use the cat command to print the contents of a file but the argument passed contained the absolute path of the file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 5 - comparing files

The 'hacker' has to use the "diff" command to compare the differences between two files stored in the /challenge directory.

## My solve

**Flag:** `pwn.college{wwlP0b9Ak8jsIH1ZbRulKc4FiWR.01MwMDOxwyM2AzNzEzW}`

I invoked the "diff" command along with the two different file names as the arguments to compare the differences between the two files.

```bash
hacker@commands~comparing-files:~$ cd /
hacker@commands~comparing-files:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~comparing-files:/$ cd /challenge
hacker@commands~comparing-files:/challenge$ ls
DESCRIPTION.md  decoys_and_real.txt  decoys_only.txt
hacker@commands~comparing-files:/challenge$ diff decoys_only.txt decoys_and_real.txt
56a57
> pwn.college{wwlP0b9Ak8jsIH1ZbRulKc4FiWR.01MwMDOxwyM2AzNzEzW}
```
There was only one difference between the two files. To the "decoys_only.txt" file, another line after line 56 was added in the second file named "decoys_and_real.txt". The added line contained the flag.

## What I learned
- Learned how to use the diff command to find the differences between two similar files.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 6 - listing files

The 'hacker' has to use the "ls" command to list down all the items present inside a directory and then find and run the renamed run file to discover the flag.

## My solve

**Flag:** `pwn.college{YEywdSXM0n6Tqx1AHjhBAxpxgaE.QX4IDO0wyM2AzNzEzW}`

I invoked the "ls" command to list down all the items present inside a directory and then saw the renamed run file and ran it.

```bash
hacker@commands~listing-files:~$ ls /challenge
31577-renamed-run-13260  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/31577-renamed-run-13260
Yahaha, you found me! Here is your flag:
pwn.college{YEywdSXM0n6Tqx1AHjhBAxpxgaE.QX4IDO0wyM2AzNzEzW}
```
This lead to the flag being printed

## What I learned
- Learned how to use the ls command to list down all the items present inside a directory.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 7 - touching files

The 'hacker' has to use the "touch" command to create two new files named "pwn" and "college" in the tmp directory, then run the command: "/challenge/run" to get the flag.

## My solve

**Flag:** `pwn.college{k5FEyVmUCS1ZXTaSEoc1fJrFv38.QXwMDO0wyM2AzNzEzW}`

I invoked the "touch" command twice inside the tmp directory to create the desired files, then ran the "/challenge/run" command.

```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{k5FEyVmUCS1ZXTaSEoc1fJrFv38.QXwMDO0wyM2AzNzEzW}
```
This lead to the flag being printed

## What I learned
- Learned how to use the "touch" command to create files in a directory.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 8 - removing files

The 'hacker' has to use the "rm" command to delete a file present in the home directory.

## My solve

**Flag:** `pwn.college{IYSR6AAdaN1sC2oeFw_9T6hP58U.QX2kDM1wyM2AzNzEzW}`

I invoked the "rm" command with the file name to be deleted as the argument. This lead to the file being deleted and I used the "ls" command to list down all the files present in the directory to make sure that the file is deleted, then I ran the "/challenge/check" command to print the flag.

```bash
hacker@commands~removing-files:~$ ls
delete_me  flag  r
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
flag  r
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{IYSR6AAdaN1sC2oeFw_9T6hP58U.QX2kDM1wyM2AzNzEzW}
```
This lead to the flag being printed

## What I learned
- Learned how to use the "rm" command to delete a file.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 9 - moving files

The 'hacker' has to use the "mv" command to move the file named "flag" present in the home directory into the "/tmp/hack-the-planet" directory.

## My solve

**Flag:** `pwn.college{8o2caP9f68F2x353_qpllPUPyz0.0VOxEzNxwyM2AzNzEzW}`

I invoked the "mv" command to move the "/flag" file from the home directory to the "/tmp/hack-the-planet" directory, then ran the command "/challenge/check".

```bash
hacker@commands~moving-files:~$ ls
flag  r
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{8o2caP9f68F2x353_qpllPUPyz0.0VOxEzNxwyM2AzNzEzW}
```
This lead to the flag being printed

## What I learned
- Learned how to use the "mv" command to move a file from one place to another.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 10 - hidden files

The 'hacker' has to use the "ls" command along with the argument -a to print out the files whose name begins with a "." since linux has a convention to not print these during "ls" and some other commands. Then he has to find the flag hidden as a dot-prepended file in the root directory.

## My solve

**Flag:** `pwn.college{IKyjfuKuS_O5_YvMLchmKiTyBPh.QXwUDO0wyM2AzNzEzW}`

I invoked the "ls" command with the "-a" argument, in the root directory, to list down all the files including the hidden ones (the ones whose name starts with a dot: ".") to find the flag stored in a dot-prepended file.

```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls
bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv           bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-2925222323759  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-2925222323759
pwn.college{IKyjfuKuS_O5_YvMLchmKiTyBPh.QXwUDO0wyM2AzNzEzW}
```
I then catted the file which lead to the flag being printed.

## What I learned
- Learned how to use the "ls" command with the "-a" argument to print hidden files.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 11 - An Epic Filesystem Quest

The 'hacker' has to use the system navigation and file handling commands to navigate through all the directories, collecting 'clues' which will lead him to the flag.

## My solve

**Flag:** `pwn.college{IKyjfuKuS_O5_YvMLchmKiTyBPh.QXwUDO0wyM2AzNzEzW}`

I invoked the "ls", "cat", and "cd" commands along with their respective arguments as needed and instructed to reach the flag

```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
MEMO  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin   challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat MEMO
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/include/linux/amba

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/include/linux/amba
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/amba$ ls
REVELATION  bus.h  clcd-regs.h  clcd.h  kmi.h  mmci.h  pl022.h  pl080.h  pl08x.h  pl093.h  serial.h  sp810.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/amba$ cat REVELATION
Yahaha, you found me!
The next clue is in: /opt/busybox/busybox-1.33.2/include/config/feature/verbose/cp
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/amba$ cd /opt/busybox/busybox-1.33.2/include/config/feature/verbose/cp
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/verbose/cp$ ls
POINTER  message.h
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/verbose/cp$ cat POINTER
Lucky listing!
The next clue is in: /usr/share/racket/pkgs/data-lib/data/compiled

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/verbose/cp$ cd /usr/share/racket/pkgs/data-lib/data/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/data-lib/data/compiled$ ls -a
.          gvector_rkt.dep  heap_rkt.zo           order_rkt.dep      skip-list_rkt.zo    union-find_rkt.dep
..         gvector_rkt.zo   interval-map_rkt.dep  order_rkt.zo       splay-tree_rkt.dep  union-find_rkt.zo
.EVIDENCE  heap_rkt.dep     interval-map_rkt.zo   skip-list_rkt.dep  splay-tree_rkt.zo
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/data-lib/data/compiled$ cat .EVIDENCE
Yahaha, you found me!
The next clue is in: /usr/local/lib/python3.8/dist-packages/networkx/algorithms/link_analysis/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/data-lib/data/compiled$ cd /usr/local/lib/python3.8/dist-packages/networkx/algorithms/link_analysis/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/networkx/algorithms/link_analysis/__pycache__$ ls
WHISPER  __init__.cpython-38.pyc  hits_alg.cpython-38.pyc  pagerank_alg.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/networkx/algorithms/link_analysis/__pycache__$ cat WHISPER
Yahaha, you found me!
The next clue is in: /opt/libslub/test

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/networkx/algorithms/link_analysis/__pycache__$ cd /opt/libslub/test
hacker@commands~an-epic-filesystem-quest:/opt/libslub/test$ ls
Makefile  libslub.gdb  test.c
hacker@commands~an-epic-filesystem-quest:/opt/libslub/test$ ls -a
.  ..  .README  Makefile  libslub.gdb  test.c
hacker@commands~an-epic-filesystem-quest:/opt/libslub/test$ cat .README
Tubular find!
The next clue is in: /usr/lib/python3.8/venv/scripts/common

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/libslub/test$ ls /usr/lib/python3.8/venv/scripts/common
Activate.ps1  GIST-TRAPPED  activate
hacker@commands~an-epic-filesystem-quest:/opt/libslub/test$ cat /usr/lib/python3.8/venv/scripts/common/GIST-TRAPPED
Tubular find!
The next clue is in: /usr/share/icons/ubuntu-mono-light/stock/16
The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/libslub/test$ cd /usr/share/icons/ubuntu-mono-light/stock/16
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-light/stock/16$ ls
ALERT
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-light/stock/16$ cat ALERT
Tubular find!
The next clue is in: /opt/linux/linux-5.4/include/config/associative
Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-light/stock/16$ ls /opt/linux/linux-5.4/include/config/associative
NOTE-TRAPPED  array.h
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-light/stock/16$ cat /opt/linux/linux-5.4/include/config/associative/NOTE-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{cAMhuOMTJOHEh8WPvDcr0hiNzxA.QX5IDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use the file handling and system navigation commands to find the flag.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 12 - making directories

The 'hacker' has to use the "mkdir" command to create a directory "/tmp/pwn" and cd into that directory. Then he has to create a file named "college" in the newly made directory.

## My solve

**Flag:** `pwn.college{YGYHn_VoN_DCdg5wKLFt_KnTfkc.QXxMDO0wyM2AzNzEzW}`

I used the "mkdir" command inside the root directory along with the argument "/tmp/pwn" to create a new directory. Then I cd'ed into that directory and used the "touch" command to create a file named college, then ran the "/challenge/run" command.
```bash
hacker@commands~making-directories:~$ ls
flag  r
hacker@commands~making-directories:~$ cd /
hacker@commands~making-directories:/$ mkdir /tmp/pwn
hacker@commands~making-directories:/$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{YGYHn_VoN_DCdg5wKLFt_KnTfkc.QXxMDO0wyM2AzNzEzW}
```
This lead to the flag being printed.

## What I learned
- Learned how to use the "mkdir" command to create a new directory.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 13 - finding files

The 'hacker' has to use the "find" command along with the argument "/" and "-name flag" to find all the files/directories named flag inside the root directory and try them out sequentially to find the flag.

## My solve

**Flag:** `pwn.college{oO-O_J5BVs0otChYktQoyg1LisS.QXyMDO0wyM2AzNzEzW}`

I used the "find" command along with the argument "/ -name flag" to find all files/directories named flag. Once I got the result, I went through each entry sequentially until I found the one with the flag stored.

```bash
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/home/hacker/flag
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/include/x86_64-linux-gnu/gap/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cd /usr/local/lib/python3.8/dist-packages/pwnlib/flag
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ ls
__init__.py  __pycache__  flag.py
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cd /usr/include/x86_64-linux-gnu/gap/flag
bash: cd: /usr/include/x86_64-linux-gnu/gap/flag: Not a directory
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cat /usr/include/x86_64-linux-gnu/gap/flag
pwn.college{oO-O_J5BVs0otChYktQoyg1LisS.QXyMDO0wyM2AzNzEzW}
```
This lead to the flag being printed.

## What I learned
- Learned how to use the "find" command to find files.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)


# Task 14 - linking files

The 'hacker' has to use the "ls" command with the "-s" argument to link the actual flag directory to the 'fake' flag directory then run the "/challenge/catflag" command to obtain the flag.

## My solve

**Flag:** `pwn.college{8GO07-3yJ-NIwAnvrSXg3mfkp0a.QX5ETN1wyM2AzNzEzW}`

I used the "ls -s /flag ~/not-the-flag" command to link the file "flag" in the root directory to the file "not-the-flag" in the home directory.
```bash
hacker@commands~linking-files:~$ ln -s /flag ~/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{8GO07-3yJ-NIwAnvrSXg3mfkp0a.QX5ETN1wyM2AzNzEzW}
```
This lead to the flag being printed.

## What I learned
- Learned how to use the "ls" command along with the respective arguments to symbolically link two files.
## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)
