# Intermediate Terminal Exercises

## Part I

1. To create an environment variable called `FIRST_NAME` with value set to my first name, type `export FIRST_NAME=Wasiu`, see `Int_Term_Part-1.jpg` for the result in terminal.
2. To print the `FIRST_NAME` variable, type `echo $FIRST_NAME`, see `Int_Term_Part-1.jpg` for the result in terminal.
3. To print the `$PATH` variable, type `echo $PATH`, see `Int_Term_Part-1.jpg` for the result in terminal.
4. The `$PATH` variable is a set of paths for our environment to find programs to run. In the `Int_Term_Part-1.jpg` file, the output showed the path to where commands can be ran.
5. Creating an environment variable helps us to secure information and also allows us to use a variable more than once
6. Environment variables can be permanently saved in the `.bash_profile` or `.zshrc` but I have it as `.bashrc` in my ubuntu terminal.
7. A Process is a specific computer program that is being executed
8. Use the `ps aux` command to list all running processes.
9. A PID is a unique identifier for a process which can be used to kill/terminate the process.
10. A process can be terminated by using the `kill` or `kill -9` command.
11. Sometimes a process ignores the signal from the `kill` command and won't terminate. The `-9` flag ensures that such process doesn't ignore the signal and is terminated using its PID.
12. The `-i` flag allows for case insensitive search when using the `grep` command.
13. The `-B` flag allows for certain number of lines before the match when using the `grep` command.
14. The `-C` flag allows for certain number of lines around the match when using the `grep` command.
15. The `-A` flag allows for certain number of lines after the match when using the `grep` command.
16. The `-w` flag allows for full word search when using the `grep` command.
17. The `-n` flag shows the line number of a match when using the `grep` command.
