# Task 1 - Translating characters
In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?

## My solve
**Flag:** `pwn.college{Adp5zqErHGOCu_6BuDOwaLwmHUi.01MxEzNxwyM2AzNzEzW}`

I piped the output of /challenge/run to the tr command. After briefly browsing for useful information, I found out that all upper case characters can be represented with "[:upper:]" and all lower case characters can be represented by "[:lower:]". Therefore, I used the command "/challenge/run | tr '[:upper:][:lower:]' '[:lower:][:upper:]'".

```bash
hacker@data~translating-characters:~$ /challenge/run | tr '[:upper:][:lower:]' '[:lower:][:upper:]'
yOUR CASE-SWAPPED FLAG:
pwn.college{Adp5zqErHGOCu_6BuDOwaLwmHUi.01MxEzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use the tr command to translate characters.
- Learned how to represent a set of characters with a common property using a shortcut.

## References
- [pwn.college](https://pwn.college/linux-luminarium/data/)
- [Stack Overflow](https://stackoverflow.com/questions/11392189/how-can-i-convert-a-string-from-uppercase-to-lowercase-in-bash)


# Task 2 - Deleting characters
I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them!

## My solve
**Flag:** `pwn.college{80yCJySrEQLSeZbfJbPELk55P2Z.0FNxEzNxwyM2AzNzEzW}`

As mentioned in the challenge description, I used the command "/challenge/run | tr -d '^%'" to delete these junk characters from the flag.

```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{80yCJySrEQLSeZbfJbPELk55P2Z.0FNxEzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use the tr command to delete characters.

## References
- [pwn.college](https://pwn.college/linux-luminarium/data/)


# Task 3 - Deleting newlines
In this challenge, we'll inject a bunch of newlines into the flag. Delete them with tr's -d flag and the escaped newline specification!

## My solve
**Flag:** `pwn.college{sez4a9F6e56L7mWQxO57wjW0pq_.0VNxEzNxwyM2AzNzEzW}`

This challenge was pretty straightforward, I just had to use the command "/challenge/run | tr -d "\n"" to obtain the flag. This command deleted all the new lines in the flag. Otherwise, the flag would have been split up into multiple lines and therefore would have been inconvenient to read.

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{sez4a9F6e56L7mWQxO57wjW0pq_.0VNxEzNxwyM2AzNzEzW}hacker@data~deleting-newlines:~$
```

## What I learned
- Learned how to use the tr command to delete new lines.

## References
- [pwn.college](https://pwn.college/linux-luminarium/data/)


# Task 4 - Extracting the first lines with head
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right! Your solution will be a long composite command with two pipes connecting three commands. Good luck!

## My solve
**Flag:** `pwn.college{AC4Ll8iMuwiobtulrwGkEcijSDK.0lNxEzNxwyM2AzNzEzW}`

I used the command "/challenge/pwn | head -n 7 | /challenge/college". This command passed the output of the command "/challenge/pwn" to head to get the first seven lines. These seven lines were then passed to the command "/challenge/college" which lead to the flag being printed.

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{AC4Ll8iMuwiobtulrwGkEcijSDK.0lNxEzNxwyM2AzNzEzW}
```

## What I learned
- Learned how to use the head command to get the needed number of lines from a command's output.

## References
- [pwn.college](https://pwn.college/linux-luminarium/data/)


# Task 5 - Extracting specific sections of text
In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.

## My solve
**Flag:** `pwn.college{cnyXVD8NNK0Ul4Rb-YwW6HSjC0m.01NxEzNxwyM2AzNzEzW}`

I used the command "/challenge/run | head -d " " -f 2 | tr -d "\n"". This command passes the output from /challenge/run to head which inturn extracts the second column and passes it to tr. The tr command then removes all the new lines. The resultant output is the flag in on coherent and straight line.

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{cnyXVD8NNK0Ul4Rb-YwW6HSjC0m.01NxEzNxwyM2AzNzEzW}hacker@data~extracting-specific-sections-of-text:~$
```

## What I learned
- Learned how to use the head command to get the needed number of lines from a command's output and then pass it onto another command.

## References
- [pwn.college](https://pwn.college/linux-luminarium/data/)


# Task 6 - Sorting data
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake flags). Go get it!

## My solve
**Flag:** `pwn.college{o8RJP7VkIfmw7iwoRLiICv3rDz9.0FM0MDOxwyM2AzNzEzW}`

When sorted alphabetically, the file contained the actual flag at the bottom so instead of that I sorted the file in the reverse alphabetical order which put the real flag on top making it easier to reach. Therefore, I used the command "sort -r /challenge/flags.txt".

```bash
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{o8RJP7VkIfmw7iwoRLiICv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.college{o8RJP7VkIfmw7iwoRLiICv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.college{o8RJP7VkIfmw7iwoRLiICv3rDz9.0FM0MDOxwyM2AyNzEzV}
pwn.college{o8RJP7VkIfmw7iwoRLiICv3rDz9.0FM0MDOxwyL2AzNyEzW}
pwn.college{o8RJP7VkIfmw7iwoRLiICv3rDz9.0FM0MDNxwyM2AzMzEzW}
pwn.college{o8RJP7VkIfmw7iwnRLiICv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.college{o8RJP7VkIfmw7iwnRLiICv3qDz9.0FM0MDOwwyL2AzNzEzW}
pwn.college{o8RJP7VkIfmv7iwoRLiIBv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.college{o8RJP7VkIfmv7iwoRLhHCv3rCy9.0FM0LDOxwyM2AzNzEzW}
pwn.college{o8RJP7VkIfmv6iwoRLiICu3rCy9.0FM0MDOwwyM2AzMzEzW}
pwn.college{o8RJP7VkIemw7iwoRLiICv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.college{o8RJP7VkIemw7iwoRKiICv3rDy9.0FM0MCOxvyM2AzNzEzW}
pwn.college{o8RJP7VkHfmv7iwoRLiICv3rDy9.0FM0MCOxwyM1AyNzDzW}
pwn.college{o8RJP7VjIflw7iwoRLiHCv3rDz9.0FM0MDOxwxM2AzNzEzW}
pwn.college{o8RJP7UkIflv7iwoRLiICu3rDz8.0FM0MDOwwyM2AzNzEzW}
pwn.college{o8RJO7VkIemw7iwoRKiICv3qDz9.0EM0LDNxwyM2AzNzDzW}
pwn.college{o8RJO7VkHfmw7iwoRKiICv2rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.college{o8RJO7VjIelw7iwnRLiICv3qDz9.0FM0MDNxwyL2AzNyEzW}
pwn.college{n8QJP7VkIfmw7iwoRLiICv3rDz9.0FL0MDOxwyM2AzNyEzW}
pwn.collefd{o8RJP6VjHflv7hwoRLiHBv3qDz8.0EM0LDOxwyM2AzNzDzW}
pwn.collefd{o7RJO6VkIfmw7hvoRLhICv2rCz8.0FM0LCOwwyM2AzMyDyV}
pwn.collefd{n8QJP7UkIflw7iwnRLiHBv2rDz9.0FM0LDOwwxL2AzMzEzW}
pwn.colldge{o7RJO7VkIfmw7iwoRLiICv3rDy8.0FM0MDOxwyL2AzNzEzW}
pwn.colldgd{o8RJP7VjHfmw7hwoRLhIBu3rDz9.0FM0MDNxwyM2AzNzEyW}
pwn.colldfe{o8RIO6VjIemw7iwoRLiIBv3rCz9.0FM0MDOxwyM2AzNyEzW}
pwn.colkege{o8RJP7VjIemw7hwnRLiICv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.colkege{o8QJP7VkHfmw6iwnRLiICu3qCy9.0FM0LDOxwyM2AzNzEzW}
pwn.colkdge{o8QIP6VkIfmv7hwoRLiHBv2rDz9.0FM0LDOwwyM1AyNyEzW}
pwn.colkdge{n8RJO7VkIemv7iwnRLiIBv2rDz8.0EM0MCOwvyM2AzMzEzW}
pwn.cokldfe{o8RIP7UjIelw7iwnRLiHCv2rDy9.0FM0MDNxwyM2AyNzEzW}
pwn.cokkege{o8RJP7VkIflw6iwoQLiICv3qCz9.0FM0MDNxwyL1AzNzDzV}
pwn.cokkegd{o7QJO7VkIemw7iwoRLiHCv2qCz8.0EM0MCOxwyM1AzNzEzW}
pwn.cnllege{o8RJP6UkIfmw7ivnQLiHCv3rDz9.0EL0MDNxwyM2AzMzEyW}
pwn.cnllege{o7RJP6UkHfmw6iwoRLiICv3rCz9.0FL0LDOxwyM2AzNzEzW}
pwn.cnllege{n8RIO7UkIfmv6iwoRLhICv3rDz9.0FM0MDOxwyM2AzNzEzW}
pwn.cnlldgd{o8QIP7VkIemw7hvoRKiICv3rDz8.0FM0LDOwvxM2AzNzEzV}
pwn.cnlkdgd{n7RJP7UkHfmw7iwoQLhICv3rDy9.0FL0MDOwwyM1AyNyEyW}
pwn.cnklege{o8RJO6VjIemw6ivoRLiIBv3rDz9.0FL0LCOxvxM2AzMzDzV}
pwn.cnkldge{n8RJP6VkHfmw7iwoQKiICv3qDz9.0FM0LDOwwxL1AzNzDzW}
pwn.bollege{o8RJP7VkHfmw7ivoRKiICu3rDz8.0EM0MDOxwyM2AzNzEzW}
pwn.bolldge{o7QJP7VjHelw6iwoQKiHCv3rDz9.0FM0LDOxwyM2AzNzEyV}
pwn.boklege{o8RJP7VkIfmw7iwoRKiHCv2rDy9.0FM0MCOxvyM2AzNzEzW}
pwn.boklege{o8QIP7VkHemw6iwoRKhIBu3qDz9.0FL0MCNxvyM2AzNzDzW}
pwn.bnllegd{o8RIP7VkIemw7iwnRLhICv3rDz9.0FM0MDOxvyM2AzNzEzW}
pwn.bnlkefe{o8RJP7VkIfmw6iwoRKhHCv3qCz8.0FM0MCOxvyM2AzNzDzV}
pwn.bnkldge{o8QJO6UjIemv7ivoQKiIBv3qDy8.0EM0MCNxwyM2AzMyEzW}
pwm.college{o8RJP7VkIemw7iwnRLiICv3rDz9.0FM0MDOxwyM1AyMyEzW}
pwm.college{o7RJP6VkIflv7hwoQLhIBv3rDz9.0FL0MCNxwyM2AyNzEyW}
pwm.college{n8RIP7VjIfmw7iwoRLiICv2rDz9.0EM0LDOxwxM2AzMzEzW}
pwm.colkefe{o8QJP7VjHemv7hvoRLhHCu3rDy9.0FM0MDOxvyM2AzNyDyV}
pwm.colkefe{n8RIP7VkIfmw7iwoRLiICv3rDz9.0FM0MDOxwyM2AzMzDzW}
pwm.colkdge{n8RJP6VjIemw7iwoRLhICu3rCz9.0FM0MCOwwyM2AyMzEzW}
pwm.cokkdge{o7RIO7VkIelv7iwnQLhIBu3rCz8.0FL0MDNxvyM2AzNzEzV}
pwm.cnllege{o8RJP6VkIflw7iwoQLiICv2rCz8.0FM0MDOxwyL2AyNyEyW}
pwm.cnllege{o8RIP7VkIflw7iwoRLiICv3rDy9.0FM0MDOwwyM2AyNzEzW}
pwm.cnlkdfe{o8RIP6VjIemw6iwoRLiHBv2rDz9.0FM0LDOwwyM1AzNzDzV}
pwm.cnklege{n8RIP7VkIfmw6hwoRLhHBu2rDz9.0FM0MDNxwxM1AzMyDzV}
pwm.boklefe{o8RIP7VkIfmw7iwoRLiICv3rDz9.0EM0MDOxvyM2AzMzEzW}
pwm.bnlkege{o8QIP7VkIelw7ivnRLiICv2rDz9.0FM0MCNxvyL2AzNzDzW}
pvn.collefe{o8RJO6VkHemw7iwnRLhICv3qDz9.0EM0MCNwwyM1AyMzDzW}
pvn.coklege{o8RJP7UkIemw6iwoQLiIBv3rDy8.0FL0MDNxwyM2AyNzEyW}
pvn.cokldge{o8RJP6VkIemw7iwoQLiICv2rCz9.0FM0LDNxvyM2AyNzDzW}
pvn.cnllegd{o8RIP6VjIfmw7iwoRLiICu3rDz8.0FM0LDOxwyM2AzNzDzW}
pvn.bnllege{o8RJP7VkIfmw6iwnQLhICv3rDz8.0FM0MDOxwyM1AzNyEyW}
pvm.college{o8RIP7VkIfmw7iwoRLiHCv3rDz9.0FM0MDOxwyM2AzNzEzW}
pvm.college{o7RJP7VkHfmw7iwoRLiHCv3qDy9.0EM0MDOwwyM2AyNzEyW}
pvm.collegd{o8RJP7VkHfmw7iwoRLhICv2rDy9.0EM0MDOxwyM2AzNyEzW}
pvm.coklege{n8RJP7UkIflw6iwoRKhHCu2qDz8.0FM0MCNxwxM2AzMzEzV}
pvm.cokkegd{o8RJP7VkHemw7iwoRLiHCv2qDy9.0FM0MDOxwxM1AzNyDzW}
own.college{o8RJO7VkIflw6ivoRLiHBv2rDz9.0FL0MDOxwxM2AzMzEzW}
own.college{o8QJP7VkIemw6iwoRLiIBv3rDz9.0FM0MCOwwyM2AyNyEyW}
own.colldge{o7RJP7VkIflv7iwoRLiICu3rDz9.0FM0LDOxwxL2AzNzEzW}
own.colldfe{n8QIO6UkIemw7iwoRLhIBv3rDz9.0FM0MDOxwyL1AzNyDzV}
own.colkege{o8QJP6VkHfmw6hwoRLiICv3rDz9.0FL0LDOxwyM2AyNzEzW}
own.colkefd{n7RJO7VkIemw6iwnQLiHCu3rDz8.0EL0MCOxwyM2AzNzEzW}
own.colkdfd{o7RIO7VjIfmw7iwoRLiIBv3rDz9.0FL0MCOxwxL2AzNzEyW}
own.coklege{o8QJP7VkIemw6hwoRKiICv2rDz9.0FM0MDOwwyM1AyNzDzW}
own.coklege{n8RJO7VkHflw6iwoRKhICv3rDy9.0FM0MCOxvyL1AzNzDzW}
own.cokldge{n8RJP7VkIfmw7ivoQKiICu3rDz9.0FM0LDNwwyL1AyNyEyW}
own.cokkefe{o8RJP7VkHfmw6hvnQKiICv3rDz9.0FM0LDOxwyM2AzMzEzV}
own.cnllege{n8QIP7UkIemw7hvoRLiICv2qDz8.0FM0MCOxwyM1AyNyEzW}
own.cnklege{n7RJP6VkIfmw7iwoRKhIBv3rDz9.0FL0LDOxwyM2AzNyEyW}
own.cnklegd{n8RJO6VkIflw7ivnQLhHCv3rDy9.0EL0MDOwwxM2AyNzEyV}
own.cnkldgd{o8QJP7VkIfmw7iwoRKiICv3rDz9.0FM0MDOwwxM2AzMzDzW}
own.bollegd{o8RJP7VkIfmw7iwoRLiIBv3rDz9.0FM0MDOxwyM1AzNzEzW}
own.bollefe{o8QJP7UjIemw6ivoQLiIBv2rDz8.0FM0MDOwwyL2AyNzEzW}
own.bolkege{o7RJP7VkIfmw6iwoQLiIBu3rDz9.0FL0LDOwwyL1AzNzEzW}
own.bolkegd{n7RIP7UkIemw7hwoQKiIBv3rDy9.0EM0MDOxvyL1AzNzEyV}
own.bnkkdgd{o8RJO6VkIflw7iwoRLiIBv2rDy9.0EM0MDOxwyL2AyNzEzW}
owm.college{o8RIP7UkIfmw7iwoQLiICv3rDz9.0FM0MDOxwyM2AzNzEyW}
owm.collefe{o8QJO7UjHfmw7hwnRLiHCv2qCy9.0EM0LDNxwyM1AyNyDzV}
owm.colldge{n7RJP6VkIflv6iwnQLiHCv3rDz9.0EM0MCOwvyM2AzNyEyW}
owm.cokkdfe{o8RIO6VkIflw6iwoRLiICv3qCz9.0FL0MDOxwxM2AyNzEzV}
owm.bollege{n8RJP7VjHfmw6ivoQKhHBu3rCz8.0FM0MDNwwyL2AzMzEzW}
ovn.coklege{o8QJP7VjIfmv7iwoRKiHCu2qCz8.0FL0MDOxvyM1AzNyEzW}
ovn.bollege{o7RIP6UjIfmv7iwnRLhIBu2rCz9.0FM0MDNxvyM2AzNzDzW}
ovn.boklege{o8RJP7VjHemw6iwoRKiICv3rCz8.0EM0MDOxwyM1AyNzDzV}
ovm.collefe{o8RIP7VkIemw7iwoRLhICu2rDz9.0FM0MCNwvxL1AyNzDzW}
ovm.coklege{n8RIP7UkIelw7hwoRKiICv2rDz9.0FL0MCNxwyM2AyMzEzV}
ovm.cokkdge{o7QJP7VkIfmw7ivnQLhICu3rCy9.0FM0MDNxwyL2AyMzEzW}
ovm.cnlkege{o7QJO7UkHfmw6ivoRKiIBv2rDz9.0FM0LDOwwyL1AyNzEzV}
```

## What I learned
- Learned how to use the sort command to sort the contents of a file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/data/)
