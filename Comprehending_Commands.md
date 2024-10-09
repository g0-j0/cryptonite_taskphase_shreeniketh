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
```grep``` is a command on Linux that searches for a string in a file. Let's say I have a ```abc.txt``` file with millions of lines, and I need to find out the string that has ```hello``` in it; I run the command ```grep abc.txt``` to figure out the entire string. Actually, running the command will provide a better understanding of how it works.
```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep 'pwn.college' /challenge/data.txt
pwn.college{_}
```
## listing files
The ```ls``` command lists the directories and files in a directory. ```ls```lists the directories and files in the home directory, and ```ls /directory_name``` lists the directories in that specific directory. In the challenge, we have to list the files in the ```challenges``` directory and get the key from there, as the key is stored in a randomly named file.
```bash
hacker@commands~listing-files:~$ ls /challenge
3934-renamed-run-7294  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/3934-renamed-run-7294
Yahaha, you found me! Here is your flag:
pwn.college{_}
hacker@commands~listing-files:~$
```
## touching files
The ```touch``` command creates a new file in the directory, the syntax being ```touch filename```. In the challenge, we have to create a pwn and college file in the ```/tmp``` directory to run the program. We do this by running ```touch /tmp/pwn``` and ```touch /tmp/college```.
```bash
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{_}
hacker@commands~touching-files:~$
```
## removing files
```rm``` command removes a file. The syntax is: ```rm filename```. We cannot keep every single file and must delete some files. Hence, the ```rm``` command. In this challenge, we have to remove a delete_me file and run the file /challenge/check
```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{_}
```

## hidden files
```ls``` command doesn't list all of the files, there are certain hidden files, typically starting with  a ```.```. that do not show up in a typical ```ls```  command. We need to add the flag ```=a```. In the challenge, we have to find the hidden file, and hence the flag.

```bash
hacker@commands~hidden-files:/$ cd
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.  ..  .dockerenv  .flag-251202052726410  bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~hidden-files:/$ cat /.flag-251202052726410
pwn.college{_}
hacker@commands~hidden-files:/$
```
## An Epic Filesystem Quest
This is my first "Actual" question in the entire challenge. Everything else up until now was learning. I'll go through my thought process:

First, I read the question carefully. It wanted me to find the hidden flag using cd, cat and ls commands and follow it. 
Second, I went to the ```\``` directory as the instructions say.

I do these two, and decided to see what happens 
There are many, many,many clues, to the point I started doubting if I had missed a trick earlier, but I decided to carry on, as it the commands weren't specifically hard. I didn;t find it hard, just slightly annoying.

I'll paste my entire logs in a bash
```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.  ..  .dockerenv  LEAD  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~an-epic-filesystem-quest:/$ cat LEAD
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/drivers/net/ethernet/intel/ixgbevf

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/drivers/net/ethernet/intel/ixgbevf
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/net/ethernet/intel/ixgbevf$ ls -a
.  ..  Makefile  REVELATION  defines.h  ethtool.c  ipsec.c  ipsec.h  ixgbevf.h  ixgbevf_main.c  mbx.c  mbx.h  regs.h  vf.c  vf.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/net/ethernet/intel/ixgbevf$ cat REVELATION
Lucky listing!
The next clue is in: /usr/lib/debug/.build-id/91

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/net/ethernet/intel/ixgbevf$ cd /usr/lib/debug/.build-id/91
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/91$ ls -a
.  ..  .BRIEF  1f10334387e649db066e64d7f4eff2dc492b7c.debug
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/91$ cat .BRIEF
Yahaha, you found me!
The next clue is in: /usr/share/doc/liberror-perl

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/91$ cd /usr/share/doc/liberror-perl
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/liberror-perl$ ls -a
.  ..  .MEMO  changelog.Debian.gz  copyright  examples
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/liberror-perl$ cat .MEMO
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/IPython/testing/plugin
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/liberror-perl$ cd /usr/lib/python3/dist-packages/IPython/testing/plugin
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/IPython/testing/plugin$ ls -a
.   DISPATCH    __init__.py  dtexample.py  iptest.py  show_refs.py  simplevars.py   test_example.txt    test_ipdoctest.py
..  README.txt  __pycache__  ipdoctest.py  setup.py   simple.py     test_combo.txt  test_exampleip.txt  test_refs.py
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/IPython/testing/plugin$ cd DISPATCH
ssh-entrypoint: cd: DISPATCH: Not a directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/IPython/testing/plugin$ cat DISPATCH
Tubular find!
The next clue is in: /opt/linux/linux-5.4/net/nfc/hci

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/IPython/testing/plugin$ cd
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/net/nfc/hci
cat: /opt/linux/linux-5.4/net/nfc/hci: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ cat ./opt/linux/linux-5.4/net/nfc/hci
cat: ./opt/linux/linux-5.4/net/nfc/hci: No such file or directory
hacker@commands~an-epic-filesystem-quest:~$ grep "pwn.college" /opt/linux/linux-5.4/net/nfc/hci
grep: /opt/linux/linux-5.4/net/nfc/hci: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/net/nfc
cat: /opt/linux/linux-5.4/net/nfc: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/linux/linux-5.4/net/nfc/hci -a
.  ..  GIST-TRAPPED  Kconfig  Makefile  command.c  core.c  hci.h  hcp.c  llc.c  llc.h  llc_nop.c  llc_shdlc.c
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/net/nfc/hci/GIST-TRAPPED
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/Documentation/devicetree/bindings/mips/cavium

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/linux/linux-5.4/Documentation/devicetree/bindings/mips/cavium -a
.  ..  NOTE-TRAPPED  bootbus.txt  cib.txt  ciu.txt  ciu2.txt  ciu3.txt  dma-engine.txt  sata-uctl.txt  uctl.txt
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/linux/linux-5.4/Documentation/devicetree/bindings/mips/cavium/NOTE-TRAPPED
/opt/linux/linux-5.4/Documentation/devicetree/bindings/mips/cavium/NOTE-TRAPPED
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/Documentation/devicetree/bindings/mips/cavium/NOTE-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/share/racket/pkgs/typed-racket-lib/typed-racket

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/share/racket/pkgs/typed-racket-lib/typed-racket
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/typed-racket-lib/typed-racket$ ls -a
.   .CUE         base-env  core.rkt  infer     language-info.rkt  minimal      optimizer  rep                 static-contracts  typecheck         typed-reader.rkt  utils
..  HISTORY.txt  compiled  env       info.rkt  logic              minimal.rkt  private    standard-inits.rkt  tc-setup.rkt      typed-racket.rkt  types
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/typed-racket-lib/typed-racket$ cat .CUE
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/include/linux/ceph
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/typed-racket-lib/typed-racket$ cd
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/include/linux/ceph
cat: /opt/linux/linux-5.4/include/linux/ceph: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/linux/linux-5.4/include/linux/ceph -a
.   MESSAGE  buffer.h      ceph_features.h  ceph_fs.h    cls_lock_client.h  decode.h   mdsmap.h     mon_client.h  msgr.h        osdmap.h    rados.h         striper.h
..  auth.h   ceph_debug.h  ceph_frag.h      ceph_hash.h  debugfs.h          libceph.h  messenger.h  msgpool.h     osd_client.h  pagelist.h  string_table.h  types.h
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/include/linux/ceph/MESSAGE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{_}
hacker@commands~an-epic-filesystem-quest:~$
```
It was fun but rather monotonous. The only mistakes I made were slight confusion in commands due to my lack of experience in Linux.

## making directories
```mkdir``` command makes a directory where you can place files. The syntax of ```mkdir``` is ```mkdir directory_name```. The next challenge requires me to make a directory ```temp/pwn``` and then make a college file, after which I can run the ```/challenge/run``` file.

```bash
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{_}
hacker@commands~making-directories:~$
```

## finding files
```find``` command lists down every single file and directory in the directory. It takes arguments to narrow down the searches. The syntax is ```find -name file_name```. It will give the output of every file with the filename in the directory. 
```bash
hacker@commands~finding-files:/$ find -name flag
find: ‘./root’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/task/7/ns’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./usr/local/lib/python3.8/dist-packages/jupyterlab/tests/mock_packages/test_no_hyphens/test_no_hyphens/flag
./usr/local/lib/python3.8/dist-packages/pwnlib/flag
./usr/local/share/radare2/5.9.5/flag
./opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
./opt/radare2/libr/flag
./nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
./nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:/$ cat ./usr/local/lib/python3.8/dist-packages/jupyterlab/tests/mock_packages/test_no_hyphens/test_no_hyphens/flag
pwn.college{_}
```
## linking files

links allow us to access data from one file to another. There are two types of links: hard linking and soft linking. Hard linking is just us copying the data into a new file, while soft linking is us accessing the original file data through the new file. This saves space and allows us to go past a few easy restrictions that can be placed on hard links. The syntax for it is ```ln -s direc_1 direc_2```. You can find if a file has a soft link by using the ```file filename``` command.

I don't know if this was the intended solution, but I noticed that the catflag was linked to the not-the-flag file. So I just htought why not link the not-the-flag file to the /flag file, and then find if that works
```bash
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{_}
```
