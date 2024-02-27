# Lab Report 4 - Vim (Week 7)
![Image](loginSSH.png)
<br/>Logging into ieng6: The keys I used to get to this point were `ssh<space>lam009@ieng6-202.ucsd.edu<enter>`. I typed that all into the terminal and was able to connect to the `ieng6` server with the `ssh` command using my UCSD specific login information. The `ssh` command stands for secure shell and connects two devices (in my case my computer to a server).

![Image](cloneLab7.png)
Cloned my fork of the repository from my Github account (using the SSH URL): The keys I used to get here were `git<space>clone<space>git@github.com:lavinma/lab7.git<enter>`. (The last part is the SSH URL.) I typed that into the terminal and was able to create a copy of my remote Github repository onto my computer with the  `git clone` command.

![Image](Lab7Fail.png)
Run the tests, demonstrating that they fail: The keys I used to get here were `bash<space>test.sh`. This ran the bash file that contained the commands to compile and run the `ListExamplesTests.java` file.

![Image](vimEditing.jpeg)
Edit the code file to fix the failing test: To fix the failing test I had to go into the `ListExamples.java` file and edit the code in the `merge` method. To do that I used the following keys: `vim ListExamples.java<enter>` to get into the `ListExamples` java file to edit and fix the code. Since, I knew what to change I found the part using the `/` command. Next, I typed `/change <enter>` to get my cursor onto the comment above the part in the code I wanted to change. Then I pressed `j` to move my cursor down to the line of code I want to edit. At this point, my cursor is on the 'e' in 'index1' and I need to get it to be on '1', so I can delete it and repace it with '2'. So, then I do: `l` `l` `x` `a` `<left arrow>` `2`. That sequence of commands moved my cursor to be above the '1' in 'index1' and then I deleted the '1' with the `x` command and went into insert mode with the `a` command and typed '2' in the right place. Now I just needed to save my edits and quit `vim`. I did that using the following key presses: `<Control><C>` to go from insert mode to normal and `:wq` to save my edits and exit `vim`.
<br/>Note: The image above depicts my code right before I pressed `:wq` to save and exit. 

Run the tests, demonstrating that they now succeed:

Commit and push the resulting change to my Github account:
