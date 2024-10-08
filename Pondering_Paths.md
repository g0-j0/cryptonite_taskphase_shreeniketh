# Pondering Paths
This module is about the directory/file paths in Linux

## The Root
The challenge introduces us to how to access a file, directory, or program in Linux by adding a ```/``` to your filename, i.e. the syntax is:  ```/filename```. In this challenge, we run a program ```pwn``` by invoking ```/pwn```.

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{0UsrXFl9wLV76m_VTitsncZBPaO.dhzN5QDL1IDM2czW}
```

## Programs and Absolute Paths
The challenge "digs" deeper into the file system by showing us the concept of absolute path and navigating down to a particular file within a directory. Here, we use the syntax ```/directory_name/file_name```. In this case, we run the command ```/challenge/run```, where ```challenge``` is a directory (a folder, for the more common term), while ```run``` is the file. 

```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4NOJXhcUUapJwWVh7jz6mu89cCE.dVDN1QDL1IDM2czW}
```

## Position Thyself
We learn about a new command, ```cd```, whose full form is "***c***urrent ***d***irectory" (A Better and more obvious way to say it would be "***c***urrent working ***d***irectory). We use ```cd``` to change where we are in the filesystem. The syntax is ```cd /directory_name```. I had to go to the ```/``` directory in this challenge, which initially confused me. I didn;t see that, and I thoguth we had to "guess" the directory or the directory was hidden in the challenge. I read the error message carefully and understood I had to run ```cd /``` command, and then run ```challenge/run```. This gives us our key

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
pwn.college{sflv6SC5-hf778Tboxnv6oMN1ix.dZDN1QDL1IDM2czW}
hacker@paths~position-thy-self:/$
```
