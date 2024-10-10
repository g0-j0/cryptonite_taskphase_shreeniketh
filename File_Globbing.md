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
```?``` is treated as a fill-in-the-blank, similar to the above example, except it's only a single character. This way, we can easily differentiate between ```file_a``` and ```file_cc```. This challenge is very similar to the above one.

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{_}
```
## Matching with []
```[]``` essentially acts like a list of ?, and if any of the characters matches, It will print it out. For example, ```echo Look: file_[ab]``` wi ill give the output ```file_a file_b``` as output, if both files exist. This challenge was easy, too; all I had to do was to run ```file_[absh]``` as a parameter to the ```/challenge/run``` program.

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_b  file_c  file_d  file_e  file_f  file_g  file_h  file_i  file_j  file_k  file_l  file_m  file_n  file_o  file_p  file_q  file_r  file_s  file_t  file_u  file_v  file_w  file_x  file_y  file_z
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{_}
hacker@globbing~matching-with-:/challenge/files$
```
## Matching paths with []
There is not much to say here; it's just that we can use the globs with absolute paths, too, and not only relative paths. We are required to do so for the challenge. It was pretty simple, I just rushed into it and thought I had to access the fie from ```/challenge/run```

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{_}
```

## mixing globs
We can have multiple globs in the same line to check for various things simultaneously. It's pretty blatant. Hence, there is nothing to add, so I'll move on to the solution.

```bash
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cpe]*
You got it! Here is your flag!
pwn.college{_}
hacker@globbing~mixing-globs:/challenge/files$
```

Originally, I thought we had to run the command, so that took some extra time. Later, I ran it in a relative path, giving the output at least. All I had to refine was what I had to write relatively.

## Exclusionary globbing

```!``` and ```^``` essentially act as an inverter, telling the computer not to find what you are searching for with globs.

```bash
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{_}
```
