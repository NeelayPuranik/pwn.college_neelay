# Task 1 - Launching Screen
For this challenge, we've hooked things up so that just launching screen will get you the flag. Easy!

## My solve
**Flag:** `pwn.college{sOlrVvjDxYE7jSLFf7K5QQg552N.0VN4IDOxwyM2AzNzEzW}`

I invoked the screen command to obtain the flag.

```bash
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{sOlrVvjDxYE7jSLFf7K5QQg552N.0VN4IDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use the screen command

## References
- [pwn.college](https://pwn.college/linux-luminarium/terminal-multiplexing/)


# Task 2 - Detaching and Attaching
For this challenge, you'll need to:

1) Launch screen
2) Detach from it.
3) Run /challenge/run (this will secretly send the flag to your detached session!)
4) Reattach to see your prize

## My solve
**Flag:** `pwn.college{wuR9jY7Gl7PzFPfxSjVeaAwhH_G.0lN4IDOxwyM2AzNzEzW}`

I invoked the screen command and then detached from it. I, then, ran the /challenge/run command for the flag to be sent to the screen in the background. I then reattached to the screen to see the flag.

```bash
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[screen is terminating]
```

## What I learned
- Learned how to use attach and detach from a screen

## References
- [pwn.college](https://pwn.college/linux-luminarium/terminal-multiplexing/)


# Task 3 - Finding Sessions
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys!

You'll need to check each one until you find it. Don't forget to detach (Ctrl-A d) before trying the next session!

## My solve
**Flag:** `pwn.college{o9cIohEnP5x0KZPT1SOFUgTZ1mq.01N4IDOxwyM2AzNzEzW}`

I invoked command "screen -ls" to list all the ongoing sessions. I then checked all of them using "screen -r [identifier]" until I found the session containing the flag.

```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        165.pts-1.terminal-multiplexing~launching-screen        (Remote or dead)
        144.session_b7003f7ea2caa172    (Detached)
        147.session_d7b4510e0d9a7aa8    (Detached)
        150.session_332940cf25ad215b    (Detached)
4 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_b7003f7ea2caa172
[detached from 144.session_b7003f7ea2caa172]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_d7b4510e0d9a7aa8
[detached from 147.session_d7b4510e0d9a7aa8]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_332940cf25ad215b
[detached from 150.session_332940cf25ad215b]
```

## What I learned
- Learned how to list all the ongoing screen sessions

## References
- [pwn.college](https://pwn.college/linux-luminarium/terminal-multiplexing/)


# Task 4 - Switching Windows
For this challenge, we've set up a screen session with two windows:

1) Window 0 has... well, you'll have to switch there to find out!
2) Window 1 has a welcome message

Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get that flag!

## My solve
**Flag:** `pwn.college{kwo0hYDQDeLAF9OiPVydgW8O5Qb.0FO4IDOxwyM2AzNzEzW}`

I invoked command "screen -r" to attach to the ongoing screen session. Then, I pressed "ctril+A 1" to switch to window 1 but did not obtain the flag, then, I pressed "ctrl+A 0" to switch to window 0 which contained the flag.

```bash
hacker@terminal-multiplexing~switching-windows:~$ screen -r
[detached from 135.challenge_session]
```

## What I learned
- Learned how to navigate through windows in a screen session

## References
- [pwn.college](https://pwn.college/linux-luminarium/terminal-multiplexing/)


# Task 5 - Detaching and Attaching (tmux)
For this challenge:

1) Launch tmux
2) Detach from it.
3) Run /challenge/run (this will send the flag to your detached session!)
4) Reattach to see your prize

## My solve
**Flag:** `pwn.college{wzTZ4gM4x0E7sqtMIqWp7XO8ZQG.0VO4IDOxwyM2AzNzEzW}`

I invoked the command "tmux" to being the sessions. Then I detached from it using "ctrl+B d". I, then, ran the command "/challenge/run" to send the flag to the detached tmux session. I then reattached to the tmux session using "tmux a" to obtain the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!




hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]


hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{wzTZ4gM4x0E7sqtMIqWp7XO8ZQG.0VO4IDOxwyM2AzNzEzW}
Congratulations, here is your flag: pwn.college{wzTZ4gM4x0E7sqtMIqWp7XO8ZQG.0VO4IDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to use tmux

## References
- [pwn.college](https://pwn.college/linux-luminarium/terminal-multiplexing/)


# Task 6 - Switching Windows (tmux)
We've created a tmux session with two windows:

1) Window 0 has the flag!
2) Window 1 has your warm welcome.

Go get that flag!

## My solve
**Flag:** `pwn.college{E1R09FVLJNVwSYbUDbQvhGCyVr8.0FM5IDOxwyM2AzNzEzW}`

I invoked the command "tmux a" to attach to the ongoing tmux session. I, then, pressed the keys "ctrl+B 0" to switch to window 0 which contained the flag.

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
[detached (from session challenge_session)]

hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{E1R09FVLJNVwSYbUDbQvhGCyVr8.0FM5IDOxwyM2AzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{E1R09FVLJNVwSYbUDbQvhGCyVr8.0FM5IDOxwyM2AzNzEzW}
```

## What I learned
- Learned how to navigate windows in a tmux session

## References
- [pwn.college](https://pwn.college/linux-luminarium/terminal-multiplexing/)
