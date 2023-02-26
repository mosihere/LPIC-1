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

## Contribution
Try to help fixing any **misspelling**, **bad grammar** or  **unmentioned tips** for this section! <br>
**Pull requests are welcome :)**

------

License
----
[MIT](https://choosealicense.com/licenses/mit/)
