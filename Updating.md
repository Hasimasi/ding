<p align="center">
<img src="http://i.imgur.com/WKG0qo0.png">
</p>

# Table of Contents

- [Introduction](#introduction)
- [Windows](#windows)
- [Linux](#linux)
- [Mac](#mac)

# Introduction
This guide tells you how to update your bot easily using Git, which you should have used when installing it for the first time. **Make sure that the bot isn't running before attempting these steps**.  Also be warned that your configuration file may have to be reconfigured if changes have been made to the configuration file in the update.

# Windows
To update MusicBot on Windows, open Git Bash in the folder that the bot is running in. This is the folder that contains most binary files such as `run.sh` and `update_deps.bat`.

To open Git Bash, open Windows Explorer in your designated folder and right-click. You will get the option `Git Bash` on the context menu. Click it to open a new shell.

![Git Bash context menu](http://i.imgur.com/ptlggmn.png) 

Make sure that the name of the branch/version is in brackets at the end of the path (should be `master` for stable releases).

![Git Bash window](http://i.imgur.com/IVI6Uoi.png)

Finally, type `git pull` to fetch the latest changes from the GitHub branch. If there are no changes, Git's response will end with "**Already up-to-date.**".

# Linux

In the console, navigate to the directory of the bot (use `cd <folder>` to enter a directory, and `ls` to list the contents of the directory).

Type `git pull` to fetch the latest changes from the GitHub branch. If there are no changes, Git's response will end with "**Already up-to-date.**".

# Mac

Open a Terminal window in the directory of the bot.

Type `git pull` to fetch the latest changes from the GitHub branch. If there are no changes, Git's response will end with "**Already up-to-date.**".