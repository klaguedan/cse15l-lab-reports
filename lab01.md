# Lab Report 1 - FileSystem

Oct. 9, 2023

---

In this blog post, I will demonstrate 3 different cases each for 3 commonly used terminal commands: `cd`, `ls`, and `cat`. 

First we will examine (1) using the command without arguments, (2) using the command with a path to a directory/folder as its argument, and (3) using the command with a path to a file as its argument.

---


### 👉 `cd` changes the directory or moves to another folder.

1. **<ins>No Argument</ins>** Working Directory: `/home`
   ```
   [user@sahara ~]$ cd         # There is no output
   
   [user@sahara ~]$ pwd        # Verifies that we are still in /home
      /home
   ```
   


2. **<ins>Directory Path Argument</ins>** Working Directory: `/home`
   ```
   [user@sahara ~]$ cd lecture1/         # There is also no output here
   
   [user@sahara ~/lecture1]$ pwd         # Checks which directory we are at
      /home/lecture1
   ```


3. **<ins>File Path Argument</ins>** Working Directory: `/home/lecture1`
   ```
   [user@sahara ~/lecture1]$ cd Hello.java
      bash: cd: Hello.java: Not a directory         # An error!

   [user@sahara ~/lecture1]$ pwd
      /home/lecture1                                # We can see we never changed directories
   ```




### 👉 `ls` lists all the directories and files within the working directory.

1. **<ins>No Argument</ins>** Working Directory: `/home/lecture1/messages`
   ```
   [user@sahara ~/lecture1/messages]$ ls
      el.txt  en-us.txt  es-mx.txt  zh-cn.txt         # 4 txt files shown
   ```


2. **<ins>Directory Path Argument</ins>** Working Directory: `/home/lecture1/messages`
   ```
   [user@sahara ~/lecture1/messages]$ ls lecture1/
      ls: cannot access 'lecture1/': No such file   # Error!
      or directory

   [user@sahara ~/lecture1/messages]$ ls ..         # List what's in one directory above (/home/lecture1/)
      Hello.class  messages                         # It works this time!
      Hello.java   README
   ```


3. **<ins>File Path Argument</ins>** Working Directory: `/home/lecture1/messages`
   ```
   [user@sahara ~/lecture1/messages]$ ls README
      ls: cannot access 'README': No such file 
      or directory
   ```

### 👉 `cat` outputs the contents of a file into the terminal.

1. **<ins>No Argument</ins>** Working Directory:



2. **<ins>Directory Path Argument</ins>** Working Directory: ``



3. **<ins>File Path Argument</ins>** Working Directory: ``
