# PCSetupProject
A small salt project to setup a baseline PC for Linux and Windows.

## What is the aim

This is a small personal project to install some software via salt on debian and windows, while also attempting to clean up windows settings and remove some unwanted software.

This is _NOT_ meant as a absolute way to remove every bad thing from Windows, but more of a proof on concept type personal project.

The file can be used either locally or applied to slaves. 

## Prerequisites

Salt installed on the system.

Sudo/Administrator rights on the target PC.

Windows might require Pro/Enterprice version. Tested on Windows 10 and Windows 11.

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


