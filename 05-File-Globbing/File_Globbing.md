# Task 1 - Matching with *
Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!

## My solve
**Flag:** `pwn.college{QkDxtVmUjDUP4QA_AA8Ol-HcIX3.QXxIDO0wyM2AzNzEzW}`

I though about what makes the directory "/challenge" unique. I therefore decided that if I type and asterisk at the end of ch, there will be no other directory left in the root directory except the challenge directory. Therefore I invoked the command "cd /ch*"

```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{QkDxtVmUjDUP4QA_AA8Ol-HcIX3.QXxIDO0wyM2AzNzEzW}
```

## What I learned
- Learned that there are shortcuts I can use to avoid writing the complete path everytime.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 2 - Matching with ?
Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!

## My solve
**Flag:** `pwn.college{QkDxtVmUjDUP4QA_AA8Ol-HcIX3.QXxIDO0wyM2AzNzEzW}`

As everything was already given in the question, I just invoked the command "cd /?cha??enge"

```bash
hacker@globbing~matching-with-:/challenge$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kTUE2FYA6oy10Gcj2ze035GeIVU.QXyIDO0wyM2AzNzEzW}
```

## What I learned
- Learned that there are different shortcuts to write the path like "*" used to replace multiple characters and "?" to replace one character.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 3 - Matching with []
Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!

## My solve
**Flag:** `pwn.college{MgLLehlt1y8YIXdtZ3wO9bj9Q8O.QXzIDO0wyM2AzNzEzW}`

I first cd'ed into the "/challenge/files" directory then I ran the command "/challenge/run file_[absh]" so that the files with the name file_a, file_b, file_s, and file_h are all included in the argument.

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{MgLLehlt1y8YIXdtZ3wO9bj9Q8O.QXzIDO0wyM2AzNzEzW}
```

## What I learned
- Learned that there are ways to use a range of characters in the 'unknown' character place, i.e., type all the letters/characters you want to be in the place of [].

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 4 - Matching paths with []
Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!

## My solve
**Flag:** `pwn.college{M77NMNhgmU22ipC2N0wTX4bBMEr.QX0IDO0wyM2AzNzEzW}`

I invoked the command "/challenge/run" with the argument "/challenge/files/file_[absh]" which passed the absolute directories of all the 4 files (file_a, file_b, file_s, file_h) to the command.

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{M77NMNhgmU22ipC2N0wTX4bBMEr.QX0IDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to pass the argument of several file directories in one argument using the [] glob.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 5 - Multiple globs
We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

## My solve
**Flag:** `pwn.college{oqYHpO7Ui6LApoAU85EofOA_0Kj.0lM3kjNxwyM2AzNzEzW}`

I initally cd'ed into the "/challenge/files" directory. I then thought about how I can pass all files containing the letter p in one argument with less than or equal to 3 characters. Therefore, I used the command "/challenge/run *p*".

```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{oqYHpO7Ui6LApoAU85EofOA_0Kj.0lM3kjNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use multiple globs in one command.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 6 - Mixing globs
We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!

## My solve
**Flag:** `pwn.college{s_UFfQ4tn0N0-zAN2_XTaS929B3.QX1IDO0wyM2AzNzEzW}`

I initially tried the combination "[c* e* p*]" but it was more than 6 characters and the shell expands it before passing so they look like three arguments being passed which the challenge did not accept. So I searched the internet for solutions and referred to a stackoverflow problem where the square brackets were being using like "[...]*". I tried this method and obtained the flag.

```bash
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{s_UFfQ4tn0N0-zAN2_XTaS929B3.QX1IDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use multiple and different type of globs together.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)
- [stackoverflow](https://stackoverflow.com/questions/39892536/bash-globbing-expressions-with-square-brackets)


# Task 7 - Exclusionary globbing
Go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

## My solve
**Flag:** `pwn.college{w8ns_O7QtciaUzu2tfbgtREUDv7.QX2IDO0wyM2AzNzEzW}`

As the task was straight forward, I just cd'ed to the /challenge/files directory and invoked the command "/challenge/run [^pwn]*

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{w8ns_O7QtciaUzu2tfbgtREUDv7.QX2IDO0wyM2AzNzEzW}
```

## What I learned
- Learned how to use globs in the opposite manner, i.e., to select the files whose names do not contain certain characters.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 8 - Tab completion
This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!

## My solve
**Flag:** `pwn.college{gOy7QmSpwOTog13ju1bwMJNlRuh.0FN0EzNxwyM2AzNzEzW}`

The task was straightforward and I pressed tab after typing out "cat /challenge/pwn" to get "cat /challenge/pwncollege".
```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{gOy7QmSpwOTog13ju1bwMJNlRuh.0FN0EzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use tab completion to get the shell to automatically fill in the predicted input to avoid accidental actions which might happen when careless globbing is used.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task  9 - Multiple options for tab completion
This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!

## My solve
**Flag:** `pwn.college{I4ZfNosXbAmeJ7StjyxVJvql6uv.0lN0EzNxwyM2AzNzEzW}`

The task was straightforward and I pressed tab first at "/challenge/files/p" then at "/challenge/files/pwncollege-fl" to get "/challenge/files/pwncollege-flag"
```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-fl
pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{I4ZfNosXbAmeJ7StjyxVJvql6uv.0lN0EzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use tab completion multiple times.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task  10 - Tab completion on commands
Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

## My solve
**Flag:** `pwn.college{A5sk8h8nkTZ016mQISRlDF9C5bj.0VN0EzNxwyM2AzNzEzW}`

The task was straightforward and I pressed tab after typing "pwncollege" into the terminal which led to the command being auto filled.
```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-9139
Correct! Here is your flag:
pwn.college{A5sk8h8nkTZ016mQISRlDF9C5bj.0VN0EzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use tab completion for commands.
## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)
