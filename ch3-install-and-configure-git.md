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


## Git GUI Clients
Performing Git commands in the terminal is not for everyone so there are GUI interfaces to provide a more friendly graphical interface. Go to the [Git website](https://git-scm.com) and look for and click on *GUI Clients*.

There are many options and each GUI Client provides information about which operating systems they support, and if they are free/paid.

One option is Visual Studio code and the next lesson talks about using Git inside of VSCode.


## (Optional) Install Visual Studio Code
Visual Studio Code is a popular code editor that is supported by all major operating systems.
You can download it from the [Visual Studio Code website](https://code.visualstudio.com)

Visual Studio Code is very similar to the online editor used with Codespaces. VSCode supports Git but also have many extension that help you write code.
For windows the middle of the website provides a download button. There is also a download button in the top right to assist you in downloading and installing VSCode on other platforms.

After VSCode is installed, open it and navigate to the left column and look for extensions. It is the icon that looks like a collection of 4 squares. Click on this and type in *Git*.
There are many helpful extensions. 

Some of the more popular extensions for git are
- Git Graph
- Git History
- Git Lens

These extensions can help you track changes, see who has last modified the file, and visualize your project's history.

Using a GUI is very beginner friendly.


## Configure Git
If you are using a Codespace for this course you don't need to configure anything.
But when working locally there are some things you should know.

There are a few different .gitconfig files. The two of most importance are the local config file and the global config file.

### Global Git Config
The global Git config file applies to all the repositories on your device.
You can find the global config file in your user directory or the home directory.

<pre>
  // Windows Global Git Config file
  C:\users\user\.gitconfig

  // macOS
  name@mac ~ % ls -la
  ...
  .gitconfig
  ...
</pre>

### Local Git Config
The local Git config file refers to a specific repository.
This is stored in a file named *config* which is in a folder called *.git*.

`.git/config`

The settings in the local config file will override the settings in the global config file.
You can modify these files in the terminal, in a text editor or code editor.
Some common settings include:
- Setting your default editor
- Defining the default branch name
- Creating aliases


### Global - Set Git Config Settings
There are some settings that are required.
First lets look at the Global config file.
Your name & email address should match the one used on your Git provider (such as GitHub).
NOTE: The instructor jumps into setting configuration settings instead of explaining how to view existing values with `git config list`. You may already have name/email set.

To configure your name you can type `git config --global user.name [Your name here]`



