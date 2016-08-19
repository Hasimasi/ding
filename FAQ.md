## How do I get an ID of ___?
Do these in any Discord text channel that you can view/post messages in.

* **User** (for `OwnerID` in the config): `\@yourname` (e.g: User `Jayden` would do `\@Jayden`).
* **Text channel**: `\#channelname` (e.g For `#musicbothelp`, I'd do `\#musicbothelp`).

In the newest versions of the Discord Client, you can also obtain the IDs of Users, Servers, and Channels through enabling "Developer Mode" in User Preferences (Appearance) and Right Clicking, Selecting "Copy ID".

Alternatively, **or for other IDs**, run the MusicBot and do the command `!listids`. 

## How do I update the bot?
1. Open Git Bash (Windows) or a Terminal window (Linux/OSX) in your MusicBot folder.
2. Run the following command: `git pull`

As long as you have setup Git properly, this will work. If you downloaded the bot's ZIP archive instead of installing it through Git, just re-download it, extract it to the same place, and replace all of the files if prompted.

## How do I play a YouTube playlist?
Just use the playlist link. You need to use the actual playlist URL though, not a song from the playlist.
- Good: `!play https://www.youtube.com/playlist?list=PLC0A615438E62547A`
- Bad: `!play https://www.youtube.com/watch?v=gbv-yqqmLH0&list=PLC0A615438E62547A`

## Does it work with Spotify?
No, and it probably never will. This is because per **Section 8** of Spotify's [Terms and Conditions of Use](https://www.spotify.com/uk/legal/end-user-agreement/#s8), "ripping" or broadcasting music to the public that originates from their service is prohibited. Additionally, Spotify do not provide an API for playing full tracks, only 30 second samples - nor does `youtube-dl` support them.

You can convert your Spotify playlists to YouTube ones using a service like [PlaylistBuddy](http://www.playlistbuddy.com/).

## Can it play streams?
No. MusicBot downloads music before playing it, and therefore streams such as Twitch are not playable.

## What sites are supported?
MusicBot uses `youtube-dl`. For a list of supported sites, see [youtube-dl supported sites](https://rg3.github.io/youtube-dl/supportedsites.html).

## Can the bot be in multiple voice channels?
* If you use a `Bot` account to run the MusicBot, it can join **one voice channel per server**.
* If you use a normal User account, it can only join **one voice channel** at a time.

## How do I create a `Bot` account?
Read the documentation on bot accounts over at the [Discord developers site](https://discordapp.com/developers/docs/intro). We won't provide much help for making these accounts.

### How do I make it join my server?
Again, read the documentation. You will need to generate an OAuth URL using your client ID.