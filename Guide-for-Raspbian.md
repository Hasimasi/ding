<p align="center">
<img src="http://i.imgur.com/v8FctVF.png">
</p>

<h1 align="center">Raspbian (Raspberry Pi 2 or 3 B)</h1>
<p align="center">Some information may not be applicable to other Raspberry Pis.</p>
<p align="center">This guide assumes that you have knowledge of how to connect to your Raspberry Pi using an SSH and (S)FTP client.</p>

## 1: Dependencies
The bot requires **other software** installed on your Raspberry Pi. Run these commands:

    apt-get install sudo
    apt-get install git
    sudo apt-get update -y
    sudo apt-get upgrade -y
    sudo apt-get dist-upgrade
    sudo apt-get install build-essential libncursesw5-dev libgdbm-dev libc6-dev
    sudo apt-get install zlib1g-dev libsqlite3-dev tk-dev
    sudo apt-get install libssl-dev openssl
    sudo apt-get install build-essential unzip -y
    sudo apt-get install software-properties-common -y
    sudo add-apt-repository ppa:fkrull/deadsnakes -y
    sudo add-apt-repository ppa:mc3man/trusty-media -y
    sudo add-apt-repository ppa:chris-lea/libsodium -y
    sudo apt-get install libopus-dev libffi-dev libsodium-dev

**If you get errors while adding the PPAs as repositories, try continuing without them. [They may not be needed](https://github.com/Just-Some-Bots/MusicBot/issues/609).**

### 1.b: Python
Raspbian doesn't come with the correct version of Python out of the box. **We will install the correct version ourselves**. **This process can take a while**, as we're building Python from scratch.

    cd ~
    wget https://www.python.org/ftp/python/3.5.0/Python-3.5.0.tgz
    tar -zxvf Python-3.5.0.tgz
    cd Python-3.5.0
    ./configure

If you own a **quad-core** Raspberry Pi (3 B or higher), you can add `-j4` to the end of the next command (making it `make -j4`) to speed up the build process considerably. **Building Python may take a while**.

    make -j4
    sudo make install

**To check that Python installed correctly**, use the command `python3.5 --version`. It should output something like `Python 3.5.0`.

### 1.c: Pip
Pip is needed to install the **Python dependencies** required to run the bot, so lets ensure that pip is installed. **Run these commands**:

    cd ~
    wget https://bootstrap.pypa.io/get-pip.py
    sudo python3.5 get-pip.py

**To check that Pip installed correctly**, use the command `pip3.5 --version`. It should output something like `pip 7.1.2 from /usr/local/lib/python3.5/site-packages (python 3.5)`.

### 1.d: FFmpeg
FFmpeg is needed to stream music to Discord. **Run these commands**:

    cd /usr/src
    sudo git clone git://git.videolan.org/x264
    cd x264
    sudo ./configure --host=arm-unknown-linux-gnueabi --enable-static --disable-opencl
    sudo make
    sudo make install

You installed **H264 support** for your Raspberry Pi. Now lets install FFmpeg.

    cd /usr/src
    sudo git clone https://github.com/FFmpeg/FFmpeg.git
    cd FFmpeg
    sudo ./configure --arch=armel --target-os=linux --enable-gpl --enable-libx264 --enable-nonfree

If you own a **quad-core** Raspberry Pi (3 B or higher), you can add `-j4` to the end of the next command (making it `make -j4`) to speed up the build process considerably. **Building FFmpeg may take a while**.

    sudo make -j4
    sudo make install

## 2: Clone
Now that the system dependencies out of the way, **run the following commands** to install the bot in your home directory and install the Python dependencies required:

    cd ~
    git clone https://github.com/Just-Some-Bots/MusicBot.git MusicBot -b master
    cd MusicBot
    sudo -H pip3.5 install --upgrade -r requirements.txt

## 3: Configure
> **At this point you should [create a bot account](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

**Connect to your Raspberry Pi using FTP**.

Inside the bot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as options.ini after editing and upload it back to the Raspberry Pi**. If you need help, read the [configuration page](https://github.com/Just-Some-Bots/MusicBot/wiki/Configuration).

## 4: Start
You can start your bot by running this command:

    python3.5 run.py

If you want your bot to run on startup of your Raspberry Pi, read [this guide](http://www.instructables.com/id/Raspberry-Pi-Launch-Python-script-on-startup/).
