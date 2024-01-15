# Lab Report 1 - Remote Access and FileSystem (Week 1)

## `cd` command
![Image 1-15-24 at 11 14 AM](https://github.com/lavinma/cse15l-lab-reports/assets/156377218/f217a889-99cd-4c73-8b8b-d1253ee5e86c)

The **first** command is an example of the `cd` command with no arguments. 
   When that command was run, the working directory was `home`. The working directory did not change when I ran the command because no argument was present in the command line, meaning it wasn't told what directory to change to. There was no output error.
<br/> The **second** command is an example of the `cd` commaand being used with a *directory* as an argument.
   When the command was run, the working directory was `lecturel` because the cd command changed the current directory, `home`, to the argument, `lecture1`. The output is not an error.
<br/> The **third** command is an example of the `cd` command with a path to a *file* as an argument.
   When the command was run, the working directory was still `lecture1` because the argument being a path to a file is not correct. 
   The arguments given to the `cd` command can only be directories, not files. The command outputted an error because of this. 

## `ls` command
<img width="1216" alt="Screen Shot 2024-01-15 at 1 05 53 PM" src="https://github.com/lavinma/cse15l-lab-reports/assets/156377218/7135e005-2768-4683-9917-73688099eb09">

The **first** command is an example of the `ls` command with no argument. `home` was the working directory when the command was run. The output in the system was `lecture1`, meaning that it is the folder in the given path. Because there was no argument given to the command, the path it looked in was where it already was, this case being `home`.
<br/> The **second** command is an example of the `ls` command with a *directory* as an argument. When this command was run, the working directory was still `home`, but since there is now an argument in front of the `ls` command, it is being told to look specifically into one path for the files and folders in it. So, the output was a list of the files and folders in `lecture1`. This output was not an error.
<br/> The **third** command is an example of the `ls` command with a path to a *file* as an argument. The working directory is still `home`. My output this time was odd and appears to be an error. It printed out the path given in the argument but that is not what the `ls` command is supposed to do. It is supposed to print out all the files and folders in the given path, not the path itself.
   

## `cat` command
<img width="1219" alt="Screen Shot 2024-01-15 at 1 19 20 PM" src="https://github.com/lavinma/cse15l-lab-reports/assets/156377218/4cd8af7c-8fe9-4446-9880-13a2032cab66">

The **first** command is an example of the `cat` command with no arguments. `home` was the working directory as this command ran. The output produced errors because the command was given nothing to read. So instead anything typed after the intial no argument would be returned back in the terminal. To leave this command, I had to manually do control C.
<br/> The **second** command is an example of the `cat` command with a *directory* as an argument. The working directory was still `home` when this command was run. The output produced an error because the argument given was a directory and the `cat` command reads files, so it needs to be given a specific path to a file, not one just ending at a directory.
<br/> The **third** command is an example of the `cat` command with a path to a *file* as an argument. The working directory is still `home`. The output was not an error as it printed out the contents in the `en-us.txt` file. This output was correct as the `cat` command is supposed to print out whatever is in the given file. 
