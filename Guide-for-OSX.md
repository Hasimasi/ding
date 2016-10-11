<p align="center">
<img src="http://i.imgur.com/9vjcnNY.png">
</p>

<h1 align="center">OS X Yosemite and above</h1>
<p align="center">Some information may not be applicable to older versions of OS X.</p>

# Introduction

Installing the bot on OSX requires the download of several libraries. [Homebrew](http://brew.sh/), [Python](http://www.python.org), a [text editor](https://atom.io/), and other software/dependencies are required to run MusicBot. This guide will show you how to install everything you need and get the MusicBot set up.

## 1: Dependencies

### 1.a: Python

[Click Here](https://www.python.org/ftp/python/3.5.2/python-3.5.2-macosx10.6.pkg) to start downloading **Python 3.5.2.** After downloading, open `python-3.5.2-macosx10.6.pkg` and complete installation to your computer's hard drive.

### 1.b: Other dependencies

The bot requires **other software** installed on your OS X machine. You should run the following commands in Terminal in order.
**Note:** When running `xcode-select --install`, a dialog bog will open asking if you want to install `xcode-select`; select install and finish the installation. Then continue on with the other commands in Terminal.

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    brew update
    xcode-select --install
    brew install git
    brew install ffmpeg
    brew install opus
    brew install libffi
    brew install libsodium

## 2: Clone

To get the latest version of the MusicBot, run the following commands in Terminal:

    cd desktop
    git clone https://github.com/Just-Some-Bots/MusicBot.git MusicBot -b master 
    cd    

`cd`ing to the Desktop allows you to quickly find your MusicBot folder as it places the folder directly on your Desktop.

## 3: Configure

> **At this point you should [create a bot account](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

Inside the MusicBot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as *options.ini* after editing**. If you need help, read the [configuration page](https://github.com/SexualRhinoceros/MusicBot/wiki/Configuration).

## 4: Terminal Permissions

In order for Terminal to run the `.command` files needed for the bot, you will need to do the following:

In Terminal, type the command below followed by a space:

    chmod +x 

Click and drag the `update_macdeps.command` file into Terminal then press `RETURN`.
Repeat the above for the `runbot_mac.command` file. You should then be able to double-click the command files to run the bot.

Example:

<p align="center">
<img src="http://i.imgur.com/qKrlWUt.png?1">
</p>

## 5: Run
In the main folder (called `MusicBot`), **double-click** `update_macdeps.command` to install the required Python dependencies. After it is finished, you can **close the window** and then **double-click** `runbot_mac.command` to run the bot.

If you **close** Terminal, your bot will stop working. This window is required to be open for the bot to run. The bot will also stop if you turn your computer off, sleep, or hibernate it. To avoid these issues, you can buy a dedicated server.