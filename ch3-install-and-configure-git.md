# Chapter 3 - Install and Configure Git

## Use a Codespace For This Course
The instructor shows how to fork a Codespace to help mirror the environment and making it easier to follow along using the same settings the instructor has.
CodeSpaces is an online environment rather than working on your local computer.
It even provides access to an online version of VSCode in the browser.

To use CodeSpaces you are going to create a fork of the LinkedIn Learning repository.

GitHub repository [git-essential-training-5988161](https://github.com/linkedInLearning/git-essential-training-5988161)


1. Open a web browser and go to the GitHub repository above. 
2. Click on the green *Code* button and select the *Codespaces* tab.
3. Click on the green button *Create codespace on main*<br>
   This will open an editor for you within the browser window.

To view and delete a Codespace you may have to refresh the screen but you can click on the green *Code* button and go to the *Codespaces* tab and see a list of them. The three small dots to the right of the name opens a small window with the option to delete the Codespace.

## Install Git on Windows
To install Git on Windows go to the [Git website](https://git-scm.com) and download the installer. The website does a good job at automatically identifying your operating system.
The downloads link also provides options for multiple operating systems.
NOTE: If you want to use Visual Studio Code as your editor, make sure this is installed before installing Git because during the installation process it lets you pick VSCode.

Once the Git installer is downloaded to your downloads folder you can double click it to start the install process.
The install asks you for a location to install Git but the default is fine.
Then it asks you about desktop icon and others but the defaults are fine.
Then it asks for a start menu folder, the default is fine.
Then it asks for an editor, this is where you can select VisualStudioCode which is friendlier than the default choice of vim (you must have VisualStudioCode installed first).
Next it asks what you would like to name the initial branch of new repositories. This option was added because the word "master" is considered racially insensitive. So it is suggested to choose main.
Next the commandline default is fine
Next SSH can be left with the default.
For line endings you can leave the default
From this point forward you can accept the defaults and then install.


To test that the installation was successful you can open the Windows Command Line and type "git" and it should display a list of usage commands.

To see the version of git you can type `git --version` at the command prompt.


## Install Git on Linux
First, many Linux distributions come with Git. Open a terminal and type `git --version` to check if Git is already installed. If not continue with the instructions below.
If you go the the Git website and notice your version is outdated you can type `sudo apt-get install git` in your terminal.
Just like Windows, go to the [Git website](https://git-scm.com)
Then click on downloads and instructions are provided to install Git for the different Linux distrubutions. For example Ubuntu uses `sudo apt-get install git`.


## Install Git on macOS
Git may already be installed on your mac. Open a terminal and type `git --version`.
If it is not installed you can go to the [Git website](https://git-scm.com) to find instructions. There are a couple options and the more popular choice is using Homebrew with `brew install git`. However you must have Homebrew installed first. This is also how you update git if it is outdated.
