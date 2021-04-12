#

- The `git clean` command allows for the removal of untracked or unmerged file from the working directory.

- The `-d` flag allows git to recursively clean the working directory when no path is specified, while the `-f` flag allows git to forcefully delete files. So, passing `-d` and `-f` flags allows git to recursively go through the files and forcefully delete them at the same time.

- The command `git checkout -b BRANCH-NAME` creates a new branch

- A fast forward merge occurs when git knows the order in which the commits happened and arranges them chronologically. A recursive merge occurs when different commits happen at different times on two branches and can't determine the order. A recursive merge is used when fast forward isn't enough.

- The command `git checkout NAME_OF_BRANCH` is used to switch to another branch.

- Use the git `checkout` command

- The command `git branch -D NAME_OF_BRANCH` is used to delete a branch. But ensure that are not on the branch

- The `git diff` is used to compare changes between two commits

- The command `git rm --cached NAME_OF_FILE` is used to remove files from the staging area

- Merge conflicts occur when there are changes to the same file on two different branches. This causes git not to know which file to merge as there are different contents in the file with same name.
