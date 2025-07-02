# Chapter 2 - How Does Git Work
Now that you know the concepts of Git, lets discuss the technical details of Git.

## Use Git Locally
On you local computer you have a file explorer or finder that gives you access to files and folders. 
Git provide 2 additional pieces
1. Staging Area
2. Local Repository (.git)

You have a file "code1.md" saved in a local folder. You work on it and come to a point you want to take a snapshot. The first step is to add the file to the staging area.
To add a file to the stagging area you use the git `add` command followed by the file name.
Open a terminal, navigate to the location of the file, then enter the command.

<pre>
myFolder/
  code1.md
  other.md
</pre>

myFolder/$ `git add code1.md`

If you make changes to multiple files and want to add all modified files to the staging area you can use `git add .`.  The example below would add all modified files (code1.md, test.md) to the staging area.

<pre>
myFolder/
  code1.md    changed
  other.md
  test.md     changed
</pre>

myFolder/$ `git add .`

NOTE: The instructor failes to mention when you add a file to the staging area, then modify it, you will have 2 different snapshots. Git will not automatically update the staging area with updates to files. You can run git add again to update the staging area with the lastest save.

NOTE: The instructor fails to mention `git status` is a command that is helpful to determine if files are staged and which branch you are on.

Files that are changed that we choose NOT to move to the staging are labeled as "modified".
Git gives you the flexibility to stage all changes or choose specify files to put in the staging area.

One the files are staged, the next step is to add them to the local repository.
The command is `git commit`. The details of this command are covered later (git commit -m 'updated title').

So by using Git to move updated files to the Staging Area, then commiting them to the Repository we can track changes to our files on our computer without having to make multiple copies of our file(s).

## Use a Git Provider
Now lets see how to push our local code to a remote repository.
This allows us to access content from other devices or by other people.
The command `git push` is used to move our snapshot(s) from out local machine to a Git Provider, such as GitHub.
NOTE: Any files that are changed but not staged & files that are in the staging area are NOT pushed to the remote repository. Only files in the local repository that were added with `git commit` will be pushed to the remote repository.

To grab files from a remote repository to modify on our local machine, the git command, `git pull` is used. This will download the content to a local folder and to the Git local repository.


## Distributed Version Control
A centralized version control system, such as Dropbox or OneDrive, does not keep file history. The server holds an old version of the file and when you save the file locally it syncs with the server to update to the latest version. Users that share Dropbox will only have access to the latest saved version.

In a distributed version control system it works differently. It still has a server that stores files. Every user has a complete copy of the repository including all snapshots.
So when you pull files from the server you get the whole history, not just the single latest update.
