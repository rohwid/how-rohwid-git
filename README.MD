# The Common Thing About Git

Here's the some command that I usually uses in Git

## Local Repository

To initialize project:

    $ git init

Add all the files into the project:

    $ git add .

But if you wanna undo or reset all the files that you've added just uses this command:

    $ git reset .

Or this, if you wanna reset or undo the specific file:

    $ git reset <name-of-the-file>

Commit all the file to the project, and the message is a must be add, like this command:

    $ git commit -m <the-commit-message>

For the example:

    $ git commit -m "initial commit"

But if you wanna undo or reset all the files that you've commited just follow [this](https://github.com/rohwid/how-rohwid-git/tree/master/manage-delete-commit-history) step.

## Remote Repository

(Skip this step if you already add the remote repository). But if you didn't add it yet need to follow this command:

    $ git remote add origin <ssh-address-repository>

for example:

    $ git remote add origin git@github.com:rohwid/try-git.git

Push the project to remote repository:

    $ git push -u origin <branch-name>

For initialization phase, usually uses `master` branch.

    $ git push -u origin master