<p align="center">
<img src="http://i.imgur.com/iVHLcAU.png">
</p>

### How do I create a bot account?
1. Go to the [Discord developers](https://discordapp.com/developers/applications/me) page
2. Click **New Application**
3. Give your bot a **name** and an **icon**, then press **Create Application** (leave other fields blank)
4. On the next page, click **Create a Bot User**
5. Next to **Token**, click **Click to reveal** to see your token
6. Enter your token inside the **configuration file** for the bot. Need help? [See here](https://github.com/SexualRhinoceros/MusicBot/wiki/Configuration#credentials)

<p align="center">
<img src="http://i.imgur.com/cN4YehO.png">
</p>

### How do I add my bot account to a server?
> **Note**: You can only add a bot account to a server that you have **Manage Server** permissions on.

The link to add your bot account to a server is **provided in the console window** when you **run the bot and it is not on any servers**.

**To get this link manually**, go to the [Discord developers](https://discordapp.com/developers/applications/me) page and click on your **application**. At the top, you will find the bot account's `Client ID`.

    https://discordapp.com/oauth2/authorize?&client_id=<CLIENT ID>&scope=bot&permissions=0

Replace `<CLIENT ID>` in the link above with the Client ID from your application page, and then go to the URL on a browser. There, you'll be able to add it to servers.

### How do I get an ID?
**To get IDs**, turn on Developer Mode in the Discord client (`User Settings` -> `Appearance`) and then right-click your name/icon **anywhere** in the client and select `Copy ID`.

**For role IDs**, you instead need to start the bot and use the command `!listids`. Role IDs aren't obtainable using Developer Mode.

<p align="center">
<img src="http://i.imgur.com/GhKpBMQ.gif">
</p>

### What sites can the bot play music from?
The bot uses **youtube-dl**. View [list of supported sites](https://rg3.github.io/youtube-dl/supportedsites.html).

### Does the bot support Spotify, Deezer, etc?
**No**. This is mostly because it violates the Terms of Service agreements of those services.

### Does the bot support Twitch and other streams?
**No**, but it will very soon.

### Can the bot play music that's already on my computer?
**No**, but it will very soon.

### Can I modify the bot?
**Yes**, but please note that we will **not** help you during this process or if something breaks because of it. You can find help with the **discord.py library** that is used by MusicBot on the Discord API server by clicking the banner below:

[![Discord](https://discordapp.com/api/guilds/81384788765712384/widget.png)](https://discord.gg/KZBHSxz)

### What license does the bot use?
The bot is licensed under the **MIT License**.