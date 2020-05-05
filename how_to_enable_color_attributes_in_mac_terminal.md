# How To Enable Color Attributes in Mac Terminal

***

## What these steps will do

* Enable colors and symbols for distinguishing file or directory types when using `ls` command in the terminal on a Mac

## Why I chose this project

* Gain more familiarity with using command line 
* Make terminal output easier to read when using the `ls` command
* Capture steps in a concise manner for future referencing

## Assumptions

* Users have basic familiarity with using the command line.
* Users can locate and edit their `.bash_profile` file

***

## Steps

(in your terminal) ================================================

* Make sure you are in your home directory

        cd ~

* Read/review the `ls` command help page / Scroll down to the ENVIRONMENT section and review the info for LSCOLORS

        man ls

* Open `.bash_profile`

* Move the cursor down to the bottom of your `.bash_profile`

* Add the following lines to your `.bash_profile`

        # change LSCOLORS for use in terminal
        # default color/color code is "exfxcxdxbxegedabagacad"
        # see [man ls] command in terminal for more info

        export LSCOLORS=gxBxhxDxfxhxhxhxhxcxcx

        # enable color output and symbols that trail file/directory types
        alias ls="ls -GF"

* Save the changes you just made

        Hit [CTRL+X] to exit the nano editor
        Hit [Shift+Y] to save the new changes
        Hit [return] to keep the .bash_profile file name

* Make your changes take effect

        source .bash_profile

Congrats!! Now when you type the `ls` command in your terminal session your files and directories will be colorized based on their type. Also, directories and/or other special types will have a trailing symbol to help identify what they are (i.e., a directory vs. an executable file, etc.). These changes help make the `ls` output a little easier to read on-screen.

***

## Explanations / Notes

* The prinicpal reference for this project was the `ls` help page. You can easily access this page by typing `man ls` in your terminal shell.  The pertinent sections to read are the  **DESCRIPTION** and **ENVIRONMENT** sections. I came across this info while researching how to customize my terminal command prompt.

* The color code listed for `export LSCOLORS=gxBxhxDxfxhxhxhxhxcxcx` above is the code I chose to use for my own terminal since I use a black background. The *LSCOLORS* variable uses paired color encodings where the first letter signifies the color for the foreground and the second letter signifies the color for the background. There are 11 attributes and the order is disucssed further in the **Environment** section of the `man ls` page. I encourage you to experiment with different color designations to determine which combination suits your needs. 

* The above steps include the default LSCOLORS scheme for my computer. Yours may be different. I recommend checking `man ls` on your specific machine to find your default color scheme. The `man ls` page should state what your default is under **LSCOLORS** in the **ENVIRONMENT** section.

* Table of explanations

| What | Remarks | Reference |
| --- | --- | --- | 
| `export` | export environment to subsequently executed programs | Ch. 11, Ref #4 | 
| `LSCOLORS` | variable that describes what color to use for which attribute | `man ls` |
| `alias` | used to create an alias for a command | Ch. 11, Ref #4 | 
| `ls` | command to list directory contents | `man ls` |
| `-GF` | enables colorized output and trailing symbols | `man ls` |