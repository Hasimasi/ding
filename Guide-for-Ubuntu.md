<p align="center">
<img src="http://i.imgur.com/iqvMAWb.png">
</p>

<h1 align="center">Ubuntu 14.04 and above</h1>
<p align="center">Some information may not be applicable to older versions of Ubuntu.</p>

## 1: Ubuntu
If you are new to using Ubuntu, there is a guide on [Digital Ocean's community tutorial site](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04) that will provide information on how to setup and configure the operating system.

## 2: Dependencies
The bot requires **other software** installed on your Ubuntu machine. You should **run the following commands** in Ubuntu's console in order.

NOTE: If you are running Ubuntu 14.04 Or earlier, run these commands:

    sudo apt-get install build-essential unzip -y
    sudo apt-get install software-properties-common -y
    sudo add-apt-repository ppa:fkrull/deadsnakes -y
    sudo add-apt-repository ppa:mc3man/trusty-media -y
    sudo add-apt-repository ppa:chris-lea/libsodium -y
    sudo apt-get update -y
    sudo apt-get upgrade -y
    sudo apt-get install git python3.5 python3.5-dev ffmpeg libopus-dev libffi-dev libsodium-dev -y

Run these commands if you are on Ubuntu 14.10 Or Above:

    sudo apt-get install build-essential unzip -y
    sudo apt-get install software-properties-common -y
    sudo add-apt-repository ppa:fkrull/deadsnakes -y
    sudo add-apt-repository ppa:mc3man/xerus-media -y
    sudo add-apt-repository ppa:chris-lea/libsodium -y
    sudo apt-get update -y
    sudo apt-get upgrade -y
    sudo apt-get install git python3.5 python3.5-dev ffmpeg libopus-dev libffi-dev libsodium-dev -y

If you are on Ubuntu 14.10 or above, you will most likely still get warnings that some index files have failed to download. Thats because chris-lea's PPA still don't support xenial yet. Ignore message.

After installing Python, it **should** come with `pip`. You can test this by using the command `pip3.5` and checking it doesn't respond with **Command not found**. If it does, run these commands to install pip:

    wget https://bootstrap.pypa.io/get-pip.py
    sudo python3.5 get-pip.py

## 3: Clone

Run the following commands to download MusicBot. This will place it in a **new folder** called `MusicBot`, which we will immediately enter.

    git clone https://github.com/SexualRhinoceros/MusicBot.git MusicBot -b master
    cd MusicBot

## 4: Configure

> **At this point you should [create a bot account](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

The folder we're in contains all of the bots files. **Do not delete or rename any files/folders**. We now need to configure the bot. **The following paragraph should be done using an FTP client connected to your Ubuntu machine**. **If you want to edit the config file from Ubuntu**, see [this AskUbuntu answer](http://askubuntu.com/a/54222).

Inside the bot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as options.ini after editing and upload it back to the Ubuntu machine**. If you need help, read the [configuration page](https://github.com/SexualRhinoceros/MusicBot/wiki/Configuration).

## 5: Start
You can test that your bot works by running this command:

    python3.5 run.py

If you **close your SSH session/console**, the bot will stop running.

### 5.a: Start permanently
**If you're already running the bot**, press `CTRL + C` a few times to stop it from running and get you back to being able to use console commands.

There are a **number of options** that can allow you to run the bot **permanently**, so that it continues even if you are not connected to your Ubuntu machine through an SSH client.

#### Tmux
Run this command to make a `tmux` console and then run the bot:

    tmux new -s bot
    python3.5 run.py

Now that the bot is running, press `CTRL+B` then `d` separately to 'detach' from the tmux session. If you ever want to have a look at the bot's console logs, SSH back into the machine and run `tmux a`.

#### Screen
Run this command to make a `screen` console and run the bot:

    screen -S bot
    python3.5 run.py

Now that the bot is running, press `Ctrl+A` then `d` separately to 'detach' from the screen. If you ever want to have a look at the bot's console logs, SSH back into the machine and run `screen -r bot`.

#### pm2
Run these commands to install node.js and pm2, then start the Python script using it:

    curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
    sudo apt-get install -y nodejs
    sudo npm install pm2@latest -g
    pm2 start run.py -n "bot"

To manage and review the status of the bot, type `pm2 status`. To view the logs/console for the bot, type `pm2 logs`. pm2 will restart the script if it breaks, and show you the uptime among other details on the status page.