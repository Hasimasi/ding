# Table of Contents

[Introduction](#introduction)  
1. [Step 1: Preparation](#step-1-preparation)  
2. [Step 2: Download and setup](#step-2-download-and-setup)  
3. [Step 3: Build the Docker image](#step-3-build-the-docker-image)  
4. [Step 4: Run the MusicBot](#step-4-run-the-musicbot)  

# Introduction

Docker is a way to virtualize the Musicbot. By using Docker you do not have to worry about any dependencies or whether it may run on your platform or not. Simply use the docker image and run the music bot.

# Installation

## Step 1: Preparation

The only requirement is that you have [Docker](https://docs.docker.com/mac/) installed. You do not require anything else. 

## Step 2: Download and setup

Download and navigate into the latest version of the MusicBot using the following command:

    git clone https://github.com/SexualRhinoceros/MusicBot.git 
    cd MusicBot

### 2.a: Change the configuration file

The configuration files are located in the `config` folder. There are two files, `example_options.ini` and `example_permissions.ini` that tell you how to configure the bot. You should copy and rename these files to `options.ini` and `permissions.ini` respectively, then edit them. 

![Music Bot Config Folder](http://i.imgur.com/GnzWRNG.png)

Open options.ini in a text editor of your choosing from the one you downloaded at the beginning of this guide. I suggest TextWrangler or Atom.

Configure the file however you want, it should explain everything you need. The two things you MUST change are the bot's Token and your OwnerID. Begin by making the following changes to the to these lines:

![Changing your options.ini](http://i.imgur.com/GoD8bGK.png)

![Getting your token](http://i.imgur.com/cN4YehO.png)

If you have any further questions, you can ask on the [help server](https://discord.gg/0iqN3da4zqpJpuY0).

## Step 3: Build the Docker image

From within the root project directory, run the following command:

      docker build -t musicbot .

This builds the Docker image for the music bot, and will take a few minutes to complete.

## Step 4: Run the MusicBot

From within the root project directory, run the following command:

      docker run -d -v $(pwd)/config:/musicBot/config musicbot

Your bot should now be running in the background!

To stop MusicBot, run the following command: 

      docker kill $(docker ps -q -f ancestor=musicbot)
  

Check out the [wiki article](https://github.com/SexualRhinoceros/MusicBot/wiki/Commands-list "Commands list") to learn how to use your bot!


