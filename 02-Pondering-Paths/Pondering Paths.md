# Task 1 - The Root

The 'hacker' has to find the flag stored in the "pwn" directory.

## My solve

**Flag:** `pwn.college{UxXdq5tD20aWEJsFNSEHoDCjGkr.QX4cTO0wyM2AzNzEzW}`

I ran the "/pwn" command in the terminal which executed the pwn program stored in the "root" directory. This lead to the flag being printed.
```bash

hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{UxXdq5tD20aWEJsFNSEHoDCjGkr.QX4cTO0wyM2AzNzEzW}

```

## What I learned
- Learned how to write the full directory including root (/) for a file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 2 - Program and absolute paths

The 'hacker' has to execute the "run" file stored in the "challenge" directory which is in turn stored in the "root" directory.

## My solve

**Flag:** `pwn.college{osMy2bowB80ZRd6lsolUaKXQH0Q.QX1QTN0wyM2AzNzEzW}`

I ran the "/challenge/run" command in the terminal which executed the run program stored in the "challenge" directory which is in turn stored in the "root" directory. This lead to the flag being printed.

```bash

hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{osMy2bowB80ZRd6lsolUaKXQH0Q.QX1QTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 3 - Position thy self

The 'hacker' has to execute the "run" file stored in the "challenge" directory from another different directory specificed (the "etc" directory in this case).

## My solve

**Flag:** `pwn.college{UtZ6ofSeDqJ38U5Bl7OVo4c9FL0.QX2QTN0wyM2AzNzEzW}`

I ran the "/challenge/run" command from the "etc" directory in the terminal which executed the run program stored in the "challenge" directory from the "etc" directory which is in turn stored in the "root" directory. This lead to the flag being printed.

```bash

hacker@paths~position-thy-self:~$ cd /
hacker@paths~position-thy-self:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~position-thy-self:/$ cd /challenge
hacker@paths~position-thy-self:/challenge$ ls
DESCRIPTION.md  run
hacker@paths~position-thy-self:/challenge$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/challenge$ cd /etc
hacker@paths~position-thy-self:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UtZ6ofSeDqJ38U5Bl7OVo4c9FL0.QX2QTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory from another directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 4 - Positioning elsewhere

The 'hacker' has to execute the "run" file stored in the "challenge" directory from another different directory specificed (the "var" directory in this case).

## My solve

**Flag:** `pwn.college{s8AKVaKht-bTjSeKKa-vW9eZXOv.QX3QTN0wyM2AzNzEzW}`

I ran the "/challenge/run" command from the "var" directory in the terminal which executed the run program stored in the "challenge" directory from the "var" directory which is in turn stored in the "root" directory. This lead to the flag being printed.

```bash

hacker@paths~position-elsewhere:/$ cd /
hacker@paths~position-elsewhere:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~position-elsewhere:/$ cd /challenge
hacker@paths~position-elsewhere:/challenge$ ls
DESCRIPTION.md  run
hacker@paths~position-elsewhere:/challenge$ ./run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:/challenge$ cd /var
hacker@paths~position-elsewhere:/var$ ./run
bash: ./run: Is a directory
hacker@paths~position-elsewhere:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{s8AKVaKht-bTjSeKKa-vW9eZXOv.QX3QTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory from another directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 5 - Positioning yet elsewhere

The 'hacker' has to execute the "run" file stored in the "challenge" directory from another different directory specificed (the "/var/lib/apt/lists" directory in this case).

## My solve

**Flag:** `pwn.college{MRhwzljgeFLxhquFlLa7Jaes1sa.QX4QTN0wyM2AzNzEzW}`

I ran the "/challenge/run" command from the "/var/lib/apt/lists" directory in the terminal which executed the run program stored in the "challenge" directory from the "/var/lib/apt/lists" directory which is in turn stored in the "root" directory. This lead to the flag being printed.

```bash

hacker@paths~position-yet-elsewhere:~$ cd /
hacker@paths~position-yet-elsewhere:/$ cd /challenge
hacker@paths~position-yet-elsewhere:/challenge$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:/challenge$ cd /var/lib/apt/lists directory
bash: cd: too many arguments
hacker@paths~position-yet-elsewhere:/challenge$ cd /var/lib/apt/lists
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{MRhwzljgeFLxhquFlLa7Jaes1sa.QX4QTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory from another directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 6 - implicit relative paths, from /

The 'hacker' has to execute the "run" file stored in the "challenge" directory using a relative directory with respect to the root directory.

## My solve

**Flag:** `pwn.college{gmkUJjo0i7bptUi2O5ACZuWcQS2.QX5QTN0wyM2AzNzEzW}`

I ran the "challenge/run" command in the terminal which executed the run program stored in the "challenge" directory with respect to the "root" directory. This lead to the flag being printed.

```bash

hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gmkUJjo0i7bptUi2O5ACZuWcQS2.QX5QTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory using a relative path to that directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 7 - explicit relative paths, from /

The 'hacker' has to execute the "run" file stored in the "challenge" directory using a explicit relative directory with respect to the root directory.

## My solve

**Flag:** `pwn.college{gT16G_h48mR6zOOdtwtCO4nOefx.QXwUTN0wyM2AzNzEzW}`

I ran the "challenge/run" command in the terminal which executed the run program stored in the "challenge" directory with respect to the "root" directory. This lead to the flag being printed.

```bash

hacker@paths~explicit-relative-paths-from-:/challenge$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gT16G_h48mR6zOOdtwtCO4nOefx.QXwUTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory using a explicit relative path to that directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 8 - implicit relative path

The 'hacker' has to execute the "run" file stored in the "challenge" directory using a explicit relative directory with respect to the challenge directory.

## My solve

**Flag:** `pwn.college{sMVqLOV-ssAFPSe7yTmUf_5weLg.QXxUTN0wyM2AzNzEzW}`

I ran the "./run" command in the terminal which executed the run program stored in the "challenge" directory. This lead to the flag being printed.

```bash

hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~implicit-relative-path:/$ ./challenge/run
Incorrect...
You are not currently in the /challenge directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{sMVqLOV-ssAFPSe7yTmUf_5weLg.QXxUTN0wyM2AzNzEzW}

```

## What I learned
- Learned how to execute a file stored in a directory using a explicit relative path to that directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)


# Task 9 - home sweet home

The 'hacker' has to execute the command "/challenge/run [argument]" which will write the contents of the file "run" into the file whose directory is mentioned in the argument passed along with the command. The command will then print the contents of the file.

## My solve

**Flag:** `pwn.college{EwT12jjeRjjr4yYbWPO1zETdYxp.QXzMDO0wyM2AzNzEzW}`

I ran the "/challenge/run ~/r" command in the terminal which copied the contents of "run" into the file named "r" in the home directory and executed the file. This lead to the flag being printed.

```bash

hacker@paths~home-sweet-home:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~home-sweet-home:/$ /challenge/run ~/r
Writing the file to /home/hacker/r!
... and reading it back to you:
pwn.college{EwT12jjeRjjr4yYbWPO1zETdYxp.QXzMDO0wyM2AzNzEzW}

```

## What I learned
- Learned how to invoke a command with a file path as an argument.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)
