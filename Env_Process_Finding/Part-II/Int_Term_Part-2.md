# Intermediate Terminal Exercises

## Part II

1. To find all files in the Desktop folder with the name of `"learn"`, type `find ~/Desktop -name "learn"`.
2. To find all files in the Desktop folder that start with a `"P"`, type `find ~/Desktop -name "P.*`.
3. To find all files in the Desktop folder that end with `.txt`, type `find ~/Desktop -name "*.txt"`.
4. To find all files in the Desktop/views folder that have  the name `data` somewher in their filename, type `find ~/Desktop/views -name "*data*"`.
5. In the imaginary `instructors.txt` file, to output the number of times the word "Elie" appears, type `grep -c "Elie" instructors.txt`.
6. In the imaginary `instructors.txt` file, to list all matches for any full word that starts with a capital "P", type `grep -w "P.*" instructors.txt`.
7. In the imaginary `instructors.txt` file, to list all the line numbers for any full word that starts with a "z", type `grep -ni "z.*" instructors.txt`.
