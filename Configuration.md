<p align="center">
<img src="http://i.imgur.com/lUGD3uG.png">
</p>

This page gives information on how to **configure** the MusicBot. When you install the bot, you will get a file inside the `config` folder named `example_options.ini`. You should open this file, **configure the options within**, and then **save it as a new file** called `options.ini`.

If the bot does not detect the `options.ini` file when it starts, then it will automatically copy it into your folder. **For Windows users**, please note that file extensions are **hidden by default**, so you may just need to save the file as `options` if you are having difficulty - the `.ini` may be hidden.

**Do not edit any configuration file using Notepad or other basic text editors, otherwise it will break. Use something like [Notepad++](https://notepad-plus-plus.org/download/)** (Windows) **or [Atom](https://atom.io/)** (Windows/Mac/Linux).

***

## Credentials

If you are using a **normal user account** for your bot, add a **semi-colon** at the start of the `Token =` line and **remove** the semi-colons at the start of the the lines for `Email =` and `Password =`. You should enter the accounts email and password after the equal signs of the appropriate lines. For example:

    ;Token =
    Email = hello@hello.com
    Password = test

If you are using a **bot account**, which you **should be using**, you **do not** have to change anything from the example options file. The `Token =` line should **not** have a semi-colon at the start, while the `Email =` and `Password =` line should. You should enter the bot account's **token** after `Token =`. For example:

    Token = MTc0ODcyPOWyNzg3MzYzODQx.DlaYdr.9PuLx1x9LAS979axVXTVfrRE5nL

<p align="center">
<img src="http://i.imgur.com/Y0GXcJQ.png">
</p>

## Permissions

### OwnerID
> **Read [this section](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-get-an-id) of the FAQ to learn how to obtain an ID**

This is the ID of your **Discord user**. Example:

    OwnerID = 154748625350688768

This is **not** the bot account itself. The owner should be **you**. This is the person that will have all permissions and ultimate control over the bot. **There cannot be multiple owners - use [permissions](https://github.com/SexualRhinoceros/MusicBot/wiki/Permissions/) for that**.

## Chat

### CommandPrefix

This is the **prefix** that will be used in commands. For example, if my prefix was `!`, then the `play` command would be used by typing `!play`. If my prefix was `#`, I'd use `#play` instead. Example:

    CommandPrefix = !

### BindToChannels

> **Note:** To use this option, **uncomment it** (remove the semi-colon at the start of the line)

> **Read [this section](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-get-an-id) of the FAQ to learn how to obtain an ID**

If you want your bot to **only work and reply in certain text channels**, this is the option you use. You should enter the IDs of each channel that you want the bot to listen to. Example:

    BindToChannels = 129489631539494912

### AutojoinChannels

> **Note:** To use this option, **uncomment it** (remove the semi-colon at the start of the line)

> **Read [this section](https://github.com/SexualRhinoceros/MusicBot/wiki/FAQ#how-do-i-get-an-id) of the FAQ to learn how to obtain an ID**

If you want your bot to **automatically join voice channels**, this is the option you use. You should enter the IDs of each voice channel that you want you bot to join when it is started. If you are using a **bot account**, you can enter multiple IDs for multiple servers (**one voice channel per server**). Example:

    AutojoinChannels = 129489636056629248

## MusicBot

### DefaultVolume

This is the **default volume** that your bot will play music at when it is started. This can be **any value** between `0.01` and `1.0`. The **recommended volume** is `0.15`.

### WhiteListCheck

This decides whether or not the bot can **only** be used by **whitelisted users**. This feature is deprecated, and we won't provide much help for it. Use [permissions](https://github.com/SexualRhinoceros/MusicBot/wiki/Permissions/) instead. **To set up which users are whitelisted**, put their IDs in the `whitelist.txt` file in the `config` folder (one per line).

### SkipsRequired & SkipRatio

This decides the **required amount of votes** needed for a song to skip. The lower value out of `SkipsRequired` or `SkipRatio` will be used. Skip ratio refers to the percentage of **non-deafened**, **non-owner** members in a voice channel.

### SaveVideos

This option decides whether **songs should be saved**. Turning this on will **sacrifice disk space** in favour of saving bandwidth, while having it off will **use more bandwidth**. If a song is **saved** (also known as 'cached'), the bot will play the saved version instead of downloading it again.

### NowPlayingMentions

This option decides if the bot should **mention the user that requested a song** when their song is played.

### AutoSummon

This option decides if the bot should **automatically join the owner's voice channel**. The owner is the user defined in the `OwnerID` option previously. If this option and `AutojoinChannels` is enabled (and the option has an ID that is in the same channel as the owner), the bot will **join the owner's channel** instead.

### UseAutoPlaylist

This option decides if the bot should play the **default playlist of music** after joining a voice channel. This playlist is defined in the `autoplaylist.txt` file. One link should be entered **per line** in this file.

### AutoPause

This option decides if the bot should **pause playing music if there is nobody else in the channel**.

### DeleteMessages

This option decides if the bot should **delete its own messages** after a period of time.

### DeleteInvoking

This option decides if the bot should **delete other user's messages that triggered a bot response** after a period of time. You need to have `DeleteMessages` enabled for this.

### DebugMode

Turning this option on will **print additional debug information** to the console, for use when there are issues and errors that should be reported.