This is not discussed in the course but if you made a typo in a previous commit you can update it.

1. run the `git rebase -i HEAD~n` command where "n" is represents the number of commits to go back. For example if your commit typo was 3 commits back you would use `git rebase -i HEAD~3` and this would go back 3 commits.<br>
Git will pop up and editor with lines representing your commits that start with "pick". Find the commit with the typo and change "pick" to "r". Don't change the message. Save and close the editor.

2. Another editor opens and this is where you modify your commit message to fix the typo. Save and close the editor.

3. After all commit messages are updated, you might want to run the `git push -f` command to update the remote repo.
