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

## Git to collaborate
Sharing code is easy enough, but what if you want to collaborate with others?
You have a file "code1" on your computer. You push this to GitHub to make available to others. Your friend downloads the file, makes changes to the file and also use Git to keep versions of the file. When they are done they push the file back to GitHub with the Git history of updates they made.
Now we can grab the update file your friend modified and see the changes that were made.

But what happens if both you and your friend are modifying the same file at the same time?
Git is very good and creating a file as the result of two versions of a file. Details are provided later in the course.

## Open source
Open source software is publically available and you are free to use it and change it. Open source is a group effort writing code, testing for bugs, etc. 

In the previous lesson we only had two people sharing a file. But what happens with many?
The concept of "branches" are introduce to help manage this scenario.
A branch is a copy of code at a given time. Any changes you make does NOT affect the original code, the branch is truly a copy of the project/file. So you create a branch then download it to your local computer.
When we are ready to create a snapshot of the code you push it back to the provider, such as GitHub. But it is pushed to the branch rather than the original.
When the changes in the branch are accepted they can be merged with the orginal and therefore the production code is not tainted while continuing to make changes/updates/bug fixes.

The act of merging the branch with the orginal is done through what is called a "pull request". The changes in the branch are reviewed by others before before merging or adding them with the origin. After the content is added/merged the branch can be removed.
On you local machine, when you change back to the main branch you will see the results of any changes accepted into the main branch.

Branches allow multiple people to make copies, download them, modify/create content then push them back onto the branch and waiting for evaluation before accepting them into the main branch.

