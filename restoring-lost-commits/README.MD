# Restoring Lost Commits

Note: Please be carefull with this step

Thanks for Nick Quaranto for [this](http://gitready.com/advanced/2009/01/17/restoring-lost-commits.html) great tutorial and I've done some modification from yours tutorials.

## Problem

So, you just did a git `reset --hard HEAD^` and threw out your last commit. Well, it turns out you really did need those changes. You'll never be able to implement that algorithm that perfectly twice, so you need it back. Don't fear, git should still have your commit. When you do a reset, the commit you threw out goes to a "dangling" state. It's still in git's datastore, waiting for the next garbage collection to clean it up. So unless you've ran a `git gc` since you tossed it, you should be in the clear to restore it.

## Solution

First thing before restoring the lost commit, let's discus about the commit history and the commit `HEAD`. Here are all the thing you need to know:

Check the `git log` to know the latest head from the list

    $ git log
      commit ded649d0550fa847926fb2327a85de0c478bf8d3 (HEAD -> master, origin/master, origin/HEAD)
      Author: Rohman Widiyanto <uname@mail.com>
      Date:   Wed Jan 13 01:29:56 2021 +0700

          finish but should be review

      commit 40026db548266e134ad86d5d224c449bf6aade8f
      Author: Rohman Widiyanto <uname@mail.com>
      Date:   Mon Jan 11 13:03:31 2021 +0700

          add readme for initialize the repository

Or show the only last git `HEAD`

    $ git show-ref -h HEAD
      ded649d0550fa847926fb2327a85de0c478bf8d3 HEAD
      ded649d0550fa847926fb2327a85de0c478bf8d3 refs/remotes/origin/HEAD

Then reset your last commit with this command, or if you need more references please read [the other markdown docs](https://github.com/rohwid/how-rohwid-git/tree/master/manage-delete-commit-history) about manage the commit history.

    $ git reset --hard HEAD^
      40026db548266e134ad86d5d224c449bf6aade8f HEAD
      40026db548266e134ad86d5d224c449bf6aade8f refs/remotes/origin/HEAD

So our `HEAD` has been backed up by one commit. At this point if we wanted it back we could just `git pull`, but we're assuming that only our local repository knows about the commit. We need the SHA1 of the commit so we can bring it back. We can prove that git knows about the commit still with the `fsck` command:

    $ git fsck --lost-found
      [... some blobs omitted ...]
      dangling commit ded649d0550fa847926fb2327a85de0c478bf8d3

You can also see the that git knows about the commit still by using the reflog command:

    $ git reflog
      40026db... HEAD@{0}: add readme for initialize the repository
      ded649d... HEAD@{1}: finish but should be review
      [... lots of other refs ...]

So, we now have our SHA1: `7c61179`. If we want to get immediately apply it back onto our current branch, doing a `git merge` will recover the commit:

    $ git merge ded649d
      Updating 40026db..ded649d
      finish but should be review
          css/screen.css |    4 ++++
          submit.html    |    4 ++--
          2 files changed, 6 insertions(+), 2 deletions(-)

This command will bring your lost changes back and make sure that HEAD is pointing at the commit. From here you can continue to work as normal! You could also checkout the SHA1 into a new branch, but really a merge is the fastest and easiest way to restore that lost commit once you have the hash. If you have other ways let us know in the comments!

Done! Goodluck!
