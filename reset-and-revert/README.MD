# Reset and Revert

Just an example to explain the git `reset --hard` and `revert`. Here's the challenge:

For the `reset --hard`:
- Use the story directory to became a repository.
- **Init** git project.
    
    ```bash
    $ git init
    ```

- Add README.MD (Optional).
- Create `story1.txt` then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "add story 1"
    ```

- Create `story2.txt` then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "add story 2"
    ```

- Create `story3.txt` then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "add story 3"
    ```

- Modify the `story2.txt` then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "modify story 2"
    ```

- Check `git log`

    ```bash
    $ git log
    ```

- Reset the with command:

    ```bash
    $ git reset --hard <the-last-commit-hash-ID>
    ```
    
- Check `git log` again and the last commit will be disapear

    ```bash
    $ git log
    ```

- Create the remote repository (e.g. **GitHub**, **GitLab** or **BitBucket**)
- **Add the remote repository (SSH is a must)**

    ```bash
    $ git remote add origin <git-remote-repository-ssh-address>
    ```

- **Push** the project to the repository in `master` branch

    ```bash
    $ git remote add origin <git-remote-repository-ssh-address>
    ```

- Modify the `story2.txt` again, then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "modify story 2"
    ```

- **Push** the project to the repository

    ```bash
    $ git push -u origin master
    ```

- Reset with command:

    ```bash
    $ git reset --hard <the-last-commit-hash-ID-or-the-N-previous-commit-hash-ID>
    ```

- Check `git log`, the last commit or the all the commit after N previous commit will be disappear

    ```bash
    $ git log
    ```

- Now you need to push with force, after reset the local repository and check the commit history in the remote repository will be disappear too

    ```bash
    $ git push -f origin master
    ```

The kind of `reset` in git:
- `--soft`: uncommit changes, changes are left staged (index)
- `--mixed` (default): uncommit + unstage changes, changes are left in working tree
- `--hard`: uncommit + unstage + delete changes, nothing left

For the **revert**:
- Modify the `story1.txt` then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "modify story 1"
    ```

- Modify the `story2.txt` then **add and commit**

    ```bash
    $ git add .
    $ git commit -m "modify story 2"
    ```

- Revert with command:

    ```bash
    $ git revert <the second previous commit hash ID>
    ```

- Check the `git log`, then you will see the `stor1.txt` are reverted, but not with the `story2.txt`. There will be new commit log added that indicate if the `story1.txt` are reverted. The commit log before reverted were kept and not deleted like `reset`.

    ```bash
    $ git log
    ```
- **Note**: It means revert is the undo process for the specific commit 
- Push the project to the remote repository, it will be the same with commit