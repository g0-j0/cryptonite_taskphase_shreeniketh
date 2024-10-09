# Comprehending Commands

## ```cat```: not the pet, but the command!
The ```cat``` command reads the files out. It con***cat***enates the output of the files if multiple files are provided, hence giving us the name. Without any argument, it reads the terminal input and prints the output in the terminal itself. The syntax for the cat command is ```cat filename```. In this challenge, we run the command ```cat flag``` to get the flag for the challenge.
```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{_}
```
## ```cat```ting absolute paths
The above ```cat``` command can also be used with absolute paths in case the relative path is complicated. The syntax, which should be obvious, is ```cat /directory_name/file_name```. We run the ```cat /flag``` command to get the flag in this challenge
```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{_}
```

## more ```cat```ting practice
In this challenge, we use ```cat``` commands to get more comfortable with them. The flag is located in the ```/lib/ecl/flag```, and we must use the ```cat``` to get the key along with the absolute path. The solution is ```cat /lib/ecl/flag```.
```bash
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/ecl/flag. Go cat it out **without** cding into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/ecl/flag
pwn.college{_}
hacker@commands~more-catting-practice:~$
```

## ```grep```ping for a needle in a haystack
```grep``` is a command on Linux that searches for a string in a file. Let's say I have a ```abc.txt``` file with millions of lines, and I need to find out the string that has ```hello``` in it; I run the command ```grep abc.txt``` to figure out the entire string. Actually running the command will provide a better understanding of how it works.
```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep 'pwn.college' /challenge/data.txt
pwn.college{_}
```
## listing files
the ```ls``` command lists the directories and files in a directory. ```ls```lists the directories and files in the home directory, and ```ls /directory_name``` lists the directories in that specific directory. In the challenge, we have to list the files in the ```challenges``` directory and get the key from there, as the key is stored in a randomly named file.
```bash
hacker@commands~listing-files:~$ ls /challenge
3934-renamed-run-7294  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/3934-renamed-run-7294
Yahaha, you found me! Here is your flag:
pwn.college{_}
hacker@commands~listing-files:~$
```
