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
