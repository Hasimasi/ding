## Credentials

Public Bots (Bots that run on more than just your personal servers) must use a Discord Developer Bot Account or risk getting shutdown by the Discord Developers.  To use the bot with a bot account, you must supply a bot token, which can be obtained through [creating a bot user](https://discordapp.com/developers/applications/me).  The token key is the third key in the configuration file (options.ini)

    Token = bot_token

However, the bot can also be used with a standard Discord Account on personal servers.  If you choose to use a User Account with the bot, you must supply the bot account's username and password 

    [Credentials]
    Username = your_bots_email@foo.com
    Password = bots_pass     
***Note:*** *While this is still a viable option we are recommending using an oAuth BOT application instead as this is what the Discord dev's are wanting bot accounts to use.*

## Permissions

You need your id, not the bot's id.  The bot does not own the bot, you do.
If you don't know how to get this, join the help server (link in the readme) *with the owner's account* and type !id in chat. You should get something along the lines of: 
> OwnerName's ID is 12300000000000789

    [Permissions]
    OwnerID = 123...789

## Chat

Change this if you don't want commands to trigger another bot on the same server. Ex: One bot uses ~play, ~skip, etc and you want your bot to use !play, !skip, etc.  
    
    [Chat]
    CommandPrefix = !
   
This means you would type !play, !skip, etc.  
This explanation exists because it seems no one knows what **pre**-fix means.  
  
You can restrict the bot to only listen to certain text channels. By default, it will listen on all channels in the server its in.  
To find the text channel(s) you want you bot to listen on, go to the server and simply right click on the text channel and copy link. It should look like:
> discordapp.com/channels/129488835553334912/143335558889992656  

Copy and paste the **second** set of numbers, and separate multiple text channels with single spaces.  
*Uncomment (remove the ; at the start of the line) and add channel IDs to enable.*  

    ;BindToChannels = 

In the `review` version of the bot, you can make the bot autojoin voice channels on start. If you are using a bot account, the bot can join multiple voice channels (one per server). To get an ID of a voice channel, use `!listids`.
*Uncomment (remove the ; at the start of the line) and add channel IDs to enable.*  

    ;AutojoinChannels =

## MusicBot

The starting volume of the bot. Scale of .01 to 1.0, 1.0 being 100% volume.  

    [MusicBot]
    DefaultVolume = 0.45  

Skips required to skip a song.  Whichever is lower will be used.  
Skip ratio refers to the percent of non-deafened, non-owner users in the voice channel needed to skip a song.  

    SkipsRequired = 4
    SkipRatio = 0.5

If no, deletes videos after they have been played. If the video is still in the queue after playing, the bot will avoid redownloading.  

    SaveVideos = yes  

Mentions the user who queued a song when the song plays.  
  
    NowPlayingMentions = no  

On startup, if the owner is in a voice channel, join that channel. Auto joining a server without the owner being online  is being worked on.  

    AutoSummon = yes

Play random songs out of included playlist when nothing is queued.  

    UseAutoPlaylist = yes

Debug prints extra output in the console and some errors to chat.  
This option is a work in progress, don't expect much.  

    DebugMode = no