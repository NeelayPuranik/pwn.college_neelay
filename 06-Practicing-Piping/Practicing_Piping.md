# Task 1 - Redirecting output
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

## My solve
**Flag:** `pwn.college{ooU7AAFGMKghqOI2V7EkmZtg-DC.QX0YTN0wyM2AzNzEzW}`

As mentioned in the description of this challenge, I used the echo command to print the letters "PWN" into a newly created file named "COLLEGE"

```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{ooU7AAFGMKghqOI2V7EkmZtg-DC.QX0YTN0wyM2AzNzEzW}
```

## What I learned
- Learned that there are ways to manipulate where the output of a command will end up.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 2 - Redirecting more output

Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!

## My solve
**Flag:** `pwn.college{UMOJjJycKU_TdkspKU2VnZH2nJ6.QX1YTN0wyM2AzNzEzW}`

I used the > command to redirect the output into the myflag file. One thing I noticed is that it still printed the info because it was stored on stderr which was not redirected and hence printed into the terminal.

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ ls
COLLEGE  flag  myflag  not-the-flag  r
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{UMOJjJycKU_TdkspKU2VnZH2nJ6.QX1YTN0wyM2AzNzEzW}
```

## What I learned
- Learned that there are stdout and stderr work seperately and can be redirected seperately.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 3 - Appending Output

To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

## My solve
**Flag:** `pwn.college{4NibVPv7QQRI35Ocx2z9oIWzPS6.QX3ATO0wyM2AzNzEzW}`

I used the >> command (append) to append the output of /challenge/run to the-flag. If I had used the > command then the output would have overwritted any previously stored data in the file which would have led to half of the flag being lost.

```bash
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ stdout >> /home/hacker/the-flag
bash: stdout: command not found
hacker@piping~appending-output:~$ ls
COLLEGE  flag  myflag  not-the-flag  r  the-flag
hacker@piping~appending-output:~$ cat the-flag
 |
\|/ This is the first half:
 v
pwn.college{4NibVPv7QQRI35Ocx2z9oIWzPS6.QX3ATO0wyM2AzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

## What I learned
- Learned that there are ways to combine the output of different commands into a single file for easy reference later on.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 4 - Redirecting errors

Let's put this into practice! In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions. You'll notice that nothing will be printed to the terminal, because you have redirected everything! You can find the instructions/feedback in instructions and the flag in myflag when you successfully pull this off!

## My solve
**Flag:** `pwn.college{41_iwpWExm0rHWqSXqReMZt87d0.QX3YTN0wyM2AzNzEzW}`

As mentioned in the description, I redirected the errors into the instructions file and the output to the myflag file.

```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{41_iwpWExm0rHWqSXqReMZt87d0.QX3YTN0wyM2AzNzEzW}
```

## What I learned
- Learned that each communication channel in linux is given a number called the file descriptor number. For input its 0, for output its 1, for errors its 2.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 5 - Redirecting input

You can do interesting things with a lot of different programs using input redirection! In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

## My solve
**Flag:** `pwn.college{AEDyANtJe4QBsYsPuB4Hw06RrGt.QXwcTN0wyM2AzNzEzW}`

I redirected the output from the echo command into a file named pwn using what I learned from the first task: (echo COLLEGE > PWN). Then I used input redirection to feed the /challenge/run command the contents of the PWN file as input: (/challenge/run < PWN)

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ PWN < /challenge/run
bash: PWN: command not found
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{AEDyANtJe4QBsYsPuB4Hw06RrGt.QXwcTN0wyM2AzNzEzW}
```

## What I learned
- Learned that input redirection can be used to give a command the contents of a file as input.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 6 - Grepping stored results

You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

In preparation for more complex levels, we want you to:

Redirect the output of /challenge/run to /tmp/data.txt.
This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
grep that for the flag!

## My solve
**Flag:** `pwn.college{gN_1skygTkjj8chU6bw89uq1QRF.QX4EDO0wyM2AzNzEzW}`

I redirected the output from the /challenge/run command to the file data.txt stored in the tmp directory and then used the grep command to search for all lines containing the string "pwn.college{" because thats what every flag contains. This lead to the flag being printed.
```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep "pwn.college{" /tmp/data.txt
pwn.college{gN_1skygTkjj8chU6bw89uq1QRF.QX4EDO0wyM2AzNzEzW}
```

## What I learned
- Learned how different commands can be used in unison to keep records and browse through them.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 7 - Grepping live output

It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can do this by using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:

```bash
hacker@dojo:~$ echo no-no | grep yes
hacker@dojo:~$ echo yes-yes | grep yes
yes-yes
hacker@dojo:~$ echo yes-yes | grep no
hacker@dojo:~$ echo no-no | grep no
no-no
```

Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. grep for the flag!

## My solve
**Flag:** `pwn.college{Iq2x_kvpUNcFilxrxikg09h8xUj.QX5EDO0wyM2AzNzEzW}`

As mentioned in the challenge description, I used the [].... | grep".."] command to grep the live output of the "/challenge/run" for the flag.
```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep "pwn.college{"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Iq2x_kvpUNcFilxrxikg09h8xUj.QX5EDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to grep the output of a command directly instead of storing the output in a file and then grepping it.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 8 - Grepping errors

You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

Try it now! Like the last level, this level will overwhelm you with output, but this time on standard error. grep through it to find the flag!

## My solve
**Flag:** `pwn.college{k69ZjI7vA8aWhOsSi54ZC1S2Vnu.QX1ATO0wyM2AzNzEzW}`

I used the "2>& 1" command to redirect the stderr to stdout then used the same technique used in the previous challenge to grep through the output (error and output combined in this case).
```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep "pwn.college{"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{k69ZjI7vA8aWhOsSi54ZC1S2Vnu.QX1ATO0wyM2AzNzEzW}
```

## What I learned
- Learned how to redirect one communication channel into another to bypass some limitations.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 9 - Filtering with grep -v

Sometimes, the only way to filter to just the data you want is to filter out the data you don't want. In this challenge, /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags (containing the word DECOY somewhere in the flag) mixed in with the real flag. You'll need to filter out the decoys while keeping the real flag!

Use grep -v to filter out all the lines containing "DECOY" and reveal the real flag!

## My solve
**Flag:** `pwn.college{U8aFDT4VvWwtTGMbqd6SxCL3hVo.0FOxEzNxwyM2AzNzEzW}`

I used the grep -v command to filter out all the lines containing decoy so the line containing the actual flag only got printed.
```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v "DECOY"
pwn.college{U8aFDT4VvWwtTGMbqd6SxCL3hVo.0FOxEzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use arguments to invert what a command does, .i.e., use grep -v to find lines which do not contain a certain word.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 10 - Duplicating piped data with tee

Now, you try it! This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!

## My solve
**Flag:** `pwn.college{sOpJHL7yf5xLTUsMpO1t39cXH_t.QXxITO0wyM2AzNzEzW}`

I used the command "/challenge/pwn | tee /tmp/data.txt | /challenge/college" to forward a copy of the output into the file "/tmp/data.txt" while also piping the output to /challenge/college. I then catted the data.txt file to read the secret key. The second time I invoked the command "/challenge/pwn --secret sOpJHL7y | /challenge/college" making sure to pass the secret key which lead to the flag being printed.
```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee /tmp/data.txt | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat /tmp/data.txt
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "sOpJHL7y"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret sOpJHL7y | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{sOpJHL7yf5xLTUsMpO1t39cXH_t.QXxITO0wyM2AzNzEzW}
```

## What I learned
- Learned how to duplicate a command output to a file as well as piping it to another command using tee placed between the output generator and the command which needs it as input


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 11 - Process substitution for input

Now for your challenge! Recall what you learned in the diff challenge from Comprehending Commands. In that challenge, you diffed two files. Now, you'll diff two sets of command outputs: /challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag.

Use process substitution with diff to compare the outputs of these two programs and find your flag!

## My solve
**Flag:** `pwn.college{Id3YbES7zcGu6eIim8UohLreCci.0lNwMDOxwyM2AzNzEzW}`

I used process substitution to pass the stdout of two commands: "/challenge/print_decoys" and "/challenge/print_decoys_and_flag" to the diff command to compare their differences. Once of their differences was the flag.
```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
71a72
> pwn.college{Id3YbES7zcGu6eIim8UohLreCci.0lNwMDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use the live output of any command anywhere as a file.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 12 - Writing to multiple programs

Now it's your turn! In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands! Scroll back through the previous challenges "Duplicating piped data with tee" and "Process substitution for input" if you need a refresher on this method.

## My solve
**Flag:** `pwn.college{wh4e4AHzTyIsf6Gfd8ay-QeI6aM.QXwgDN1wyM2AzNzEzW}`

I used tee together with process substitution. tee duplicated the output steam into two file.
```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{wh4e4AHzTyIsf6Gfd8ay-QeI6aM.QXwgDN1wyM2AzNzEzW}
```

## What I learned
- Learned that tee can write to process substitutions as well.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 13 - Split-piping stderr and stdout

Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of >(), 2>, and |. How to do it is a task I'll leave to you.

In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program

Go get the flag!

## My solve
**Flag:** `pwn.college{EGw3XOhitm9JLwLeVGbjO4BKfTF.QXxQDM2wyM2AzNzEzW}`

I used the 2> command to redirect the stderr as stdin to the file /challenge/the using process substitution. I then used the pipe (|) to send FD 1 into /challenge/planet.
```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >( /challenge/the ) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{EGw3XOhitm9JLwLeVGbjO4BKfTF.QXxQDM2wyM2AzNzEzW}
```

## What I learned
- Learned that several redirection methods can be employed to get the desired result like done in this case.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 14 - Named pipes

This challenge will be a simple introduction to FIFOs. You'll need to create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it. If you're successful, /challenge/run will write the flag into the FIFO! Go do it!

## My solve
**Flag:** `pwn.college{8mlEcZmHCHhGdq6SqqY3dRY3EQq.01MzMDOxwyM2AzNzEzW}`

I created a named pipe called flag_fifo in the tmp directory. I then redirected the output of /challenge/run into flag_fifo then catted the file to get the flag.
```bash
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
mkfifo: cannot create fifo '/tmp/flag_fifo': File exists
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{8mlEcZmHCHhGdq6SqqY3dRY3EQq.01MzMDOxwyM2AzNzEzW}
```

## What I learned
- Learned that the user can create permanent named pipes which are always stored in the memory instead of creating temporary pipes.


## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

