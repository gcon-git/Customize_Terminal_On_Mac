# How to Customize Your Terminal Shell Prompt on a Mac

***

## What these steps will do:
* Change what is used for the shell prompt
* Change colors of shell prompt
* Save new Settings/changes your `.bash_profile` file
* Give a prompt that is more easily read

## Why I chose this project
* Gain more familiarity with using the Linux command line
* Customize my terminal shell prompt for easier reading
* Capture steps in a concise manner for later referencing 

## Assumptions

* Users know where to find the terminal on their computer.
* Users have some basic familiarity with using the command line. 

***

## Example scenario

Your command prompt currently looks like the following:

        mycomputer:currentworkdirectory user$

Instead, you'd like to change it to look like the following


        mycomputer::user in currentworkdirectory -->> 

where 
+ `user` is red 
+ `::` is green
+ `mycomputer` is blue
+ `currentworkdirectory` is orange
+ `-->>` is yellow

The following steps will utilize this example scenario as the basis to show one how he/she can customize their terminal prompt.

## Steps

(in your text editor) ================================================

* Using a text editor of your choice, open a blank text file. Keep this window open to the side.

(in your terminal) ================================================

* Open the terminal 

* Make sure that you are in your home directory. 

        cd ~

* Check your current PS1 setting. This will be your default setting. 

        echo $PS1

* Copy your default PS1 setting.

(in your text editor) ================================================

* Paste your default PS1 setting into the blank text file & add your new settings, which could look like the following:
        
        # default PS1 setting for terminal shell prompt
        # PS1=\h:\W \u$


        # New terminal shell prompt
        red=$(tput setaf 9)
        green=$(tput setaf 46)
        blue=$(tput setaf 21)
        orange=$(tput setaf 208)
        yellow=$(tput setaf 226)
        startover=$(tput sgr0)

        PS1="\[${blue}\]\h"          # hostname 
        PS1+="\[${green}\]::"        # :: divider
        PS1+="\[${red}\]\u"          # username
        PS1+="\[${startover}\]  "    # reset to default font color
        PS1+="\[${orange}\]\W"       # current working directory
        PS1+="\[${startover}\] "     # reset to default font color
        PS1+="\[${yellow}\]-->>"     # -->> new prompt symbol
        PS1+="\[${startover}\] "     # reset to default font color

        export PS1

* Copy the all of the lines above that you have on your text file

(in your terminal) ================================================

* Open your `.bash_profile` (in terminal). 

        nano .bash_profile

* Using the arrow keys, move the cursor down to the bottom of the `.bash_profile` file

* Paste the lines that you copied from your text file into your `.bash_profile`

* Save the changes you just made

        Hit [CTRL+X] to exit the nano editor
        Hit [Shift+Y] to save the new changes
        Hit [return] to keep the .bash_profile file name

* Make your changes take effect

        source .bash_profile

Congrats!! Your new customized terminal shell prompt will be effective in all of your future terminal shell sessions, and likely other software platforms that enable you to use a terminal. For software that I use, the new terminal shell prompt customizations are present in terminal sessions in my VS Code text editor and my RStudio IDE.

(in your text editor) ================================================

* At this point, you can keep or discard the text file that you created earlier.

* If you choose to keep it you should save it under a different file name. I do NOT recommend saving it as `.bash_profile` since that could cause complications with your computer.

***

## Explanations / Notes

* If you want to see what different colors look like on your terminal before using them you can type the following in your terminal shell prompt without needing to alter your `.bash_profile`

        echo $(tput setaf ##) name_of_color $(tput sgr0)

    where `##` is the number of the color you want to check and `name_of_color` is a descriptive name to help you recall the color you're checking

* The numbers representing the chosen colors above were obtained from a 256-color chart (see reference #1 of the README.md file of this repository)

* There are other customizations that you can do with your terminal shell prompt. I encourage you to check out the references listed in the README.md file and explore other possibilities.

* Table of explanations 

| What | Remarks | Reference for More Info |
| --- | --- | --- |
| `PS1` | stands for *prompt string 1* | Ch. 13, Ref #4
| `+=` | allows you to append a variable assignment | Ref #3 
| `$()` | references a variable | Sec 3.1, Ref #2 
| `tput` | queries the terminfo database | See `man tput` page in terminal 
| `setaf` | used to set foreground (text) color | Sec 6.5, Ref #2
| `sgr0` | turns off set attributes / resets to your defaults | Sec 6.5, Ref #2 
| `\[` | start of series of non-printing characters | Table 13-1, Ref #4 
| `\]` | end of series of non-printing characters | Table 13-1, Ref #4
| `{}` | braces used to enclose variable names for readability | 
| `\h` | host name of local machine without trailing domain name | Table 13-1, Ref #4
| `\u` | user name of current user | Table 13-1, Ref #4
| `\W` | last part of current working directory name | Table 13-1, Ref #4
| `#` | comment character | Ch. 11, Ref #4 
| `export`| export environment to subsequently executed programs | Ch. 11, Ref #4