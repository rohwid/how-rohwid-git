# Reset and Revert

Just an example to explain the git **reset** and **revert**. Here's the challenge:

- Use the story directory to became a repository
- **Init** git project
- Add README.MD (Optional)
- Create `story1.txt` then **add and commit**
- Create `story2.txt` then **add and commit**
- Modify the `story2.txt` then **add and commit**
- Check `git log`
- Reset the with command:

    $ git reset --hard <the hash of the last commit>

- Check `git log`, the last will be disapear
- Create GitHub, GitLab or BitBucket repository
- **Add the remote repository (SSH is a must)**
- **Push** the project to the repository
- Modify the `story2.txt` then **add and commit**
- Create `story3.txt` then **add and commit**
- Modify the `story1.txt` then **add and commit**
- Create `story4.txt` then **add and commit**
- Modify the `story2.txt` then **add and commit**
- Push the project to the repository`
- Push the `master` branch

The expected output should be like the images below, you can access within **Insight** menu then select **Network**.