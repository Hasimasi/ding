**This guide was written for Ubuntu 14.04.** If you are not using Ubuntu 14.04, this guide may not work. Future/past versions of Ubuntu may be different.

# Table of Contents

[Introduction](#introduction)

1. [Step 1: Preparation](#step-1-preparation)
    - [1.a: Setup Ubuntu](#1a-setup-ubuntu)
    - [1.b: Updating package lists and adding repositories](#1b-updating-package-lists-and-adding-repositories)
    - [1.c: Installing dependencies](#1c-installing-dependencies)
2. [Step 2: Download and setup MusicBot](#2-download-and-setup-musicbot)
    - [2.a: Install python dependencies](#2a-install-python-dependencies)
    - [2.b: Change configuration file](#2b-change-configuration-file)
3. [Step 3: Start the bot](#3-start-the-bot)
    - [3.a: Test the bot (non permanent)](#3a-test-the-bot-non-permanent)
    - [3.b: Start the bot (permanent)](#3b-start-the-bot-permanent)

# Introduction

A Ubuntu server is a very cheap way to have your MusicBot to stay online permanently, as many websites offer cheap VPS hosting for Ubuntu servers. If you're looking for a cheap server provider, (@deansheather) would suggest a [Digital Ocean](https://www.digitalocean.com/) (not an affiliate link) *'droplet'* for hosting your server. All you need to run this bot is a $5 per month 512mb droplet running Ubuntu 14.04.

Every block of code written in a box that looks like the box below should be run on your server unless otherwise stated.

    example command

# Step 1: Preparation

Let's get everything ready to install.

### 1.a: Setup Ubuntu

Once you've created your Ubuntu server on your host, it's a good idea to set up a few things first so everything runs nicely. Follow the guide in [Digital Ocean's community tutorial site](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04) to set everything up and make it all secure. This tutorial should work even if you aren't hosting with Digital Ocean. I'd suggest naming your new account `bot` or something.

### 1.b: Updating package lists and adding repositories

First of all, we'll add the repositories needed to install prerequisites for MusicBot later on in this tutorial.

    sudo apt-get install build-essential unzip -y
    sudo apt-get install software-properties-common -y
    sudo add-apt-repository ppa:fkrull/deadsnakes -y
    sudo add-apt-repository ppa:mc3man/trusty-media -y
    sudo add-apt-repository ppa:chris-lea/libsodium -y
    sudo apt-get update -y
    sudo apt-get upgrade -y

## 1.c: Installing dependencies

These are the things we need to run the bot.

    sudo apt-get install git python3.5 python3.5-dev ffmpeg libopus-dev libffi-dev libsodium-dev -y
    
Python 3.5 should come with pip, but for if some reason you don't have it, run the following:

    wget https://bootstrap.pypa.io/get-pip.py
    sudo python3.5 get-pip.py

## 2: Download and setup MusicBot

Run the following commands to download MusicBot:

    git clone https://github.com/SexualRhinoceros/MusicBot.git MusicBot -b master
    cd MusicBot

### 2.a: Install python dependencies

This next step is somewhat optional, as MusicBot will attempt to do this for you if you haven't, but may require root to do so.  

    sudo -H pip3.5 install --upgrade -r requirements.txt
    
This installs the various python dependencies used by the bot.

### 2.b: Change configuration file

A fairly easy way to edit the configuration is with SFTP software, such as CyberDuck or WinSCP or Filezilla. Filezilla works on Linux, Windows, and Mac computers, CyberDuck works with Windows and Mac computers, and WinSCP only works with Windows computers. Linux users can also generally use the file manager built into their distro - try looking in the file menu for a 'Connect to server' option. For the purposes of this tutorial, we will explain how to use CyberDuck to access your server's files, but a quick Google should help you understand how to use other tools similarly.

**NOTE:** CyberDuck **is** free software, but you will be prompted for donations each time you use it. If you donate, you will receive a license key which will remove the donation prompt.

**The following screenshots have been taken on a Windows 10 machine, but the process should be the same for other operating systems.**

Download the CyberDuck installer for your operating system from [CyberDuck's website](https://cyberduck.io "CyberDuck's website"), install it and open it.

In CyberDuck, click the 'Open Connection' button.

![CyberDuck Open connection](http://i.imgur.com/INjb2P8.png)

Select 'SFTP (SSH File Transfer Protocol)' from the dropdown and enter your server and user information.

![CyberDuck connection settings](http://i.imgur.com/ThWigdU.png)

Open the MusicBot folder, and then the config folder.

![CyberDuck config folder](http://i.imgur.com/w4Pr0mN.png)

Now you require a text editor other than notepad, as notepad won't work for this situation. I suggest [Notepad++](https://notepad-plus-plus.org "Notepad++").

**SINGLE** click `options.ini` and then select Notepad++ (or your other chosen text editor) from the 'Edit' dropdown at the top, otherwise, you'll see one big line full of stuff in notepad.

![CyberDuck open options.ini](http://i.imgur.com/GthqaYC.png)

Read through the various comments in the file and set options as you please. To save to the server, just save the file in the editor where it is. It should automatically upload. The two things you MUST change are the bot's Token and your OwnerID. Begin by making the following changes to the to these lines:

![Changing your options.ini](http://i.imgur.com/7NBtTdf.png)

![Getting your token](http://i.imgur.com/cN4YehO.png)

If you have any further questions, you can ask on the [help server](https://discord.gg/0iqN3da4zqpJpuY0).

## 3: Start the bot 

> **At this point you should [create a bot account](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

### 3.a Test the bot (non permanent)
Go back to the SSH for your server and make sure you're in the `MusicBot` folder (you should see `username@host:~/MusicBot$` or something similar in front of the cursor).

Run this:

    python3.5 run.py

If you see this:

    Connected!

    Username: [Bot Username]
    ID: [Bot User ID]
    --Server List--
    [Server Name(s)]

that means everything is good and running correctly!

### 3.b: Start the bot (permanent)

Close the test bot first by hitting `Ctrl+C` in the SSH window while the bot is running.  You may need to press it a few times.

The following are solutions for running the bot permanently, even if you disconnect from SSH.

#### Tmux
> Tmux is a more powerful version of screen, and allows for extra features such as full Unicode support, and window splitting.

Run this command to make a `tmux` console:

    tmux new -s bot

You will now enter the tmux instance, clearing your window. To start the bot in tmux, run:

    python3.5 run.py

Now that the bot is running, press `CTRL+B` then `d` separately to 'detach' from the tmux session. This will keep the bot running while not even needing to be connected to SSH.

If you ever want to have a look at the bot's console logs, SSH back into the machine and run:

    tmux a

#### Screen
> Screen is a basic terminal multiplexer.

Run this command to make a `screen` console:

    screen -S bot

You will now enter the screen instance, clearing your window. To start the bot in this screen, run:

    python3.5 run.py

Now that the bot is running, press `Ctrl+A` then `d` separately to 'detach' from the screen. This will keep the bot running while not even needing to be connected to SSH.

If you ever want to have a look at the bot's console logs, SSH back into the machine and run:

    screen -r bot

### pm2
> pm2 is a `node.js` application that manages your processes. You should only use it to run your bot if you have the technical knowledge and ability to follow this guide. We will not provide help for running the bot using pm2 - this guide is just here as a straight forward "how to".

First, install `node.js`

    curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
    sudo apt-get install -y nodejs

Then, using Node's package manager (`npm`), install pm2

    sudo npm install pm2@latest -g

Now start the Python script using pm2

    pm2 start run.py -n "bot"

To manage and review the status of the bot, type `pm2 status`. To view the logs/console for the bot, type `pm2 logs`. pm2 will restart the script if it breaks, and show you the uptime among other details on the status page.