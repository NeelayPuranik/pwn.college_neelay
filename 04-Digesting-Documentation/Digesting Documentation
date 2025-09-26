# Task 1 - Learning from Documentation
The "hacker" has to invoke the command "/challenge/challenge" with the argument "--giveflag".

## My solve
**Flag:** `pwn.college{wbqqvSOaxF4uJqPZt8uR8yVfuMd.QX0ITO0wyM2AzNzEzW}`

I realised that I cannot just run the "/challenge/challenge" command without an argument to get the flag so I pass the argument "--giveflag" along with the command to obtain the flag.
```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{wbqqvSOaxF4uJqPZt8uR8yVfuMd.QX0ITO0wyM2AzNzEzW}
```

## What I learned
- Learned that arguments change how a command behaves and are essential to get the desired output
- Learned that problems can be solved by carefully going through documentation.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)


# Task 2 - Learning Complex Usage
The "hacker" has to invoke the command "/challenge/challenge" with the argument "--giveflag" and this argument also has needs the file path to be passed as an argument.

## My solve
**Flag:** `pwn.college{4wqo2vkwf2xDxRW-JccbSm2OW1B.QXxcTN0wyM2AzNzEzW}`

At first, I was not clear where the flag was stored, so I used the "ls" command to print all the files in the home directory. Luckily, the flag was in the home directory only and therefore I then ran the command "/challenge/challenge --printfile ~/key". This command has two arguments: one is the "--printfile" argument and the other is the "~/flag" argument. I used "~" instead of writing the whole path for the flag as it saves time.

```bash
hacker@man~learning-complex-usage:~$ ls
flag  not-the-flag  r
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile ~/flag
Correct argument! Here is the /home/hacker/flag file:
pwn.college{4wqo2vkwf2xDxRW-JccbSm2OW1B.QXxcTN0wyM2AzNzEzW}
```

## What I learned
- Learned how to pass two arguments along with the command.
- Learned that exploring yourself can lead to the problem being solved. External help is not always needed.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)


# Task 3 - Reading Manuals
The "hacker" has to use the "man" command to find out more about the "challenge" command. In the manual page for the "challenge" command, the argument to get the flag will be mentioned.

## My solve
**Flag:** `pwn.college{AQ-mQvuAm8yRJimEvrcNCjSI143.QX0EDO0wyM2AzNzEzW}`

Initially, as instructed, I used the "man" command and passed the command I wanted the manual on ("Challenge") as an argument. The manual page popped up and I went through it. It said that I had to pass a specifc argument "--mvumyi NUM" with NUM being 814 to obtain the flag, so I went ahead and did that.

```bash
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --fortune
Don't relax!  It's only your tension that's holding you together.
hacker@man~reading-manuals:~$ /challenge/challenge --mvumyi 814
Correct usage! Your flag: pwn.college{AQ-mQvuAm8yRJimEvrcNCjSI143.QX0EDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to gather information on a command through the linux terminal itself without referring to any external document.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)


# Task 4 - Searching Manuals
The "hacker" has to use the "man" command to find out more about the "challenge" command. He then has to navigate the manual page to find the argument for printing the flag.

## My solve
**Flag:** `pwn.college{MY83IBfNi0Pcej643xCB-EaPhOQ.QX1EDO0wyM2AzNzEzW}`

Like the last task, I used the "man" command with the argument as "challenge" to open the manual for the challenge command. I then thought that the argument to print the flag will most probably contain the word "flag" in its description. Therefore I typed "/flag" to search for the word flag in the manual. I got several hits and used the "n" key to naviate to the needed argument.

```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --uyuhdt
Initializing...
Correct usage! Your flag: pwn.college{MY83IBfNi0Pcej643xCB-EaPhOQ.QX1EDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to navigate the manual page of a command to find the desired information.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)


# Task 5 - Searching For Manuals
The 'hacker' has to use the "man" command to find out more about the "man" command itself so that the 'hacker' can figure out how to search for manual pages containing specific words inorder to obtain the flag.

## My solve
**Flag:** `pwn.college{Qus21x436wuyMIzgRLjsVSnySto.QX2EDO0wyM2AzNzEzW}`

I pass "man" as an argument to the "man" command. This resulted in the manual page for the "man" command being displayed. I then went through the manual to find the argument which allows me to search for certain keywords in manual pages. I found out that it is "-k [keyword]". I then invoked the command "man -k flag" to get the manual with the flag keyword. I then invoked the command "/challenge/challenge --usxwuy 214" as mentioned in the manual page for the challenge command to obtain the flag.

```bash
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
usxwuyzgjs (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man usxwuyzgjs
hacker@man~searching-for-manuals:~$ /challenge/challenge --usxwuy 214
Correct usage! Your flag: pwn.college{Qus21x436wuyMIzgRLjsVSnySto.QX2EDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to navigate through and search for the desired manual pages.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)


# Task 6 - Helpful Programs
The 'hacker' has to use the "--help" argument along with the "/challenge/challenge" command to obtain more information on the challenge command in order to get the flag.

## My solve
**Flag:** `pwn.college{cl_LlXZsspviWi3tiXkYaFN2h6V.QX3IDO0wyM2AzNzEzW}`

I passed the "--help" argument along with the command ("/challenge/challenge") I needed more information on. This lead to the arguments associated with the given command being printed. I then went through this list to obtain the desired argument. I then invoked the command "/challenge/challenge -p" as per the information given in the help menu. I then invoked the "/challenge/challenge -g 326" command.

```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 326
hacker@man~helpful-programs:~$ /challenge/challenge -g 326
Correct usage! Your flag: pwn.college{cl_LlXZsspviWi3tiXkYaFN2h6V.QX3IDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use the "--help" argument to get more details on the commands.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)


# Task 7 - Help for Builtins
The 'hacker' to use the builtin help command to find out more about the challenge command to get the flag.

## My solve
**Flag:** `pwn.college{sls5dK1csb9ndvK7Nd-D6fL2s4Y.QX0ETO0wyM2AzNzEzW}`

I pass the "help" builtin with "challenge" as the argument to get more info on the command. It told me to invoke the "challenge" command with the argument "--secret sls5dK1c" to get the flag.

```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "sls5dK1c".
hacker@man~help-for-builtins:~$ challenge --secret sls5dK1c
Correct! Here is your flag!
pwn.college{sls5dK1csb9ndvK7Nd-D6fL2s4Y.QX0ETO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use the builtin "help" command to find more information on the commands.

## References
- [pwn.college](https://pwn.college/linux-luminarium/man/)
