# Chapter 4 - Push Your Code with Git

## Set up a remote repository
A *remote repository* is a repository setup an a Git provider, such as GitHub.
There are several well known Git providers
- GitHub
- GitLab
- Bitbucket

The course examples focus on *GitHub* and *GitHub Codespace*.

If you don't have a GitHub account, create one, it's free & requires an email address to get started.

NOTE: To use VSCode for multiple repos you can always open a new VSCode window.

To create a new repository you can navigate to `https://github.com/new` or by going to your list of repositories and click the green "New" button.
To get to a list of your repositories for you GitHub account, click the account icon in the top right, then select "Your repositories".

When creating a new repository you need to fill in a few details and GitHub provides an online form to make this fairly easy.<br>
The demonstration creates a private repository with a name "git-repository", and chooses to have a README created. 

- The name of the repository<br>
  GitHub will let you know if the given name is available.
  Since this name will be part of the url, avoid spaces.<br>
  EX: git-repository
- (optional) description
- visibility<br>
  You have two choices (public/private)<br>
  Public means anyone can view it but not edit it.<br>
  Private is only visible to you.
- initialize<br>
  Adding a README file is a good practice<br>
  Other choices are optional but a MIT license is good for opensource

After picking and choosing the details of the repository click the *Create Repository* button.


## Fork the course repository
Forking a repository creates a copy of an existing repo owned by you or someone else.
Since it is a copy, the original remains unmodified.
Forking is common to make contributions to a repository that you do not own.

1. Fork the instructor's repository.
NOTE: A fork of a repository is always PUBLIC, you don't have a choice to make it private.
    1. go to the instructors repo<br>
  https://github.com/linkedInLearning/git-essential-training-5988161
    2. in the top right of this page you should see a "fork" button, click it.<br>
  This will create a copy of the repo to our own GitHub account.<br>
  You have the option to change the name of the forked repository or leave it.
  Leave the checkbox as is *Copy the main branch* and click *Create Fork*.


2. clone your forked repository to your local machine.
    1. Go to your GitHub account and go to the forked repository
    2. Click on the green *Code* button and in the dropdown, go to the *Local* tab.
       In the submenu of Local there is a tab *HTTPS* which has a url of your forked repository. Click the icon to the right of the name to copy the url.
    3. Create a folder on your computer where you will save your local repository.
    4. You can use your computer shell/terminal or GUI to download the repo.
       If you are using VSCode you can use the integrated terminal or the GUI.
       The VSCode GUI shows a *Clone Repository* button that a launches a window to insert the copied url and asks you to specify the location (the directory you created earlier). If you don't see this button go to the left sidebar and look for the icon that looks like a Y, similar to a tree branch.
       If you are using the terminal, open it and navigate to the folder you created and use the *clone* command to clone the repo. NOTE: you may be asked to login to GitHub.<br>
       `/$ cd Code`<br>
       `Code/$`<br>
       `Code/$ git clone [the copied url gets pasted here]`

       This will create a new subdirectory with the name of the downloaded repo.
       To open this in VSCode you can provide the git file to the code command `code [.\git-essential-training-5988161]`, or you can open VSCode and use the file menu to open the folder for the repo you downloaded. It asks you to trust the author then open the repo in VSCode.

   To visualize this, the forked remote repository is in your GitHub account.
   You will download this to you computer, saving the files to your local file system.
   A local repository is created, allowing you to modify the downloaded repository files directly on your computer. You modify, stage, and commit files on your computer. The remote repository is not directly modified when working in your local repository, as this requires a separate step to push changes up to your forked remote repo.


## Create a file and stage it
With the forked repo downloaded to your computer and up and running within VSCode, we will learn how to create a file and add this file to the Staging Area.

1. Create a new file named *Example.md* in the parent directory with the text "This is content". Then save the file.<br>
NOTE: The instructor provides an illustration showing created files are on our local machine. However it would help if the instructor had you go to GitHub and view your remote repo to help reaffirm this.

2. Open an integrated terminal in VSCode if it is not already open.<br> 
   NOTE: The instructor fails to show how to open a terminal in VSCode but it can be done a couple ways. You can go to the main menu and click on *Terminal* then click on *New Terminal*. The other way is to right click on a directory in the GitHub Explorer and select *Open in integrated Terminal*.

3. In the terminal type the Git *add* command followed by the file name to stage a single file.
   Alternatively you could use `git add .` to add all modified files to the staging area.<br>
   `/$ git add Example.md`

One usefull command is Git's *status* command. This is used to check on how our repository is doing. You can see it displays which branch you are on and informs you the staged *Example.md* file is awaiting a commit, and even provides a tip on how to unstage the file.<br>
<pre><code>
/$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be commited:
  (use "git restore --staged &lt;file>..." to unstage)
          new file:    Example.md

/$
</code></pre>


## Commit a file
Currently the *Example.md* file is staged but we have yet to commit it to the local repo to create a snapshot. Git's *commit* command is used to create a commit. It uses a switch to specify a message to describe the purpose of the commit.

The instructor makes the following commit:<br>
/$ `git commit -m "adds Example.md to demonstrate the git process"`<br>

The result of the command is a confirmation message displayed in the terminal.<br>
`1 file changed, 1 insertion(+)`<br>
`create mode 100644 Example.md`

You can check the status of the commit using Git's *status* command. This shows us that the file is no longer in the Staging Area and the commit was successful. It tells us that the commit is ahead by 1 of the original repo. It also provides a tip on how to push this local commit to your remote repo.<br>
<pre><code>
/$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" top publish your local commits)

nothing to commit, working tree clean
</code></pre>


## Push the file to the remote repository
The last lesson made a commit on the file *Example.md* placing a snapshot in the local repo. The local repo is now ahead of the remote repo. To send the file from the local repo to the remote repo, use Git's *push* command.

`/$ git push`

If you go to the remote repo you should now see the new *Example.md* is part of your forked repo. The commit message should also be visible.


## Pull changes from the remote repository
If a remote repository is ahead of a local repository it is possible to pull files from the remote repo to your local repo.
For this example we will go to GitHub and create a file on the forked repo to simulate a situation where a repo has one or more files that are ahead of your local repo.

1. Go to the forked repo at GitHub and click the *Add File* button then select *Create new file*. Give the file a name, such as *Example02.md* and add some text "This is some text". Then click the button *Commit changes*. A default commit message is provided so you can leave this and continue by clicking *Commit changes*.

2. Go back to your local repo and you will see that it does not have the new file that we just created. To download the new content to the local repo, use Git's *pull* command. After running this command you should see the new *Example02.md* file in your local repo.<br>
`/$ git pull`


## Initialize a repository locally and sync it
Sometimes you will have local files and want to create a new remote repository for them.

1. First let's create a new folder on your computer with a couple files in it.<br>
<pre><code>
  GitInitExample/
    File01.md
    File02.md
</code></pre>

2. Open this folder in VSCode or a terminal and generate a new local repository by using Git's *init* command.<br>
`GitInitExample/$ git init`

After you run this command you can use the terminal to list the files in the directory and you should see a new hidden *.git* file was created.
<pre><code>
  GitInitExample/
    File01.md
    File02.md
    .git
</code></pre>

3. Next, lets add both of these files to the Staging Area and then create a new commit. It is common to provide the text "initial commit" to a commit when generating a new repo and making the first commit. It is your starting point.

`GitInitExample/$ git add .`<br>
`GitInitExample/$ git commit -m "initial commit"`


With our local repository created, lets go to GitHub and create an empty remote repository.
If you remember, you can go to a url https://github.com/new to create a new repo or you can navigate to your repositories and click on the green button "New" to create a new repo.
Create a new repo as follows:
1. Click "New" to create a new repository
2. Provide a name for the repository, like "git-init-example"
3. Make the repository PRIVATE
4. Do NOT initialize it. This means you do NOT generate a README, you should select None for Add .gitignore, and select None for the license.
5. The click on Create Repository

When you create the Repo on GitHub it provides the repo url and some info on ways to use the repo. 

6. Copy the repo url
7. In your terminal you need to connect your local repo to your remote repo. To do this use the following command and paste in the url you copied from the previous step.<br>
`GitInitExample/$ git remote add origin [the copied url]`

This should link your local and remote repo. However at this point your local files have not been pushed to the remote repo.
 
8. Use Git's *push* command to push your local repository files to your remote repo. You might be surprised but doing this results in an ERROR<br>
<pre><code>
GitInitExample/$ git push
fatal: The current branch main has no upstream branch
To push the current branch and set the remote as upstream, use

  git push --set-upstream upstream origin main
</code></pre>

This is telling us we need to take additional steps to push to the remote repo.
What is happening is that our local repo has a *main* branch, but the remote repo does not have a branch yet. To fix this we follow the error message suggestion to set the upstream branch.<br>
NOTE: If you did not change the default branch name, you may see "master" instead of "main".To change this you can type `git branch -m master main` and to see the current branch you can type `git branch`<br>
`GitInitExample/$ git push --set-upstream origin main`

Then you can try Git's *push* command again and it should now work.<br>
`GitInitExample/$ git push`<br>
`Everything up-to-date`

The final step is to go to GitHub, refresh the page and you should see your local files have been pushed to your remote repo.

