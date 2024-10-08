# Pondering Paths
This module is about the directory/file paths in Linux

## The Root
The challenge introduces us to how to access a file, directory, or program in Linux by adding a ```/``` to your filename, i.e. the syntax is:  ```/filename```. In this challenge, we run a program ```pwn``` by invoking ```/pwn```.

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{_}
```

## Programs and Absolute Paths
The challenge "digs" deeper into the file system by showing us the concept of absolute path and navigating down to a particular file within a directory. Here, we use the syntax ```/directory_name/file_name```. In this case, we run the command ```/challenge/run```, where ```challenge``` is a directory (a folder, for the more common term), while ```run``` is the file. 

```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{_}
```

## Position Thyself
We learn about a new command, ```cd```, whose full form is "***c***urrent ***d***irectory" (A Better and more obvious way to say it would be "***c***urrent working ***d***irectory). We use ```cd``` to change where we are in the filesystem. The syntax is ```cd /directory_name```. I had to go to the ```/``` directory in this challenge, which initially confused me. I didn't see that, and I thought we had to "guess" the directory or the directory was hidden in the challenge. I read the error message carefully and understood I had to run the ```cd /``` command and then run ```challenge/run```. This gives us our key.

```bash
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /
hacker@paths~position-thy-self:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{_}
hacker@paths~position-thy-self:/$
```

## Position elsewhere

This was the same as the above. I wanted to know if there was anything new in the text given in the challenges, but I didn't notice anything. The commands we had to use were the same too. Nothing much to add

```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /
hacker@paths~position-elsewhere:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{_}
hacker@paths~position-elsewhere:/$
```

## Position yet elsewhere

We can traverse the filesystem more quickly by writing down the required directory. There are technically two solutions, using the ```cd``` command to traverse through each directory, or the shorter ```cd /var/lib/apts/lists``` command, though it might end up being more challenging to keep track of when traversing a more complex system. Nevertheless, the solution was trivially found by running the above command.
```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{_}
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$
```

# Implicite relative paths, from /
Relative paths are a different way of traversing the filesystem. While absolute paths are based on the root, relative paths are based on your position. Lets say you are in the ```a``` directory, to traverse to ```\a\b\c\d```, you can run ```b\c\d``` to run the file ```d```. I was slightly confused because I kept running the ```/challenges/run``` command, but then I quickly realised my mistake.

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{_}
hacker@paths~implicit-relative-paths-from-:/$
```

## Explicit relative paths, from /
Explicit relative paths don't deal with specific directory names. Instead, we use ```.``` and ```..``` for directory names. an example of how this works is ```./challenge``` is the same as ```././challenge././``` as the ```.``` symbol is the symbol for being in the same directory.

```bash
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{_}
hacker@paths~explicit-relative-paths-from-:/$
```

## implicit relative paths
In Linux, we cannot run a file implicitly, i.e. if we are in the ```/challenges``` directory, we cannot use the command ```run```. Instead, we have to use the ```./``` command; in the above example, we would use ```./run``` command. This is a safety feature in Linux to prevent accidentally running programs you didn't want to.
```bash
hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4sNE_ZFds_2KmxvUtCwILQwolCK.dFTN1QDL1IDM2czW}
hacker@paths~implicit-relative-path:/challenge$
```
