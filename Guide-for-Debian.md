<p align="center">
<img src="http://i.imgur.com/OUwHaXO.png">
</p>

<h1 align="center">Debian Jessie or Stretch</h1>
<p align="center">Some information may not be applicable to older versions of Debian.</p>
<p align="center">This guide assumes that you have knowledge of Debian's command line.</p>

## 1: Dependencies
The bot requires **other software** installed on your Debian machine. You should **run the following commands** in Debian's console in order.

````
sudo apt-get install git libopus-dev libffi-dev libsodium-dev -y
sudo apt-get install build-essential libncursesw5-dev libgdbm-dev libc6-dev zlib1g-dev libsqlite3-dev tk-dev libssl-dev openssl -y
```

**If you are using Debian Jessie**, you also need to install the backported `ffmpeg` version. First, ensure that you have **added backports** to your `sources.list` file. [Click here for more information on how to do this](https://backports.debian.org/Instructions/#index2h2). Then, run this command:

```
sudo apt-get -t jessie-backports install ffmpeg x264 -y
```

## 1.a: Python
**If you are using Debian Stretch**, Python 3.5 is available from official repositories. You can therefore install it like so:

```
sudo apt-get install python3.5 -y
```

**If you are using Debian Jessie**, you will need to follow [these instructions](https://gist.github.com/jaydenkieran/75b2bbc32b5b70c4fdfb161ecdb6daa2) for installing Python 3.5 with `pyenv`. We do not recommend building it from source and installing it manually, [see here for an explanation as to why](https://wiki.debian.org/DontBreakDebian).

## 2. Clone

Now that the system dependencies out of the way, **run the following commands** to install the bot in your home directory and install the Python dependencies required:

```sh
cd ~
git clone https://github.com/Just-Some-Bots/MusicBot.git MusicBot -b master
cd MusicBot

# If you are using Debian Jessie with pyenv
sudo -H python -m pip install --upgrade -r requirements.txt

# If you are using Debian Stretch
sudo -H python3.5 -m pip install --upgrade -r requirements.txt
```

## 3: Configure
> **At this point you should [create a bot account](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

Inside the bot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as options.ini after editing**. If you need help, read the [configuration page](https://github.com/Just-Some-Bots/MusicBot/wiki/Configuration).

## 4: Start
You can start your bot by running this command:

```sh
# If you are using Debian Jessie with pyenv
python run.py

# If you are using Debian Stretch
python3.5 run.py
```