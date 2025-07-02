# Chapter 4 - Push Your Code with Git

## Set up a remote repository
A *remote repository* is a repository setup an a Git provider, such as GitHub.
There are several well known Git providers
- GitHub
- GitLab
- Bitbucket

The course examples focus on *GitHub* and *GitHub Codespace*.

If you don't have a GitHub account, create one, it's free & requires an email address to get started.

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







