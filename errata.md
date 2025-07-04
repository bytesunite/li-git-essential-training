# Errata
LinkedIn Learning - Git Essential Training by Barbara Forbes

A collection of errors, issues, and feedback while taking the course.

## Ch3-7 Configure Git
1. The instructor fails to mention `git config list` before jumping in setting the name and email settings. You may already have setup these settings. Only after showing how to modify settings is the `git config --list` discussed. Both syntaxes work but this command should come first. So should `git config -h`


## Ch4-4 Create a file and stage it
1. The instructor fails to mention setting up a workspace in VSCode before jumping in and showing how to create a new file.
2. The instructor skips over how to open a terminal in VSCode, assuming it is already open.
3. The instructor starts the lesson with an illustration showing all created files are on the local machine. However, after creating the file *Example.md* on our computer in the local repository, it would help to have students visit their forked remote repository to confirm this.

## Ch5-8 Go back in Git history
1. The instructor fails to mention you cannot have modified or staged files when running Git's checkout command. The working tree must be clean.
