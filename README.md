# PCSetupProject
A small salt project to setup a baseline PC for Linux and Windows.

## What is the aim

This is a small personal project to install some software via salt on debian and windows, while also attempting to clean up windows settings and remove some unwanted software.

This is *NOT* meant as a absolute way to remove every bad thing from Windows, but more of a proof on concept type personal project.

The file can be used either locally or applied to slaves. 

## Prerequisites

Salt installed on the system. (Links below)

Sudo/Administrator rights on the target PC.

Windows might not work in Home/Education editions.

## Changes made

### Installed software:

#### Linux
```
Steam
Blender
Wine (Linux, windows "emulation" for games)
micro
ufw
```

#### Windows
```
Notepad++
GIMP
Firefox
Discord
GOG Galaxy
blender
7zip
git
PuTTY
```

### Other changes

#### Linux
```
ufw:
Opens following ports/protocol

22/tcp
80/tcp
4505/tcp
4506/tcp
```

#### Windows
```
Disable Windows tips
Deny local login
Turn off cloud optimized content
Disable drivers with Windows Updates
Disable the use of biometrics
Set minimum password length
Make sure the setting for "store passwords using reversible encryption" is set to Disabled
Disable OneSettings Downloads
Disable "show feedback notifications"
Turn off hybrid sleep (plugged in)
Turn off the advertising ID
Changes hosts file to included hosts file. Obtained from https://winhelp2002.mvps.org/hosts.txt 
```

## Instructions

For the sake of simplicity, these instructions will go over a local installation only.

Salt for Windows: https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/windows.html#install-windows

Salt for Debian: `sudo apt-get install salt-minion` (salt-minion and salt-master both work for this, salt-master uses `salt`, salt-minion `salt-call`)

For other systems please refer to the salt install documents (https://docs.saltproject.io/salt/install-guide/en/latest/)

Grab the files found in this repo, or at the very least the folder PCSetup and the files inside it.

### Windows

Windows requires Git for salt package management to work. Fastest way is to just use PowerShell and winget, `winget install Git.Git` will install Git on your machine, or you can get it from their repo https://github.com/git-for-windows/git/releases/ . If you used PowerShell close it after the installation, at the latest before trying to run salt-call commands, because it will not recognize the commands otherwise (or you have to run the commands from the salt install directory with .\salt-call).

Download the salt installer (.exe or .msi doesn't really matter). Run the installer. If the installer asks about missing vcredist package, select to install it.

Since this is a local config we can just go with the default settings, so basically just press next until the software is installed.

Afterwards open PowerShell as Administartor. In powershell, run the command `salt-call --version` just to check that it's actually installed. You should see `salt-call 3004.2` or similar output.

Update the Salt Windows package repository `salt-call --local winrepo.update_git_repos`

Update the related local database `salt-call --local pkg.refresh_db`

Now it's time to move the folder and it's contents into the proper location. For Windows the location is `C:\ProgramData\Salt Project\Salt\srv\salt`. After placing the folder there, you can run it by calling it by the folder name, in this case PCSetup (case sensitive).

In PowerShell, run the command `salt-call --local state.apply PCSetup` and wait, depending on device and internet speed it might take a while. You will see some of the programs open up their installers or autorun after their installation. After the installation is complete, you will see a report on the actions performed.

______

### Debian

Debian has next to no prerequisites as far as this installation is concerned.

Install salt `sudo apt-get update && sudo apt-get install salt-minion`

You can test the installation with `salt-call --version`

Download the files from this repo. 

The folder PCSetup and it's contents need to be copied to /srv/salt/ directory.

From terminal, cd your way the downloaded folder. Copy the PCSetup folder and it's contents into /srv/salt/ `sudo cp -R PCSetup /srv/salt/`

Now you can run it with `sudo salt-call --local state.apply PCSetup`. This can take a while (10+ minutes) and the finished output can be _very long_ due to wine and blender combined installing something closer to a 1000 different packages and dependencies.

If you get a error here, likely something akin to `No matching sls found for PCSetup in env base` you're missing either the directory from /srv/salt/ (so it has only the init.sls and hosts files), the directory contents (PCSetup exists but is empty), or they're both missing from that location (_or_ you've changed the default salt base location)

## After installation and salt-call run

You can (and possibly should) remove the salt-minion or salt-master installations if you have no further use for them.


______


## Sources used:

https://terokarvinen.com/2018/configure-windows-and-linux-with-salt-jinja-if-else-and-grains/

https://stackoverflow.com/questions/41479482/how-do-i-allow-a-salt-stack-formula-to-run-on-only-certain-operating-system-vers

https://docs.saltproject.io/en/latest/topics/development/conventions/formulas.html#abstracting-static-defaults-into-a-lookup-table

https://docs.saltproject.io/en/latest/ref/states/all/salt.states.pkg.html

https://wiki.debian.org/Steam

https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/

https://docs.saltproject.io/en/latest/ref/states/all/salt.states.reg.html

https://learn.microsoft.com/en-us/windows/package-manager/winget/

https://docs.saltproject.io/en/latest/ref/states/all/salt.states.win_lgpo.html

https://winhelp2002.mvps.org/hosts.txt

dpkg man page
