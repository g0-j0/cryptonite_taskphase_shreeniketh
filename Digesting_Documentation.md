# Digesting_documentation
In this module, I will learn to use docs and how to look for help related to commands, programs, etc.
 ## learning from docs
 whenever something has the syntax ```-(name)```, it's called an argument.. Like in ```ls -a```, ```-a``` is an argument that allows us to see hidden files and directories. We must run the /challenge/challenge file with the right command in the next challenge.
 ```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{_}
hacker@man~learning-from-documentation:~$
```

## learning complex usage
some commands are more complex than I know, such as ```sed``` and ```awk```. While we won't write something as nearly as complicated as that, we should get more used to longer commands. The next task is quite similar to the one above. I had a slight issue with where the flag would be, but then I remembered that /flag stores the flag.
```bash
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{_}
```

## Reading Manuals
```man``` command is short for manual. It provides the manual on how to use any command ```command_name```. The command name you pass is an argument for the ```man``` command. We have to run the ```man``` command with the ```challenge``` argument.

```bash
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                                                                  Challenge Commands                                                                                 CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --webaof NUM
              print the flag if NUM is 042

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                                                        May 2024                                                                                      CHALLENGE(1)
hacker@man~reading-manuals:~$ /challenge/challenge --webaof 042
Correct usage! Your flag: pwn.college{_}
hacker@man~reading-manuals:~$
```

