# Task 1 - Chaining with Semicolons
In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

## My solve
**Flag:** `pwn.college{QLSa-7TtAiaDPi0xqf5xAkASjol.QX1UDO0wyM2AzNzEzW}`

I chained those two commands using ";" to obtain the flag.

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{QLSa-7TtAiaDPi0xqf5xAkASjol.QX1UDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to chain two commands together using the semicolon

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 2 - Building on Success
In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the && operator. Try running each command separately first to see what happens (which is that you will not get the flag). But if you chain them with &&, the flag will appear!

## My solve
**Flag:** `pwn.college{c4iBEDqEIyQat9fUKJ81FRfvc3p.0lM0MDOxwyM2AzNzEzW}`

I chained these two commands using the AND operator so that the second command will run only if the first command exits with a success exit code. This gave me the flag.

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{c4iBEDqEIyQat9fUKJ81FRfvc3p.0lM0MDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to chain two commands together using the AND operator

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 3 - Handling Failure
In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator. Go for it!

## My solve
**Flag:** `pwn.college{8qPL_LwRL206m-r9aBnRSEV1-i3.01M0MDOxwyM2AzNzEzW}`

I chained these two commands using the || operator such that the second command ran only if the first one failed. This got me the flag.

```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{8qPL_LwRL206m-r9aBnRSEV1-i3.01M0MDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to chain two commands together using the || operator

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 4 - Your First Shell Script
Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

## My solve
**Flag:** `pwn.college{0S5YlfmGW3xfpKFV8jZo9K5Vrl4.QXxcDO0wyM2AzNzEzW}`

I used the touch command to create a file x.sh. Then, I ran the command "echo > '/challenge/pwn ; /challenge/college' > x.sh". This send the contents "/challenge/pwn ; /challenge/college" into the script. Then, I ran the script using "bash x.sh" to get the flag.

```bash
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ echo '/challenge/pwn; /challenge/college' > x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{0S5YlfmGW3xfpKFV8jZo9K5Vrl4.QXxcDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to create a script

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 5 - Redirecting Script Output
In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command!

## My solve
**Flag:** `pwn.college{AuiD22l7lOEhIXrBYZhAwaxtiD_.QX4ETO0wyM2AzNzEzW}`

I did repeated everything done in the previous task to create the x.sh script file. Then, I ran the command "bash x.sh | /challenge/solve" to pipe the output from the script to the /challenge/solve command. This gave me the flag.

```bash
hacker@chaining~redirecting-script-output:~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ echo '/challenge/pwn; /challenge/college' > x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{AuiD22l7lOEhIXrBYZhAwaxtiD_.QX4ETO0wyM2AzNzEzW}
```

## What I learned
- Learned how to pipe the output of a script to another command

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 6 - Executable Shell Scripts
Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

## My solve
**Flag:** `pwn.college{QO6XI18XDc85QKqwrmLotr8CuqR.QX0cjM1wyM2AzNzEzW}`

I did repeated everything done in the previous task to create the x.sh script file. Then, I ran the command "chmod +x x.sh" to make the script an executable. Lastly, I ran the command "./x.sh" to execute the script and obtain the flag.

```bash
hacker@chaining~redirecting-script-output:~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ echo '/challenge/pwn; /challenge/college' > x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{AuiD22l7lOEhIXrBYZhAwaxtiD_.QX4ETO0wyM2AzNzEzW}
```

## What I learned
- Learned how to pipe the output of a script to another command

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 7 - Understanding Shebangs
For this challenge, create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". Remember to make it executable, then run /challenge/run to verify your script works correctly!

## My solve
**Flag:** `Flag: pwn.college{Mz_bxaxPO6l5s8h7fJ2WeXY5vw1.0VOzMDOxwyM2AzNzEzW}`

First of all, I created the file solve.sh using touch. Then, I ran the command "echo '#!/bin/bash' > solve.sh" so that the first line in the script is the path to the interpreter. Then, I ran the command "echo 'echo "hack the plane"t' >> solve.sh" so that the script prints "hack the planet". Then, I made the script an executable. Lastly, I ran the /challenge/run command to obtain the flag.

```bash
hacker@chaining~understanding-shebangs:~$ touch solve.sh
hacker@chaining~understanding-shebangs:~$ echo '#!/bin/bash' > solve.sh
hacker@chaining~understanding-shebangs:~$ echo 'echo "hack the plane"t' >> solve.sh
hacker@chaining~understanding-shebangs:~$ chmod +x solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{Mz_bxaxPO6l5s8h7fJ2WeXY5vw1.0VOzMDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to selected which interpreter should interpret the script using a shebang and the path to the interpreter.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 8 - Scripting with Arguments
For this challenge, you need to write a script at /home/hacker/solve.sh that:

1) Takes two arguments
2) Outputs them in REVERSE order (second argument first, then the first argument)

Once your script works correctly, run /challenge/run to get your flag!

## My solve
**Flag:** `pwn.college{ME0DYB_p448ZHF6kjXfXQ7iLt-b.0VNzMDOxwyM2AzNzEzW}`

First of all, I created the file solve.sh using touch. Then, I ran the command "echo '#!/bin/bash' > solve.sh" so that the first line in the script is the path to the interpreter. Then, I ran the command "echo 'echo "$2 $1"' >> solve.sh" so that the script prints the second argument then the first argument. I, then, checked that the script works as expected. Lastly, I ran the command /challenge/run to get the flag.

```bash
hacker@chaining~scripting-with-arguments:~$ touch solve.sh
hacker@chaining~scripting-with-arguments:~$ echo '#!/bin/bash' > solve.sh
hacker@chaining~scripting-with-arguments:~$ echo 'echo "$2 $1"' >> solve.sh
hacker@chaining~scripting-with-arguments:~$ bash solve.sh hello world
world hello
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{ME0DYB_p448ZHF6kjXfXQ7iLt-b.0VNzMDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use arguments in a script

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 9 - Scripting with Conditionals
For this challenge, write a script at /home/hacker/solve.sh that:

1) Takes one argument
2) If the argument is "pwn", output "college"
3) For any other input, output nothing

Once your script works correctly, run /challenge/run to get your flag!

## My solve
**Flag:** `pwn.college{U1icznR_FHhqqjTE0z6hFqM7cuF.0lNzMDOxwyM2AzNzEzW}`

First of all, I created the file solve.sh using touch. Then, I ran the command "echo '#!/bin/bash' > solve.sh" so that the first line in the script is the path to the interpreter. Then, I ran the commands given in the bash below to obtain the flag.

```bash
hacker@chaining~scripting-with-conditionals:~$ touch solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'if [ "$1" == "pwn" ]' > solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'then' >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'echo pong' >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'fi' >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{U1icznR_FHhqqjTE0z6hFqM7cuF.0lNzMDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use conditionals in a script

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 10 - Scripting with Default Cases
For this challenge, write a script at /home/hacker/solve.sh that:

1) Takes one argument
2) If the argument is "pwn", output "college"
3) For any other input, output "nope"

Once your script works correctly, run /challenge/run to get your flag!

## My solve
**Flag:** `pwn.college{AYgjnCAuJeSQcKZL9MNabUiYzoY.01NzMDOxwyM2AzNzEzW}`

First of all, I created the file solve.sh using touch. Then, I ran the command "echo '#!/bin/bash' > solve.sh" so that the first line in the script is the path to the interpreter. Then, I ran the echo command sequentially to print the if statement and so on and so forth. I checked that the script behaves as expected and then ran the /challenge/run command to get the flag.

```bash
hacker@chaining~scripting-with-default-cases:~$ touch solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo '#!/bin/bash' > solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'if [ "$1" = "pwn" ]' >> solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'then' >> solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo '  echo college' >> solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'else' >> solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo '  echo nope' >> solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'fi' >> solve.sh
hacker@chaining~scripting-with-default-cases:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ bash solve.sh anythingelse
nope
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{AYgjnCAuJeSQcKZL9MNabUiYzoY.01NzMDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use conditionals with a default case in a script

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 11 - Scripting with Multiple Conditions
For this challenge, write a script at /home/hacker/solve.sh that:

1) Takes one argument
2) If the argument is "hack", output "the planet"
3) If the argument is "pwn", output "college"
4) If the argument is "learn", output "linux"
5) For any other input, output "unknown"

Once your script works correctly, run /challenge/run to get your flag!

## My solve
**Flag:** `pwn.college{sYJGqGjiVvWajObcI_2Vkl84l77.0FOzMDOxwyM2AzNzEzW}`

First of all, I created the file solve.sh using touch. Then, I ran the command "echo '#!/bin/bash' > solve.sh" so that the first line in the script is the path to the interpreter. Then, I ran the echo command sequentially to print the if statement and then the elif statement and so on and so forth. I checked that the script behaves as expected and then ran the /challenge/run command to get the flag.

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ touch solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '#!/bin/bash' > solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'if [ "$1" = "hack" ]'>> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'then' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '  echo the planet' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'elif [ "$1" = "pwn" ]' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'then' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '  echo college' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'elif [ "$1" = "learn" ]' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'then' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '  echo linux' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'else' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '  echo unknown' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'fi' >> solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh hack
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ bash solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{sYJGqGjiVvWajObcI_2Vkl84l77.0FOzMDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use multiple conditionals in a script

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)


# Task 12 - Reading Shell Scripts
In this level, we will learn to read shell scripts. /challenge/run is a shell script that requires you to put in a secret password, but that password is hardcoded into the script iself! Read the script (using, say, cat), figure out the password, and get the flag!

## My solve
**Flag:** `pwn.college{8-k4eIXCb9ZjPXxNtf-58DwYHd4.0lMwgDOxwyM2AzNzEzW}`

First off, I catted /challenge/run to read the code stored inside the script. Upon analyzing, I realised that when the script is given "hack the PLANET" as input, the script outputs the flag. Therefore, I obtained the flag on doing the same.

```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{8-k4eIXCb9ZjPXxNtf-58DwYHd4.0lMwgDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to analyze the code in shell scripts

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)
