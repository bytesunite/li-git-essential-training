# Chapter 1 - Why Do You Want to Use Git?
First the instruction focuses on the concepts of Git before learning how to use it later in the course.

## Git for version control
One use for Git is for version control.
Take the idea of a single code file. You make changes to this file but then think about keeping backups of this file so you if you run into problems you can safely go back to a state of the file that is working.
So a natural way to do this without Git would be to save multiple copies of the same file.
For example you would start with "code1" and save it. Then modify the file and save the modified version as "code2", and so on. This can become a mess and this is where Git can help.

So with Git you have your file system with a file, and you also have Git.
Git is software installed on your machine.
So using the same example as above, you start with a file "code1" and save a "version" in Git, which is called a "commit".
Instead of making a copy of the file on your filesystem, Git keeps track with a commit. You can keep working on your code and when you are ready to make another version, you make a new commit to Git. You can do this over and over.
So all those old versions are stored in Git and we can access the history of our file(s) as we write code.

In addition to using git on our local computer you can store versions of your code in the cloud, protecting you if your computer is lost/damaged/etc. A cloud provider that works with Git, such as GitHub, is one solution to not only storing it locally but also on the cloud.

## Git to share code
Have you ever shared code with a coworker or friend?
If you have a file "code1" and you share this with your friend you want to make sure they have access to it. Emailing code is problematic as it can be marked as spam or the email provider limits the size of the attachment. You could put it on a USB thumb drive but this is not very convenient unless your friend or coworker is close.

With a cloud provider, such as GitHub, we can make our code public so others can gain access to it by giving them the url where they can access the content. On GitHub a "repository" is a location where you can store your code and make it available to others. This provides an easy way for other to access your code as long as they have an Internet connection.

