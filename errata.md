# Errata
LinkedIn Learning - Git Essential Training by Barbara Forbes

A collection of errors, issues, and feedback while taking the course.

## Ch3-7 Configure Git
1. The instructor fails to mention `git config list` before jumping in setting the name and email settings. You may already have setup these settings. Only after showing how to modify settings is the `git config --list` discussed. Both syntaxes work but this command should come first. So should `git config -h`


## Ch4-4 Create a file and stage it
1. The instructor fails to mention setting up a workspace in VSCode before jumping in and showing how to create a new file.
2. The instructor skips over how to open a terminal in VSCode, assuming it is already open.
3. The instructor starts the lesson with an illustration showing all created files are on the local machine. However, after creating the file *Example.md* on our computer in the local repository, it would help to have students visit their forked remote repository to confirm this.

## Ch5
1. After lession 5-9 "Revert Commit", it would help to follow up with a lesson to show how to use Git's reset command to remove multiple commits that you've mistakenly made. Discuss the pros and cons of using the reset command.

## Ch5-8 Go back in Git history
1. The instructor fails to mention you cannot have modified or staged files when running Git's checkout command. The working tree must be clean.

## Ch6
1. It would help to show how to fix a typo in a previous commit title
with `git rebase -i HEAD~n` where "n" is how many commits to go back.

## Ch6-4 Create and merge a pull request
1. After merging the logfolder branch the instructor fails to show how to delete the branch.
2. The instructor should explain Git pull --rebase after merging branches on GitHub and making sure the local repo and remote repo are inline with each other. Lesson 6-6 does provide an quick overview of troubleshooting a merge conflict but it would help to explore this topic further.

## Ch6-6 Solving a merge conflict
1. This lesson does a pretty good job at demonstrating how a conflict can arise between a remote and local repository. However, it would help to provide further details in what a "rebase" means explore different options.
