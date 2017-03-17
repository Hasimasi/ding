MusicBot is available under the [MIT License](https://choosealicense.com/licenses/mit/). You are free to fork the repository and modify the bot as you see fit. This page serves as a starting point to doing so, and some general guidance.

## Prerequisites
* Python 3.5 or higher
* A development environment. This can be a full-fledged Python IDE, such as [PyCharm](https://www.jetbrains.com/pycharm/). Since the development we will be doing is fairly light, using an advanced text and code editor such as [Atom](https://atom.io/) works too
* Basic knowledge of Python development. If you don't know the basics of Python, do not try and modify this bot
* Knowledge of `asyncio` and the asynchronous features introduced in Python 3.5 are **very important**
* Knowledge of [`discord.py`](https://github.com/Rapptz/discord.py). Documentation is here: http://discordpy.readthedocs.io/en/latest/api.html

## Structure
* `bot.py` contains the main class, `MusicBot`, along with all commands and Discord integration.
* `config.py` and `permissions.py` use the standard Python library `configparser` to read from `config.ini` and `permissions.ini` respectively.
* `downloader.py` is the main wrapper for [`youtube-dl`](https://github.com/rg3/youtube-dl).
* `player.py` contains the various classes that allow for the bot to play music and maintain queues on each server.
* `playlist.py` is for managing and processing media for queues.
* `utils.py` contains various utility functions.

## Command framework
MusicBot currently uses its own command framework, rather than discord.py's command extension module. In the main MusicBot class, if a function begins with `cmd_`, it becomes detectable to the bot as a command, and will show up in `!help` and elsewhere. Therefore, the following code will be a command:

```py
async def cmd_test(self):
    print("Hello, world!")
```

Adding this within the class and using `!test` will print a message to the console. However, it won't print a message to Discord. That is instead done by returning a [Response](https://github.com/Just-Some-Bots/MusicBot/blob/master/musicbot/bot.py#L60).

```py
async def cmd_test(self):
    return Response("Hello, world!")
```

This code will send a message to the Discord channel that the command was called from, saying `Hello, world!`. Take note of the various parameters that can be provided to the Response class, such as `reply`, which when passed as `True` will mention the user who called the command before the message, and `delete_after`, which is an integer that can be passed indicating how long after the message is sent should it be deleted.

There are a number of [parameters](https://github.com/Just-Some-Bots/MusicBot/blob/master/musicbot/bot.py#L1859-L1887) that can be passed to command functions for use within them. For example, passing `channel` will allow you to use the [Channel](http://discordpy.readthedocs.io/en/latest/api.html#channel) object associated with the invoking message (the message that called the command). Example:

```py
async def cmd_test(self, channel):
    return Response("Hello, {}".format(channel.name))
```

A final thing to note is that the docstring of a command function becomes its "help text". This is shown when doing `!help <command>`, or if the command is used incorrectly (an incorrect number of arguments is passed). Example:

```py
async def cmd_test(self, channel):
    """
    Sends a test message to the channel
    """
    return Response("Hello, {}".format(channel.name))
```

### Examples
There are a few of example commands that aren't currently in the bot for you to look at it, and implement yourself if you desire.

* [Simple ping command](https://gist.github.com/jaydenkieran/8cf64f91fec73ba0bd127a08f6578988)
* [Send a message to all bot's servers](https://gist.github.com/jaydenkieran/c18ddef3817c58ad1cbb6018d33790eb)
* [Leave a server by ID](https://gist.github.com/jaydenkieran/96ae5633dec9ea87c70c48ab191413ed)

There is also an example of editing an existing command:

* [Broadcast restarts to all servers](https://gist.github.com/jaydenkieran/01a91e5270bbf0daf3884c60eb161329)

## Helper functions

MusicBot wraps various functions of discord.py in the MusicBot class in order to handle exceptions, so you should use these instead of their discord.py counterparts:

* `safe_send_message` (instead of `send_message`)
* `safe_edit_message` (instead of `edit_message`)
* `safe_delete_message` (instead of `delete_message`)

When printing to console, it is advised to use the MusicBot class function [`safe_print`](https://github.com/Just-Some-Bots/MusicBot/blob/master/musicbot/bot.py#L515) instead of Python's default `print`. This avoids any potential UnicodeDecodeErrors.

## Resources

The bot utilises [`youtube-dl`](https://github.com/rg3/youtube-dl) to download media. Information on the various options that can be provided to the library are available in the README file on youtube-dl's repository. If you want to edit the way that downloading media or extracting information about it works, you should read through the source.

Music is streamed to Discord using [`ffmpeg`](https://ffmpeg.org/). The documentation for ffmpeg is available here: https://ffmpeg.org/ffmpeg.html.

## Support

❗️ We **do not** provide support for modifying MusicBot, other than the guidance on this page. If you break something, that is your problem to fix, not ours. If, however, you need support with using the discord.py library which the bot utilises (such as the various [Client functions](http://discordpy.readthedocs.io/en/latest/api.html#client)), then you can find support on the [Discord API server](http://discord.gg/discord-api).