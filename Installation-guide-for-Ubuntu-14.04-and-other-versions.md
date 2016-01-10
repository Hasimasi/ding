**THIS GUIDE IS FOR INSTALLING THE `develop` BRANCH ONTO A UBUNTU 14.04.** If you are not using Ubuntu 14.0.4, please use another article to install your RhinoBot. This guide should also work with other versions of Ubuntu (citations needed).

# Table of Contents

Introduction

1. Preparation
    - 1.a: SSH into machine and perform setup
    - 1.b: Updating package lists and adding repositories
2. Step 2: Installing Git
3. Step 3: Installing Python
4. Step 4: Installing ffmpeg
5. Step 5: Installing opus codec
6. Step 6: Install and configure RhinoBot
    - 6.a: Download RhinoBot
    - 6.b: Change configuration file
    - 6.c: Start the bot (non permanent for testing)
    - 6.d: Start the bot (permanent with screen)

# Introduction

A Ubuntu server is a very cheap way to have your RhinoBot to stay online permanently, as many websites offer cheap VPS hosting for Ubuntu servers. If you're looking for a cheap server provider, I (@deansheather) would suggest a [Digital Ocean](https://www.digitalocean.com/) (not an affiliate link) *'droplet'* for hosting your server. All you need to run this bot is a $5 per month 512mb droplet running Ubuntu 14.04.

Every block of code written in a box that looks like the box below should be run on your server unless otherwise stated.

    example command

# Step 1: Preparation

Let's get everything ready to install.

### 1.a: Setup Ubuntu

Once you've created your Ubuntu server on your host, it's a good idea to set up a few things first so everything runs nicely. Follow the guide in [Digital Ocean's community tutorial site](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04) to set everything up and make it all secure. This tutorial should work even if you aren't hosting with Digital Ocean. I'd suggest naming your new account `bot` or something.

### 1.b: Updating package lists and adding repositories

First of all, we'll add the repositories needed to install prerequisites for RhinoBot later on in this tutorial.

    sudo add-apt-repository ppa:fkrull/deadsnakes -y
    sudo add-apt-repository ppa:mc3man/trusty-media -y
    sudo apt-get update -y
    sudo apt-get dist-upgrade -y
    sudo apt-get install gcc -y
    sudo apt-get install yasm -y
    sudo apt-get install unzip -y

# Step 2: Installing Git

First of all, we need to install Git. If you already have Git installed onto your machine, you can skip to Step 3.

To install Git, run the following:

    sudo apt-get install git -y

You have now successfully installed Git onto your machine! :)

# Step 3: Installing Python 3.5

Now we have Git installed on this machine, we need to install Python.

To install Python 3.5, run the following:

    sudo apt-get install python3.5 -y

You have now successfully installed Python onto your machine! :)

# Step 4: Installing ffmpeg

To install ffmpeg, which is needed to run RhinoBot, run the following:

    sudo apt-get install ffmpeg -y

You have now successfully installed ffmpeg onto your machine! :)

# Step 5: Installing opus codec

This is where it gets very complicated, so make sure you pay **very close** attention to the instructions.

Run the following:

    sudo wget http://downloads.xiph.org/releases/opus/opus-1.1.1.tar.gz
    sudo tar -xzf opus1.1.1.tar.gz
    ./configure --prefix=/usr

Have a quick scroll through the terminal window and look for any errors. If you see something that says `Type "make; make install" to compile and install` near the bottom then you should be good to continue without asking for help on the RhinoBot Discord server ([https://discord.gg/0iqN3da4zqrSz036](https://discord.gg/0iqN3da4zqrSz036)).

    sudo make

Check for errors once again before proceeding.

    sudo make install

Now you need to restart your machine if no errors occurred.

    sudo reboot

Reconnect via SSH to your machine.

You have now successfully installed opus onto your machine! :)

# Step 6: Install and configure RhinoBot

Let's get right into it, shall we?

### 6.a: Download RhinoBot

Run the following commands to download RhinoBot:

    sudo wget https://github.com/SexualRhinoceros/MusicBot/archive/develop.zip -O MusicBot-develop.zip
    sudo unzip MusicBot-develop.zip
    cd MusicBot-develop

### 6.b: Change configuration file

The easiest way to edit the configuration is with SFTP software, such as CyberDuck or WinSCP. CyberDuck works with Windows and Mac computers, whereas WinSCP only works with Windows computers. Due to this, this tutorial will explain how to use CyberDuck to access your server's files (sorry Linux users...).

**NOTE:** CyberDuck **is** free software, but you will be prompted for donations each time you use it. If you donate, you will receive a license key which will remove the donation prompt.

**The following screenshots have been taken on a Windows 10 machine, but the process should be the same for other operating systems.**

Download the CyberDuck installer for your operating system from [CyberDuck's website](https://cyberduck.io "CyberDuck's website"), install it and open it.

In CyberDuck, click the 'Open Connection' button.

![CyberDuck Open connection](http://i.imgur.com/INjb2P8.png)

Select 'SFTP (SSH File Transfer Protocol)' from the dropdown and enter your server and user information.

![CyberDuck connection settings](http://i.imgur.com/ThWigdU.png)

Open the MusicBot-develop folder, and then the config folder.

![CyberDuck config folder](http://i.imgur.com/w4Pr0mN.png)

Now you require a text editor other than notepad, as notepad won't work for this situation. I suggest [Notepad++](https://notepad-plus-plus.org "Notepad++").

**SINGLE** click `options.txt` and then select Notepad++ (or your other chosen text editor) from the 'Edit' dropdown at the top, otherwise, you'll see one big line full of stuff in notepad.

![CyberDuck open options.txt](http://i.imgur.com/GthqaYC.png)

Change the configuration settings to what you need according to [this wiki article](https://github.com/SexualRhinoceros/MusicBot/wiki/%5Bdevelop%5D-Configuration-file "develop branch configuration file"). To save to the server, just save the file in the editor where it is. It should automatically upload.

### 6.c: Start the bot (non permanent for testing)

Log into the bot's account on your Discord client and join the server you want your bot to live on.

Go back to the SSH for your server and make sure you're in the `MusicBot-develop` folder (you should see `username@host:~/MusicBot-develop$` or something similar in front of the cursor).

Run this:

    sudo python3 run.py

If you see this:

    Connected!
    
    Username: [Bot Username]
    ID: [Bot User ID]
    --Server List--
    [Server Name(s)]

that means everything is good and running correctly! 

If you see an error, you might want to try installing dependencies by hand. You can do this by executing the command `pip3 install -r requirements.txt`.

### 6.d: Start the bot (permanent with screen)

Close the test bot first by hitting `Ctrl+C` in the SSH window while the bot is running.

Run this to make a `screen` console:

    screen -S bot

This creates a `screen` console with the name 'bot' so you can easily come back later if there are any problems. Don't be alarmed that the SSH window became empty.

To start the bot in this screen, run:

    sudo python3 run.py

Once that's online and good, hit `Ctrl+A` then click `D` separately to 'detach' from the screen. Your music bot should still be online on your server.

Now you can close your SSH window or terminal and play with your bot!

If you ever want to have a look at the bot's console logs, SSH back into the machine and run:

    screen -r bot

That should bring everything back up.

You don't need to do anything else! :smile: You can check out the [wiki articles](https://github.com/SexualRhinoceros/MusicBot/wiki/%5Bdevelop%5D-Commands-list "Commands list") to find out how to use your bot. :grin: