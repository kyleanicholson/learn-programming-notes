- Unix Shell is both a command line interface (CLI) and a scripting language
- '/' at the beginning of path refers to the root directory in Unix.
- The ~ character at the start of a path means 'the current user's home directory'.
- The - character with 'cd' is translated into 'the previous directory I was in'
- Press 'Tab' to auto complete (case must be correct)
- *  matches zero or more characters-- *.txt matches all files ending in .txt
- ?  matches exactly one character. -- ?.txt matches a.txt but not any.txt

Useful Unix commands:

$ pwd  #print working directory
$ [command name] --help  # displays info on how to use the command.
$ man [command name]  #more comprehensive list of options
$ mkdir [path] # create a new directory (use -p option to create embedded directories)
$ cd ~   # go to home directory
$ cd ..  # go back one directory
$ cd -   # go to the last directory I was in
$ touch [file name].[file extension] # create new file (e.g. touch hello.py) 
$ rm [file name]     # remove file 
$ rm -r [folder] # removes folder and all contents (use with caution)
$ mv [old] [new] # moves or renames file 
    (e.g. $ mv thesis/draft.txt thesis/quotes.txt #renames the file)
    (e.g. $ mv thesis/quotes.txt . #moves file into current working directory)
$ cp [old] [new] # copies a file instead of moving it.


Useful Tips:
-Don’t use spaces (use - or _)
-Stick w/ letters, numbers, period, dash and underscore