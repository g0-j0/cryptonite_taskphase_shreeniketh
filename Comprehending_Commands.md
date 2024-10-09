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
In this challenge, we use cat commands to get more comfortable with them. The flag is located in some random directory, and it is our job to figure where it is.
