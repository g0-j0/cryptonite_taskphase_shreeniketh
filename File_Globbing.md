# File Globbing

Globbing is a way to type files without going through the entire path.

## Matching with *
```*``` basically acts as a fill-in-the-blank, where the * character can be replaced by any string of characters. An example is if I run ```echo Look: file_*```, it prints out every single file starting with ```file_```. This could save the amount of time required to type out the file.

```bash
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{_}
```
## Matching with ?
```?``` treats it as a fill-in-the-blank, except it's only a single character. This way, we can easily differentiate between ```file_a``` and ```file_cc```. This challenge is very similar to the above one.

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{_}
```
