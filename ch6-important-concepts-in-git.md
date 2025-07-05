# Chapter 6 - Important Concepts in Git

When working with Git there are some files you probably don't want to track.
- log files
- personal configuration file

In cases like this there is a special file called ".gitignore" that you can use to tell Git not to track files, folders, or use wildcards to match a given pattern such as files ending with ".log". The ".gitignore" file is a plain text file and Git understands anything listed inside of it should be ignored.

To try this out, first create two sample log files that we will attempt to ignore with Git. These files can be put in a directory named "Second_Folder"<br>
ATTENTION: These files are NOT staged or committed.
- Second_Folder/log01.log
- Second_Folder/log02.log

Now, create a new file named ".gitignore". Inside this file we can specify what is ignored.

[.gitignore]
<pre>
node_modules
.tmp
npm-debug.log

log02.log
</pre>

Save this file and you should see that we have 2 modified files instead of three. You will also see that the file "log02.log" is grayed out in the file explorer.
- .gitignore
- log01.log

NOTE: ignoring "log02.log" will ignore the file regardless of whether it is in a folder or not.

Let's modify our ".gitignore" file to ignore the folder "Second_Folder". After saving this change, both "log01.log" and "log02.log" are ignored.

[.gitignore]
<pre>
node_modules
.tmp
npm-debug.log

log02.log

Second_Folder
</pre>

So right now any file named "log02.log" and all files in the folder "Second_Folder" are ignored by Git.

We can also use a wildcard to match multiple files. For example if we wanted to matach all files that end with ".log" that are in the "Second_Folder" folder, we could do the following.

[.gitignore]
<pre>
node_modules
.tmp
npm-debug.log

log02.log

Second_Folder/*.log
</pre>

It is important to understand .gitignore only works on files that weren't previously tracked. If you want Git to ignore a previously tracked file there are several suggestions, one of them is removing the file.


To try this out, first create two sample log files that we will attempt to ignore with Git. These files can be put in a directory named "Second_Folder"<br>
ATTENTION: These files are NOT staged or committed.
- Second_Folder/log01.log
- Second_Folder/log02.log

Now, create a new file named ".gitignore". Inside this file we can specify what is ignored.

[.gitignore]
<pre>
node_modules
.tmp
npm-debug.log

log02.log
</pre>

Save this file and you should see that we have 2 modified files instead of three. You will also see that the file "log02.log" is grayed out in the file explorer.
- .gitignore
- log01.log

NOTE: ignoring "log02.log" will ignore the file regardless of whether it is in a folder or not.

Let's modify our ".gitignore" file to ignore the folder "Second_Folder". After saving this change, both "log01.log" and "log02.log" are ignored.

[.gitignore]
<pre>
node_modules
.tmp
npm-debug.log

log02.log

Second_Folder
</pre>

So right now any file named "log02.log" and all files in the folder "Second_Folder" are ignored by Git.

We can also use a wildcard to match multiple files. For example if we wanted to matach all files that end with ".log" that are in the "Second_Folder" folder, we could do the following.

[.gitignore]
<pre>
node_modules
.tmp
npm-debug.log

log02.log

Second_Folder/*.log
</pre>

It is important to understand .gitignore only works on files that weren't previously tracked. If you want Git to ignore a previously tracked file there are several suggestions, one of them is removing the file.

## The .git folder
A git repository has a hidden ".git" folder. By default VSCode hides these files but you can make these visible. In VSCode open the Command Palette.<br>
Windows: ctrl + shift + p<br>
Mac: cmd + shift + p

With the Command Palette open, type "user settings" and select the option "Preferences: Open User Settings (JSON)". This allows you to create your own settings and one is the ability to show hidden files.
<pre>
{ 
"files.exclude": {
"**/.git": false
}
}
</pre>

If you have saved the "settings.json" in your project, you should now see the hidden ".git" folder.

Within the ".git" folder there is a file named "config" which holds details about your repository.

It is NOT suggested to change anything in the ".git" folder as it may break your repository.

If you delete the ".git" folder, you will no longer have a Git repository. Instead, you will just have a plain file system directory
