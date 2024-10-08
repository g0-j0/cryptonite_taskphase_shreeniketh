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

## Searching manual

You can use the ```/``` command to search, ```n``` to go next, ```N``` to go to the previous search. The ```?``` command searches backwards. I used the / command to search the word "flag" to find an argument to use.
```bash
hacker@man~searching-manuals:~$ man challenge
--jwvy This argument will give you the flag!
hacker@man~searching-manuals:~$ /challenge/challenge --jwvy
Initializing...
Correct usage! Your flag: pwn.college{_}
```

## Searching for manual

This is the first time I had to search online to see how to search for the manual. I got confused due to the rather verbose language (although understandably so) and needed a shorter description. I found a better and easier version of the argument on GeeksforGeeks and understood that the ```-k``` command searches across all the man pages. from this, I saw the command ```chkinauypo```. I ran the ```man chkinauypo``` command, and it worked. I got the syntax of the argument

 ```bash
hacker@man~searching-for-manuals:~$ /challenge/challenge --chkina 468
Correct usage! Your flag: pwn.college{_}
```

## helpful programs
running the ```--help```, ```-h ```, or the ```/?``` argument with the program will usually tell you the description of the program. We have to do the same here.
```bash
hacker@man~helpful-programs:~$ /challenge/challenge -h
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 808
hacker@man~helpful-programs:~$ /challenge/challenge -g 808
Correct usage! Your flag: pwn.college{_}
```
## ```help``` for Builtins
the ```help``` command can be used if the command/program you are trying to get the description for and details about is a shell builtin. We run the ```help``` command with ```challengee```.
```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "sKX-yp6W".
hacker@man~help-for-builtins:~$ challenge --secret sKX-yp6W
Correct! Here is your flag!
pwn.college{sKX-yp6WOr44cOtoSAAWOW_qVh8.dRTM5QDL1IDM2czW}

hacker@man~help-for-builtins:~$
```
