<p align="center">
<img src="http://i.imgur.com/OUwHaXO.png">
</p>

<h1 align="center">Debian Jessie</h1>
<p align="center">Some information may not be applicable to older versions of Debian.</p>
<p align="center">This guide assumes that you have knowledge of Debian's command line.</p>

## 1: Dependencies
The bot requires **other software** installed on your Debian machine. You should **run the following commands** in Debian's console in order.

Before running the commands, ensure that you have **added backports** to your `sources.list` file. [Click here for more information on how to do this](https://backports.debian.org/Instructions/#index2h2).

    sudo apt-get install git libopus-dev libffi-dev libsodium-dev -y
    sudo apt-get -t jessie-backports install ffmpeg x264 -y
    sudo apt-get install build-essential libncursesw5-dev libgdbm-dev libc6-dev zlib1g-dev libsqlite3-dev tk-dev libssl-dev openssl -y

## 1.a: Python
Debian doesn't come with the correct version of Python out of the box. **We will install the correct version ourselves**.

* [Download this tarball](https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz) and save it somewhere

**Extract it**:

    tar -xvf Python-3.5.2.tgz
    cd Python-3.5.2

**Build it**:

    sudo ./configure
    sudo make
    sudo make altinstall

Python 3.5 and pip will have been **installed** to `/usr/local/bin` now.

## 2. Clone

Now that the system dependencies out of the way, **run the following commands** to install the bot in your home directory and install the Python dependencies required:

    cd ~
    git clone https://github.com/SexualRhinoceros/MusicBot.git MusicBot -b master
    cd MusicBot
    sudo -H pip3.5 install --upgrade -r requirements.txt

## 3: Configure
> **At this point you should [create a bot account](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

Inside the bot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as options.ini after editing**. If you need help, read the [configuration page](https://github.com/SexualRhinoceros/MusicBot/wiki/Configuration).

## 4: Start
You can start your bot by running this command:

    python3.5 run.py