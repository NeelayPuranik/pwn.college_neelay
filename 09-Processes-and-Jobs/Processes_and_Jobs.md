# Task 1 - Listing Processes
In this level, I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory! But I also launched it, so you can find it in the running process list, figure out the filename, and relaunch it directly for the flag! Good luck!

## My solve
**Flag:** `pwn.college{ApuqSPZqgZyTI_hqBotuGyfm5Yk.QX4MDO0wyM2AzNzEzW}`

As mentioned in the task description, I passed the command "ps -efww". The "ef" part of the argument tells the ps command to list every process in full format and the "ww" part of the argument tells the command to not truncate the output to match the size of the terminal.

```bash
hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 10:11 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 10:11 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 10:11 ?        00:00:00 /challenge/4123-run-2858
root         135     132  0 10:11 ?        00:00:00 sleep 6h
hacker       137       0  0 10:12 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       143     137  0 10:12 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       152     143  0 10:14 pts/0    00:00:00 ps -efww
hacker@processes~listing-processes:~$ /challenge/4123-run-2858
Yahaha, you found me! Here is your flag:
pwn.college{ApuqSPZqgZyTI_hqBotuGyfm5Yk.QX4MDO0wyM2AzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

## What I learned
- Learned that just like the ls command, the ps command is used to print all the running processes inside a terminal.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 2 - Killing Processes
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission. Good luck.

## My solve
**Flag:** `pwn.college{QQcfhKNyeGprvNkiAgMwoFVrAEl.QXyQDO0wyM2AzNzEzW}`

I observed that in the challenge description, when the sleep command was to be killed, the user used the grep command to directly get the processes which had the sleep keyword instead of manually search through all the processes. Likewise, I also ran the command "ps -ef | grep dont_run" to directly get the processes with the string "dont_run" in them. I then found the desired process which had to be killed and used the kill command to terminate the process. Then, I ran the "/challenge/run" command to get the flag.

```bash
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker       136     135  0 10:20 ?        00:00:00 /challenge/dont_run
hacker       170     160  0 10:21 pts/1    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{QQcfhKNyeGprvNkiAgMwoFVrAEl.QXyQDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use ps and grep together to find the desired process and then use the kill command to terminate it

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 3 - Interrupting Processes
You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

Try it here! /challenge/run will refuse to give you the flag until you interrupt it. Good luck!

## My solve
**Flag:** `pwn.college{cSXGlNwXZvezOzYn0GLDTOdLKtX.QXzQDO0wyM2AzNzEzW}`

I first ran the "/challenge/run" command and then interrupted it using ctrl+c to obtain the flag.

```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{cSXGlNwXZvezOzYn0GLDTOdLKtX.QXzQDO0wyM2AzNzEzW}
```

## What I learned
- Learned that some commands which clog up the terminal can be terminated by pressing ctrl+c which sends an interrupt to the process causing it to cleanly exit

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 4 - Killing Misbehaving Processes
In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which (like in the Practicing Piping FIFO challenge) /challenge/run wants to write your flag. You need to kill this process.

## My solve
**Flag:** `pwn.college{8jIls-rcZuFoiWy2KZoz42ng3Rm.0FNzMDOxwyM2AzNzEzW}`

First of all, I ran the command "ps -ef | grep decoy" to get all the processes with decoy in their name. Then, I killed the desired decoy process using the kill command, after which, I ran the "/challenge/run" command. This command sent the flag to /tmp/flag_fifo. I catted /tmp/flag_fifo to obtain the flag.
```bash
hacker@processes~killing-misbehaving-processes:~$ ps -ef | grep decoy
root         139       1  0 10:52 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       142     139  0 10:52 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       175     165  0 10:54 pts/1    00:00:00 grep --color=auto decoy
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{8jIls-rcZuFoiWy2KZoz42ng3Rm.0FNzMDOxwyM2AzNzEzW}
^C
hacker@processes~killing-misbehaving-processes:~$
```

## What I learned
- Learned how to kill misbehaving processes

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 5 - Suspending Processes
You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this works and, in the next level, we'll figure out how to resume those suspended processes!

This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!

## My solve
**Flag:** `pwn.college{EIohN0qsWuo0Qq1_y0yhiK_vrC2.QX1QDO0wyM2AzNzEzW}`

I first ran the /challenge/run command and then pressed ctrl+z to suspend it. I then ran the same command again which lead to the flag being printed.

```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         155     146  0 11:13 pts/1    00:00:00 bash /challenge/run
root         157     155  0 11:13 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         155     146  0 11:13 pts/1    00:00:00 bash /challenge/run
root         162     146  0 11:14 pts/1    00:00:00 bash /challenge/run
root         164     162  0 11:14 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{EIohN0qsWuo0Qq1_y0yhiK_vrC2.QX1QDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to suspend commands instead of completely terminating them

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 6 - Resuming Processes
Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

Go try it out! This challenge's run needs you to suspend it, then resume it. Good luck!

## My solve
**Flag:** `pwn.college{8kqtBt7OdT9JGUTCn_r3Z0HyIgC.QX2QDO0wyM2AzNzEzW}`

Firstly, I ran the /challenge/run command and then suspended it using ctrl+z. Then I ran the command fg to bring the suspended process back into the foreground of the terminal. This printed the flag.

```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{8kqtBt7OdT9JGUTCn_r3Z0HyIgC.QX2QDO0wyM2AzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

## What I learned
- Learned how to bring back suspended commands

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 7 - Backgrounding Processes
You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command! This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

This level's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background!

## My solve
**Flag:** `pwn.college{AJLraGeVsvtTIbrHwV97bFSk8dL.QX3QDO0wyM2AzNzEzW}`

I first ran the command "/challenge/run" and then pressed ctrl+z to suspend it. Then I ran the command bg to keep it running in the background. I then ran /challenge/run again to get the flag.

```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         153 S+   bash /challenge/run
root         155 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         153 S    bash /challenge/run
root         163 S    sleep 6h
root         164 S+   bash /challenge/run
root         166 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{AJLraGeVsvtTIbrHwV97bFSk8dL.QX3QDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to send a suspended command to the background

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 8 - Foregrounding Processes
Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level will walk you through that!

## My solve
**Flag:** `pwn.college{EK1voxaeyi2IOvo8zXIwttPClY0.QX4QDO0wyM2AzNzEzW}`

I first ran the command /challenge/run to get instructions. I then pressed ctrl+z to suspend the process and then ran bg to background it. Then I ran fg to bring the process to the foreground which got me the flag.

```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{EK1voxaeyi2IOvo8zXIwttPClY0.QX4QDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to foreground a backgrounded process

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 9 - Starting Backgrounded Processes
Now it's your turn to practice! Launch /challenge/run backgrounded for the flag!

## My solve
**Flag:** `pwn.college{kNHSiekXIVyk6OVbU5SAT8nIuBg.QX5QDO0wyM2AzNzEzW}`

I ran the command /challenge/run with "&" appended at its end: "/challenge/run &" to start the process directly in the background.

```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 171
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{kNHSiekXIVyk6OVbU5SAT8nIuBg.QX5QDO0wyM2AzNzEzW}
^C
[1]+  Done                    /challenge/run
```

## What I learned
- Learned how to directly start a process in the background

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)


# Task 10 - Process Exit Codes
In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument. Good luck!

## My solve
**Flag:** `pwn.college{Av-sniuxlznEuax1ijsyMc-Ukwa.QX5YDO1wyM2AzNzEzW}`

I ran the command /challenge/get-code so that it could exit with its exit code. Then I ran echo $? to get the exit code of the most recently executed command. I then passed that exit code as an argument to the command /challenge/submit-code to get the flag.

```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
168
hacker@processes~process-exit-codes:~$ /challenge/submit-code 168
CORRECT! Here is your flag:
pwn.college{Av-sniuxlznEuax1ijsyMc-Ukwa.QX5YDO1wyM2AzNzEzW}
```

## What I learned
- Learned how to obtain the exit codes of a given process

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)
