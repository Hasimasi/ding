<p align="center">
<img src="http://i.imgur.com/9vjcnNY.png">
</p>

<h1 align="center">OS X Yosemite and above</h1>
<p align="center">Some information may not be applicable to older versions of OS X.</p>

# Table of Contents

[Introduction](#introduction)

1. [Step 1: Preparation](#step-1-preparation)
    - [1.a: Installing a TextEditor](#1a-installing-a-texteditor)
    - [1.b: Installing Homebrew](#1b-installing-homebrew)
    - [1.c: Installing xcode-select](#1c-installing-xcode-select)
    - [1.d: Installing Python](#1d-installing-python)
    - [1.e: Installing dependencies](#1e-installing-dependencies)
2. [Step 2: Download and setup MusicBot](#2-download-and-setup-musicbot)
    - [2.a: Allowing Terminal to Run Files](#2a-allowing-terminal-to-run-files)
    - [2.b: Install python dependencies](#2b-install-python-dependencies)
    - [2.c: Change configuration file](#2c-change-configuration-files)
3. [Step 3: Start the bot](#3-start-the-bot)
4. [Step 4: Running the bot in a Screen (Optional)](#4-running-the-bot-in-a-screen-optional)

# Introduction

Installing the bot on OSX requires the downloading of several libraries. These libraries are best managed with [Homebrew](http://brew.sh/). Homebrew and a basic text editor are required for this MusicBot to function.

# Step 1: Preparation

Let's get everything ready to install.

### 1.a: Installing a TextEditor

If you do not have a text editor, download a basic text editor from the Apple App Store (TextWrangler, or equivalent) or download an outside editor such as [Atom](https://atom.io/).

### 1.b: Installing Homebrew

Following that, you will install [Homebrew](http://brew.sh/)
To install Homebrew open up Terminal.app found on your computer and copy+paste the following command then press `RETURN`:

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
 
Run `brew update` to fetch the latest package data.

###1.c: Installing xcode-select

In order for the bot to function properly you need to install xcode command line tools to your mac. You will do this in Terminal.app by running the following command line:

    xcode-select --install

A dialog box will open asking if you want to install `xcode-select`. Select install and finish the installation.

###1.d: Installing Python

Next, you need to install Python3.5 or later.
[ClickHere](https://www.python.org/ftp/python/3.5.1/python-3.5.1-macosx10.6.pkg) to start downloading Python3.5.1.

After downloading, open the `python-3.5.1-macosx10.6.pkg` you downloaded to begin installation.

This will be the first thing you see when it opens. 
**Click Continue.**
![Python installer initial screen](http://i.imgur.com/rNDbcMQ.png)

**Click Continue.**
![Python read me screen](http://i.imgur.com/BvWwg2a.png)

**Read the Software License Agreement then Click Continue**
![Python license screen](http://i.imgur.com/SUWJePm.png)

**Click Agree.**
![Python license accept screen](http://i.imgur.com/RuKTcG3.png)

**Choose your installation destination (Recommended: Downloads), then Click Install.**
![Python installation destination and type](http://i.imgur.com/tNHIehd.png)

**After the installation screen you will see this... Click Close.**
![Python install successful screen](http://i.imgur.com/pF7rBq8.png)

**Congratulations you have successfully installed Python3.5!!**

### 1.e: Installing dependencies

To install dependencies, enter the following commands in Terminal.app:

    brew install git
    brew install ffmpeg
    brew install opus
    brew install libffi
    brew install libsodium

## 2: Download and setup MusicBot

To get the latest version of MusicBot, run this command using Terminal.app:

    cd desktop
    git clone https://github.com/SexualRhinoceros/MusicBot.git MusicBot -b master 
    cd    

cd'ing to the desktop allows you to quickly find your MusicBot folder as it places the folder directly on your desktop.

###2.a: Allowing Terminal to Run Files

In order for Terminal.app to run the .command files needed for the bot you will need to do the following:

In Terminal.app type the command below followed by a space:

    chmod +x 

Click and drag the file `update_macdeps.command` into terminal then press `RETURN`.
Repeat the above for the `runbot_mac.command` file. You should then be able to double-click the command files to run the bot.

Example:

![Terminal chmod commands](http://i.imgur.com/qKrlWUt.png)

### 2.b: Install python dependencies

Run the following file that is located in your MusicBot's main folder.    
**Run this file:**    

    update_macdeps.command    

*You may have to right click the file, mouse over 'Open With' then select 'Terminal.app'*    
    
This installs the various python dependencies used by the bot.

### 2.c: Change configuration files

> **At this point you should [create a bot account](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

The configuration files are located in the `config` folder. There are two files, `example_options.ini` and `example_permissions.ini` that tell you how to configure the bot. You should copy and rename these files to `options.ini` and `permissions.ini` respectively, then edit them. 

![Music Bot Config Folder](http://i.imgur.com/GnzWRNG.png)

Open options.ini in a text editor of your choosing from the one you downloaded at the beginning of this guide. I suggest TextWrangler or Atom.

Configure the file however you want, it should explain everything you need. The two things you MUST change are the bot's Token and your OwnerID. Begin by making the following changes to the to these lines:

![Changing your options.ini](http://i.imgur.com/7NBtTdf.png)

![Getting your token](http://i.imgur.com/cN4YehO.png)

If you have any further questions, you can ask on the [help server](https://discord.gg/0iqN3da4zqpJpuY0).

## 3: Start the bot 

To start the bot navigate back to your MusicBot's main folder.    
**Run:**    

    runbot_mac.command    

*You may have to right click the file, mouse over 'Open With' then select 'Terminal.app'*    

If you see this:

    Connected!

    Username: [Bot Username]
    ID: [Bot User ID]
    --Server List--
    [Server Name(s)]

that means everything is good and running correctly!

You don't need to do anything else! :smile: You can check out the [wiki articles](https://github.com/SexualRhinoceros/MusicBot/wiki/Commands-list "Commands list") to find out how to use your bot. :grin:
If you have further questions please visit our [Help Server](https://discord.gg/0iqN3da4zqpJpuY0) on Discord.
    
    
    
    
### 4: Running the bot in a Screen (Optional)

Running the bot in a screen allows you to close Terminal without it shutting down the bot. If you don't run the bot in a screen, closing Terminal will cancel the bots operations and disconnect it from Discord. Screen simply allows you to close Terminal with out this happening.    
**(This is an optional step that is only for user preference. You don't have to do this.)**

To make your life easier, this is best performed by keeping your MusicBot's folder on the desktop.

If your bot is currently running cancel its operations by pressing `Ctrl+C` before continuing on to these steps.

If you aren't already in a the music bots folder through Terminal go ahead and perform these steps (if your Terminal line looks like this `Name-MacBook-Pro:MusicBot-1.9.7 Username$` or similar, skip to "Run this to make a `screen` console"):

    cd desktop
    cd MusicBot

Run this to make a `screen` console:

    screen -S bot

This creates a `screen` console with the name 'bot' so you can easily come back later if there are any problems. Don't be alarmed that the Terminal window became empty.

To start the bot in this screen, run:

    python3.5 run.py

Once that's online and good, press `Ctrl+a` then `d` separately to 'detach' from the screen. Your music bot should still be online on your server.

Now you can close your Terminal window and play with your bot!

If you ever want to have a look at the bot's console logs, SSH back into the machine and run:

    screen -r bot

That should bring everything back up.
**NOTE: You can close the terminal without the bot disconnecting, however if you shut down your computer, close the lid, or let it sleep you will have to restart the bot again.**