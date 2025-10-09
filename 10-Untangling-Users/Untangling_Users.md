# Task 1 - Becoming root with su
But THIS challenge (and only this challenge) does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag!

## My solve
**Flag:** `pwn.college{8pC5dq1pLTP1t6UWG5FMRdD_zZv.QX1UDN1wyM2AzNzEzW}`

I entered su and then the password to gain root access. I, then, used the ls command to list all files and found the file containing the flag. I catted that file to obtain the flag.

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{8pC5dq1pLTP1t6UWG5FMRdD_zZv.QX1UDN1wyM2AzNzEzW}
```

## What I learned
- Learned how to elevate a user's access level to root

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 2 - Other users with su
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me. Good luck!

## My solve
**Flag:** `pwn.college{Q4oe3u3fYjG4jip9fpO_GkSBSmf.QX2UDN1wyM2AzNzEzW}`

I entered su along with the argument "zardus" to change my user to zardus. I entered the password to login to zardus' account. I then ran the command /challenge/run to obtain the flag.

```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{Q4oe3u3fYjG4jip9fpO_GkSBSmf.QX2UDN1wyM2AzNzEzW}
```

## What I learned
- Learned how to change from one user to another

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 3 - Cracking passwords
This level simulates this story, giving you a leak of /etc/shadow (in /challenge/shadow-leak). Crack it (this could take a few minutes), su to zardus, and run /challenge/run to get the flag!

## My solve
**Flag:** `pwn.college{MSWz5VlZ_oKV0OZBdBq0W7wLg74.QX3UDN1wyM2AzNzEzW}`

I used the john command to decrypt the hashes stored in the "/challenge/shadow-leak" directory. Hence, I obtained the decryped password: "aardvark". Then, I used the su command with the argument "zardus" and entered the password to login to zardus' account. I then ran /challenge/run to obtain the flag.

```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04777g/s 278.2p/s 278.2c/s 278.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{MSWz5VlZ_oKV0OZBdBq0W7wLg74.QX3UDN1wyM2AzNzEzW}
```

## What I learned
- Learned how to decrypt passwords using the john the ripper tool

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)


# Task 4 - Using sudo
In this level, we will give you sudo access, and you will use it to read the flag. Nice and easy!

## My solve
**Flag:** `pwn.college{olWR_ifj2Hnt8mDKKyawvTwc54c.QX4UDN1wyM2AzNzEzW}`

I first used the ls command to print all the files in the home directory. I then used the command "sudo cat /flag" to cat the flag as someone who has root level access. This gave me the flag.

```bash
hacker@users~using-sudo:~$ ls
COLLEGE  PWN  flag  flag_fifo  instructions  myflag  not-the-flag  pwn_out.txt  r  the-flag
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{olWR_ifj2Hnt8mDKKyawvTwc54c.QX4UDN1wyM2AzNzEzW}
```

## What I learned
- Learned how to use the sudo command to execute commands as someone who has root level access

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)
