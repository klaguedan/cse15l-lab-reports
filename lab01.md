# Lab Report 1 - FileSystem

Oct. 9, 2023

---

In this blog post, I will demonstrate 3 commonly used terminal commands: `cd`, `ls`, and `cat` through 3 different argument types.

First we will examine (1) using the command without arguments, (2) using the command with a path to a directory/folder as its argument, and (3) using the command with a path to a file as its argument.

---


### 👉 `cd` changes the directory or moves us to another folder.

1. **<ins>No Argument</ins>**

   In this example, we can see that it's possible to run `cd` without arguments. However, since I provided it no argument—no other directory to change to—it didn't do anything noticeable.

   The terminal gave no error message (and no output at all, actually!) and this may be because `cd` does not really have anything to output, it just performs a simple action on the user.  Lines 2-3 confirm that our working directory did not change.


   
   ```
   WORKING DIRECTORY: /home
   
   1   [user@sahara ~]$ cd
   2   [user@sahara ~]$ pwd
   3   /home
   ```


1. **<ins>Directory Path Argument</ins>**

   Here, I show a more useful application of the `cd` command. From `/home`, I navigate to the `lecture1` directory that is inside.

   Like with the previous case, `cd` did not output anything either and it does not need to for its purposes. In Line 2, I use `pwd` to confirm that the working directory had moved to `/home/lecture1`. Another place that reflects this change is the shell prompt itself. Specifically, in Line 1 the prompt only says `[user@sahara ~]$` but in Line 2 it says `[user@sahara ~/lecture1]$`. So, this is another way to see that the `cd` command was successful.

   ```
   WORKING DIRECTORY: /home
   
   1   [user@sahara ~]$ cd lecture1/
   2   [user@sahara ~/lecture1]$ pwd
   3   /home/lecture1
   ```


4. **<ins>File Path Argument</ins>**

   In Line 1, I execute the `cd` command with a path to a file as the argument, but I encounter an error in Line 2 that says `Hello.java` is not a directory. It makes sense that the command didn't work since `Hello.java` is a file. By definition, `cd` only works with directories.

   We can see that in Line 4, our working directory was not affected.

   ```
   WORKING DIRECTORY: /home/lecture1
   
   1   [user@sahara ~/lecture1]$ cd Hello.java
   2   bash: cd: Hello.java: Not a directory
   3   [user@sahara ~/lecture1]$ pwd
   4   /home/lecture1
   ```




### 👉 `ls` lists all the directories and files within the working directory.

1. **<ins>No Argument</ins>**

   While in `/home/lecture1/messages/`, `ls` with no arguments is successful. In Line 2, the command outputs a whole list of the files within the working directory.

   ```
   WORKING DIRECTORY: /home/lecture1/messages
   
   1   [user@sahara ~/lecture1/messages]$ ls
   2   el.txt  en-us.txt  es-mx.txt  zh-cn.txt
   ```


2. **<ins>Directory Path Argument</ins>**


   ```
   WORKING DIRECTORY: /home/lecture1/messages
   
   1   [user@sahara ~/lecture1/messages]$ ls lecture1/
   2   ls: cannot access 'lecture1/': No such file or
       directory
   3   [user@sahara ~/lecture1/messages]$ ls ..
   4   Hello.class  messages
   5   Hello.java   README
   ```


3. **<ins>File Path Argument</ins>**
   ```
   WORKING DIRECTORY: /home/lecture1/messages
   
   1   [user@sahara ~/lecture1/messages]$ ls README
   2   ls: cannot access 'README': No such file 
       or directory
   ```

### 👉 `cat` outputs the contents of a file into the terminal.

1. **<ins>No Argument</ins>**

   ```
   WORKING DIRECTORY: /home
   
   1   [user@sahara ~]$ cat
   2
   3
   4   hi
   5   hi
   6
   7   
   8   what
   9   what
   ```


2. **<ins>Directory Path Argument</ins>**


   ```
   WORKING DIRECTORY: /home
   
   1   [user@sahara ~]$ cat /home/lecture1
   2   cat: /home/lecture1: Is a directory
   ```


3. **<ins>File Path Argument</ins>**


   ```
   WORKING DIRECTORY: /home
   
   1   [user@sahara ~]$ cat /home/lecture1/messages/es-mx.txt
   2   ¡Hola Mundo!
   ```
