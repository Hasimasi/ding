<p align="center">
<img src="http://i.imgur.com/Xluk1hv.png">
</p>

The bot is **open source**. This means that you can edit, and modify the **Python** code to do what you want with it. **We are totally fine with this** - but please note we will not help you in our help server on Discord, if your problem appears to be directly caused by your changes.

As a small guide, we've written some information below about modifying the bot. The bot uses the libraries `youtube-dl` and `discord.py` to download and stream media, as well as interact with Discord.

General notes:

* **IMPORTANT - You should read [discord.py's documentation](http://discordpy.readthedocs.io/en/latest/api.html)**
* **The class `MusicBot` is a subclass of [discord.Client](http://discordpy.readthedocs.io/en/latest/api.html#client) so you should use `self` when using [discord.Client](http://discordpy.readthedocs.io/en/latest/api.html#client) functions inside the class in `bot.py`**
* **Most functions are a [coroutine](http://discordpy.readthedocs.io/en/latest/faq.html#what-is-a-coroutine), so you should insert the `await` keyword before using it**

***

The following utility functions can be used in the `MusicBot` class (`bot.py`), which handle and deal with exceptions properly.

* [safe_send_message](https://github.com/SexualRhinoceros/MusicBot/blob/master/musicbot/bot.py#L470) (in substitute of discord.py's `send_message`)
* [safe_edit_message](https://github.com/SexualRhinoceros/MusicBot/blob/master/musicbot/bot.py#L503) (in substitute of discord.py's `edit_message`)
* [safe_print](https://github.com/SexualRhinoceros/MusicBot/blob/master/musicbot/bot.py#L515) (in substitute of `print` - handles Unicode issues)

## Adding a command
Our command framework is easy enough to work with. To create a new command, define a new **asynchronous function** that starts with the `cmd_` prefix. It accepts the following arguments (which will be passed by the event `on_message`):

* `message` - The [Message](http://discordpy.readthedocs.io/en/latest/api.html#message) that triggered the command
* `channel` - The [Channel](http://discordpy.readthedocs.io/en/latest/api.html#channel) that the command was triggered in
* `author` - The [Member](http://discordpy.readthedocs.io/en/latest/api.html#member) that triggered the command
* `server` - The [Server](http://discordpy.readthedocs.io/en/latest/api.html#server) that the command was triggered in
* `player` - The MusicPlayer (see `MusicBot/player.py`) associated with the server (if available)
* `permissions` - The [Permissions](http://discordpy.readthedocs.io/en/latest/api.html#permissions) that the user has
* `user_mentions` - A list of all [Members](http://discordpy.readthedocs.io/en/latest/api.html#member) mentioned in the message
* `channel_mentions` - A list of all [Channels](http://discordpy.readthedocs.io/en/latest/api.html#channel) mentioned in the message
* `voice_channel` - The voice [Channel](http://discordpy.readthedocs.io/en/latest/api.html#channel) the bot is in on the server (if available)
* `leftover_args` - A list of the arguments given with the command that **aren't required** arguments

Notes about commands:

* **Docstrings are used when using `!help command` or when a user doesn't use the command correctly (e.g missing arguments)**

### Example: Ping command

```py
    async def cmd_ping(channel):
        """
        Usage:
            {command_prefix}ping
        Ping command to test latency
        """
        await self.safe_send_message(channel, "Pong!")
```

### Example: Send a message to all servers

```py
    async def cmd_sendall(args, leftover_args):
        """
        Usage:
            {command_prefix}sendall <message>
        Sends a message to all servers the bot is on
        """
        if leftover_args:
            args = ' '.join([args, *leftover_args])
        for s in self.servers:
            await self.safe_send_message(s, args)
```

***

If you have issues with and need help with the **discord.py library** that is used by MusicBot, you can join the Discord API server by clicking the banner below:

[![Discord](https://discordapp.com/api/guilds/81384788765712384/widget.png)](https://discord.gg/KZBHSxz)

**Reminder: We will not provide help on OUR help server for issues with modifying the bot**