# 200 - Setup and Installation

See also https://www.remotion.dev/docs

## 100 - Prerequisites

The only dependencies for Remotion are FFMPEG and Node.js.

Please read these guides to install them in case you haven't yet.

- [Installing FFMPEG](https://github.com/adaptlearning/adapt_authoring/wiki/Installing-FFmpeg) - Supported: >=4.1.0, >5.0.0
- [Installing Node.js](https://nodejs.org/en/download/) - Minimum: Version 12.10.0

**NOTE**: For ``ffmpeg`` to be found from the PATH environment variable on Windows in Visual Studio Code, add the following entry in Visual Studio Code file:

```
{
    ...
    "terminal.integrated.env.windows": {
        "PATH": "${env:PATH}"
    },
    ...
}
```
settings.json

Replace ```windows``` by ```osx``` or ```linux``` depending on which OS your Visuasl Studio Code is running.

Restart your Visual Studio Code integrated Terminal and test access to the PATH environment variable as follows:

For PowerShell:
```
$ echo $env:PATH
```

For bash:
```
$ echo "$PATH"
```

Add from within the Visual Studio Code intergrated Terminal (PowerShell) the following (adjust the path to refer to your settings, here 'C:\ffmpeg\bin'):

```
$ $ffmpeg = 'C:\ffmpeg\bin'
```

Check if ```ffmpeg``` can be found as follows:

```
$ ffmpeg -version
```

You should see something like this:

```
ffmpeg version 5.0-full_build-www.gyan.dev Copyright (c) 2000-2022 the FFmpeg developers
built with gcc 11.2.0 (Rev5, Built by MSYS2 project)
...
```

## 200 - Installation

You can initialize a new Remotion video using:

- npm:

```
$ cd containers/app
$ npm init video
```

OR

- yarn:

```
$ cd containers/app
$ yarn create video
```

OR

- pnpm:

```
$ cd containers/app
$ pnpm dlx create-video
```

That's it! Wait for the installation to be finished and follow the instructions in the terminal.

You will be asked: "What would you like to name your video?"

Answer: ```remotion```

You will be asked: "Choose a template:"

Choose: ```Hello World: The default starter template (recommended)```

A new directory "```remotion```" will have been created, inside of which are the files and directories required by Remotion.

### 100 Additional step for Linux users

Linux users need to install some additional packages to get Chrome/Puppeteer working correctly.

**Ubuntu**

```
$ apt install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget libgbm-dev
```

**Arch linux**

```
$ sudo pacman -S dconf alsa-lib atk glibc cairo libcups dbus expat fontconfig gcc gdk-pixbuf2 glib2 gtk3 nspr pango gcc-libs libx11 libxcomposite libxcursor libxdamage libxext libxfixes libxi libxrandr libxrender libxss libxtst ca-certificates ttf-liberation libappindicator-gtk3 nss lsb-release xdg-utils wget mesa
```
