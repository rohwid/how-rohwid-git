# Using Multiple GitHub Accounts with SSH Keys

Thanks to [oanhnn](https://github.com/oanhnn) for the [tutorials](https://gist.github.com/oanhnn/80a89405ab9023894df7), and I've done some modification from your tutorials.

## Problem
I have two Github accounts: *rohwid* (personal) and *rohman* (for work).
I want to use both accounts on same computer (without typing password everytime, when doing git push or pull).

## Solution
Use ssh keys and define host aliases in ssh config file (each alias for an account).

## How to?
1. [Generate ssh key pairs for accounts](https://help.github.com/articles/generating-a-new-ssh-key/) and [add them to GitHub accounts](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).
2. Edit/Create ssh config file (`~/.ssh/config`):

   ```conf
   # Default github account: rohwid
   Host github.com-rohwid
      HostName github.com
      IdentityFile ~/.ssh/oanhnn_private_key
      IdentitiesOnly yes
      
   # Other github account: rohman
   Host github.com-rohman
      HostName github.com
      IdentityFile ~/.ssh/superman_private_key
      IdentitiesOnly yes
   ```
   
3. [Add ssh private keys to your agent](https://help.github.com/articles/adding-a-new-ssh-key-to-the-ssh-agent/):

   ```shell
   $ ssh-add ~/.ssh/oanhnn_private_key
   $ ssh-add ~/.ssh/superman_private_key
   ```

4. Test your connection

   ```shell
   $ ssh -T git@github.com
   $ ssh -T git@github-superman
   ```

   With each command, you may see this kind of warning, type `yes`:

   ```shell
   The authenticity of host 'github.com (192.30.252.1)' can't be established.
   RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:
   Are you sure you want to continue connecting (yes/no)?
   ```

   If everything is OK, you will see these messages:

   ```shell
   Hi rohwid! You've successfully authenticated, but GitHub does not provide shell access.
   ```
   
   ```shell
   Hi rohman! You've successfully authenticated, but GitHub does not provide shell access.
   ```

5. Now all are set, just clone your repositories. But don't forget modify the git address into your custom `Host` in 
(`~/.ssh/config`).

   ```shell
   $ git clone git@github.com-rohman:umbrella-corp/project-name.git
   $ cd /path/to/project-name
   $ git config user.email "rohman@umbrella-corp.com"
   $ git config user.name  "rohman"
   ```

Done! Goodluck!
