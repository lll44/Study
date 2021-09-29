## **10  
ORGANIZING FILES**

![Image](https://automatetheboringstuff.com/2e/images/000060.jpg)

In the previous chapter, you learned how to create and write to new files in Python. Your programs can also organize preexisting files on the hard drive. Maybe you’ve had the experience of going through a folder full of dozens, hundreds, or even thousands of files and copying, renaming, moving, or compressing them all by hand. Or consider tasks such as these:

  * Making copies of all PDF files (and _only_ the PDF files) in every subfolder of a folder
  * Removing the leading zeros in the filenames for every file in a folder of hundreds of files named _spam001.txt_, _spam002.txt_, _spam003.txt_, and so on
  * Compressing the contents of several folders into one ZIP file (which could be a simple backup system)

All this boring stuff is just begging to be automated in Python. By programming your computer to do these tasks, you can transform it into a quick-working file clerk who never makes mistakes.

As you begin working with files, you may find it helpful to be able to quickly see what the extension (._txt_, ._pdf_, ._jpg_, and so on) of a file is. With macOS and Linux, your file browser most likely shows extensions automatically. With Windows, file extensions may be hidden by default. To show extensions, go to **Start** ▸ **Control Panel** ▸ **Appearance and Personalization** ▸ **Folder Options**. On the View tab, under Advanced Settings, uncheck the **Hide extensions for known file types** checkbox.

### **The shutil Module**

The shutil (or shell utilities) module has functions to let you copy, move, rename, and delete files in your Python programs. To use the shutil functions, you will first need to use import shutil.

#### **_Copying Files and Folders_**

The shutil module provides functions for copying files, as well as entire folders.

Calling shutil.copy(source, destination) will copy the file at the path source to the folder at the path destination. (Both source and destination can be strings or Path objects.) If destination is a filename, it will be used as the new name of the copied file. This function returns a string or Path object of the copied file.

Enter the following into the interactive shell to see how shutil.copy() works:

   >>> import shutil, os  
   >>> from pathlib import Path  
   >>> p = Path.home()  
➊ >>> shutil.copy(p / 'spam.txt', p / 'some_folder')  
   'C:\Users\Al\some_folder\spam.txt'  
➋ >>> shutil.copy(p / 'eggs.txt', p / 'some_folder/eggs2.txt')  
   WindowsPath('C:/Users/Al/some_folder/eggs2.txt')

The first shutil.copy() call copies the file at _C:\Users\Al\spam.txt_ to the folder _C:\Users\Al\some_folder_. The return value is the path of the newly copied file. Note that since a folder was specified as the destination ➊, the original _spam.txt_ filename is used for the new, copied file’s filename. The second shutil.copy() call ➋ also copies the file at _C:\Users\Al\eggs.txt_ to the folder _C:\Users\Al\some_folder_ but gives the copied file the name _eggs2.txt_.

While shutil.copy() will copy a single file, shutil.copytree() will copy an entire folder and every folder and file contained in it. Calling shutil.copytree(source, destination) will copy the folder at the path source, along with all of its files and subfolders, to the folder at the path destination. The source and destination parameters are both strings. The function returns a string of the path of the copied folder.

Enter the following into the interactive shell:

>>> import shutil, os  
>>> from pathlib import Path  
>>> p = Path.home()  
>>> shutil.copytree(p / 'spam', p / 'spam_backup')  
WindowsPath('C:/Users/Al/spam_backup')

The shutil.copytree() call creates a new folder named _spam_backup_ with the same content as the original _spam_ folder. You have now safely backed up your precious, precious spam.

#### **_Moving and Renaming Files and Folders_**

Calling shutil.move(source, destination) will move the file or folder at the path source to the path destination and will return a string of the absolute path of the new location.

If destination points to a folder, the source file gets moved into destination and keeps its current filename. For example, enter the following into the interactive shell:

>>> import shutil  
>>> shutil.move('C:\bacon.txt', 'C:\eggs')  
'C:\eggs\bacon.txt'

Assuming a folder named _eggs_ already exists in the _C:\_ directory, this shutil.move() call says, “Move _C:acon.txt_ into the folder _C:\eggs_.”

If there had been a _bacon.txt_ file already in _C:\eggs_, it would have been overwritten. Since it’s easy to accidentally overwrite files in this way, you should take some care when using move().

The destination path can also specify a filename. In the following example, the source file is moved _and_ renamed.

>>> shutil.move('C:\bacon.txt', 'C:\eggs\new_bacon.txt')  
'C:\eggs\new_bacon.txt'

This line says, “Move _C:acon.txt_ into the folder _C:\eggs_, and while you’re at it, rename that _bacon.txt_ file to _new_bacon.txt_.”

Both of the previous examples worked under the assumption that there was a folder _eggs_ in the _C:\_ directory. But if there is no _eggs_ folder, then move() will rename _bacon.txt_ to a file named _eggs_.

>>> shutil.move('C:\bacon.txt', 'C:\eggs')  
'C:\eggs'

Here, move() can’t find a folder named _eggs_ in the _C:\_ directory and so assumes that destination must be specifying a filename, not a folder. So the _bacon.txt_ text file is renamed to _eggs_ (a text file without the _.txt_ file extension)—probably not what you wanted! This can be a tough-to-spot bug in your programs since the move() call can happily do something that might be quite different from what you were expecting. This is yet another reason to be careful when using move().

Finally, the folders that make up the destination must already exist, or else Python will throw an exception. Enter the following into the interactive shell:

>>> shutil.move('spam.txt', 'c:\does_not_exist\eggs\ham')  
Traceback (most recent call last):  
  --snip--  
FileNotFoundError: [Errno 2] No such file or directory: 'c:\does_not_exist\  
eggs\ham'

Python looks for _eggs_ and _ham_ inside the directory _does_not_exist_. It doesn’t find the nonexistent directory, so it can’t move _spam.txt_ to the path you specified.

#### **_Permanently Deleting Files and Folders_**

You can delete a single file or a single empty folder with functions in the os module, whereas to delete a folder and all of its contents, you use the shutil module.

  * Calling os.unlink(path) will delete the file at path.
  * Calling os.rmdir(path) will delete the folder at path. This folder must be empty of any files or folders.
  * Calling shutil.rmtree(path) will remove the folder at path, and all files and folders it contains will also be deleted.

Be careful when using these functions in your programs! It’s often a good idea to first run your program with these calls commented out and with print() calls added to show the files that would be deleted. Here is a Python program that was intended to delete files that have the _.txt_ file extension but has a typo (highlighted in bold) that causes it to delete _.rxt_ files instead:

import os  
from pathlib import Path  
for filename in Path.home().glob('*.rxt'):  
    os.unlink(filename)

If you had any important files ending with _.rxt_, they would have been accidentally, permanently deleted. Instead, you should have first run the program like this:

import os  
from pathlib import Path  
for filename in Path.home().glob('*.rxt'):  
    #os.unlink(filename)  
    print(filename)

Now the os.unlink() call is commented, so Python ignores it. Instead, you will print the filename of the file that would have been deleted. Running this version of the program first will show you that you’ve accidentally told the program to delete _.rxt_ files instead of _.txt_ files.

Once you are certain the program works as intended, delete the print(filename) line and uncomment the os.unlink(filename) line. Then run the program again to actually delete the files.

#### **_Safe Deletes with the send2trash Module_**

Since Python’s built-in shutil.rmtree() function irreversibly deletes files and folders, it can be dangerous to use. A much better way to delete files and folders is with the third-party send2trash module. You can install this module by running pip install --user send2trash from a Terminal window. (See [Appendix A](https://automatetheboringstuff.com/2e/chapter10/#calibre_link-2) for a more in-depth explanation of how to install third-party modules.)

Using send2trash is much safer than Python’s regular delete functions, because it will send folders and files to your computer’s trash or recycle bin instead of permanently deleting them. If a bug in your program deletes something with send2trash you didn’t intend to delete, you can later restore it from the recycle bin.

After you have installed send2trash, enter the following into the interactive shell:

>>> import send2trash  
>>> baconFile = open('bacon.txt', 'a')   # creates the file  
>>> baconFile.write('Bacon is not a vegetable.')  
25  
>>> baconFile.close()  
>>> send2trash.send2trash('bacon.txt')

In general, you should always use the send2trash.send2trash() function to delete files and folders. But while sending files to the recycle bin lets you recover them later, it will not free up disk space like permanently deleting them does. If you want your program to free up disk space, use the os and shutil functions for deleting files and folders. Note that the send2trash() function can only send files to the recycle bin; it cannot pull files out of it.

### **Walking a Directory Tree**

Say you want to rename every file in some folder and also every file in every subfolder of that folder. That is, you want to walk through the directory tree, touching each file as you go. Writing a program to do this could get tricky; fortunately, Python provides a function to handle this process for you.

Let’s look at the _C:\delicious_ folder with its contents, shown in [Figure 10-1](https://automatetheboringstuff.com/2e/chapter10/#calibre_link-1195).

![image](https://automatetheboringstuff.com/2e/images/000047.jpg)

_Figure 10-1: An example folder that contains three folders and four files_

Here is an example program that uses the os.walk() function on the directory tree from [Figure 10-1](https://automatetheboringstuff.com/2e/chapter10/#calibre_link-1195):

import os  
  
for folderName, subfolders, filenames in os.walk('C:\delicious'):  
    print('The current folder is ' + folderName)  
  
    for subfolder in subfolders:  
        print('SUBFOLDER OF ' + folderName + ': ' + subfolder)  
  
    for filename in filenames:  
        print('FILE INSIDE ' + folderName + ': '+ filename)  
  
    print('')

The os.walk() function is passed a single string value: the path of a folder. You can use os.walk() in a for loop statement to walk a directory tree, much like how you can use the range() function to walk over a range of numbers. Unlike range(), the os.walk() function will return three values on each iteration through the loop:

  * A string of the current folder’s name
  * A list of strings of the folders in the current folder
  * A list of strings of the files in the current folder

(By current folder, I mean the folder for the current iteration of the for loop. The current working directory of the program is _not_ changed by os.walk().)

Just like you can choose the variable name i in the code for i in range(10):, you can also choose the variable names for the three values listed earlier. I usually use the names foldername, subfolders, and filenames.

When you run this program, it will output the following:

The current folder is C:\delicious  
SUBFOLDER OF C:\delicious: cats   
SUBFOLDER OF C:\delicious: walnut  
FILE INSIDE C:\delicious: spam.txt  
  
The current folder is C:\delicious
