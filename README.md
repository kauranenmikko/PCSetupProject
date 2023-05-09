# PCSetupProject
A small salt project to setup a baseline PC for Linux and Windows.

## What is the aim

Debian comes with pretty much nothing installed. 

Windows comes with _too much_ crap installed.

The idea is to make a single script/file that will setup either a debian or a windows installation with programs that I will use, while also cleaning up unneeded stuff.

## Prerequisites

Salt installed on the system.

Sudo/Administrator rights on the target PC.

Windows might require Pro/Enterprice version. Also this will be tested and done on Windows 10, 11 probably works (if the packages are available) but there might be issues with registry/Group Policies.

## Changes made

### Installed software:

```
Steam
Blender
VirtualBox
Wine (Linux, windows "emulation" for games)
FireFox


```

### Other changes

#### Linux

```
Enables UFW
Opens port 22 for SSH


```

#### Windows
```
Disable Cortana
Disable telemetry
Disable fast start-up
Disable windows tips
Disable Cloud Content
Disable MS ""consumer experience""
Disable MS Store
Uninstall pre-installed bloatware/games
Install PowerToys

```
## Instructions


