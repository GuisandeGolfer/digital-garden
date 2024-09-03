---
{"dg-publish":true,"dg-path":"Resources/PARA/Obsidian/How to Set up Obsidian Git.md","permalink":"/resources/para/obsidian/how-to-set-up-obsidian-git/","created":"2024-09-01T14:28:32.440-07:00","updated":"2024-09-01T14:28:32.440-07:00"}
---


References resources:
https://publish.obsidian.md/git-doc/Authentication
https://publish.obsidian.md/git-doc/Getting+Started


>[!book] Step 1: Install git on your Computer
> you can install through their [website](https://git-scm.com/download/win) with all the default settings, have `3rd party software access enabled` 
- enable git credential manager

>[!book] Step 2: Create a GitHub account and a New empty repository

- create a new repository and make sure there is nothing in it.

>[!book] Step 3: Set up Authentication on MacOS

There are two methods: *SSH* and *HTTPS*

- HTTPS
use MacOS keychain to store credentials
```bash
git config --global credential.helper osxkeychain
```

- SSH
[generate a new ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=mac#generating-a-new-ssh-key)
[add ssh key to ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=mac#adding-your-ssh-key-to-the-ssh-agent)

[The rest of the steps continue from here](https://publish.obsidian.md/git-doc/Getting+Started#For+existing+remote+repository)
