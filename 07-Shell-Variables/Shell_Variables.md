# Task 1 - Printing Variables
Let's start with printing variables out. The /challenge/run program will not, and cannot, give you the flag, but that's okay, because the flag has been put into the variable called "FLAG"! Just have your shell print it out!

## My solve
**Flag:** `pwn.college{8i1ccanzbIkUtHvXkZyzzYNiDUi.QX3UTN0wyM2AzNzEzW}`

I used the echo command along with the argument $FLAG to print the value stored in the variable flag.

```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{8i1ccanzbIkUtHvXkZyzzYNiDUi.QX3UTN0wyM2AzNzEzW}
```

## What I learned
- Learned that the linux shell supports variables and commands like echo can be used to print their values.

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 2 - Setting Variables
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

## My solve
**Flag:** `pwn.college{Mz87nJ6Ya4lYZwqmPmdVW7HCg0p.QX5UTN0wyM2AzNzEzW}`

I used the command "PWN=COLLEGE" to create and set the value of the variable PWN as COLLEGE.

```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Mz87nJ6Ya4lYZwqmPmdVW7HCg0p.QX5UTN0wyM2AzNzEzW}
```

## What I learned
- Learned that variables can be created in the shell.

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 3 - Multi-word Variables
In this level, you'll need to set the variable PWN to COLLEGE YEAH. Good luck!

## My solve
**Flag:** `pwn.college{4syNmKmK-l0u5F3bDmX3VKGvq9j.QXwYTN0wyM2AzNzEzW}`

I used the command [PWN="COLLEGE YEAH"] to create and set the value of the variable PWN as "COLLEGE YEAH".

```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4syNmKmK-l0u5F3bDmX3VKGvq9j.QXwYTN0wyM2AzNzEzW}
```

## What I learned
- Learned that variables can store multi-word values.

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 4 - Exporting Variables

In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported (e.g., not inherited by /challenge/run). Good luck!

## My solve
**Flag:** `pwn.college{cEg6u8f5aif4Wcl1Nl7bCLH99uq.QXyYTN0wyM2AzNzEzW}`

I invoked the "export PWN=COLLEGE" and the "COLLEGE=PWN" commands to create a global variable PWN which stores COLLEGE and a local variable COLLEGE which stores PWN.

```bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{cEg6u8f5aif4Wcl1Nl7bCLH99uq.QXyYTN0wyM2AzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## What I learned
- Learned that variables are of two types: global and local.
- Local variables are good for security since sensitive information does not leak out.

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 5 - Printing Exported Variables

Try the env command: it'll print out every exported variable set in your shell, and you can look through that output to find the FLAG variable!

## My solve
**Flag:** `pwn.college{QqxyJOR9vdwW2hkmGgncH-VQM5f.QX4UTN0wyM2AzNzEzW}`

I invoked the "env" command to print out all the exported variables out of which one was the flag variable which contained the flag.

```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=14b33eb12806280f1580a43ae2d5b982b9c72bf1e787f4aaac41947c68786e8d
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{QqxyJOR9vdwW2hkmGgncH-VQM5f.QX4UTN0wyM2AzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

## What I learned
- Learned that there are multiple ways to access variables in bash.

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 6 - Storing Command Output

Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!

## My solve
**Flag:** `pwn.college{Mg1KC-9tWMBDzaJvy_DNL7Je891.QX1cDN1wyM2AzNzEzW}`

I invoked the "PWN=$(/challenge/run)" command to store the output of the command "/challenge/run" into the variable PWN. Then I printed the contents of the variable.

```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{Mg1KC-9tWMBDzaJvy_DNL7Je891.QX1cDN1wyM2AzNzEzW}
```

## What I learned
- Learned that the output of commands can be stored in a variable.

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 7 - Reading Input

In this challenge, your job is to use read to set the PWN variable to the value COLLEGE. Good luck!

## My solve
**Flag:** `pwn.college{wDeEKo8zeH210-VnHRXlk19xWhQ.QX4cTN0wyM2AzNzEzW}`

I invoked the command "read -p "INPUT: " PWN". This prompted the user to input the value of the variable PWN. I entered the value as COLLEGE (mentioned in the challenge) which lead to the flag being printed.

```bash
hacker@variables~reading-input:~$ read -p "INPUT: " PWN
INPUT: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wDeEKo8zeH210-VnHRXlk19xWhQ.QX4cTN0wyM2AzNzEzW}
```

## What I learned
- Learned how to take input from the user and store it in a variable

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)


# Task 8 - Reading Files

Read /challenge/read_me into the PWN environment variable, and we'll give you the flag! The /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command!

## My solve
**Flag:** `pwn.college{EeFyYZY5UWlhUY2-mS2cpVPsC6o.QXwIDO0wyM2AzNzEzW}`

I invoked the "read PWN < /challenge/read_me" command to redirect the stdin of read to the file /challenge/read_me. This lead to the contents of /challenge/read_me being stored in the variable.

```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{EeFyYZY5UWlhUY2-mS2cpVPsC6o.QXwIDO0wyM2AzNzEzW}
```

## What I learned
- Learned that input redirection can be used to store the values needed in a variable

## References
- [pwn.college](https://pwn.college/linux-luminarium/variables/)
