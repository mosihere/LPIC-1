# An introduction to LPIC-1

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

## Move Command

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

## Tip

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

## File Command

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

## Contribution
Try to help fixing any **misspelling**, **bad grammar** or  **unmentioned tips** for this section! <br>
**Pull requests are welcome :)**

------

License
----
[MIT](https://choosealicense.com/licenses/mit/)
