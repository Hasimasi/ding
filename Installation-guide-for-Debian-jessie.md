Before starting make sure you have:

 * 30 minutes of time
 * A device running Debian jessie or knowledge on how to apply this guide to other Debian versions
 * Basic knowledge on using the command line in Debian

# 1. Install dependencies

## ffmpeg and x264 codecs

`$ sudo apt-get -t jessie-backports install ffmpeg x264 -y`

## All other dependencies
`$ sudo apt-get install git libopus-dev libffi-dev libsodium-dev -y`

# 2. Build python 3.5 from source

You *must* have python 3.5.0+ to run MusicBot, but the `python3` package is only python 3.4.

## Install build dependencies

The following command is a single line.

`$ sudo apt-get install build-essential libncursesw5-dev libgdbm-dev libc6-dev zlib1g-dev libsqlite3-dev tk-dev libssl-dev openssl -y`

## Download latest python 3 source

Go to [this page](https://www.python.org/downloads/source/) and click the link that says "Latest Python 3 Release - Python 3.5.x" where `x` is some number. Scroll down and copy the download link "Gzipped source tarball" and download it somewhere.

Extract the tarball (remember, `x` is some number):

```
$ tar -xvf Python-3.5.x.tgz
$ cd Python-3.5.x
```

## Build

```
$ sudo ./configure
$ sudo ./make
$ sudo ./make altinstall
```

This will install python3.5 and pip3.5 to `/usr/local/bin`.

# 3. Install the bot

## Fetch the bot source from Github

Determine where you want to install the bot, such as `/srv/rhinobot`. This location will be referred to as `<install_dir>` from now on; replace it the location you decided on. If your install dir is your home directory, you can leave `sudo` off of the following commands.

```
$ sudo git clone https://github.com/SexualRhinoceros/MusicBot.git <install_dir>
$ cd <install_dir>
$ sudo checkout master
```

## Install Python dependencies

You'll most likely have to use `sudo` here, even if you are installing to your home directory.

```
$ sudo pip3.5 install -r requirements.txt
```

# 4. Configure the bot

At this point, you need to create your bot's `config/options.ini` file with your bot token and other settings. If you are unsure of how to do this, refer to the end of the [generic Linux guide](https://github.com/SexualRhinoceros/MusicBot/wiki/Installation-guide-for-Ubuntu-14.04-and-other-versions#2b-change-configuration-file).

# 5. (Optional) Set up the bot to run on computer boot

You should be able to run the bot with the commands in section 6, but if you'd like your bot to run automatically when the computer is turned on, follow these optional steps. If you don't care about this, skip this step.

Create the following file `/etc/systemd/system/rhinobot.service` (you will need sudo for this). Replace both instances of `<install_dir>` with your full installation directory (such as `/srv/rhinobot`):

```
[Unit]
Description=RhinoBot
After=multi-user.target
[Service]
WorkingDirectory=<install_dir>
User=root
Group=root
ExecStart=/usr/local/bin/python3.5 <install_dir>/run.py
Type=idle
Restart=always
RestartSec=15

[Install]
WantedBy=multi-user.target
```

Finally, run the following command:

```
$ sudo systemctl enable rhinobot.service
```

# 6. Done!

You should now be able to run the bot. If you followed section 5, you can run the bot with:

```
$ sudo service rhinobot start
```

And you can check if your bot is currently running with

```
$ sudo service rhinobot status
```

If you skipped section 5, you can run the bot like so (remember your install directory as noted in section 3):

```
$ cd <install_dir>
$ sudo python3.5 run.py 
```