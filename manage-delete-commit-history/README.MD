# Delete commits from a branch in Git

Thanks all the people in this [stackoverflow](https://stackoverflow.com/questions/1338728/delete-commits-from-a-branch-in-git) and I've done some modification from yours tutorials.

## Problem

I would like to know how to delete a commit.

By delete, I mean it is as if I didn't make that commit, and when I do a push in the future, my changes will not push to the remote branch.

I read git help, and I think the command I should use is `git reset --hard HEAD`. Is this correct?

## Solution

Assuming you are sitting on the commit or last commit, this command will be reset or delete your last commit.

      git reset --hard HEAD~1

or

      git reset --hard HEAD^

The `HEAD~1` means the commit before head.

Or you could look at the output of `git log`, find the commit `id` of the commit you want to back up or set is as check point, it means the commit before that will be reset or delete. And then do this:

To get the commit `id`.

      git log

Then set the commit check point.

      git reset --hard <sha1-commit-id>

Obviously you can also use `HEAD~n` to "go back" `n` commits from your head. Maybe from this point you can interpreted.. `--hard HEAD` also as `HEAD~0` => deleting work in progress. 

If you already pushed it to git repository such as GitHub or GitLab, you will need to do a force push to get rid of it.

      git push origin HEAD --force

**However**, if others may have pulled it, then you would be better off starting a new branch. Because when they pull, it will just merge it into their work, and you will get it pushed back up again.

If you already pushed, it may be better to use `git revert`, to create a "mirror image" commit that will undo the changes. However, both commits will be in the log.

Done! Goodluck!
