# Git Branch, Git Checkout

The simple explanantion about `Git Branch` is works like tree branch and each tree branch is the place to works. When we creates new git repository, the only branch that has included was `master` branch. So, we need to add it manually with this command:

    $ git branch <new-branch-name>

For the example is `development`. So, it will be like this:

    $ git branch development

To check all the branch that we have created, you can uses this command:

    $ git branch
    * development
      master

Here we come to the `git checkout`, this feature usually uses to change the branch. For the example, if we wanna change the branch from the `master` branch into the `development` branch.

Check all the branch with this command:

    $ git branch
      development
    * master

Then move to the aimed branch (ex. `development`) with this command:

    $ git checkout development

# Merge or Rebase in Git

Thanks all the people in this [stackoverflow](https://stackoverflow.com/questions/14168677/merge-development-branch-with-master) and I've done some modification from yours tutorials.

## Problem

I would like to merge from the `development` branch into `master` branch.

I have two branches namely `master` and `development` in a GitHub Repository. I am doing all my development in development branch as shown.

## Solution

I generally like to merge the `master` into the `development` first so that if there are any conflicts. So, I can resolve in the `development` branch itself and my master remains clean. But, if you're really sure, it's okay to do it.

Make sure you're in the `development` branch, before pull the `master` branch.

    $ git branch
    * development
      master

Merge the `master` branch into the `development` branch. If there are any conflict please fix that first!

    $ git merge master

Then, merge the `development` branch into the `master` branch would be like this:

    $ git checkout master
    $ git merge development (there won't be any conflicts now)

There isn't much of a difference in the two approaches, but I have noticed sometimes that I don't want to merge the branch into master yet, after merging them, or that there is still more work to be done before these can be merged, so I tend to leave master untouched until final stuff.

Done! Goodluck!


## CI/CD Case

When perform CI/CD, we do create PR from the `feature` branch then merge to the `master` branch. After the PR were accepted and merged to the `master` branch. To continue work with the `feature` branch, we must rebase or merge from the `master` branch to the `feature` branch.

    $ git checkout <feature branch>
    $ git rebase master

or

    $ git checkout <feature branch>
    $ git merge master

# Simulation

If you want simulating this steps, please use and follow the `../try-git` project from the main directory by creating new project.