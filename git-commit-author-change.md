## Last Commit Author Change

ref: https://stackoverflow.com/questions/3042437/how-can-i-change-the-commit-author-for-a-single-commit

If you just want to change the author of your last commit, you can do this:

Reset author for the current repo:

```
git config --local user.name "Alex Smith"

git config --local user.email alex@email.com

Now reset the author of your commit without edit required:

git commit --amend --reset-author --no-edit

Force push your changes without overwriting anyone else's commits:

git push --force-with-lease

Note that this will also change the author timestamp.

To do this for the last N commmits:

git rebase --onto HEAD~N --exec "git commit --amend --reset-author --no-edit" HEAD~N
```

### To fix authoring on the last six commits
First set the correct author for current Git repo

```
git config --local user.name "FirstName LastName"
git config --local user.email first.last@example.com
Then apply the fix to the last six commits

git rebase --onto HEAD~6 --exec "git commit --amend --reset-author --no-edit" HEAD~6
Finally force push to the remote Git repo

git push --force-with-lease
```
