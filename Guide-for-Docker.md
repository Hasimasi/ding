<p align="center">
<img src="http://i.imgur.com/L6WQOD2.png">
</p>

<h1 align="center">Docker</h1>

## 1: Clone
The only requirement is that you have [Docker](https://docs.docker.com/mac/) installed. You do not require anything else. **Download and navigate into the latest version of the MusicBot using the following commands**:

    git clone https://github.com/SexualRhinoceros/MusicBot.git MusicBot -b master
    cd MusicBot

## 2: Configure

> **At this point you should [create a bot account](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

The folder we're in contains all of the bots files. **Do not delete or rename any files/folders**. We now need to configure the bot.

Inside the bot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as options.ini after editing**. If you need help, read the [configuration page](https://github.com/SexualRhinoceros/MusicBot/wiki/Configuration).

## 3: Docker Image
From within the root project directory (named `MusicBot`), run the following command to build the docker image:

    docker build -t musicbot .

## 4: Start

Now run the following command to start the bot:

    docker run -d -v $(pwd)/config:/musicBot/config musicbot

To stop MusicBot, run the following command: 

    docker kill $(docker ps -q -f ancestor=musicbot)