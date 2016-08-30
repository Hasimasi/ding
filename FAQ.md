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
**No**, but this is in the works.

### Can I modify the bot?
**Yes**, but please note that we will **not** help you during this process or if something breaks because of it. You can find help with the **discord.py library** that is used by MusicBot on the **Discord API server**: https://discord.gg/KZBHSxz.

> ***Any modifications are done at <u>your own risk</u>.***

### What does `SSL: CERTIFICATE_VERIFY_FAILED` mean?
You are **missing** an SSL certificate from a major authority. Download [this file](https://support.comodo.com/index.php?/Knowledgebase/Article/GetAttachment/969/821026) and install it on your system. Then shutdown the bot and start it again. **If you still have problems**, see [here](https://github.com/SexualRhinoceros/MusicBot/wiki#need-help).

### What does `[s16le @ 0x1926e60] Using AVStream.codec to pass codec parameters to muxers is deprecated, use AVStream.codecpar instead.` mean?
You can **ignore** this message. It doesn't affect your bot.

### What does `No module named 'musicbot'` mean?
Open your **main** `MusicBot` folder and find the folder inside named `musicbot`. **Make sure the name is all lowercase**.