<p align="center">
<img src="http://i.imgur.com/H3c2tJ8.png">
</p>

<h1 align="center">Windows 7 and above</h1>
<p align="center">Some information may not be applicable to older versions of Windows.</p>

## 1: Dependencies
The bot requires **other software** installed on your Windows computer to run successfully.

### 1.a: Python
To install the correct version of Python, click on the link for the version that is right for your system.

* 32-bit: https://www.python.org/ftp/python/3.5.1/python-3.5.1.exe
* 64-bit: https://www.python.org/ftp/python/3.5.1/python-3.5.1-amd64.exe

If you don't know your system's architecture, see this [How-To Geek article](http://www.howtogeek.com/howto/21726/how-do-i-know-if-im-running-32-bit-or-64-bit-windows-answers/).

**Run the setup program** by double-clicking it. You'll go through a series of prompts. **Make sure you check the boxes**:

* `Install launcher for all users (recommended)`
* `Add Python 3.5 to PATH`

At the end of the installation, click **Close** to exit the setup wizard.

### 1.b: Git
Git is needed to download the bot from GitHub. We will **only help you in future** if you download the bot using this method, as it is required to easily update the bot when needed.

* Download Git for Windows here: <https://git-for-windows.github.io/>

**Run the setup program** by double-clicking it. You'll go through a series of prompts. **Make sure you check the boxes**:

* `Use Git from Git Bash only` (under **Adjusting your PATH environment**)
* `Checkout Windows-style, commit Unix-style endings` (under **Configure the line ending conversions**)
* `Use MinTTY (the default terminal MSYS2)` (under **Configuring the terminal emulator to use with Git Bash**)

At the end of the installation, you will **be able to use Git Bash** by **right-clicking a folder** and selecting `Git Bash` (or `Git Bash Here`) from the menu.

## 2: Clone
Open **Git Bash** (as explained at the end of the last section) and enter the following command to **clone** (download) the MusicBot.

    git clone https://github.com/Just-Some-Bots/MusicBot.git ~/MusicBot -b master

After using this command, a folder called `MusicBot` will be added inside your Windows user's directory (usually `C:/Users/<name>`).

## 3: Configure
> **At this point you should [create a bot account](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-create-a-bot-account) and [add it to your server](https://github.com/Just-Some-Bots/MusicBot/wiki/FAQ#how-do-i-add-my-bot-account-to-a-server)**.

**Open** the folder that was created, called `MusicBot`. The folder contains all of the bots files. **Do not delete or rename any files/folders**.

Inside the bot's folder is another folder called `config`. Open it, and then open the `example_options.ini` file. This is the file containing the **bot's settings**. All options are explained in the file. **Make sure you save the file as options.ini after editing**. If you need help, read the [configuration page](https://github.com/Just-Some-Bots/MusicBot/wiki/Configuration).

## 4: Run
> In some cases, your system may be missing an SSL certificate from a major authority, causing your requests while using the bot to fail. To avoid this, [install this certificate](https://support.comodo.com/index.php?/Knowledgebase/Article/GetAttachment/969/821026).

In the main folder (called `MusicBot`), **double-click** `update_deps.bat` to install the required Python dependencies. After it is finished, you can **close the window** and then **double-click** `runbot.bat` to run the bot.

If you **close** the Command Prompt, your bot will stop working. This window is required to be open for the bot to run. The bot will also stop if you turn your computer off, sleep, or hibernate it. To avoid these issues, you can buy a dedicated server.