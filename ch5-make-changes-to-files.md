# Making Changes to Files

## Git Status
Git's `git status` command provides information about your repositories current state.

When you first create a new file and save it, the state is known as *untracked*. Even if you make changes to this file and save it again, its first state is *untracked*.
You can try this out by creating a file "gitStatus.md", saving it and then open a terminal and type `git status`. 

1. Create a new file "gitStatusDemo.md"
2. View the status
<pre>
myRepoDir/$ <code>git status</code>
<samp>Your branch is up to date with 'origin/main'

Untracked files:
  (use "git add &lt;file>..." to include in what will be committed)
      gitStatusDemo.md

nothing added to commit but untracked files present (use "git add" to track)
</samp>
</pre>

Git confirms that "gitStatusDemo.md" is *untracted*.

Go ahead and stage this file with the `git add` command, then check the status again with the `git status` command. This adds the file to the Staging Area and tells you it is ready to be commited. It also provides instructions on how to remove it from the staging area.<br>
NOTE: If there are any other files that have not been staged or commited, they will show up as *untracked*<br>
<pre>
myRepoDir/$ <code>git add gitStatusDemo.md</code>
myRepoDir/$ <code>git status</code>
<samp>On branch main
Your branch is up to date with 'origin/main'

Changes to be committed:
  (use "git restore --staged &lt;file>..." to unstage)
      new file:  gitStatusDemo.md
</samp>
</pre>


With the file staged, lets commit the file with Git's `git commit` command and view the status with Git's `git status` command. After our commit it tells us that our working tree is clean. It also provides hints on how to push this file to a remote repository.
<pre>
myRepoDir/$ <code>git commit -m "added gitStatusDemo.md to demonstrate status"</code>
<samp>[main 23455b6] added gitStatusDemo.md to demonstrate status
1 files changed, 1 insertion(+)
create mode 100644 gitStatusDemo.md

myRepoDir/$ <code>git status</code>
On branch main
Your branch is ahead of 'orgin/main' by 1 commit.
  (use "git push" to publish your local commits)
Nothing to commit, working tree clean
</samp>
</pre>

As you can see our local repo is 1 commit ahead of the remote repo. The push the updated file to the repo use Git's `git push` command.
<pre>
myRepoDir/$ <code>git push</code>
...
myRepoDir/$ <code>git status</code>
<samp>On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
<samp>
</pre>


## Edit a File and View Changes
In the previous lesson you created a file "gitStatusDemo.md", staged it, commited it, and pushed it to a remote repository.

But Git can not only track new files added to your repo, but changes inside of the file. To track these changes is easy because it follows the same process, except you are modifying an existing file rather than creating a new one.

In a previous lesson a file named 'Example.md' was created, staged and commited. Let's modify this file and save it. After you do this run Git's `git status` command. It will tell you this previously committed file is now *modified* but not staged.
<pre>
myRepoDir/$ <code>git status</code>
<samp>On branch main
Your branch is up to date with 'origin/main'

Changes not staged for commit:
  (use "git add &lt;file>..." to update what will be committed)
  (use "git restore &lt;file>..." to discard changes in working directory)
      modified:   Example.md

no changes added to commit (use "git add" and/or "git commit -a")
<samp>
</pre>

The next step is to stage the modified file, commit it, and push it to your repo.

myRepoDir/$ `git commit -m "added an additional line of text"`

Changes can add up quickly, so how can we see changes we made to a file?
Go ahead and make another change to "Example.md", and save the file.

[Example.md] Before (shows editor line numbers, not part of the content)
<pre>
1. This is content
2.
3. This is an extra line
</pre>

[Example.md] After (shows editor line numbers, not part of the content)
<pre>
1. This is content
2.
3. This is an extra line
4.
5. And another small change
</pre>

Git's `git status` shows "Examples.md" as *modified*. We have not staged or committed it yet.

Use Git's `git diff` command to see the differences from the previous state and now.<br>
NOTE: You can specify a file name or leave it blank to compare all file changes.
<pre>
myRepoDir/$ <code>git diff Example.md</code>
<samp>diff --git a/Example.md b/Example.md
index a5580a3..68b9f67 100644
--- a/Example.md
+++ b/Example.md
@@ -1, 3 + 1, 5 @@
This is content

-This is an extra line
\ No newline at end of file
+This is an extra line
+
+And another small change
\ No newline at end of file
</samp>
</pre>

The results are pretty easy to follow. It tells us there was not a line ending at the end of the file before it was edited. Then, a blank line was added after "This is an extra line", a new line "And another small change" was added. It tells us that after the file was edited there is no new line at the end of the modified file.<br>
NOTE: There is no such directory as "a" or "b". Git uses this to denote the previous/current state of a file.

Go ahead a modify another file, "Example02.md" and save. Then run `git diff`. You will get the same result as before (changes in Example.md) except there is a colon at the end of the output, meaning there is more information. Press the spacebar and it will show you differences in "Example02.md".<br>
The `git diff` command lets you see differences in multiple files or a single file based on how you run the command.<br>
NOTE: If you see [END] and can't move on, press the q key to return to the prompt.

But what if you staged the file and want to still see changes to the file?
Use Git's `git diff --cached` command.<br>
To demonstrate this, stage the file "Example.md", show the status, then show the cached diff. You should see the same results we saw before the modified file was added to the Staging Area.
<pre>
myRepoDir/$ <code>git add .</code>
myRepoDir/$ <code>git status</code>
On branch main
Your branch is up to date with 'origin/main'.

Changes to be commited:
  (use "git restore --stages &lt;file>..." to unstage)
    modified: Example.md

myRepoDir/$ <code>git diff --cached</code>
<samp>diff --git a/Example.md b/Example.md
index a5580a3..68b9f67 100644
--- a/Example.md
+++ b/Example.md
@@ -1, 3 + 1, 5 @@
This is content

-This is an extra line
\ No newline at end of file
+This is an extra line
+
+And another small change
\ No newline at end of file
</samp>
</pre>


This additional change is acceptable so go ahead and commit & push the file "Example.md".


## Delete Files
When you delete a file in a Git repository this change is tracked. You can delete a file using a GUI or command line. Git even has a command `git rm &lt;file>`.

For example, delete the file "Example02.md", the use the command `git status` to see how Git responded to the deletion. It shows the file has been deleted.
<pre>
myRepoDir/$ <code>git status</code>
On branch main
Your branch is up to date with 'origin/main'

Changes not staged for commits:
  (use "git add/rm &lt;file>..." to update what will be committed)
  (use "git restore &lt;file>..." to discard changes in working directory)
      deleted:   Example02.md

no changes added to commit (use "git add" and/or "git commit -a")
</pre>


Like any other change, a deleted file is a tracked action and you must stage it and commit the changed.
<pre>
myRepoDir/$ <code>git add .</code>

myRepoDir/$ <code>git commit -m 'removed Example02.md'</code>
<samp>[main 80dfb12] removed Example02.md
1 file changed, 1 deletion(-)
delete mode 100644 Example02.md
</samp>
myRepoDir/$ <code>git push</code>
</pre>


If you look in your remote repository the file should no longer exist. However, there is still a commit that logs this file was removed. Later in the course it will discuss how to recover files.


## Rename Files
To see this in action, rename the file "Example.md" to "NewName.md" and then run `git status` to see the results. The response might surprise you but we'll describe what is going on.
<pre>
myRepoDir/$ <code>git status</code>
On branch main
You branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add/rm &lt;file>..." to update what will be committed)
  (use "git restore &lt;file>..." to discard changes in working directory)
      deleted:   Example.md

Untracked files:
  (use "git add &lt;file>..." to include in what will be committed)
      NewName.md

no changes added to commit (use "git add" and/or "git commit -a")
</pre>

So what is going on? Right now Git is telling us that the old file was deleted and a new file was created. That can't be right...can it? To gain a better understanding let's stage the renamed file and then view the status.
<pre>
myRepoDir/$ <code>git add .</code>

myRepoDir/$ <code>git status</code>
...
Changes to be committed:
  (use "git restore --staged &lt;file>..." to unstage)
      renamed:    Example.md -> NewName.md
</pre>

After we stage the renamed file, Git now understands the file was renamed from "Example.md" to "NewName.md".

Before moving on commit changes on the renamed file.
<pre>
myRepoDir/$ <code>git commit -m "rename Example.md to NewName.md"</code>
</pre>

Now lets change a name directly in the terminal with Git's `git mv` command. When we do this you can see our file explorer is updated with the new name. Git also also stages the renamed file automatically. 
<pre>
myRepoDir/$ <code>git mv gitStatusDemo.md newStatus.md</code>

myRepoDir/$ <code>git status</code>
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged &lt;file>..." to unstage)
      renamed:    gitStatusDemo.md -> newStatus.md
</pre>


We can now commit to renamed file that Git automatically staged for us when using `git mv` to rename the file.
<pre>
myRepoDir/$ <code>git commit -m "rename gitStatusDemo.md to newStatus.md"</code>
</pre>

So you can choose whichever method you prefer. Using Git will automatically stage the renamed file & without using Git you will have to stage the file yourself.


## Working With Folders
Just like files, Git can keep track of folders.

If you create a new folder "First_Folder" and add files to it, Git considers this "untracked files". When you move a file to a folder, running `git status` will report a file was deleted, but all you need to do is stage the moved file. This behavior was mentioned in the last lesson when we renamed a file and the status was not updated until we staged the renamed file.

To try this out first create a folder, then use `git status` to check the status. It should say there are untracked files. For example add a folder named "First_Folder" (use terminal or GUI).
<pre>
myRepoDir/$ <code>mkdir First_Folder</code>

myRepoDir/$ <code>git status</code>
</pre>

Git does not let you know a new folder was created. The empty folder "First_Folder" is clearly in our local repo but Git is not recognizing anything yet.

Next, in VSCode move an existing file "NewName.md" into the new folder "First_Folder" by dragging and dropping it. Then check the git status again.
<pre>
myRepoDir/$ <code>git status</code>
...
Changes not staged for commit:
  deleted newStatus.md

Untracked files: ...
    First_folder/
</pre>

After we added the file "newStatus.md" into the folder "First_Folder" Git tells us that the file was deleted and a new folder was created.
The folder we created earlier is magically visible by Git now, because it contains a file. Previously the empty folder was not recognized by Git. But remember from the last lesson that a renamed file was also marked as deleted until it was staged. The same is true with moving files...the moved file shows up as deleted until you stage it.

Stage the moved file "newStatus" with `git add .`, then view the status.
<pre>
myRepoDir/$ <code>git add .</code>

myRepoDir/$ <code>git status</code>
...
   renamed: NewName.md -> First_Folder/NewName.md
</pre>

Notice how Git says "renamed" instead of "moved". This is close enough, as we know the file was not deleted or renamed, but we simply moved the file into a directory.

Go ahead and commit these changes and push to the remote repo.
Then go to GitHub to confirm the new folder exists and that it contains the file we moved.
<pre>
myRepoDir/$ <code>git commit -m 'moved NewName.md to First_Folder'</code>

myRepoDir/$ <code>git push</code>
</pre>

If you want to create a directory structure with some empty folders and track them, the best solution is to create a ".gitkeep" file inside an empty folder. The file inself does not need to contain any content, it can be an empty file. Git will then recognize the folder. After adding files to the folder you can remove the .gitkeep file, as Git will continue to track a folder that contains files.

<pre>
Second_Folder/
  .gitkeep
</pre>

So what did we learn?
- Git does not track empty folders by default. A file must be added first, or an empty .gitkeep file.
- Moving a file to a folder does not delete the file. Files must be staged to see changes.


## Undo Your Changes
It is possible to remove a staged file from the Staging area. It is also possible to undo changes to one or more modified files, restoring them to the state of the last known commit. The `git restore` command is used in both of these cases, except the "--staged" switch is required to remove a file from the Staging Area.

First, lets see how you unstage a file.<br>
You can unstage a file with Git's `git restore` command.

Remove the third line from the file "NewName.md" and stage it.

[NewName.md] Before (including line numbers)<br>
<pre>
1. This is content
2.
3. This is an extra line
4.
5. And another small change
</pre>

[NewName.md] After (including line numbers)<br>
<pre>
1. This is content
2.
3. This is an extra line
</pre>

After modifying this file lets stage it
<pre>
myRepDir/$ <code>git add .</code>

myRepoDir/$ <code>git status</code>
<samp>...
  Changes to be committed:
    modified: NewName.md</samp>
</pre>

Now we realize we are not ready to stage this so let's remove it from staging.
<pre>
myRepoDir/$ <code>git restore --staged NewName.md</code>

myRepoDir/$ <code>git status</code>
<samp>  Changes: not staged for commit
    modified:  NewName.md</samp>
</pre>

Great, we removed the file from staging.<br>
But what if we also want to take this a step further. What if we want to undo the changes we made to NewName.md? Remember, we removed the third line from "NewFile.md". You can use Git's `git restore <file>` command.

WARNING: If you modified multiple files you can confirm which files are currently "modified" using the `git status` command, where the dot means "all" modifed files. To undo changes to ALL modified files use the `git restore .` command. To undo changes to only ONE file use the `git restore <file>` command.
<pre>
myRepDir/$ <code>git restore NewName.md</code>

myRepDir/$ <code>git status</code>
... working tree clean
</pre>

If all went well the results will include
1. The file looks like it did before you modified it. In the case of "NewName.md" you should see the third line you previously deleted is back (its restored).
2. The modified file is no longer displayed when using `git status` because it is no longer in a modified state. It is back to a state of your last commit.


## View Commit History
We have talked using Git to track the history of our files, what has changed and when.
But how to we see the history? Git's `git log` command shows us a commit history.<br>
Each entry includes
- unique identifier for each commit, called a "checksum"
- author's name
- date and time of the commit
- commit description

When use use `git log` and there are lots of commits you can use press the spacebar to scroll futher down the list. You can press the "q" key to exit the log.
<pre>
myRepoDir/$ <code>git log</code>
commit: 208c44a....
Author: Barbara
Date: Tue Apr 1, 12:24:34 2025 -0700

    Create Example02.md

commit: f9908c44a....
Author: Barbara
Date: Tue Apr 1, 20:24:34 2025 -0700

    adds Example.md to demonstrate the git process
...
</pre>


There are also options to filter this list. For example to see details about a specific commit you can copy the "checksum" of a commit and paste it after Git's `git show <checksum>` command.<br>
NOTE: If the commit content is long, use the spacebar to cycle through it & type "q" to exit.

This command will display
- unique commit checksum
- author
- date
- commit message
- details of the content that changed (additions, deletions)

<pre>
myRepoDir/$ <code>git show f994a4...</code>
<samp>commit: 4a4a8...
Author: Barbara
Date: Tue Apr 1, 20:24:34 2025 -0700

    adds Example.md to demonstrate the git process
diff --git a/Example.md b/Example.md
new file mode 100644
...
+ This is content
\ No newline at end of file</samp>
</pre>


Additionaly the "-p" switch can be used to list commit history with information about what changes were performed (new file, rename, deleted file, etc.). Use the `git log -p` command.

The "--oneline" switch makes the commit history log more readable. It shortens the commit checksum to 7 characters and provides a short summary.
<pre>
myRepoDir/$ <code>git log --oneline</code>
<samp>
7ac56j  (HEAD -> main, origin/main, origin/HEAD) Adds Second Folder
3hduoi  moves newName.md to First_folder
898sl8  renames gitStatusDemo.md to newStatus.md
7x7sxx  renames Example.md to NewName.md
...</samp>
</pre>

The "--grep" switch allows you to search for a commit with all or part of the commit message. Use the command `git log --grep='some string to search with'` to specify a string to search for. A list of commits with mention of the search string are displayed.
<pre>
myRepoDir/$ <code>git log --grep="Example"</code>
<samp>
commit: 747sdj9...
Author: Barbara
Date: Tue Apr 1, 21:31:45 2025 +0000

  renames Example.md to NewName.md

commit: 8skehT...
Author: Barbara
Date: Tue Apr 1, 21:45:45 2025 +0000

  Removes removes Example02.md

commit: 8skehT...
Author: Barbara
Date: Tue Apr 1, 13:45:45 2025 +0000

  Create Example02.md

...
</samp>
</pre>


This course we stuck to a single branch but Git provides `git log --branch` which provides a visual representation to help see how commits align with specific branches.

The commit history viewed in the command line is not as pretty as a GUI. When using a remote repository such as GitHub, it contains a commit history where you can scroll through the list and select a specific commit to view it in a color coded interface right in the browser. Simply go to your remote repo and in the top right above the list of files/folders there is a "Commits" button you can click on.


## Go Back in Git History
We have seen how to use Git's `git log` command to view a history of commits. Let's take this a step further and see how we can browse the code of an older version of our project.

WARNING: The instructor fails to mention you must NOTE have any modified or staged files before running the `git checkout` command.

For example, what if we wanted to see what the project looked like before the file "Example02.md" was deleted. We would log our commits to find the commit checksum before this commit.

First, we would list all commits:
<pre>
myRepoDir/$ <code>git log --oneline</code>
<samp>
g7ac56j  (HEAD -> main, origin/main, origin/HEAD) Adds Second Folder
w3hduoi  moves newName.md to First_folder
8898sl8  renames gitStatusDemo.md to newStatus.md
47x7sxx  renames Example.md to NewName.md
4cidhf0  Removes Example02.md
pOj863x  adds extra lines to demonstrate git diff
nlIL932  Adds an extra line to show how git tracks changes
msWQp48  gitStatusDemo.md to demonstrate git status
QYil2hL  Adding Challenge01.md as a challenge
...</samp>
</pre>

Then we would grab the commit checksum BEFORE the one that removes "Example02.md". In the list above, you will see the commit prior to this was "adds extra lines to demonstrate git diff". Copy the commit checksum.

With the copied checksum, use Git's `git checkout <checksum>` command and paste in the copied checksum. The description of what is happening is discussed after the example below. In short, it is a way to view the previous state of a project.<br>
ATTENTION: After running this command, pay attention to your file Explorer because files that were created or modified after this point are no longer available.

<pre>
myRepoDir/$ <code>git checkout pOj863x</code>
<samp>
Note: switching to 'pOj863x'.

You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may do so (now or later) by using -c with the switch command. Example:

  git switch -c &lt;new-branch-name>

Or undo this operation with:

  git switch -

HEAD is now p0j863x adds extra lines to demonstrate git diff
</samp>
</pre>

You are now in what is known as a "detached HEAD" state. This is often where you can go to view a previous state of a project, but not the best place to modify the project.<br>

To view the current branch of your project you can use the `git status` command.
<pre>
myRepoDir/$ <code>git status</code>
HEAD detached at pOj863x
nothing to commit, working tree clean
</pre>

Use the `git checkout main` to exit the "detached HEAD" state and return to current state of your project.
<pre>
myRepoDir/$ <code>git checkout main</code>
<samp>Previous HEAD position was p0j863x adds extra lines to demonstrate git diff
Switched to branch 'main'
Your branch is up to date with 'origin/main'
</samp>
</pre>

## Revert a Commit
There may be previous commits that you want to undo. The `git revert <commit>` command will will undo the changes made by a specific commit. You provide the commit checksum value.

For example, what if we wanted to undo the commit we made for renaming 'gitStatusDemo.md" to "newStatus.md".<br>
First, we would track down that commit id/checksum using the `git log` command, or on GitHub. If you are using the command, remember you can use the "--oneline" switch to provide a condensed list. You could also use the "--grep" switch to use a search string.<br>

<pre>
myRepoDir/$ <code>git log --oneline</code>
<samp>
7a86cab  (HEAD -> main, origin/main, origin/HEAD) Adds Second Folder
3db990c  moves newName.md to First_folder
8dcf740  renames gitStatusDemo.md to newStatus.md
47x7sxx  renames Example.md to NewName.md
4cidhf0  Removes Example02.md
pOj863x  adds extra lines to demonstrate git diff
nlIL932  Adds an extra line to show how git tracks changes
msWQp48  gitStatusDemo.md to demonstrate git status
QYil2hL  Adding Challenge01.md as a challenge
...</samp>
</pre>

Then, we would run the `git revert <commit>` command. This command opens an editor window, which allows you to modify the commit message. The default message is typically fine as it simply writes "Revert", followed by the commit message. When you close the editor, the commit is finished.<br>
NOTE: If this command opens up a Vim editor instead of one in VSCode, you can type ":qa" to quit.
<pre>
myRepoDir/$ <code>git revert 8dcf740</code>
</pre>

Now if you go look in your file explorer you should see the file is named "gitStatusDemo.md" as it was before it was changed in an earlier commit. You will also see that this command created a new "commit".

If there were any conflicts, Git will provide steps to remedy them. The next lesson will attempt to discuss potential conflicts and how to handle them.<br>
If running this command provides conflicts and you want to cancel the revert you can use the `git revert --abort` command.

To have Git try to resolve conflicts you can use the `git revert --continue` command.


## Make Use of the GUI of Visual Studio Code
Visual Studio Code provides a GUI interface for interacting with Git. First, in the left column there is an icon that looks like a Y, called "Source Control". When you make changes to a file and save it, this icon will show a number, indicating there are detected changes. If you click on this icon it will give you details on which changes were detected and even lets you add the files to the Staging area and commit them without using the terminal. It also provides a commit history.

![Visual Studio Code - Source Control interface](vscode-source-control.png)

To see a visual side-by-side comparison of changes you made, click on the Source Control icon, and click on a file you made changes to.<br>
NOTE: If you are not seeing a side-by-side editor window, make sure your VSCode window is expanded to the width of your screen. You can also collapse the Explorer column if it helps you better see both files.

The files in the Source Control column have a + sign next to the file. Click this will add the file to the Staging area. There is also a + sign above all files when you hover over the word "Changes". Clicking this will stage ALL changed files.<br>
When files are staged this interface also provides a - button that makes it easy to remove them from the Staging Area.

Once files are added to the Staging Area, VSCode will tell you they are staged. VSCode also provides a text box to enter the commit message and a green "Commit" button to commit changes.<br>
After you commit files to your local repository, VSCode also provides a button "Sync Changes", which allows you push your updates to the remote repo. The first time you do this VSCode alerts you that both (pull & push) are executed to download any new content and push your commit to the remote repo.

Additionally, there is a triple dot button ... that is to the right of "CHANGES" that provides many options which gives you more control:
- Pull
- Push
- Clone
- Checkout to...
- Fetch
- Commit
- Changes
- Pull, Push
- Branch
- Remote
- Stash
- Tags
- Show Git Output


## Challege - Make a Change and Revert
In this challenge you will make a change in your repository and then revert this change.

1. Create a new Markdown file in our repository
2. Add a line to it and commit it to the local repository
3. Add another line to the file
4. Commit this file
5. Move the file into a folder
6. Do a new commit
7. Revert the file to the previous commit,<br> 
   which uses the git history to move the file back out of the folder

It is up to you to push these commits to a remote repository or keep them locally.

Instructor Solution:
1. create a file "important_File.md", add a single line of text "This is an important file"
2. add it to the staging area with `git add .`
3. commit changes with `git commit -m "creates importantFile.md"`
4. add an extra line "This is an important update". Save the file
5. add it to the staging area with `git add .`
6. commit changes with `git commit -m "adds extra line to importantFile.md"`
7. create a new folder named "Important_Folder" and move the file "important_File.md" into it
8. stage the changes with `git add .`
9. commit changes with `git commit -m "Moved importantFile.md to Important_Folder"`
10. push all changes to the remote repo with `git push`
11. review git history with `git log --oneline`
12. copy the very last commit id and press q to get to the prompt
13. revert using the copied commit id with `git revert <commit id goes here>` and Git creates a commit message automatically. An editor is opened but you can accept the default commit message and close the editor
14. check the status with `git status` and you should see a new commit message for reverting moving the file.

If you look at your file explorer the file "important_File.md" should not be in the folder "Important_Folder" any more.
