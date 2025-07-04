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
myRepoDir/$ '<code>it push</code>
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





