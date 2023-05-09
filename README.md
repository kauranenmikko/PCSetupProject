# PCSetupProject
A small salt project to setup a baseline PC for Linux and Windows.

## What is the aim

Debian comes with pretty much nothing installed. 

Windows comes with _too much_ crap installed.

The idea is to make a single script/file that will setup either a debian or a windows installation with programs that I will use, while also cleaning up unneeded stuff.

## Prerequisites

Salt installed on the system.

Sudo/Administrator rights on the target PC.

Windows might require Pro/Enterprice version.

## Changes made

### Installed software:

```
Steam
Blender
VirtualBox
Wine (Linux, windows "emulation" for games)

```

### Other changes

#### Linux

```
Enables UFW
Opens port 22 for SSH


```

#### Windows
```
Disabled Cortana
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


