
[[For a complete list of commands, check bash-cmd-reference.pdf]]
- Instead of creating enormous programs that try to do many different things, Unix programmers focus on creating lots of simple tools that each do one job well, and that work well with each other. This programming model is called ‘pipes and filters’.
-Any program that reads lines of text from standard input and writes lines of text to standard output can be combined with every other program that behaves this way as well

$ wc counts lines, words, and characters in its inputs.
$ cat displays the contents of its inputs.
cut is used to remove or cut out certain sections of each line in the file.
$ sort sorts its inputs.
$ echo command prints text
$ head displays the first 10 lines of its input.
$ tail displays the last 10 lines of its input.

$ command > [file] redirects a command’s output to a file (overwriting any existing content).
$ command >> [file] appends a command’s output to a file.

$ [first] | [second] is a pipeline: the output of the first command is used as the input to the second.
-- e.g. $ sort -n lengths.txt | head -n 1

- The best way to use the shell is to use pipes to combine simple single-purpose programs (filters).

