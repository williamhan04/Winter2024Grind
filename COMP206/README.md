# Introduction to Software Systems
## 1-2. Unix/Linex Operating System
### System
- A set of interconnect components (artifacts)
    - Each component performs a specific function
    - Components can interact with one another (send/receive data, execute a fct)
        - They interact with each other according to a set of rules (protocols: HTTP, ssh)
        - They can be subsystems
#### Software Systems
- Involves interactions between software programs
- These softwares work as a team to solve a problem
#### Systems Programming
- Software is often divided in two main types:
    - Application software: services to user
    - Systems software: services to other softwares
- System programming is concerned with systems software, it involves;
    - Directly interacting with either the operating system or the machine
    - May not be easily portable
    - Little runtime overhead and works in low resources environments
    - Manual memory management
#### Command-line development
- Often required
    - Remote systems development
    - OS job-language(scripts to control the OS)
    - Diagnosing OS and peripheral issues
    - Not everything has a graphic user interface (GUI) (e.g. scientific equipment)
- Often prefered by developpers
    - Efficiency (tab completion, pipelining, no deep menus, etc.)
    - Easier to automate (scripts)
    - Easier to share commands than step-by-step instructions
    - Single environment for multiple tasks
    - Flexibility
    - Shell history
    - Customizable
### What is an operating system?
- Piece of software that allows us to interact with a computer without knowing it's inner working
- Manages the computer resources
- Provides us with libraries to interact with these resources
- It manages things for us and helps us control the computer
## 3. The Shell
### What it is
Program that has 3 basic tasks
- get user input
- display OS information
- store session information
### Directory
- Linux directory the same as GUI folder
    - An OS structure that contains files (can be named)
- 4 special directories
    - Home: top folder in  user's directory tree (~)
    - Root: top folder of the OS (/)
    - Current: current folder (.)
    - Parent: folder above (..)
### Path
String that describes the location of a file or directory within an OS
- Absolute path
    - String that begins at the root
    - /dir/dir/file
- Relative path
    - String that begins at current location
    - dir/dir/file or ../dir/dir/file
#### Directory Content
- ls: see content of directory
- ls -l: see content in long format
- ls -l letter.doc: see particular file in long format
- ls -a: display all files,, including hidden
#### Current directory
- pwd: print working directory; displays current directory
- cd: allows user to change directories
#### Directory Manipulation
- cd [directory]: change directory
- ls [options] [directory or file list]: directory content or file permissions
- mkdir [options] directory: make a directory
- pwd: print current working directory
- rmdir [options][directory]: remove directory
#### File Manipulation
- cp [options] file1 file2: copy file1 into file2; creates or overwrites file2
- mv [options] file1 file2: move file1 in file2
- rm [options] file: deletes a file or directory
#### Options for cp, mv and rm
- -i: interactive (cp, mv and rm)
    - prompt and wait for confirmation before proceeding
- -r or -R: recursive (cp and rm)
    - recursively visits a directory, first visiting the files and subdirectories beneath it
- -f: force (mv and rm)
    - don't prompt for confirmation (overrides -i)
#### More file manipulation
- cat [options] files
    - file concatenate and display the concatenated result
- less [options] file
    - page through a text file
- logout
- exit
- man: access manual pages of various commands on the shell (man ls)
- history
- Ctrl + C: force stop program 
- Ctrl + D: force tell program to stop waiting for an input
## 4. Regular Expressions and Wild Cards
### Wild Cards
Symbols used to replace one or more characters in a filename. In Bash:
- *.doc: any pattern
- ?at.doc: any single character
- cat.d[aoz]c: any character within the bracket
    - cat.d[a-d]c = cat.d[abcd]c
    - cat.d[!a]c 
### Filename Expansion (globbing)
- Note that if a filename is hidden, it must be matched explicitly
- Globbing is applied on each segments of a pathname separatly
    - Docs/myfile.txt = */*.txt != *.txt
- Wild cards are interpreted by shell. If they can't be matched, shell won't do anything with them and wild cards will be sent to command literally
    - In a dir with no .doc, echo ls *.doc will echo back ls *.doc and ls will think that you're trying to open a file called *.doc
### Regular Expressions
Other than wild cards, regular expressions allow you to search on more advanced text patterns
#### Popular commands using regular expressions
- grep [options] STRING FILE_LIST: search for occurences of the string
- sed [options] FILE_LIST: stream editor for editing files
- awk [options] FILE_LIST: scan for patterns in a file and process the results
#### Grep
- grep is used to search for the patterns in files
- the regular expression to match is what is called STRING above. Usually, surround string with single quotes. This way, the shell won't expand any wildcard or variables
    - -i: ignore case
    - -c: report only a count of lines containing matches
    - -v: invert the search, displaying only lines that don't match
    - -n: display line number along with the line on which a match was found
    - -l: list filenames, but not lines, in which matches were found
#### When to Use Grep
- Useful tool to find specific things:
    - Outlining all the errors in a log file
    - Finding a specific string in a collection of source files
- Powerful when combined with other utilities
### Redirection
The ability to send the output from one program to the input of another program
#### File Descriptors
- Created by OS when a file is opened. It is a reference to that file
- Unix has 3 special file descriptors which are always opened, representing three streams:
    - STDIN: 0 Standart in, channel where keys typed by the user are gathered
    - STDOUT: 1 Standart out, channel where normal application output is sent
    - STDERR: 2 Standart error, channel where error output is sent
- Normal output and error output is separated on two different channels since they are often monitored in different ways
#### Redirection
- Normal output goes to the screen
    - AKA: STDOUT
- Output sent to the screen can be redirected
    - symbol: > redirect output to a file (ls -la>list.txt)
    - symbol: >> redirect output, append to existing file (ls -la>>list.txt)
    - symbol: | output from one program sent as input to another program (this is known as piping) (cat test.txt sample.txt | more)
- input from file can be redirected (as is from keyboard)
    - symbol: < contents of a file sent as input into the program (myprogram<input.txt>output.txt)
#### Examples
- ls -la | more : will present a paginate list of files
- ls -la | head : will present only the first 10 lines
- ls -la | tail : last 10 lines
- cat $(ls *.log | tail -n5) >> text.out : concatenate the last 5 log files in the current directory and write them to text.out file
#### Redirection with TEE
Redirection can be in two forms:
- Pipe : cat filename | sort > sortedFilename 
- Tee : send the output to 2 programs : who | tee list | wc -l
## 5. Vim and Developer Techniques
### Text File/Source Code Editors
#### Editors 
Command line text editors allow you to create /edit files at the command line. Several text editors are available:
- vi or vim: one of the original text editors available on Unix. Difficult to learn but very strong and available on every Unix machine
- pico: simple text editor based on pine mail client. Easy to use and available on most Unix machine
- nano: similir to pico but better
- emacs: popular and powerful but heavyweight application
#### Emacs or Vi
- both command line editors 
- both very common in Unix environments
- vi is preinstalled on most Linux distributions
- vi is lightweight program (needs less system ressources)
- emacs heavyweight 
- both have devoted followers
- vi is supported on more remote connections
- emacs hasd more features, although vim and additional plugins for vim have practically reduced that gap
### Vi Editor
#### Vi's Modes
- since no menu system, it uses modes (keyboard switch)
- insert mode:
    - to edit your text
    - can press any keyboard characters
    - most vi's let you use arrow keys
- Escape mode/ normal mode:
    - terminates edit
    - can use arrow keys 
    - can use special one letter commands
- Command mode:
    - issue commands like Save, Load, Quit, Search, etc.
#### Important Commands
- to get into insert mode:
    - i, I, a, A, o, O
        - i: insert text before the cursor
        - I: insert at start of line before first non-blank
        - a: append text after the cursor
        - A: append text at end of line
        - o: begin a new line below cursor and insert text
        - O: same but above cursor
- normal mode:
    - to delete:
        - dd: delete a line
        - D: delete rest of line
        - x: delete a character
        - r: replace a character
    - to search:
        - /: forward
        - ?: backwards
        - once press enter, n/N for next/prev result
    - to copy(yank) and paste a line: 
        - yy or Y: yank
        - p: paste before cursor
        - P: paste after cursor
- command mode: 
    - :w - save file
    - :q - quit current window
    - :wq - save and quit
    - :q! - quit and discard changes
    - :number - go to a specific line number
    - :e filename - edit a file
### Development Techniques
- Important to manage system ressources properly
    - E.g.: file management, directories, disk space, nomenclature
    - Find a good way and stick with it
- Definition of good:  
    - Low system requirements, limit ressources impact
    - Useful qualities in goodness:
        - Fast processes
        - Keep things simple
#### Developer's Directory Structure
- Archive: history backups of all stable versions
- Backup: temporary copy of current version
- Doc: reading materials related to the project
- Assets: images, sounds, videos
- Database: all data saved/read by the program
- Source: current source code of the project
#### Common Usage Procedures 
- At log in:
    - Write scripts to help you get where you want to go
    - Write scripts to customize the environment
- During development:
    - Write scripts that help you to:
        - compile quickly and manage errors and executing the program
        - copying to and from master project
        - making your own local backup
- During logout:
    - Write scripts that do housekeeping:
        - Automating backup procedures
        - Automating the logging of events
        - Automating the deletion of files (empty trash)
### Common Developer Commands
#### Terminology
- File : single document in disk storage
- TAR : collection of files stored within a single document
- ZIP : single compressed document in disk storage. It contains the same information as in file but takes up less disk storage
- Archive (homework.gz) : a collection of ZIP files stored  within a single document
#### Archiving Programs
- TAR, GZIP, GUNZIP
- An archive is a collection fo files combined into one file
    - being one file, archives are easier to manipulate (move, store, copy, backup, etc.)
    - archives are often compressed, so they require less space
- The two most common archives tools used on Unix systems is tar and gzip (gunzip)
    - tar allows you to combine several files into a single file
    - gzip allows you to compress a single file
    - to compress a collection of files, you need to use both tar and gzip
- Other archive tools are available
    - zip, bzip2, 7z,...
#### Tar
- Allows the manipulation (creation, extraction) of archive files
    - a file ending with .tar extension is a tar archive file
    - a file ending with .tgz extension is a compressed (gzipped) tar archive file
- Switches:
    - -c : creates new tar archive
    - -r : update the tar archive
    - -x : extract from the tar archive
    - -f : specifies the archive file name
    - -v : activates verbose mode, which means the tar command will output lots of information
    - -z : allows you to compress the archive (the archive is compressed/decompressed using gzip)
- Examples: 
    - Create archive with log files
        - tar -cvf log.tar *.log
        - tar -zcvf log.tgz *.log
    - Extract those two archives
        - tar -xvf log.tar /tmp/log
        - tar -zxvf log.tgz /tmp/log
#### DIFF
- Comparison of two files
    - find out if two source files are the same or what was changed in the source file
- diff [options] file1 file2
#### ln: Hard and Symbolic Links
- LN and LN -S
- the ln command can be used to create links to files and folders
    - hard link: ln /path/file link_name
    - soft link: ln -s /path/file link_name
- When creating a hard link, you are simply giving another name to a file (it shows up separately on an ls- a direct pointer in directory)
    - the link will point to the same physical space on the disk
    - a file can only be deleted once all its hard link are deleted
- When creating a symbolic link (using ln -s), a new file is created (an indirect pointer in directory)
    - the new file automatically redirects to the target file
    - symbolic links can be created across volumes (or disks)
    - deleting a symbolic link does not affect the target file
#### More commands
- sort [options] file
    - sort the lines of the file
- wc [options] [file(s)]
    - display a counter of words(or character or line)
### Security
#### Permissions on the File Systems
- all files are owned by a user and a group
    - usually, this owner is the user that created the file
- permissions on files exist at three levels: user, group and others
- three type of rights can be given: read, write and execute
- any combination of these rights must be given to these three levels
- displayed as a string of 10 characters
    - 1 : indicates if the file is a directory
    - 2, 3, 4: read write execute for owner
    - 5, 6, 7: read write execute for group owner
    - 8, 9 ,10: read write execute for all other users
#### Do Permissions Overlap?
- Given the permission "-------rwx" of a file I own, can I read the file?
    - no, people in the group neither but others will
#### CHMOD -change mode
- chmod command is used to change permissions
    - Who:
        - u: the user who owns the file (this means me)
        - g: the group the file belongs to
        - o: the other users
        - a: all of the above
    - Permission:
     - r: permission to read the file
     - w: permission to write or delete the file
     - x: permission to execute the file, or in case of a directory, search it
- Changes to:
    - = : become
    - +: add
    - -: remove
- Examples:
    - chmod g+r file.txt
    - chmod u=r, g=x file4.* file2.txt
#### Binary Settings
- Bit setting:
    - 1 is on 0 is off
    - 111 000 111 = 707 in base 10 version of bits
    - chmod 707 *.doc rwx for owner and others but not group
## 6. Introduction to Bash Scripting
### vim
Turning syntax highlighting on/off
- :syn on
- :sym off
- :colorscheme<sp><tab>
    - type colorscheme, leave a space, then tab through the options
### Scripts are Used Here
- At log in:
    - Write scripts to help you get where you want to go
    - Write scripts to customize the environment
- During development and testing:
    - Write scripts that help you to:
        - compile quickly and manage errors and executing the program
        - copying to and from master project
        - making your own local 
        - help run testing(repeated tasks, good candidate for automation)
- At logout:
    - Write scripts that do housekeeping:
        - Automating backup procedures
        - Automating the logging of events
        - Automating the deletion of files (empty trash)
#### Two Types of Scripts
- System scripts
    - Used to modify the OS environment
    - Boot/Shutdown scripts
        - Maintained by super user(root/admin)
    - Login/Logout scripts
        - Created by account owner for account
- User scripts
    - Created by users to automate and standardize command-line activities
#### Scripts
- A collection of commands
- Command types:
    - Internal command built into the shell (the shell implements action)
    - External commands are programs stored on disks
- Scripts are interpreted
- Scripts run in a similar way to any programming language
- Since scripts are text files, the OS must be told that it is a program. It must be CHMOD'd to execute
### Bash
- BASH is a Unix scripting language that implements some programming language control flows, like:
    - functions
    - if
    - for
    - while
- It is interpreted by the Shell not compiled
- Communicates with the OS, not the CPU
#### Compiled vs Interpreted
- Compiled:
    - C source file -> Compiler -> Object file - 1:1 mapping between object statement and CPU instruction > CPU
- Interpreted:
    - Bash script -> Shell - Each line parsed before execution and can change environment > OS -> CPU
#### The sha-bang
- scripts will automatically run in the default shell
- if you want a specific shell, then:
    - use the sha-bang #!
        - the first line of the script should start with #! THE-NAME-OF-SHELL-OR-INTERPRETER-WITH-PATH
        - indicates the OS that the script is to be executed using an interpreter, e.g., sh, bash perl, python, ruby etc.
- to use the Bourne shell on mimi the first line must be:
    - #!/bin/sh
- to use the Bash shell on mimi the first line must be:
    - #!/bin/bash
#### The Alias and PS1 options
- the alias command
    - you can give an alternate name to commands
    - syntax: alias NEWNAME=OLDEXPRESSION
    - example: alias dir='ls -l -a'
- the PS1 Shell Variable
    - you redefine the prompt
    - different shell versions: PS1, PS2, prompt
    - syntax: export PS1=STRING
## 7. Bash Expressions
### Variables
There are four kinds of variables in a shell script
- environment variables: used to customize the operating system and the shell(export)
- user-created: these are script variables (simply declare the variable: x=5) no space around =
- positional parameters: command line parameters (using $1, $2, etc)
- session variables: defined by the OS or Shell when the user logs in
#### Positional Parameters
- Passing parameters from the command-line prompt to the script
    - Eg(no arguments): ./script
    - Eg(with arguments): ./script 5 2 Bob
- From within the script, you can access the 5,2,Bob using $position notation   
    - X=$1 :puts 5 into variable X
    - Y=$2 :puts 2 into Y
    - Z=$3 :puts Bob into Z
#### Positional Variables
- System parameters:
    - $# : number of arguments on the command line
    - $- : options supplied to the shell
    - $? : exit value of the last command executed
    - \$\$ : process number of the current process
    - $! : process number of the last command done in background
- Command-line parameters:
    - $n : where n is from 1 through 9, reading left to right
        - \${10} , \${11} …
    - $0 : the name of the current shell or program
    - $* : all arguments on the command line "$1 $2 ... $9" as a string
    - $@ : all arguments on the command line ("$1", "$2", . . ., "$9") as an array
#### User-Created Variables
Declaring in Scripts is type free:
- x=10
- x="bob"
- **SENSITIVE TO WHITE SPACES NO SPACE**
#### Quotes
- ' single-quote: as is, literal string
- " double-quote: pre-process first
- ` backtick: capture outpput
- $(cmd) insert quote: like backtick
- ${var}b concat quote: concat b to output
- $ escape: this is not a string
#### Bash Variables and Expressions
- Bash is untyped
    - this means that variables can be assigned to anything
    - don't need to be declared
- Bash variables and strings look similar
    - therefore the need of $ operator
        - X="Bob"
        - Y=Bob
        - X=$Bob
- Bash expressions can have type information
    - declare OPTION(s) VARIABLE=value
        - declare -i Bob=5
#### Capturing Complex Output
- $ date
- $ set $(date)
    - the output will be stored in $1="Sun", $2="Aug", etc.
    - note that using set will erase any data you might already have in the positional parameters
#### Expressions with expr and bc
- Command-line tools
    - integer tool (expr, with +,-,*,/,=,!=,%,>,<, etc.)
        - expr 5 + 2
        - expr 5 = 5
        - expr $x = $y
    - basic calculator---bc
        - use bc to evaluate arithmetic expressions using C programming language syntax
        - echo $[3/4]
            - at command prompt would return 0 because bash only uses integers when answering
            - use bc:
                - echo "scale=2; 3/4" | bc
#### Expressions
- Bash language syntax
    - on the command-line (or a shell) 
        - echo 1 + 1 will not work
        - echo $((1+1))
        - Bash: echo$[1+1]
        - echo $["$x"+"$y"]
        - Bash: echo $[$x+$y]
    - $(command) is the same as `command`
    - $((expression))
        - will evaluate the expression instead of a command
    - ${} expression tool
        - animal="cat"
        - echo $animals -> No such variable as cat
        - echo ${animal}s -> cats
#### Operators
-  The ones you are used to
    - = != + - * / %
- New ones
    - =~ for regular expressions [[\$ANSWER =~ ^y(es)$]]
    - \*,? basic pattern matching [[$ANSWER = y*]]
#### Double Quote
- Preprocess interpretation
    - X='Hello $LOGNAME'
    - Y="Hello $LOGNAME"
    - echo $X
        - outputs: Hello $LOGNAME
    - echo $Y
        - outputs: Hello whan19
    - Escape characters:
        - \n new line
        - \t tab
        - \b back space
        - \a alert
        - \\ display a backslash
#### Writing to STDOUT
The echo command writes to STDOUT
- echo "text with default  carriage return"
- echo -e "text with backslash preprocessing"
- echo -n "text without default carriage return"
#### Reading from STDIN
- The read command allows you to read a string from STDIN
- That string is then storedin the specified variable
## 8. Bash Control Structures
### Control Structures
Any element of a program that diverts code execution from the standart top-down left-right execution pattern
- if statements
- loops
- functions
- recursions
- threads
- etc.
### Conditionals
#### The Test Command
- The test command is used to evaluate a condition
- The test command can evaluate a condition at the file, string or integer level
    - if [[ EXPRESSION ]]
#### File Tests
Example: if [[ -r .cshrc ]]  **Space before and after [[ ]]
- -r file: true if it exists and is readable
- -w file: true if it exists and is writable
- -x file: true if it exists and is executable
- -f file: true if it exists and is a regular file
- -d name: true if it exists and is a directory
- -h or -L file: true if it exists &  a symbolic link 
- and many more... 
#### String Tests
Ex: if [[ -z $x ]]
- -z string: true if string length is 0
- -n string: true if string length is not 0
- string1 = string 2: true if same string
- string1 != string 2: true if not same
- string: true if string is not NULL
#### Integer Tests
- n1 -eq n2: true if integers n1 and n2 are equal
- n1 -ne n2: true if not equal
- n1 -gt n2: true if n1>n2
- n1 -ge n2: true if n1 $\ge$ n2
- n1 -lt n2: true if n1<n2
- n1 -le n2: true if n1 $\le$ n2
### Control Structures
#### if Statement
- Bash if-statement behaves similar to Java
```bash
if _condition_
then
    _code_
elif _condition_
then
    _code_
else 
    _code_
fi
```
#### The Case Statement
A case statement is similar to a Java switch statement
```bash
case condition in
    condition1) action 1;;
    condition2) action 2;;
    condition3 | condition4) action 3;;
    *) else_action;;
esac
```
#### The for Loop
- The for loop is similar to Java iterator
- It allows ou to iterate over a list of strings
```bash
for var in list
do
    actions
done 
```
#### The while Statement
- Very similar to Java
```bash
while condition
do 
    actions
    [continue]
    [break]
done
```
#### Using parameters
- The following script will pad a file with zeros
```bash
#!/bin/bash

i=$(wc -c < $1);
while [[ $i -lt $2 ]]
do 
    echo -n "0" >> $1;
    i=$(wc -c < $1);
done
```
#### Functions
- Bash functions are limited
    - Passing parameters is possible through positional variables
    - 'return' keyword can only return an exit code
    - To return a value:
        - we can use global variable (yuck), or
        - we can have the function write to stdout and redirect with command substitution $(...) to capture the output (yum)
    - Scope rules are very different
        - bash is so-called "dynamically scoped":
            - a function can access the local variables of any parent calling function
#### Scope rules
A variable is identified in the following order based on where it was used and where it was created:
- 1st block: defined within a control structure
- 2nd local: defined within a function
- 3rd global: defined at the top of the script
#### Returning values
- You cannot return values from a function
- When a bash function ends its return value is its status: 0 for success, non-zero for failure
- Options for returning values:
    - set a global variable with the result
    - use command substitution
    - call-by-reference
```bash
// Use a global variable
myresult=""
function myfunc()
{
    myresult='some value'
}
myfunc
echo $myresult
// use command substitution
function myfunc()
{
    local myresult='some value'
    echo "$myresult"
}
result=$(myfunc)
echo $result //echo in the fct does not print to the screen: example of redirection
// use eval (call-by-reference)
function myfunc(){
    local __result=$1  //double underscore so unlikely the caller uses same variable name when calling fct
    local myresult='some value'
    eval $__result="$myresult"
}

myfunc result
echo $result
```
#### Exit Status
- Function and Scripts terminate with an Exit Status
    - This is analogous to the exit status returned by a command
    - The exit status may be explicitly specified by a return statement or the exit statement, otherwise it is the exit status of the last command in the function or the script(0 if success non-zero error code if not)
    - This exit status may be queried in the script by referencing it as $?
    - This mecanism effectively permits script functions to have a "return value" similar to Java function return integer values, except the range is limited from 0 to 225
#### Note about exit
- The exit command is used to terminate a script therefore it is used, normally in two ways:
    - as the last instruction in your script returning the error status of your script to the command-line
        - 0 for all is well, positive int number for error
        - as the developer you determine what meaning is given to each positive integer error status value
    - anywhere within your script as part of an if statement. The if statement checks to see if something bad has happened requiring the termination of the script
## 9. Bash Developer Techniques
### Bash as an Aid to Developers
- to make their life easier
- to control their workflow
- to standardize good practices when workingin team or alone

It is common for developers to setup the "run-time environment"(OS/Command-line/Language/Tools/IDE) by defining these kind of processes
### Techniques
- Shell memory to control script processing
- Backup and Archive scripts
- Development environment setup
- Debugging shell scripts
#### Shell memory to control script processing (configuration)
- Many programs and scripts require a configuration file (a config file) before execution. The config file provides default parameters, like the location of a database
- Programs and scripts can also be configured through the shell's memory, this is more dynamic, and allows rapid configuration changes
#### Shell memory to control script processing 
- Methods of passing data to a script
    - Positional parameters via the command-line
    - Bash read command to prompt user for input
    - Pre-initialization within the shell memory
    - Example:
    ```
    Bash-prompt $ export x=10
    Bash-prompt $ ./script
    ```
    Within the script
    ```bash
    #!/bin/bash
    if [[ $x -eq 10 ]]
    etc.
    ```
- Pre-initialization within the shell memory
    - Special directory path declaration
        - Libraries, OS tools, executable programs, etc.
    - Working directory declaration
    - Data directory declaration
    - Variables that retain their value across multiple executing programs and scripts
#### Shell memory to control script processing (already defined for you)
- PATH used by OS, CLASSPATH used by Java
- PATH and CLASSPATH contain paths to folders:
    - PATH is used by the shell to determine where to find the program when you type ./script or ./program
    - CLASSPATH is used by Java to find the Java program (at the command-line type echo $PATH to print it out)

Shell variables permit developers to define parameters without requiring editing of the source code

For example: 
- WORKINGDIR - the program's working directory
    - no matter what folder you are in it will default to that working directory
    - e.g.:
        - Bash-prompt $ export WORKINGDIR="/home/jack/project1"
        - Script: cd $WORKINGDIR
- DATAPATH - the path to important data
    - the user can change this information from the command-line without needing to open up the script to reprogram
    - e.g.: 
        - Bash-prompt $ export DATAPATH="/home/mary/project1/pictures"
        - Script: files=$DATAPATH/dog.jpg
#### Controlling Workflow Backup and Archive Scripts
- It is common that developers want to make backups on a regular basis but get tired of inputting all commands each time
    - A main backup script:
        - In the HOME directory
        - A simple script listing all the files to backup with an optional destination
        - Or: a script that calls all the other backup scripts (using source)
    - A project specific backup script:
        - Like the main backup script but
        - Stored in project's top directory
        - Responsible for the project
```bash
//main backup script
#/!/bin/bash
echo "Calling all the backup scripts"
source ./project1/backup.sh
source ./project2/backup.sh
source ./project3/backup.sh
echo "Backups completed"
exit 0

//Project backup script
#!/bin/bash
#default destination for backup
destination="../backup"
#check for environment variable
if [[ -n "$BACKUPPATH" ]]; then
    destination=$BACKUPPATH
fi
#check for command-line argument
if [[ -n "$1" ]]: then
    destination=$1
fi
#the files to backup
cp file1 $destination
cp file2 $destination
```
#### Development environment setup scripts
A collection of scripts for a project or user environment
- Good practices:
    - Standardizing your technique
    - Automathing best practices
- Developers will often create a script to initiate the environment they want to work under
    - or the team leader will create a script that defines the standart working environment for the team members
    - this would include
        - the project directory structure
        - backup procedures
        - start and end project procedures
        - compiling procedures
        - repository procedures
- Six common scripts
    - NewProject -setup the OS environment for the project
    - Backup - setup the way backups will happen
    - EnterProject - the beginning of your workday
    - ExitProject - the end of your workday
    - Compile 
    - Repository
#### Enter Project Script
Things you may want to standardize at the beginning of your workday on a project:
- Make sure you have the latest version of the source code from your team members
     - GIT commands
- Define Shell variables (if needed)
    - export workingdir="/home/jack/testing"
- Setup Shell environment (like: alias and prompt)
    - alias ll='ls -l'
    - export PS1="I am the greatest>"
- Some of these tasks can be setup in an "environment script" to run it together
- Check to see special instructions 
    - cat /project/message.txt
#### Exiting a Project
Things you want to standardize at the end of your workday
- Make sure to backup everything
    - backup.sh
- Make sure to update the repository
    - GIT
#### Basic debugging for Bash scripts
```bash
#!/bin/bash
clear
who
echo " done executing who"
pinky bob
```
echo commands throughout your script is useful in debugging, especially during development. You can comment them out once everything is working
## 10. Advanced Unix Utilities
### find
- search for files and directories
- can be combined with other utilities to execute commands on the files or directories located by find
#### Examples
- find [options...] STARTINGDIR -name SEARCHFOR
    - STARTINGDIR is relative or absolute path of directory to start the search from
    - SEARCHFOR can be an actual dir/file name or a pattern
- find /home/sheila/comp206 -name '*tips.txt'
- find /home/sheila/comp206 -type d
    - type f: regular files
    - type d: directories
    - this find recursively lists all directories
- find /home/sheila/comp206 -perm 664
    - 664: list those files that match this permission exactly
    - -664: list files that have at least all of those permissions
    - /664: list files that have at least one of these permissions
- find /home/sheila/comp206 -name 'lecture*.txt' -newer notes.txt
    - newer COMPARETOFILE: only matches those files that were modified mroe recently than COMPARETOFILE
    - searches for lecture notes which was modified more recently compared to notes.txt
- mtime N:
    - N: matches files that were modified N*24 hours ago
    - +N: matches files that were modified more than N*24 hours ago
    - -N
#### find -execute actions
```bash
$ find./ -name '*e.txt'
./one.txt
./three.txt
./five.txt
```
\$find./ -name '*e.txt' -exec ls -l '{}' \;
- ls: command to execute
- -l: option to execute
- quotes and escape character important so that shell doesn't eat the brackets or semicolon
- ls is executed 3 times
```bash
-rw------- 1 jdsilv2 root 0 Jul 27 19:00 ./one.txt
-rw------- 1 jdsilv2 root 0 Jul 27 19:00 ./three.txt
-rw------- 1 jdsilv2 root 0 Jul 27 19:00 ./five.txt
```
```bash
//ls is executed one time
$ find ./ -name '*e.txt' -exec ls -l '{}' +
-rw------- 1 jdsilv2 root 0 Jul 27 19:00 ./one.txt
-rw------- 1 jdsilv2 root 0 Jul 27 19:00 ./three.txt
-rw------- 1 jdsilv2 root 0 Jul 27 19:00 ./five.txt
```
#### find -other capabilities
- Search by size
- Ignore the case of the filename while searching
- Search by owner, group
- Combine multiple search conditions (AND OR logic)
- Execute multiple actions
- and more...
### sed
- stream editor, works on a line-by-line basis
- very sophisticated, have several optionsfor complex editing on-the-fly
    - We will focus only a handful of most commonly used options
#### sed -common usage syntax
```bash
sed SCRIPT INPUTFILE
sed -e SCRIPT -e SCRIPT2 ... INPUTFILE
sed -n ...
```
for rest of sed, awk, sort. look lecture notes, bonus questions
### Process Control
- Terminology
    - Program: an executable file on disk
    - Process: a running executable program
    - An executable program in Linux means chmod +x
- What does process control mean
    - Determining when and in what order a program executes
- Executing commands on the command-line
    - semi-colon (;)
        - in-order execution of the commands
    - ampersand (&)
        - parallel execution of the commands
            - all executables compete for the CPU
            - in multi-core then more than one executable can run at the same time
            - if there are more executables than CPU they wait in a queue and revert to in-order execution but with a queue insert competition
- Processor status (TTY vs PTS)
    - this command tells you which programs are executing
    - ps
    - ps -a
- Terminating a process (SIGTERM)
    - Using an executable's PID, you can influence them
        - kill pid
        - kill -9 pid
### Scheduling -at and crontab
Scheduling is an important part of automation in real-world systems
- at -> execute a command (possibly a user written program/script) at a specific time (onetime action)
- crontab -> used to execute commands/programs/scripts on a recurring schedule
#### at crontab
look notes