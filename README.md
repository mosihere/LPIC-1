# An introduction to LPIC-1

## GuideLine

- [Move](#move)
- [Remove](#remove)

Check the **details** of a file with:
> ls -ltrh file_name
---

Use to check the **format** of a file:
> file file_name
---

**Copy** a file: 

> cp ~/Pictures/screenshot.png (optionally new_name_for_file) (destination)

<br>
Use this command to copy a file at the same place :

>  cp test.txt copyTest.txt 

<br>
We can also **copy multiple files** into another directory like below:

> cp new newfile mostafa.txt myjob
 
 **Tip** -->  myjob is a **Directory**.

---

**Convert** a file like this:
> convert ~/Pictures/screenshot.png screenshot.gif

---
This act like **Double-click** on a file:
 >  xdg-open < file name >
---

- Check the **format** of a file with **ascii**, **hex** and etc:

> od -a < fileName > | head

**Tip** -->  **head** shows 10 first lines of a file!

---

We can use **hexedit** to edit the signature of a file (change the file format to encrypt and interrupt that) 

> hexedit < fileName >

- **F1** to show help
- **F2** to save
- **CTRL + x** to save and exit

---

Open the file:
> feh < file_name >

<br>

## Move

**Rename** a file:

> mv old.txt new.txt

- it will change the name of new file to old with all content
<br>

Move **Multiple files** at once:

> mv old test tips mydir/

<br>

Rename **Directories**:

> mv mydir mydirecotry

<br>

## Remove

**Remove Files**:

> rm myfile

**Remove Directory**

> rmdir mydir


**Hint** --> if we want to **create a nested directory** for example create a mydir/test/Mosihere, we can't use mkdir mydir/test/mostafa

we have to used -p switch to do that (-p means parent it will create directories in parent easily)

> mkdir -p mydir/test/mostafa

**Tip** --> we can back directory two or second time with this command:

> cd ../../..

**Hint** --> we can't remove a directory that has a file or another directory
we need to use -r switch to recursively delete directory and items in it.

> rm -r myDirectory/

We can't **copy a directory to another directory** we have to use -r switch

cp -r mydir seconddir

<br>

### Tip

If we copy a file to another existing file the second file will be **lost contents** and **overwrite** with the first file !

**Solutions** --> use -i switch to interactive

> cp -i first second

we can use -b switch to make a **backup**:

> cp -b test test_2

it will create a new file named test_2~ (~ means back up)

Another Important Switch for cp command is **-p**

> cp -p first second

it will save the **detail of attributes** like -> Date - Time - access

**-f** is default and **force** the file to overwrite without permission

<br>

## Work with ls in advanced level

Use **\*** to select all files or we can use it like this:

copy all files start with f and copy them to test directory

> cp f* test

copy all files that starts with (f) and end with (p)

> cp f*p test

Using question mark (?)
which means all files start with f and has one character after that !
> ls f? 

means all files that start with f and has 2 more character !
> ls f??

it means all files start with f and one more character and end with everything else ( it means it need more than on character )

> ls f?* --> 


**Hint** --> we can use:
> ls [ab]* 

 which means all files and directories start with (a) or (b) and end with every char with every length.

 > ls ?[a1]*
 
 show all files and directories that start with one character and second char is (a) or (1) and everything after that ...

<br>

## Touch

if we use **touch** for a file that **exists**,  we just modify info of that file (creation date).

if that **doesn't exist** -> it will create a new file.

we can also use switch to handle touch

> touch -d yesterday test.txt

**-d** stands for **date**

 if we want to write a longer string that needs spaces we have to use qutation:
 > touch -d '6 october 1998' myfile

**-t** stands for **time stamp**:
> touch -t 202008101510.59 myfile

special advanced mode --> to use date of a file to another file:
> touch -r first-file.txt second-file.txt

**-r** Switch stands for **Reference of date**.

it will modify the second file creation date with first file --> for example if first file date is 8 septemper and second is 20 septemper --> second will be 8 septemper too !

<br>

## Find

we can use this command to find all files and directory that starts with special character.

> find -iname 'f*'

**-iname** switch is stands for **inSensitive name** --> find both a-A ...

find all files and directories that start with f and end with everything

if we want to find **directory** we have another switch like this:

> find home/mosihere/myProject/python -type d -iname 'f*'

find just files start with (d)
> find . -type f -iname 'd*'


**Tip** --> find by size:

>find . -size 0

**Hint** --> we also have **-empty** switch to find 0 bite files:

> find . -empty

 100 bites or 100 character
 
> find . -size 100b

find all files with more than 1GB

> find . -size +1G

and ...
> find . -size 100k
> find . -size 100m

<br>

**Find Files** with three more ways:

1. (access time) last time we read file.
> find . -atime

2. (change time) when we change the user or we change the date or change the user ( not only change the real data of file).

> find . -ctime

3. (modify time) we exactly change the data in the file.

> find . -mtime

fetch us the files that access in 6 * 24 hours --> like 6 days ago --> we also can use +6 or -6 or just exactly 6

> find . -atime 6 --> 

we also can find files with **Minutes** !

find all that has been accesed in last 60 min.

> find . -amin -60

1. **-amin** --> **'access minutes'**
2. **-mmin** --> **'modify minutes' **
3. **-cmin** --> **'change minutes' **

**Hint**:  if we want to do it in a most simple way, we should use  **-daystart** switch instead -amin or -mmin or -cmin

we also can use **-ls**  right after find command:

 find all files in this directory that access in last 2 hours and then list them
 
> find . -amin -120 -ls 

or we can use **-print** instead of -ls

> find . -amin -120 -print

**Tip** --> we can find our needed files and make change on them like this:

> find . -iname '.htm*' -exec mv '{}' '{}l' \;

it means find all files named .htm and execute them (execute used for access the another command like 'mv') so move them (here means rename) {} all u find into all u find just append 'l' to them finaly all htm files changed to html files.

<br>

## File

Check **details** of a file:

> file equlizer.srt

for example in windows we can just check the .jpg or .mp4 and etc.. to find out what this file is !?

but in linux we can check them and really find out what's happen !

Check this example below:

> find . -iname '*jpg' -exec file '{}' \;

It'll find all files end by **.jpg** and make them execute and finally run the file command on each of them and list them!

file also has a special switch that and it is  **-i**

>file -i mydir

**-i** stands for **mime** so it describes what kind of file it is !

<br>

## Compressing File

**compress** our file to .gz:

#### Using **gzip** and **gunzip**:

to make a zip file:

> gzip < fileName >

 to **unzip** file:

**gunzip** < fileName >

<br>

#### Using **bzip2** and **bunzip2**:

To make a zip file:
  
  > bzip2 < fileName >

To unzip a zip file:
> bunzip2 < fileName >

<br>


## Archive Files with Tar

**Archive files** means make all files into one big file.

> tar cf myArchive.tar (filesName)

**Hint** --> but if we wanna create a file and **zip** that immediately we have to use this switch:

> tar cfz myArchive.tar *

**Tip** : If we want to see **which files are compress** we can use this switch:

(Create File Zip Verbos)

> tar cfzv myarchive.tar *

<br>

#### How to open a archive .tar file:

>tar xf myArchive.tar

it will (xf switch is stand for Extract File ) open the archive file and after that delete the compress file

**Trick** ---> we can also append a new file to our archive file (our big tar file)

we should first of all with (mv) change the .tar to .tar.gz and next we have to use:

> gunzip myArchive.tar.gz

and finaly use this command:
> tar rfv (newFile that we want to append)

<br>

## CPIO

we want to archive some files into one and we can open it later

the command is like this bellow:

> ls | cpio -o > cpioArchive

first we want a list of files of our directory and then with pipe ( | ) we send our data to cpio --> the -o switch means OutPut

finally we send output to a < fileName >

#### how to extract the cpio file

> cpio -id < cpioArchive

**-id** switch is stands for 
- i == input   d 
- == directory

if we don't use d it won't open directory as default.

<br>

## dd

dd is something like copy but it's much more complete For Instance:

> dd if=myArchive.tar of=newfile

it will copy all data of if to of 
- if == Input File
- of == OutPut File

but we can do more than this with dd command for example we can directly

**bootable a USB** or **create a system backUp** for ourselves !

like this:

> sudo dd if=archlinux-2020.05.01-x86_64.iso of=/dev/sdb bs=4096

it means our input file is arch iso and our input file is our USB and finally

**bs** stands for (Bite Size == 4096KB) it is a CD Standard !

<br>

#### Creating a backUp:

> dd if=dev/sda1/ of=backupsda1.dd bs=4096

#### Restore backup:

that's easy, just use if instead of and vice versa

> dd if=backupsda1.dd of=/dev/sda1 bs=4096

<br>

#### create a file with 100MB with dd

> dd if=/dev/zero of=1g.test bs=100M count=1

it'll fetch data from zero directory or file and write it in a single 100MB Block with name of 1g.test --> count=1 means 1 time 100MB Block created

<br>

## Stdin-Stdout-Stderr

1. **stream input**: every data we declare such as keyboard typing and etc ..

2. **stream output**: every output that we see in shell like ls command.

3. **stream error**: every error that we see in terminal such as:
 > ls x*
 
  if there is no file start with x , then we see an error.

**Hint** --> how to control these three ! ---> for example we want to use ls command and if there is no error, the answer send to inputFile.

if this command raise an error for example ls x* --> there is no file that start with x !

> ls x* m* 2> error 1> listFile

now we can < cat > error to see the error if there is an error.

and also we can < cat > listFile to see result of ls command in it !

**Tip**

 0 means input (stdin)

1 means output (stdout)

2 means error (stderr)

if we don't use any number between these three ! terminal set **0** as default

for example --> ls > mylist ( will contains data output in mylist and it means as default it use 1 (stdout)

*** Hint *** as default when we use this method --> ls a* > myfile

each time we use this command the data will overwrite

but what if we wanna just append the new data to other ?

**solution is**:

> ls m* >> myfile

when we use double arrow it means **append**!

we call all these **Redirect**.

<br>

#### Important ShortCut:

 now think we wanna redirect both output and error at the same time in a same file or whatever !

**what can we do?**:
*
**&>** it's a cool shortcut.

**for instance**:
> ls x* a* &> myStream

It'll send both output(stdout'1') and error(stderr'2') to the myStream File.

if we don't use this shortcut we have to use this long command bellow :

> ls x* a* 1> myStream 2> mystream

Another ShortCuts are (( &0 &1 &2 ))

it means right there that the data is send

lemme crystallize that for you:

>ls x* a* > output 2> 1&

it exactly means check every file start with **x** or **a** and print output in output file and if there is an error, send the error to the (stdout) path

#### Conclusion:
- **0&** refers to **stdin**
- **1&** refers to **stdout** 
-  **2&** refers to **stderr**

#### ok now let me introduce a dark big hole to you :))

 every data that send here are going to hell and they will be lost, sounds odd :)) !

> /dev/null

that's it:

> ls -R / x* > /dev/null 2> myError

it will create a recursively list of all root system and ofc there are so many files and directory !

we won't see the list and we just parse raised error and manage them seprately, send them to the myError File !

#### How to control stream of data in input :

>  tr ' ' ',' < file.txt

 < tr > means **translate** all spaces in file.txt and use comma instead of space !

with this method we can create a unique keyword and control our stream(input) like this:

>tr ' ' '-' << END_OF_DATA

when we use this command, shell wait for us to give the data and we can type whatever we want and finally when we use the unique key again, the input going to close soon !

<br>

## Pipe

Pipe --> ( | ) will send the **output of first** command to **input of second** command.

for instance:

> sort fileX | cat fileY - fileZ

it means first of all sort file x

second send the data to the cat

finally it will cat fileY first then sorted fileX and last cat FileZ

#### sort a file and cat that:

> cat howcool | sort 

or we can simply use this:

>sort howcool

or use:

>sort < howcool

but some command like <tr> **doesn't accept** this operand

we must use a input for that

> tr 'j' '*' < howcool 

or

> cat howcool | tr 'j' '*'

<br>

## xargs

xargs read input from (stdin) and use them for arguments we will use for xargs

for better understanding this look at the story bellow:

we wanna use ls command and echo them all

but we can't !

we have to use this:

> -ls | xargs echo these are my files

**XARGS** put all input data to next command after itself !

exactly it means ls then with pipe( | ) send data to xargs --> so now xargs will pass the data to next command of itself and that command is echo

and echo finally print out all data after everything we write

ok now we can use it in better way

listen ! lets delete all files started with a

all we have to do is:

1. find them with find commnad
2. use pipe to send the data to another command
3. use xargs to do sth with next command about these files that founden before !
4. use rm

ok lets start:

> find . -name- 'a*' -type f | xargs rm

find files from here, name start with **a** and type of them must be Files --> send them to xargs, xargs pass them to rm and finally remove all of them

#### xargs has a switch called --> --max-args < number >

we also can use:
 **-n 2** instead of **--max-args 2**

command:
> xargs --max-args 2 echo myfiles are << END

job

python_work_out

github

games

END ( is unique key and ofc it will finish the input)

so the output is --> my files are job python_workout

my files are github games

-L Switch is also use for line --> if we type 5 files in a line and then use Enter --> this switch will print 5 files name and then start again for next line

more simpler command is:
> ls | xargs --max-args echo 3 Files Are:

it will send the ls command to xargs -> xargs with switch max args 3

will set the 3 files name after this sentence ( Files Are: )

so finally the output must be --> Files Are --> 1 2 3

Files Are --> 4 5 6

etc ...

now another switch is -I < keyword >:
> ls | xargs -I INPUT echo the name is INPUT and it is fun

**HINT**: here -I is used with a keyword (INPUT) and every Where we use INPUT the file name is going to fill that !

**conclusion** --> output will be --> the name is newFile and it is fun

we want to copy files start with number to another directory (named number) with xargs

first of all we find them like this:

> find . -name '[0-9]*'

then pass it to xargs with switch -I and use mv command after xargs

> find . -name '[0-9]*' | xargs -IX mv X number/

it will move all files start with number to /number directory.

**Tip** when we say stdin ( standrad input ) we can use 3 ways

1. pipe |

2. Redirect  > 

3. Typing ( without two above )

<br>

## TEE

we can use this command to see the **details** of **standard input live** in the **shell**.

for instance:
> ls | tee fileout

will send the stdout to fileout File and also print it in the shell, it's similar to redirect data to some file and cat that file.

**switch -a**: if we use -a in tee it means append --> the command won't overwite data and ofc it's append to the past data

<br>

## Process In Terminal

how to kill process.

how to start process in background and etc.

with  **&**  after every command we can **run that in background**

> sleep 100 &

 ( pc sleep for 100 secs)

**CTRL + C**: break a command that running !

**CTRL + Z**: will freeze a command and that command stop but still exist in background !

later we can start it again and unfreeze that.

**hint**:  we can check app or commands those work in background with this command :

> jobs

we can start,  stopped(freeze) process in background  with this command:

> bg

with fg command we can bring background running program to forground

> fg 

for crystallize look at the example bellow :

> sleep 1000 &

pc will sleep for 1000 seconds in background because of &

and we can fetch it from background to forground with this command :

> fg %2

 if it's the second program that run in background

we also can use:

> kill all

 or
 
>  kill %2

<br>

#### what is NOHUP:

we can use this command to **run programes in background after log out and shutdown system** !

like this:

> nohup sleep 1000 &

it will create a file named **nohup.out** so we can check it later.

**Hint**:  when we close terminal when it contains running background apps

we can use this command to check all "nohup" program

> ps -ef | grep sleep
 
 it will show us all sleep command that used before and continue in background

**Tip**: we also can use this method:

> nohup script.sh > mynohup.out 2>&1 &

its exactly mean --> **run script even when i log out the system**

send the data of that to a file named mynohup.out and also send all errors there too ! finally run this in background !

we can kill this nohup too -->

> kill %1

(the number that find in jobs command)

switch **-9** for **kill command** will force close the app but the default switch is -15 ( when we don't use switch, default switch is this ! )

**Hint**: when we use:

>kill -9 %2

it will kill process.

but:

> kill %2

 it will terminate the process ( does not forced the app ).

if we have 5 bg sleep command, and we wanna close them all

we have to used:

>killall sleep

**Tip**: if we want to find process ID of apps that start in background we can use this commnad: 

> jobs -l

-l switch means **Long**

<br>

## PS

if we wanna check out all process those running in system, we could use:

> ps -aux 

will show all process in system

> ps

will show just running app in background not from whole system

> ps -l 

will show long data

> ps -lf 

will show long data and full command

<br>

## Top

we can check all process in terminal with top command, something like task manager

when we use top it will show us memory usage and cpu usage and etc.

1. **q** for **quit**
2. **h** for **help**

with capital **M** for **changing view** **from cpu usage** **to memory usage**

we can use **c** to **show full command** instead of command name

**k** is used for **kill app** used in cpu

for example we push the k button then ask for pid ( process id )

we have to find pid of our intended process

then we can kill that

hint --> kill send a signal to process and it has 2 signal at all

15 is default ( softly close program ) -- 9 ( force close program )

<br>

## free

it used for find out how much memory is free !

the famous switches for that are:

> free -g
> free -m

**m** stands for **MB** and **g** stands for **GB**

<br>

## uptime

up time will show us how much time does system on.

> uptime

<br>

## nice

we can control process with nice command.

if nice == 0 it means it is **normal**.

if nice is **high** it means it **allow others process run first**.

if nice **-10** or negative it means this process is so unfriended and want to run first of all

-20 is the most angry process and 19 is super nice.

**Tip**:  if we want to use a program or command and we want to use less cpu or kinda that's program not important too much, we can use command like this:

> nice sleep 1000 &

it means first use cpu for another process

if it is ok then use cpu for this sleep command !

**Hint**: nice default is 0

**n Switch**: 

>nice -n 19 sleep 1000 & 

use the lowest level of cpu for this command

now for example we run a program with nice command and now we wanna change the niceness of that --> we have to use :

> sudo renice -n < process ID of that program >

we can also find process id with this command:

> ps -lf

**Tip**: we can **increase** the priority (niceness) of process **without root permission**.

but we **can't decrease** priority (niceness) without sudo ( root permission ).

**Tip**: we can also use something like this to find PID (process ID):

> ps -lf | grep xeyes

<br>

## REGULAR EXPRESSION

> grep f friends.txt

find all f characters in friends file:

> grep a+ 

means find a if a is one or more , but if there is no a it will not show anything

> grep a* 

it means find a if a is zero or more.

**Hint**: sometimes we need to use escape character to use regular expression truely, for instance:
 
 > grep a*

will look for a and start in text 

we have to use:

> grep 'a*'

so we have a solution:

> grep -E 'a*s' friends 

**-E** switch means **Extended** and **if we use this switch**, we **don't need to escape characters** anymore !

it exactly means find if there is any a or there isn't any **a** and after that is there any **s** ? if yes, find them.

**Tip**:
1. a+ ( 1 a or more )
2. a* ( 0 a or more )
3. a? ( 0 a or 1 )

<br>

### egrep

we can use ( egrep ) instead of (( grep -E ))

if we want to find all names that includes a or b or c we have to use this command:

> egrep '(a|b|c)' friends.txt

if we wanna find any character and after that a for example:

> egrep ".a" friends.txt

 --> mi(n)a

> egrep "[A-F]"

 --> find all character between A to F

if we want to find all a after any character ( it means second character must be a )

we have to use this command:

> egrep "^.a" friends.txt

if we use:

> egrep "a$" friends.txt

means **a** must be the last character

**Tip**: 
1. **first character** come after **^** 
2. **last character** is before **$**

hard example:

> egrep "^ [a-h].*a$" friends.txt

find all names that start with a-b-c-d-e-f-g-h and after that any character with any duplicate and finally end with (a).

<br> 

### egrep Swithces

1. -c (show the count per line ) --> egrep -c o what_I_have.txt ( find 6 lines that includes o )

2. -v (reverse the search) --> egrep -v o what_I_have.txt ( will find all o and then because of reverse, won't show o, show all names that NOT include o)

3. -n(show line number)

4. -l(only show file names)

5. -i(case insensetive)

<br>

## Fixed Grep

fgrep or grep -F

lemme show u a bug, if we want to find a name that finished with (d$)

David\$, what should we do ! we can't use egrep "\$\$" or egrep "d$"

solution is:

> fgrep or grep -F

> fgrep "d\$"

 it exactly looks for d$ in names !

<br>

## Sed

 subsitute all a with b in friends.txt
 
> sed "s/a/b/" friends.txt
> 
  -r is for understanding the REGEX
  
> sed -r "s/^a/b/" friends.txt

it means subsitute all names start with a --> subsitute a with b

**Tip**: we also can use sed to find something not only subsitute

for instance:
> sed -rn "/a/p" frieds.txt

**-rn switch**: **r** means **regex** and **n** means i dont want to show the final answer to me after doing something.

"/a/p" --> exactly means find all **a** and **p** means **print them**.

or we can use something like this:

> sed -rn ".{5}/p" friends.txt

it means find all five characters names and print them

but still this method find names with 6 characters or more

if we want fix that we have to use:

> sed -rn "^/.{5}$/p" friends.txt

<br>

## VIM

**i** ->  used for insert mode.

**esc** ->  use for back to command mode.

#### in command mode we can use so many keys to do some special stuffs.

**x** -> delete a character we stands on it !

**G** -> go to the end of file.

**G10** -> go to the tenth line !

**L** ->  use to jump to line but from bottom to top.

**4L** -> go to the fourth line from the end !

**2H** -> jump to second line from top.

<br>

#### how to edit text in command mode ?

**a** -> used for append --> go to insert mode in the end of that line.

**r** -> used for replace a character --> in command mode use r and then G --> G will replace instead each character that was there

**u** -> used for undo

**o** -> will open a new line and go to insert mode (bottom line).

**O** -> will open a new line and go to insert mode (above line).

**c** -> used for replace a sentence or whatever.

if we use **cw** it means replace a word and overwrites (w means word).

**d** -> delete --> **dw** means delete a word.

**d3w** -> delete 3 words.

**dd** -> delete a line.

**8dd** -> delete 8 lines.

**p** -> paste.

for example if we use dd in a line and delete all that line

and then go to another line and use p, it'll paste the deleted line there

**P** ->  is for paste to above line

**xp** -> if we had a typographical mistake for example --> we wrote ot (to).

if we use (xp) it will delete first character and then paste it again so. ot will change to (to).

<br>

#### how to seach in VIM --->

**/** -> search forward.

**?** -> search backward.

**n** -> repeat previous search

<br> 

#### Exiting

use esc to enter command mode

then use :

> q!

 ( Quit editing without save )

> :w!

(write the file (whether modified or not)) it means we can save file and still stand in it.

** Tip**: we also can save a file without change the original one with:

> :w <name.txt> --> :w cute.txt

To reload file from disk when u fuck the real file :)):

> :e!

using shell command:
> :! ls

<br>

## Partitions

> fdisk -l /dev/sda

l switch stands for list (will print data about our hard disks).

**Tip**: fdisk is a dangerous command.

> fdisk /dev/sda

will open danger zone :))

we can format partition remove them or add them, change the format of them and etc.

if we want to delete a partition:

> sudo fdisk /dev/sda

**m** -> use for help.

**d** -> remove the partition.

**n** -> create a new partition.

for format a partition we have to use:

> sudo mkfs -t ext4 -L Movies /dev/sda1

(Make File System 't' stands for TYPE --> ext4 --> L switch stands for Label

but for format a partition for SWAP we have to use:

> sudo mkswap /dev/sda1

**Tip**: we can check all formates in our linux:

> ls /sbin/mk*

### What is UUID:
Universal Unique ID --> it's a id that always same and not changeable.

check UUID of Hardware like Hard Disk:

> blkid /dev/sda1

for GPT system NOT MBR ---> we can use gdisk instead of fdisk

> gdisk /dev/sda

<br>

## du & df

### Disk Free
df will show us "Disk Free" space:

> df -h (-H)

h means human and H is also mean human too but -H is better because it calculate as 1024 not 1000.

> df -TH

Disk Free Space TYPE and Human Readable.

> df -ih

 i means inode,  "Inodes keep some infromation about Files".

**Tip**: vfat format doesn't have any inodes (like efi boot system) it manes vfat doesn't know when file edited or when it opens who is the owner and etc.

### DISK USAGE

> du -H . /tmp

 it will check the disk usage both the directory we stand and the /tmp directory.

important switches for "du" command:

-c -h -H --max-depth=1 -s  -c means caclucalte the total disk usage.

> du myProject/instabot -H -c

 will show us the total and also one by one files that used our disk.

> du -H -C --max-depth=1

 this command won't show us all nested direcotories one by one instead of that it'll show just parent directory and usage of all childrens of that directory.

> du -hs 

will give us a summary human readable summary.

for example :

> du -hs myProject

 (500MB)

if we wanna find big files that used most of our usage -> we have to use sth like this bellow:

> du -h --max-depth=2 | grep G M

 ( GB or MB Use one of them )

**Tip**: what is **journal file system** --> it's something like a journal letter.

if the system break or light off in a sudden the system will break ! right ? but the journal will remember what we had done before.

for example if we modified an important file system and suddenly lights off, actually we have to face some problems, the journal in files will fix this problem and it remember what should computer to and what did the system done and that's not complete yet !

**CONCLUSSION** --> A journal differs from a simple {log}.

in that the contents of the journal can be used to reconstruct the state of the system after a failure by re-applying the transactions in the journal to a snapshot of the system previous state.

**Hint**: ext2 and fat are not journalling but ext3 ext4 are journalling.

<br>

## Mount

> sudo mount /dev/sda1 /media/mosihere/

it will mount hard sda1 in media/mosihere, it means if we have 2 linux in our hard drive the second linux mount in our main and in used linux --> (We Mount A Partition in a Directory).

if we want to unmount this again:

> umount /media/mosihere/

or

> sudoumount /dev/sda1

**Tip**: it's better to mount stuffs in a empty directory, because when we mount things in a directory till we unmount that we can't see our real files and stuffs in directory.

famous switches for mount command are:
 1. -t ext4 (stands for type)
 2. -o ro ( o stands for options and ro means with READ ONLY option mount this **rw** means read and write.

> sudo mount -o remount,ro /dev/sda1 /media/mosihere/

it means mount with option and remount again if it already mounted and start it in read only mode.

**Tip**: we can't unmount a hardware or whatever when we stand in that directory. 

**solution**:

we have to leave that directory then use --> sudo umount /dev/sda1

**hint**:  mount command will show all mounted stuffs in our systems:

> mount

<br>

## Swap

with command:

> sudo swapon -a

start our swap partition, also we can turn it off with:

> sudo swapoff -a

**Tip**: we can check our memory usage and much more things with (top) command:

> top

> swapon -s

 will show us the partition of our swap, for example:
 
 dev/sda5 type = partition / size = 8GB / used = 0 / priority= -1

<br>

## Manage File-Permission and Ownerships

when we create a file if we use:

> ls -l

 we can see the owner of file.

group of user and another persons in system.

something like this:
> -wr-wr-r--

1. first wr means write and read for User (Me)
2. second is for group (for example Mosihere Group )
3. third one is for all another persons that not in any group

ok ! now we want to create a shell.sh:

> vim hello.sh

#!/bin/bash
it'll be run with bin bash

> echo 'hello'

now if we run it:

>sh hello.sh

now we wanna make it execute to run it we have to use:

> chmod u+x hello.sh

it means give the permission to user to execute.

now if we again use:
> ls -l hello.sh

we'll see the output like this:

-rwxrw-r-- (it means user access the execute).

and ofcourse now we can run the hello.sh directry in terminal like this :

> ./hello.sh

**Tip**: if we want to remove the access of user to execute we have to use this command:

>chmod u-x hello.sh

 (remove the execute for user).

> chmod ug+x hello.sh

 (change mod of user and group of user to access the execute)

> chmod o-r hello.sh

(others don't have permission to read this file).

> chmod o=wr hello.sh

(it means add read and write for others)

> chmod o=r,g=r,u=wrx hello.sh

(others can read , group can read, user can read and write and execute)

in another way ( technical way ) we can use octal numbers (8):

rwx 7

rw- 6

r-x 5

r-- 4

-wx 3

-w- 2

--x 1

--- 0

chmod < number for user > < number for group > < number for others > hello.sh

> chmod 754 hello.sh
 
(it means user can write read and execute/ group can read and execute / and others can just read).

**Access mode**: sometimes we can access sth dangerous without permission like this:

> ls -l /usr/bin/passwd

 we can see -rwsr-xr-x

this **s** means SUID --> (Set User ID)

> chmod u+s hello.sh
 
 will set SUID for hello.sh.

it means anyone run this command, the command run with user root, not that guy access.

**Tip**: if you use this command:
> ls -ld /tmp

(d switch is stands for directory, not the files in that directory) you'll see sth like this:

drwxrwxrwt --> what is **t** ? ( it means Sticky Bit )

with set sticky bit we let users can't erase others directory and files.

#### in the end we have 3 access mode:


|        < access mode >        |< octal >                          |< symbolic >                         |
|----------------|-------------------------------|-----------------------------|
|SUID |            4000            |u+s            |
|GUID          | 2000            |g+s            |
|Sticky          |1000| t      |

<br>

#### How to change the Owner and Groups:

chown command will help us

> chown mosi:adm hello.sh

(it means change the owner to mosi and the group is adm)

#### important switch for chmod and chown:

-R that stands for Recursive.

> sudo chown -R mosihere:mosihere /home

(it means change the owner of home and all directories files and sub directories to mosihere and the group is mosihere too).

<br>

## Hard Link & Soft link (symbolic)

> ls -i

(will list our inodes)

> ls -il

(will list items and inodes of them)

when we copy a file with new name --> the inodes of them are different

but if we exactly want to link 2 files and inodes of them are same too, we have to use **LN** command --> for example we want to copy file.txt to file2.txt --> inodes are different you can check with:

> ls -li

**solution**:

> ln myfile.txt hardlink.txt
 
 now ls -li will show both inodes same.

**CONCLUSION**: copy will create a new file with the same stuffs.

but link will refered to a same file at all --> 2 name will refer to same place --> copy is little different 2 files refer 2 to place with same content.

**for instance**: we have 3 files:

first our original file 
second is copy of the original
and third is link of original

original.txt / 2-copy.txt / 3.hardlink.txt

first we use:
> cp original.txt copy.txt

then:

> ln original.txt hardlink.txt

now if we write something instead of previous content of original file and cat the link.txt --> the hardlink.txt will update soon, but copy.txt still contain previous content.

> unlink hardlink.txt

will remove hardlink.txt.

### Soft Link:
we have to use -s Switch ( -s Stands for Soft Link )

we can easily create a softLink like this bellow:

> ln -s original.txt softLink.txt

if we use:
> ls -il

we'll see a softLink.txt use a arrow to refer to original.txt and here is the point, the inodes are different.

now the Question is, why when we have hardlink, use softlink again ?

**answer**: we can't create hard link between 2 device or 2 partition and etc.. because the inodes from one device is different from another.

in this situation we have to use softlink that create a new file with unique inodes and also can share between 2 partition or 2 devices.

**Hint**: if we want to create a softlink in an inner directory, we have to use "Relative Path" --> it means full path look example bellow:

> ln -s original.txt myDir/

it will create a soft link file with in broken type --> it means it has error --> solution is:

> ln -s ../original.txt .
 
it means create a softLink from outer directory with original.txt name and create it here where I'm stand.

#### but what if we wanna make a link to a 'Directory':

we can't use hard link at all.

so we can use sth like this -->we have a directory named myDir and etc...

> ln -s myDir LinkedDir

it will create a LinkedDir and all data in myDir are also exist in LinkedDir.

**Trick**:  we can find all files in system like this:

> find / -type l 

find all files are softlink from root.

<br> 

## Find system files and place files in correct location

**FHS** ( File Hierarchy Standard ) --> selsele maratebie standard.

**bin** --> Essential Command Binaries.

**boot** --> Static files of the boot loader.

**dev** --> Device Files.

**etc** --> Host-Specific system configuration.

**lib** --> Essential shared libraries and kernel modules.

**media** --> Mount point for removable Media.

**mnt** --> Mount point for mounting a filesystem temporarily.

**opt** --> Add-on application software packages.

**sbin** --> Essential system binaries.

**srv** --> Data for services provide by this system.

**tmp** --> Temporary Files.

**usr** --> Secondary Hierarchy.

**var** --> variable Data.

**home** --> User Home Directory (Optional).

**lib** --> Alternate Format essential shared libraries (Optional).

**root** --> Home Directory for the root user ' / ' (Optional).

<br>

## Tricks

> which ls

 will tell us how the command run.

> which -a ping

stands for all path.

> type root

 it's better than which.

> whereis ping

> locate kernel 

is too fast.

#### why too fast:
it has a trick because **locate** work with a **offline DataBase** and it'll create a data base and find from there !
for updating that data base we have to use 'sudo updatedb' manually or
it will make backup once a day.

## Contribution
Try to help fixing any **misspelling**, **bad grammar** or  **unmentioned tips** for this section! <br>
**Pull requests are welcome :)**

------

License
----
[MIT](https://choosealicense.com/licenses/mit/)
