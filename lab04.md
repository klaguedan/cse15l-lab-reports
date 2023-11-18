# Lab Report 4 - Vim

Nov. 19, 2022

In this lab report, I will track the keystrokes needed to SSH into ieng6, clone a repository using a SSH URL, run tests, edit code in vim, and commit and push the changes back onto Github.


At the start of this, we will assume that I already have Visual Studio Code or another similar program open on a blank workspace.

<br>

## 1️⃣ SSH into ieng6


**Keys Pressed:** `<CTRL>+<\`>`

    This keystroke will open the terminal so that we can start inputting commands.

---

**Keys Pressed:** ssh `<SPACE>` cs15fa23hl `<SHIFT>+2` ieng6 `<.>` ucsd `<.>` edu `<ENTER>`

**Final Command:** `ssh cs15fa23hl@ieng6.ucsd.edu`

    These keystrokes are used for my specific login into the UCSD ieng6 computer.

<br>

## Clone Repository

**Prep:** The Github SSH URL is copied and in the clipboard using `<CTRL>+C`.

---

**Keys Pressed:** git `<SPACE>` clone `<SPACE>` `<CTRL>+V` `<ENTER>`

**Final Command:** `git clone git@github.com:klaguedan/lab7.git`

    This command will let me clone the `lab7` repository onto my local machine. Used in combination with the Github SSH URL, I will be able to make and push changes much more quickly from the command line since I won't have to enter my password.

    I paste the SSH URL with `<CTRL>+V` here to save time.



