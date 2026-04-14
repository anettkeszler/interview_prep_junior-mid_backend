# Command Line

**Graphical User Interfaces (GUIs)**: a system for interacting with electronic devices using visual elements like icons, buttons, and menus instead of text-based commands. They offer an easy way to interact with devices, but they limit the scope of human-computer interaction.
You interact with your phone and computer through a graphical user interface, which is just a layer above underlying commands that tells the device what to do.

**Command line**: its an **alternative of GUI**. It allows to perform tasks, such as creating directories, files, copying, moving files, performing advanced searches, writing scripts to automate processes, start and stop programs, etc... Usage is limitless.

**Benefits of using the command line:**
- The Command Line Interface (CLI) uses less CPU and memory than a Graphical User Interface (GUI)
- Most cloud providers provide command line access
- Many tasks can be automated through the command line

**Unix commands** are simply a layer below the normal actions. 
Each Unix command has a set of helper instructions, which give detailed information about how the commands can run and which 'flags' can be passed to that command.

```
cd ~/Desktop        - change directory to (~)Home/Desktop
cd ..               - go up one level
touch example.txt   - create a new empty file or to update a timestamp on a file
mkdir html          - make directory with the name of html
echo                - output any text that we provide
history             - to view the history of the most recently typed commands
code example.js     - it will open the file in VSCode

man                 - manual, it's a  helper command, it will display a detailed manual instructions of that given command. 

man ls              - detailed manual of instructions of list command 
ls                  - list the contents of the current working directory 
ls -l               - '-l' is a flag, it gives a detailed list of content of the current directory (gives an ordered list, shows the read and write permissions and owners)
ls -a               - list all files, even the hidden ones 
pwd                 - present working directory, shows the full path of the current directory 
cp                  - copy, copies files or folders from one destination to another 
mv                  - move files from one directory to another OR rename a file 
rm file             - remove a file
rm -r folder        - delete folder / rm is permanent, rm -rf=dangerous(force delete everything)
cat                 - print entire contents of a file, or concatenation of a file
less file.txt       - displays the contents of a file one page at a time, scrollable (much better for big files)
head file.txt       - displays the first 10 lines of the file
tail file.txt       - displays the last 10 lines of the file
tail -f logs.txt    - live logs (very useful is backend/devops)
grep                - Global regular expression, allows for searching contents of files or folders

```

## Editing files 
- **VI or VIM** 
- **VI** stands for **Visual Editor**
- **VIM** is better version of VI - **Visual Editor iMproved**
- When you open a file, you can navigate through text, search words, delete or copy lines, etc. 
```
h, j, k, l          - Move left, down, up and right
/search_term        - search for a word or phrase
:w                  - save the file
:q                  - quit the editor
:wq                 - save and quit the file
```

- Insert mode: Allows the contents of the files to be edited directly. It can be entered by pressing i (insert), a (append), or o (open new line).
- Command line mode:  It can be entered by typing colon : in Normal mode.

## Using Bash in practice

### Let's create a simple script and make it executable!
- read (r), write (w), execute (x)
```
cd ~
ls -la
vim testshell.sh

insert this: 

#!/bin/bash                   - this lets the operating system know that this is a bash script 
echo "Hello World!"
```
- press 'escape' from get out insert mode, than press ':wq', which saves and quit the file. 
```
ls -la                       -rw-r--r--   1 anettkeszler  staff     32 Nov  7 13:20 testshell.sh
```
- This file can't be run at the moment, it's not executable, it's just a read-write file. 
- To be able to run the file, you can make it executable by adding the proper permission. 
```
chmod 755 testshell.sh
ls -la
-rwxr-xr-x   1 anettkeszler  staff     32 Nov  7 13:20 testshell.sh
```
- Now I can run the file from the command line. 
```
./testshell.sh
Hello World!
```

### Rename a file and move it to another directory in one command: 
```
mv notes.txt ~/Markdown/notes.md
``` 
- Here I renamed the notes.txt files to notes.md and moved it to the Markdown folder. 

### Check the file content :
```
cat file.txt                - this returns the content of the file
```
### Count the number of words in a file: 
```
wc file.txt -w              - '-w' flag tells the wc command to return the word count
```

### Using Piepes:
- Pipes are used to pass the output of one command as input to another command. 
```
ls | wc -w                  output: 2 (there is 2 file in the directory )
cat file.txt | wc -w        output: 181 (there is 181 words in the file1.txt file)
cat file1 file2 | wc -w     output: 362 (there is 362 words in the file1 and file2. 
```

### Grep - global regular expression print 
- It's used for searching across files and folders as well as the contents of files.
```
grep "Sam" names.txt        - It searches all of the names starting with 'Sam' in names.txt file.
grep sam names.txt          - It will return a totally different list (grep is case sensitive)

grep -r "Sam" .             - search recursively
grep -i Sam names.txt       - To ignore case sensitivity we pass in a flag '-i'
grep -w Sam names.txt       - '-w' does exact match, which means it'll match exactly what I'm looking for. Output: Sam 
```
- **Grep is case sensitive**

- Using **pipe** for combine searches:
```
ls /bin | grep zip 
```
- First, I check all the executable files inside the bin directory, than I search for files containing 'zip' in their name. 

### Redirection 
- The basic workflow of any Linux command is that it takes an input and gives an output. The standard input device(stdin) is the keyboard, the standard output device(stdout) is the screen. 
- With redirection you can change the standard input and/or output. 
- There are **3 types of IO (input/output) redirection**:

#### 1.) Standard Input: 0
- **The standard input redirection gives you the option to record your input and save it to a file either by overwriting or appending the file.**
- ```>``` --> overwrite file
- ```>>```--> append to file
```
echo "hello" > file.txt
```
- Taking input usually refers to a user typing information from the keyboard. 
- We use '>' sign for user input.
- The cat command can be used to record user input and save it to a file. 
```
cat > input.txt
```
- write the input you want, press Enter, than ctr + d 
- to output the content of the file:
```
cat < input.txt         - to display the content of the file 
```

#### 2.) Standard Output: 1
- **The redirection standard output allow you to control where the output goes.**
- Output direction is handled with a greater than sign (>). 
- To send output to a text file
- Every time you run a command like ls, and press Enter, it sends the output of the file to an stdout file. In Linux, if you want to control, where the output goes, you can use a redirection. 
```
ls -l > output.txt
less output.txt           - it displays the result of ls -l command 
```

#### 3.) Standard Error: 2
- **The standard error redirect allows you to specify that the error should be written to a file.** 
- Errors occur when things go wrong. When using redirection, you also have to specify that the error should be written to a file. 
```
ls -l /bin/usr 2> error.txt
less error.txt                  --> 'ls: /bin/usr: No such file or directory' is displayed in the error file
```

- You can handle both output and error at once:
```
ls -l /bin/usr > error_output.txt 2>&1
```
**Summary**: 
```
< input.txt
> output.txt
2> error.txt
```
### Relative vs absolute path 
- **Absolute path** provides the full, complete location of a file or directory starting from the root directory (e.g., /home/user/docs/file.txt), making it valid regardless of the current working directory. (cd /Users/yourname/projects)
- **Relative path** defines a file's location in relation to the current directory (e.g., ./docs/file.txt), making it shorter but dependent on context. (cd ../projects)