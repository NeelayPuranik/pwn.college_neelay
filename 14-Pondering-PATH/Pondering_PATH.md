# Task 1 - The PATH Variable
In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command!

## My solve
**Flag:** `pwn.college{INtDUzwZFnpciDjJphhm36z4A3i.QX2cDM1wyM2AzNzEzW}`

I changed the PATH to nil (""), i.e., the path where the shell will search for the rm command is set to nil so the rm command's directory cannot be found by any child processes. Therefore, when I ran the /challenge/run command, it could not remove the flag and ended up printing it.

```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{INtDUzwZFnpciDjJphhm36z4A3i.QX2cDM1wyM2AzNzEzW}
```

## What I learned
- Learned how to exploit the PATH shell variable to obtain the desirable output

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)


# Task 2 - Setting PATH
This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. Good luck!

## My solve
**Flag:** `pwn.college{o3QKh4SDM9pL4CyJtXL5GJGwEbO.QX1cjM1wyM2AzNzEzW}`

I changed the PATH to "/challenge/more_commands/" so that bash searches for commands in that directory. Then, I ran the command "/challenge/run" which invoked the win command by name. The win command ran by its name because the PATH was set to where the win command was stored.

```bash
hacker@path~setting-path:~$ PATH="/challenge/more_commands/"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{o3QKh4SDM9pL4CyJtXL5GJGwEbO.QX1cjM1wyM2AzNzEzW}
```

## What I learned
- Learned how to set the PATH shell variable to a specific directory
## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)


# Task 3 - Finding Commands
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory!

## My solve
**Flag:** `pwn.college{gtN-kR5QDa-Ux5WxcMwRa6AWUAO.01NzEzNxwyM2AzNzEzW}`

I used the which command along with the argument "win" to obtain the directory where the command "win" is stored. Upon finding that, I cd'ed to that directory and used ls to list all contents that directory. This directory contained the flag which reconfirmed that I was in the correct directory. I then catted the flag file to get the flag.

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/23292/win
hacker@path~finding-commands:~$ cd /challenge/paths/23292
hacker@path~finding-commands:/challenge/paths/23292$ ls
flag  win
hacker@path~finding-commands:/challenge/paths/23292$ cat flag
pwn.college{gtN-kR5QDa-Ux5WxcMwRa6AWUAO.01NzEzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use the which command to obtain the directory where a command is stored

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)


# Task 4 - Adding Commands
Previously, the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!

## My solve
**Flag:** `pwn.college{4GyzmO1qWqxOYy9nSZWoiWXZQ4l.QX2cjM1wyM2AzNzEzW}`

I first used the touch command to create a file named win. Then, I used the command which to find the location of the cat command. I, then, put the command "/run/dojo/bin/cat /flag" into win. This command contained the absolute path to the cat command so changing the PATH later would not make a difference. After that, I made win executable. Lastly, I ran /challenge/run to obtain the flag.

```bash
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ ls
COLLEGE  PWN  flag  flag_fifo  instructions  myflag  not-the-flag  pwn_out.txt  r  solve.sh  the-flag  win  x.sh
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ echo '/run/dojo/bin/cat /flag' > win
hacker@path~adding-commands:~$ chmod +x win
hacker@path~adding-commands:~$ PATH="$pwd"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{4GyzmO1qWqxOYy9nSZWoiWXZQ4l.QX2cjM1wyM2AzNzEzW}
```

## What I learned
- Learned how to combine making shells with editing the PATH shell variable to obtain the desirable output

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)


# Task 5 - Hijacking Commands
Armed with your knowledge, you can now carry out some shenanigans. This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you.

How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it. What else can you create?

## My solve
**Flag:** `pwn.college{4GyzmO1qWqxOYy9nSZWoiWXZQ4l.QX2cjM1wyM2AzNzEzW}`

I first created a fake rm command which actually contained a command to print the flag. I then made it executable and changed PATH to search through a directory which only contained the fake rm command. Therefore, when I ran /challenge/run, it printed the flag instead of removing it

```bash
hacker@path~hijacking-commands:~$ ls
COLLEGE  PWN  flag  flag_fifo  instructions  myflag  not-the-flag  pwn_out.txt  r  solve.sh  the-flag  win  x.sh
hacker@path~hijacking-commands:~$ echo '#!/bin/bash' > rm
hacker@path~hijacking-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~hijacking-commands:~$ echo '/run/dojo/bin/cat /flag' >> rm
hacker@path~hijacking-commands:~$ echo 'exit 0' >> rm
hacker@path~hijacking-commands:~$ chmod +x rm
hacker@path~hijacking-commands:~$ PATH="$pwd"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{M2-mTeJkrL0nxVtyUKO9qTt6gYD.QX3cjM1wyM2AzNzEzW}
```

## What I learned
- Learned how to change existing commands to behave in a malicious manner

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)
