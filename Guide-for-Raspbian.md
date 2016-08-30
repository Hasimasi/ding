# First words
Before beginning with this tutorial make sure you have the following at hand:
* A Raspberry Pi 2 or 3 B with Raspbian
* At least 3 hours of time
* Patience
* Basic Knowledge on how to use the shell   

# Installing sudo and git
Since some debian distros don't come with sudo pre-installed we're gonna install it.
Feel free to just use the su command if you know what you're doing though. If not run:  
`apt-get install sudo`  
`apt-get install git`  

# Installing Python 3.5 on your Raspberry Pi
Raspbian does not have the correct version of Python installed out of the box, so we are going to install it manually by ourselves. But first, we're starting with getting everything up to date. To do this enter the following steps into the shell.

`sudo apt-get update`  
`sudo apt-get upgrade -y`  
`sudo apt-get dist-upgrade`  

Now we need install components which will be necessary for our Python build:

`sudo apt-get install build-essential libncursesw5-dev libgdbm-dev libc6-dev `  
`sudo apt-get install zlib1g-dev libsqlite3-dev tk-dev`  
`sudo apt-get install libssl-dev openssl`  

## Building Python

Now let's go home then download, build and install our new Python.
Going home:  
`cd ~`  
Retrieving source codes of Python 3.5 :  
`wget https://www.python.org/ftp/python/3.5.0/Python-3.5.0.tgz`    
Unpacking sources archive (it can take approx half a minute):  
`tar -zxvf Python-3.5.0.tgz`  
`cd Python-3.5.0`  

Configuring (takes few minutes):  
`./configure`  
Now if you own a Raspberry Pi 2 B or above you can use -j4 appended to the following command to use all 4 cores. Make sure your raspberry Pi is properly cooled, because this will produce considerable load on the CPU for extended time. If you don't cool your Raspberry properly it might get damaged. Remove -j4 if you don't own a quadcore Pi.
Building (takes approx. 30 minutes):  
`make -j4`  
Installing our own-built-python-release (few minutes for this operation):  
`sudo make install`

## Testing Installation
If everything is OK you will be able to find python3.5 command by pressing TAB after printing python to your shell. Also, you can test installation by running command:  
`python3.5 --version`  
If everything is OK you will get output like this:  
`Python 3.5.0`
Congratulations, now you have installed Python 3.5.

## Installing pip

If you want to use pip for your Python 3.5 installation let's install it.
Going home:  
`cd ~`  
Downloading needful script:    
`wget https://bootstrap.pypa.io/get-pip.py`  
Running this script using our Python 3.5:  
`sudo python3.5 get-pip.py`  

## Testing pip
Let's test just installed pip:  
`pip3.5 --version`  
We will get something like this:  
`pip 7.1.2 from /usr/local/lib/python3.5/site-packages (python 3.5)`


# Installing ffmpeg
## Install H264 support  
Run the following commands, one at a time.  
`cd /usr/src`  
`sudo git clone git://git.videolan.org/x264`  
`cd x264` 
`sudo ./configure --host=arm-unknown-linux-gnueabi --enable-static --disable-opencl`  
`make`  
`sudo make install`  

## Installing ffmpeg

`cd /usr/src`  
`sudo git clone https://github.com/FFmpeg/FFmpeg.git`  
`cd FFmpeg`  

***
The following code until the next text-block is a single line (formating sometimes splits it in 2):  
`sudo ./configure --arch=armel --target-os=linux --enable-gpl --enable-libx264 --enable-nonfree`  
***

Now if you own a Raspberry Pi 2 you can use -j4 appended to the following command to use all 4 cores. Make sure your raspberry Pi is properly cooled, because this will produce considerable load on the CPU for extended time. If you don't cool your Raspberry properly it might get damaged. Expect this command to take up to an hour!  Remove -j4 if you don't own a quadcore Pi.  
`sudo make -j4`  
`sudo make install`  

# Installing the bot
We're done setting up everything and are now ready to install the bot. Enter the following commands (some might not be necessary, but just to be sure) :  
`sudo apt-get install build-essential unzip -y`  
`sudo apt-get install software-properties-common -y`  
`sudo add-apt-repository ppa:fkrull/deadsnakes -y`  
`sudo add-apt-repository ppa:mc3man/trusty-media -y`  
`sudo add-apt-repository ppa:chris-lea/libsodium -y`  
`sudo apt-get update -y `  
`sudo apt-get upgrade -y`  

## Install dependencies
We only need to do partial installations from the linux tutorials now, since we did parts of it manually:  
`sudo apt-get install libopus-dev libffi-dev libsodium-dev`  

## Download and setup the MusicBot
First, lets go back home:  
`cd ~`  
Run the following commands to download MusicBot:

`git clone https://github.com/SexualRhinoceros/MusicBot.git MusicBot -b master`  
`cd MusicBot`  

## Install python dependencies
This next step is somewhat optional, as MusicBot will attempt to do this for you if you haven't, but may require root to do so.  

`sudo -H pip3.5 install --upgrade -r requirements.txt`  
This installs the various python dependencies used by the bot.

# Configuring the bot
> **At this point you should [create a bot account](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

For configuring the bot refer to the end of the [linux / ubuntu tutorial](https://github.com/SexualRhinoceros/MusicBot/wiki/Installation-guide-for-Ubuntu-14.04-and-other-versions#2b-change-configuration-file).

# Running the bot
If you want to run the bot type the following commands into the command line (prior configuring required).  
`cd MusicBot`  
`python3.5 run.py`  

# Automatically run the bot when booting

If you want to run the bot when the Pi boots refer to the following tutorial (Note: The tutorial does have multiple pages, use the orange buttons to see the full tutorial, or use the "view all steps"-button). Use the commands that start the bot (from the linux tutorial) in the script instead of the shown commands in the tutorial.
[Awesome Tutorial](http://www.instructables.com/id/Raspberry-Pi-Launch-Python-script-on-startup/)
Instead of the lines used in this tutorial, use the lines in "Running the bot".
Updating the bot is also identical to the steps in the linux tutorial.
