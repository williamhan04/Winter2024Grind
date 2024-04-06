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
    - -z : allows you to compress the archive (the archive is compressed/decompressed using )