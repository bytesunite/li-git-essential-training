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
