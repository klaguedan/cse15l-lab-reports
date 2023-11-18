# Lab Report 4 - Vim

Nov. 19, 2022

In this lab report, I will track the keystrokes needed to SSH into ieng6, clone a repository using a SSH URL, run tests, edit code in vim, and commit and push the changes back onto GitHub.


At the start of this, we will assume that I already have Visual Studio Code or another similar program open on a blank workspace with the terminal open.

<br>

## 1️⃣ SSH into ieng6

**Keys Pressed:** ssh `<SPACE>` cs15fa23hl `<SHIFT>+2` ieng6 `<.>` ucsd `<.>` edu `<ENTER>`

**Final Command:** `ssh cs15fa23hl@ieng6.ucsd.edu`

> These keystrokes are used for my specific login into the UCSD ieng6 computer.

<br>

## 2️⃣ Clone Repository

**Prep:** The GitHub SSH URL is copied and in the clipboard using `<CTRL>+C`.

---

**Keys Pressed:** git `<SPACE>` clone `<SPACE>` `<CTRL>+V` `<ENTER>`

**Final Command:** `git clone git@GitHub.com:klaguedan/lab7.git`

> This command will let me clone the `lab7` repository onto my local machine. Used in combination with the GitHub SSH URL, I will be able to make and push changes much more quickly from the command line since I won't have to enter my password.
> 
> I paste the SSH URL with `<CTRL>+V` here to save time.

<br>

## 3️⃣ Run Tests (and fail)

**Keys Pressed:** bash `<SPACE>` t `<TAB>` `<ENTER>`

**Final Command:** `bash test.sh`

> Runs the tests. I am able to use `<TAB>` to autocomplete the name of the script.

<br>

## 4️⃣ Edit `ListExamples.java` with vim

**Keys Pressed:** vim L `<TAB>` `<.>` `<TAB>` `<ENTER>`

**Final Command:** `vim ListExamples.java`

> Opens ListExamples.java in vim using autocomplete on the file name and extension.

---

**Keys Pressed:** `<SHIFT>+<;>` 44 `<ENTER>`

**Final Command:** `:44`

> Jumps to 44th line of editor.

---

**Keys Pressed:** 12 `<SHIFT>+<\>`

**Final Command:** `12|`

> Jumps to 12th column of current line. So now, the cursor is at (44,12) in the file, exactly where the fix needs to happen.

---

**Keys Pressed:** r2

> Replaces character at cursor with 2.

---

**Keys Pressed:** `<SHIFT>+<;>` wq `<ENTER>`

**Final Command:** `:wq`

> Save changes and quit vim.

<br>

## 5️⃣ Run Tests (and pass)

**Keys Pressed:** `<UP>` `<UP>` `<ENTER>`

**Final Command:** `bash test.sh`

> Recovers the necessary command `bash test.sh` since it is in the terminal history for two commands ago.

<br>

## 6️⃣ Commit and Push to GitHub

**Keys Pressed:** git `<SPACE>` add `<SPACE>` `<TAB>` `<ENTER>`

**Final Command:** `git add ListExamples.java`

> Adds the file to the commit. `<TAB>` will autocomplete to `ListExamples.java` since it was the only file edited.

---

**Keys Pressed:** git `<SPACE>` commit `<SPACE>` `<->`m `<SPACE>` `<SHIFT>+<'>` Fixed `<SPACE>` typo `<SHIFT>+<'>` `<ENTER>`

**Final Command:** `git commit -m "Fixed typo"`

> Finalizes the commit and the `-m` makes it so that we can add a commit message from the command line.

---

**Keys Pressed:** git `<SPACE>` push `<SPACE>` origin `<ENTER>`

**Final Command:** `git push origin`

> Pushes the changes to GitHub.



Thank you for reading!
