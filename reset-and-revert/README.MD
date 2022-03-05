# Reset and Revert

Just an example to explain the git `reset --hard` and `revert`. Here's the challenge:


For the `reset --hard`:
- Use the story directory to became a repository
- **Init** git project
- Add README.MD (Optional)
- Create `story1.txt` then **add and commit**
- Create `story2.txt` then **add and commit**
- Create `story3.txt` then **add and commit**
- Modify the `story2.txt` then **add and commit**
- Check `git log`
- Reset the with command:

    $ git reset --hard <the hash of the last commit>

- Check `git log`, the last commit will be disapear
- Create GitHub, GitLab or BitBucket repository
- **Add the remote repository (SSH is a must)**
- **Push** the project to the repository
- Modify the `story2.txt` again, then **add and commit**
- **Push** the project to the repository
- Reset with command:

    $ git reset --hard <the hash of the last commit>

- Now you need to push with force, after reset the local repository.

    $ git push -f origin master

- Check `git log`, the last will be disappear and check the commit history in the remote repository will be appear too.


The kind of `reset` in git:
- `--soft`: uncommit changes, changes are left staged (index).
- `--mixed` (default): uncommit + unstage changes, changes are left in working tree.
- `--hard`: uncommit + unstage + delete changes, nothing left.


For the **revert**:
- Modify the `story1.txt` then **add and commit**
- Check `git log`
- Revert with command:

    $ git revert <the hash of the last commit>

- Push the project to the repository
- Check `git log`
- Push the `master` branch
